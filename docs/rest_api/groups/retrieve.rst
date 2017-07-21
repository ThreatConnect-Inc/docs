Retrieve Groups
---------------

.. include:: groups/filters.rst

Retrieve All Group Types
^^^^^^^^^^^^^^^^^^^^^^^^

To retrieve groups of all types, use the following query:

.. code::

    GET /v2/groups

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 2,
        "group": [
          {
            "id": 12345,
            "name": "Likely Nation State Intrusion on Remote Server",
            "type": "Document",
            "ownerName": "Example Organization",
            "dateAdded": "2017-07-13T16:43:19Z",
            "webLink": "https://app.threatconnect.com/auth/document/document.xhtml?document=12345"
          },
          {
            "id": 12346,
            "name": "Investment Status",
            "type": "Email",
            "ownerName": "Example Organization",
            "dateAdded": "2017-07-13T19:28:10Z",
            "webLink": "https://app.threatconnect.com/auth/email/email.xhtml?email=12346"
          }
        ]
      }
    }

Retrieve Multiple Groups
^^^^^^^^^^^^^^^^^^^^^^^^

To retrieve multiple groups of a certain type, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}

The ``{groupType}`` can be any one of the available group types:

- ``adversaries``
- ``campaigns``
- ``documents``
- ``emails``
- ``incidents``
- ``signatures``
- ``threats``
  
For example, the query below will retrieve a list of all incidents in the default owner:

.. code::

    GET /v2/groups/incidents

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 2,
        "incident": [
          {
            "id": "54321",
            "name": "Test Incident",
            "ownerName": "Wanna Cry Hits Stoic Department",
            "dateAdded": "2017-07-13T17:50:17",
            "webLink": "https://app.threatconnect.com/auth/incident/incident.xhtml?incident=54321",
            "eventDate": "2017-03-21T00:00:00Z"
          },
          {
            "id": "54322",
            "name": "PoS Malware Detected at Denver Location",
            "ownerName": "Example Organization",
            "dateAdded": "2017-07-13T17:51:17",
            "webLink": "https://app.threatconnect.com/auth/incident/incident.xhtml?incident=54322",
            "eventDate": "2017-06-27T00:00:00Z"
          }
        ]
      }
    }

Retrieve a Single Group
^^^^^^^^^^^^^^^^^^^^^^^

To retrieve a single Group, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}

For example, if you wanted to retrieve the threat with the ID 12345, you would use the following query:

.. code::

    GET /v2/groups/threats/12345

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "threat": {
          "id": 12345,
          "name": "Bad Dude",
          "owner": {
            "id": 1,
            "name": "Example Organization",
            "type": "Organization"
          },
          "dateAdded": "2017-05-13T18:40:22Z",
          "webLink": "https://app.threatconnect.com/auth/threat/threat.xhtml?threat=12345"
        }
      }
    }

Retrieve Group Metadata
-----------------------

Retrieve Group Attributes
^^^^^^^^^^^^^^^^^^^^^^^^^

To retrieve a Group's Attributes, use the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/attributes

For example, if you wanted to retrieve the attributes on the threat with the ID 12345, you would use the following query:

.. code::

    GET /v2/groups/threats/12345/attributes

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 2,
        "attribute": [
          {
            "id": "54321",
            "type": "Description",
            "dateAdded": "2016-07-13T17:50:17",
            "lastModified": "2017-05-02T18:40:22Z",
            "displayed": true,
            "value": "Description Example"
          },
          {
            "id": "54322",
            "type": "Source",
            "dateAdded": "2016-07-13T17:51:17",
            "lastModified": "2017-05-02T18:40:22Z",
            "displayed": true,
            "value": "Source Example"
          }
        ]
      }
    }

To retrieve the Security Labels that are on an attribute, use the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/attributes/{attributeId}/securityLabels

Here is an example query:

.. code::

    GET /v2/groups/threats/12345/attributes/54321/securityLabels

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 1,
        "securityLabel": [
          {
            "name": "TLP Amber",
            "description": "TLP Amber information requires support to be effectively acted upon, yet carries risks to privacy, reputation, or operations if shared outside of the organizations involved.",
            "dateAdded": "2017-07-13T17:50:17"
          }
        ]
      }
    }

Retrieve Group Security Labels
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To retrieve the Security Labels for a Group, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/securityLabels

For example, the query below will retrieve all Security Labels for the Threat with ID 12345:

.. code::

    GET /v2/groups/threats/12345/securityLabels

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 1,
        "securityLabel": [
          {
            "name": "TLP Amber",
            "description": "TLP Amber information requires support to be effectively acted upon, yet carries risks to privacy, reputation, or operations if shared outside of the organizations involved.",
            "dateAdded": "2017-07-13T17:50:17"
          }
        ]
      }
    }

Retrieve Group Tags
^^^^^^^^^^^^^^^^^^^

To retrieve the Tags for a Group, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/tags

For example, the query below will retrieve all Tags for the Threat with ID 12345:

