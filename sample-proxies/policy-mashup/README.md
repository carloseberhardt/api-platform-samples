# Policy Composition Mashup

This sample "mashes up" two web services:

* The Google Geocoding web service
* The Google Elevation web service

It exposes an API that takes two query parameters:

* country: A two-letter country code
* postalcode: A postal code valid in that country

It returns a JSON result that includes the geocoded location for the center
of that postal code, and the elevation at that location.

It uses a series of policies in order to accomplish this:

1. An AssignMessage policy to generate the request for the geocoding web service
2. A ServiceCallout policy to call it
3. An ExtractVariables policy to parse the response and extract the latitude and longitude
4. An AssignMesage policy to set the parameters for the elevation service
5. An ExtractVariables policy to parse the elevation response
6. A Javascript policy to generate the response JSON from the variables set by the
previous policies.
7. A StatisticsCollector policy to send the values of "country" and "postalcode"
to Analytics for use in a custom report.

# Set up

* The username and password that you use to login to enterprise.apigee.com.
* The name of the organization in which you have an account. Login to 
  enterprise.apigee.com and check account settings.

# Configure 

Update /setup/setenv.sh with your environment details

# Import and deploy sample project

Run:

/setup/deploy.sh

Testing

$ sh invoke.sh

# Get help

For assistance, post to http://support.apigee.com

Copyright 2013 Apigee Corporation

Licensed under the Apache License, Version 2.0 (the "License"); you may not use
this file except in compliance with the License. You may obtain a copy
of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.