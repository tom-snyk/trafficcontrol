..
..
.. Licensed under the Apache License, Version 2.0 (the "License");
.. you may not use this file except in compliance with the License.
.. You may obtain a copy of the License at
..
..     http://www.apache.org/licenses/LICENSE-2.0
..
.. Unless required by applicable law or agreed to in writing, software
.. distributed under the License is distributed on an "AS IS" BASIS,
.. WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
.. See the License for the specific language governing permissions and
.. limitations under the License.
..

.. _to-api-profileparameter:

********************
``profileparameter``
********************
.. deprecated:: 1.1
	Use :ref:`to-api-profileparameters` instead.

``POST``
========
Create one or more profile/parameter assignments.

:Auth. Required: Yes
:Roles Required: "admin" or "operations"
:Response Type:  Object

Request Structure
-----------------
:paramIds:  An array of integral, unique identifiers for parameters which shall be assigned to the profile identified by ``profileId``
:profileId: The integral, unique identifier of a profile to which parameters will be assigned
:replace:   An optional boolean (default: false) which, if ``true``, will cause any conflicting profile/parameter assignments to be overridden.

.. code-block:: http
	:caption: Request Example

	POST /api/1.4/profileparameter HTTP/1.1
	Host: trafficops.infra.ciab.test
	User-Agent: curl/7.47.0
	Accept: */*
	Cookie: mojolicious=...
	Content-Length: 38
	Content-Type: application/json

	{
		"profileId": 18,
		"paramIds": [2, 3]
	}

Response Structure
------------------
:paramIds:  An array of integral, unique identifiers for parameters which have been assigned to the profile identified by ``profileId``
:profileId: The integral, unique identifier of a profile to which parameters have been assigned
:replace:   An optional boolean (default: false) which, if ``true``, caused any conflicting profile/parameter assignments to be overridden.

.. code-block:: http
	:caption: Response Example

	HTTP/1.1 200 OK
	Access-Control-Allow-Credentials: true
	Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept, Set-Cookie, Cookie
	Access-Control-Allow-Methods: POST,GET,OPTIONS,PUT,DELETE
	Access-Control-Allow-Origin: *
	Content-Type: application/json
	Set-Cookie: mojolicious=...; Path=/; HttpOnly
	Whole-Content-Sha512: N2ahnhEnfZ0UqnjylN6Vu3HaOZk340YuiuyiqkhTbk0pENp+kwBPYu4Z/sqBAloCfXSQaWlJzaeXw4uOD5heWw==
	X-Server-Name: traffic_ops_golang/
	Date: Mon, 10 Dec 2018 15:18:23 GMT
	Content-Length: 147

	{ "alerts": [
		{
			"text": "2 parameters were assigned to the 18 profile",
			"level": "success"
		}
	],
	"response": {
		"profileId": 18,
		"paramIds": [
			2,
			3
		],
		"replace": false
	}}