.. code::

    GET /v2/groups/threats/12345/tags

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 1,
        "tag": [
          {
            "name": "Nation State",
            "webLink": "https://app.threatconnect.com/auth/tags/tag.xhtml?tag=Nation+State&owner=Common+Community"
          }
        ]
      }
    }

Retrieve Group Associations
---------------------------

Retrieve Associated Groups
^^^^^^^^^^^^^^^^^^^^^^^^^^

To view Groups associated with a given Group, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/groups

For example, the query below will retrieve all of the Groups associated with a Threat with the ID 12345:

.. code::

    GET /v2/groups/threats/12345/groups

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 1,
        "group": [
          {
            "id": "54321",
            "name": "New Incident",
            "type": "Incident",
            "ownerName": "Example Organization",
            "dateAdded": "2017-07-13T17:50:17",
            "webLink": "https://app.threatconnect.com/auth/incident/incident.xhtml?incident=54321"
          }
        ]
      }
    }

You can also find associated Groups of a given type using the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/groups/{associatedGroupType}

For example, we could use the following query to find all Incidents associated with the Threat with ID 12345:

.. code::

    GET /v2/groups/threats/12345/groups/incidents

We can also drill down even further by adding the ID of an associated Group to the end of the query like:

.. code::

    GET /v2/groups/threats/12345/groups/incidents/54321

Where ``54321`` is the ID of an incident associated with Threat 12345.

Retrieve Associated Indicators
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To view Indicators associated with a given Group, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/indicators

For example, the query below will retrieve all of the Indicators associated with a Threat with the ID 12345:

.. code::

    GET /v2/groups/threats/12345/indicators

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 1,
        "indicator": [
          {
            "id": "54321",
            "ownerName": "Example Organization",
            "type": "Address",
            "dateAdded": "2016-07-13T17:50:17",
            "lastModified": "2017-05-01T21:32:54Z",
            "rating": 3.0,
            "confidence": 55,
            "threatAssessRating": 3.0,
            "threatAssessConfidence": 55.0,
            "webLink": "https://app.threatconnect.com/auth/indicators/details/address.xhtml?address=0.0.0.0&owner=Example+Organization",
            "summary": "0.0.0.0"
          }
        ]
      }
    }

You can also find associated Indicators of a given type using the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/indicators/{associatedIndicatorType}

For example, we could use the following query to find all Address Indicators associated with the Threat with ID 12345:

.. code::

    GET /v2/groups/threats/12345/indicators/addresses

We can also drill down even further by adding the ID of an associated Indicator to the end of the query like:

.. code::

    GET /v2/groups/threats/12345/indicators/addresses/54321

Where ``54321`` is the ID of an Address associated with Threat 12345.

Retrieve Associated Victim Assets
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To view Victim Assets associated with a given Group, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/victimAssets

For example, the query below will retrieve all of the Victim Assets associated with a Threat with the ID 12345:

.. code::

    GET /v2/groups/threats/12345/victimAssets

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 2,
        "victimAsset": [
          {
            "id": "54321",
            "name": "bad@badguys.com",
            "type": "EmailAddress",
            "webLink": "https://app.threatconnect.com/auth/victim/victim.xhtml?victim=123"
          },
          {
            "id": "54322",
            "name": "nobody@gmail.com",
            "type": "EmailAddress",
            "webLink": "https://app.threatconnect.com/auth/victim/victim.xhtml?victim=123"
          }
        ]
      }
    }

You can also find associated Victim Assets of a given type using the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/victimAssets/{associatedVictimAssetType}

For example, we could use the following query to find all Victim Assets that are Email Addresses which are associated with the Threat with ID 12345:

.. code::

    GET /v2/groups/threats/12345/victimAssets/emailAddresses

We can also drill down even further by adding the ID of an associated Victim Asset to the end of the query like:

.. code::

    GET /v2/groups/threats/12345/victimAssets/emailAddresses/54321

Where ``54321`` is the ID of a Victim Asset associated with Threat 12345.

Retrieve Associated Victims
^^^^^^^^^^^^^^^^^^^^^^^^^^^

To view Victims associated with a given Group, use a query in the following format:

.. code::

    GET /v2/groups/{groupType}/{groupId}/victims

For example, the query below will retrieve all of the Victims associated with a Threat with the ID 12345:

.. code::

    GET /v2/groups/threats/12345/victims

JSON Response:

.. code:: json

    {
      "status": "Success",
      "data": {
        "resultCount": 1,
        "victim": [
          {
            "id": "54321",
            "name": "Bad Guy",
            "org": "Example Organization",
            "webLink": "https://app.threatconnect.com/auth/victim/victim.xhtml?victim=54321"
          }
        ]
      }
    }

We can also drill down even further by adding the ID of an associated Victim to the end of the query like:

.. code::

    GET /v2/groups/threats/12345/victims/54321

Where ``54321`` is the ID of a Victim associated with Threat 12345.