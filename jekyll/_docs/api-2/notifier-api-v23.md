---
layout: classic-docs
title: Notifier API v23
categories: [api-2]
last_updated: May 11, 2016
description: notifier API v23
---

Airbrake accepts error notifications via a RESTful XML API. Clients send XML data to Airbrake using an HTTP `POST` to `http://api.airbrake.io/notifier_api/v2/notices`. Airbrake also accepts notifications over HTTPS for accounts that support SSL.

If you're looking to read your existing data from Airbrake, and not send new data, you'll want to read up on the [Data API](http://help.airbrake.io/faqs/api-2/api-overview).

**iOS notifier**<br/>
If you are using the iOS notifier make sure you are using the most current version available.

* Pull the latest code from GitHub
* Push a new version of your application to the App Store
* If using [App Version](http://help.airbrake.io/kb/ios/app-versions) to ignore errors from previous versions update the [App Version Field](http://cl.ly/2d0A0b3T1y2E3S243M0c) in the [Edit This project](http://cl.ly/1Q3h3P3e3B0n3U1x1i2F) section of your iOS app.

**Content Type**<hr/>

All error notification requests should set a content type of "text/xml." Other content types will not be processed.

**Schema**<hr/>

Airbrake validates incoming XML using an XSD schema, available at http://airbrake.io/airbrake_2_3.xsd. When writing a notifier client, we recommend [**Validating XML**](http://www.xmlforasp.net/schemavalidator.aspx) in unit tests using the [**XSD schema**](http://airbrake.io/airbrake_2_3.xsd).

**Incoming Errors**<hr/>

Incoming errors should be described using XML in the POST body of the HTTP request. The available elements are described below. The elements are listed as xpath, so /notice/api-key means an api-key element underneath a notice element, and /notice/@version means the version attribute of the notice element.

*/notice/@version*

Required. The version of the API being used. Should be set to "2.3"

*/notice/api-key*

Required. The API key for the project that this error belongs to. The API key can be found by viewing the edit project form on the Airbrake site.

*/notice/notifier/name*

Required. The name of the notifier client submitting the request, such as "hoptoad4j" or "rack-hoptoad."

*/notice/notifier/version*

Required. The version number of the notifier client submitting the request.

*/notice/notifier/url*

Required. A URL at which more information can be obtained concerning the notifier client.

*/notice/error/class*

Required. The class name or type of error that occurred.

*/notice/error/message*

Optional. A short message describing the error that occurred.

*/notice/error/backtrace/line*

Required. This element can occur more than once. Each line element describes one code location or frame in the backtrace when the error occurred, and requires @file and @number attributes. If the location includes a method or function, the @method attribute should be used.

*/notice/request*

Optional. If this error occurred during an HTTP request, the children of this element can be used to describe the request that caused the error.

*/notice/request/url*

Required only if there is a request element. The URL at which the error occurred.

*/notice/request/component*

Required only if there is a request element. The component in which the error occurred. In model-view-controller frameworks like Rails, this should be set to the controller. Otherwise, this can be set to a route or other request category.

*/notice/request/action*

Optional. The action in which the error occurred. If each request is routed to a controller action, this should be set here. Otherwise, this can be set to a method or other request subcategory.

*/notice/request/params/var*

Optional. A list of var elements describing request parameters from the query string, POST body, routing, and other inputs. See the section on var elements below.

*/notice/request/session/var*

Optional. A list of var elements describing session variables from the request. See the section on var elements below.

*/notice/request/cgi-data/var*

Optional. A list of var elements describing CGI variables from the request, such as SERVER_NAME and REQUEST_URI. See the section on var elements below.

*/notice/server-environment/project-root*

Optional. The path to the project in which the error occurred, such as RAILS_ROOT or DOCUMENT_ROOT.

*/notice/server-environment/environment-name*

Required. The name of the server environment in which the error occurred, such as "staging" or "production."

*/notice/server-environment/app-version*

Optional. The version of the application that this error came from. If the App Version is set on the project, then errors older than the project's app version will be ignored. This version field uses [Semantic Versioning](http://semver.org/) style versioning.

*//var elements*

The params, session, and cgi-data elements can contain one or more var elements for each parameter or variable that was set when the error occurred. Each var element should have a @key attribute for the name of the variable, and element text content for the value of the variable.

**Success responses**<hr/>

The server will respond with a 200 OK response if the error is accepted. The response body will contain a notice

**Failure Responses**<hr/>

If Airbrake cannot create a notice, it will respond with a failure code and message. There are several possible failure responses:

 * 403 - the requested project does not support SSL - resubmit in an http request
 * 422 - the submitted notice was invalid - check the notice xml against the schema and ensure the API key is correct
 * 500 - unexpected errors - submit a bug report at http://help.airbrake.io

The response body for a failure will contain XML describing the error. The XML will have an errors root element with one or more error children, describing each error that occurred.

**Tracking deploys**<hr/>

When Airbrake receives a deploy notification, it will automatically set all errors on that environment to resolved. When new errors come in that get grouped with previously resolved errors, Airbrake will notify you via email and unresolve the entire group again.

If your plan supports deploy tracking, you can `POST` to `http://api.airbrake.io/deploys.txt`

The parameters supported are:

* `api_key` (required)
* `deploy[rails_env]`: (required). Which environment was just deployed to. For example, staging or production.
* `deploy[scm_repository]`: What's your version control repo's address.
* `deploy[scm_revision]`: What's the version control revision.
* `deploy[local_username]`: Who deployed?

The last three parameters are just used for displaying in the deploy history view.

**Error grouping**<hr/>

Airbrake groups similar exceptions into one error group. Errors are currently considered unique if all of the following are equal: the error class, the last file and line number in the backtrace, the controller and action, and the server environment name. This is subject to change and should not be depended on.

**Restrictions**<hr/>

For storage and performance reasons, Airbrake limits the size of incoming exceptions. The following restrictions are currently in place:

 * Error messages, files, components, actions, environment names, request URLs, and error class names are truncated after 255 characters.
 * Any incoming element with text content over 2 kilobytes will be truncated.
 * Only the first 2000 var elements will be accepted in notice XML. The rest will be discarded.

**Example Request and Response**<hr/>

@@@
$ cat example.xml
@@@

**Make sure the code below [validates](http://www.xmlforasp.net/schemavalidator.aspx) using our [XSD schema](http://airbrake.io/airbrake_2_3.xsd)!**

@@@ xml
<?xml version="1.0" encoding="UTF-8"?>
<notice version="2.3">
  <api-key>76fdb93ab2cf276ec080671a8b3d3866</api-key>
  <notifier>
    <name>Airbrake Notifier</name>
    <version>3.1.6</version>
    <url>http://api.airbrake.io</url>
  </notifier>
  <error>
    <class>RuntimeError</class>
    <message>RuntimeError: I've made a huge mistake</message>
    <backtrace>
      <line method="public" file="/testapp/app/models/user.rb" number="53"/>
      <line method="index" file="/testapp/app/controllers/users_controller.rb" number="14"/>
    </backtrace>
  </error>
  <request>
    <url>http://example.com</url>
    <component/>
    <action/>
    <cgi-data>
      <var key="SERVER_NAME">example.org</var>
      <var key="HTTP_USER_AGENT">Mozilla</var>
    </cgi-data>
  </request>
  <server-environment>
    <project-root>/testapp</project-root>
    <environment-name>production</environment-name>
    <app-version>1.0.0</app-version>
  </server-environment>
</notice>
@@@

@@@
$ curl -XPOST -H"Content-type: text/xml" --data-binary @example.xml http://api.airbrake.io/notifier_api/v2/notices
@@@

@@@ xml
<notice>
  <id>9ef134aa-2118-9e28-fc51-cd52ecf75b91</id>
  <url>http://airbrake.io/locate/9ef134aa-2118-9e28-fc51-cd52ecf75b91</url>
</notice>
@@@
