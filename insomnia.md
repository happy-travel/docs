# Request Structure in Insomnia


## Top Level

All requests must be structured into folders where a top level folder represents a service and has a human readable name.

_Examples:_
* Currency Converter
* Netstorming Connector
* Edo


## Path to Action

A path to an action must match URL topology except a part common for a service and a valuable part.

_Examples:_
* `api/1.0/conversions/USD/RUR/100` becomes `Conversions`\
* `en/api/1.0/admin/management/register` becomes `Admin/Management` where _Management_ is a sub-folder of _Admin_.


## Request Name

A name may be either an action name in a simple case and the action match the REST specs, either a case name if the action is complex in any way.

_Examples:_
* Get
* Post
* Get Master Customer Token
* Transfer to Default agency


## Query Parameters

Query parameters, headers and authorization methods must be provided with proper Insomnia tabs for better modification and automation.


## Environment Variables

All service or higher level variables like service base URLs, tokens, etc. should be placed as environment variables where possible.


> :exclamation: Sensitive values must not be revealed for the Production environment
