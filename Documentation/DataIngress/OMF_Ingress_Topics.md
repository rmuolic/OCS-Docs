---
uid: omfIngressTopics
---

Topics 
============

Topic information 
-----------------------

A Topic is used to aggregate data received from publishers and make it available for consumption 
via a Subscription. A topic must contain at least one publisher. Publishers may be added to or 
removed from an existing topic. A given publisher may also belong to multiple topics. 

When a topic is created, data sent from its assigned publishers is routed to a special queue 
where it can be consumed by a subscription. This queue provides a buffer of up to one day for 
subscriptions which are temporarily unable to receive data. 

The API calls in this section are used to create and manipulate topics. 

Data Models 
-----------

Topic information is contained in an object called ``Topic`` and has the following format: 


| Property        | Type                    | Details                                |
|-----------------|-------------------------|----------------------------------------|
| TenantId        | string                  | Identifies the owner of the Topic      |
| Id              | string                  | Unique Id generated by the API during creation  |
| NamespaceId     | string                  | Identifies the namespace for the Topic |
| Name            | string                  | A friendly name for the Topic          |
| Description     | string                  | An optional description for the Topic. |
| CreationDate    | string                  | The time that the Topic was created. The string is formatted using ISO 8601 format. |
| Publishers	    | string array            | An array of Publisher Ids mapped to the Topic   |

********************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/topics/count``
------------------------------------------------

Get the number of topics for a tenant. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace.

**Returns**

An integer. 

**************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/topics/{topicId}``
------------------------------------------------------------

Get a specific topic. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``topicId``
  Unique Id for the topic. 
``namespaceId``
  Unique Id for the namespace.

**Returns**

A Topic object. 

**************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/topics?skip={skip}&count={count}``
-------------------------------------------

Get all topics for a tenant. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace.
``int skip``
  An optional parameter representing the zero-based offset of the first topic to retrieve. If not specified, a default value of 0 is used. 
``int count``
  An optional parameter representing the maximum number of topics to retrieve. If not specified, a default value of 100 is used.

**Returns**

An array of Topic objects. 

************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/topics/{topicId}/subscriptions?skip={skip}&count={count}``
-------------------------------------------

Get all subscriptions across all namespaces mapped to a topic.

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace of the topic.
``topicId``
  Unique Id for the topic.
``int skip``
  An optional parameter representing the zero-based offset of the first subscription mapped to a topic to retrieve. If not specified, a default value of 0 is used. 
``int count``
  An optional parameter representing the maximum number of subscriptions mapped to a topic to retrieve. If not specified, a default value of 100 is used.

**Returns**

An array of Subscription objects. 

************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/publishertopicmappings/topic/{topicId}?skip={skip}&count={count}``
-------------------------------------------------------------------------------------

Gets a list of publishers that are currently mapped to a topic 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace of the topic.
``topicId``
  Unique Id for the topic. 
``int skip``
  An optional parameter representing the zero-based offset of the first publisher mapped to a topic to retrieve. If not specified, a default value of 0 is used. 
``int count``
  An optional parameter representing the maximum number of publishers mapped to a topic to retrieve. If not specified, a default value of 100 is used.

**Returns**

An array of strings, each the Id of a publisher that is mapped to the provided topic

***************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/topics``
-------------------------------------------------------------------------------------

Gets the default Access Control List for new topics.

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 

**Returns**

An AccessControlList object.

***************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/topics/{topicId}/accesscontrol``
-------------------------------------------------------------------------------------

Gets the Access Control List for a particular topic.

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``topicId``
  Unique Id for the topic. 

**Returns**

An AccessControlList object.

***************************

``POST api/tenants/{tenantId}/namespaces/{namespaceId}/topic``
-----------------------------------------

Creates or updates a topic. Only the topic name and description can be updated. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 

**Body**

A MappedTopic object. 

**Returns**

A MappedTopic object. 


***********************

``PUT api/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/topics``
----------------------------------------------------------

Update the default Access Control List for new topics

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 

**Body**

An AccessControlList object.

************************

``PUT api/tenants/{tenantId}/namespaces/{namespaceId}/topics/{topicId}/accesscontrol``
----------------------------------------------------------

Update the Access Control List for a particular topic

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``topicId``
  Unique Id for the topic. 

**Body**

An AccessControlList object.

************************

``DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/topics/{topicId}``
----------------------------------------------------------------

Delete a topic. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``topicId``
  Unique Id for the topic. 

************************