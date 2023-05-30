# Wireless Broadband Alliance Defined Vendor Specific Attributes

The Wireless Broadband Alliance's vendor ID 14122 defines the following RADIUS Vendor Specific Attributes (VSAs) to be used in RADIUS signalling for Wi-Fi authentication, authorization and accounting.

---
<br/>

# "WBA-" Vendor Specific Attributes


## WBA-Offered-Service

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (12)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       Offered-Service
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 12

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

Offered-Service

 - A UTF-8 encoded text string that signals the service offered by the Access Network provider.

WBA OpenRoaming defines the use of the following strings for signalling the offered service:
* “OpenRoaming Bronze”
* “OpenRoaming Silver”
* “OpenRoaming Gold”

An IDP that authorizes their user to receive a particular service tier shall copy the text string in the Offered-Service VSA into the Filter-Id attribute (#11) returned in the Access-Accept message. This filter-ID attribute may be used by the ANP as a confirmation that the IDP has authorized their user to receive the corresponding service level.

## WBA-Financial-Clearing-Provider

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (13)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Financial-Clearing-Provider
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 13

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

Financial-Clearing-Provider

 - A UTF-8 encoded string encoding the identity of the provider of financial clearing services. The first character of the Financial-Clearing-Provider string is used to encode a namespace identifier. A single namespace identifier is defined for use in the Financial-Clearing-Provider VSA:
    - “4”  (0x34)	: 	WBAID - This identifier is used to indicate that the remaining characters of the string are used to indicate a WBAID.

**It is mandatory for the WBA-Financial-Clearing-Provider attribute to be signalled towards a IDP when the ANP supports the OpenRoaming Settled Service.**
**It is mandatory for the WBA-Financial-Clearing-Provider attribute to be returned to the ANP when the IDP is authorizing the use of the OpenRoaming Settled Service.**


## WBA-Data-Clearing-Provider

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (14)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                   Data-Clearing-Provider
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 14

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

Data-Clearing-Provider

 - A UTF-8 encoded string encoding the identity of the provider of data clearing services. The first character of the Data-Clearing-Provider string is used to encode a namespace identifier. A single namespace identifier is defined for use in the Financial-Clearing-Provider VSA:
    - “4”  (0x34)	: 	WBAID - This identifier is used to indicate that the remaining characters of the string are used to indicate a WBAID.

When a receiving entity receives a message with a WBA-Financial-Clearing-Provider attribute and no WBA-Data-Clearing-Provider attribute, it can assume that the organization responsible for providing data clearing service to the sending entity is identical to the organization providing financial clearing service to the sending entity. 


## WBA-Linear-Volume-Rate

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (15)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|  Currency-CH1 |  Currency-CH3 |  Currency-CH3 |    Index      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                             NANOS                             |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 15

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

Currency-CH1

 - encodes a single 8-bit UTF-8 character (i.e., an ASCII character)

Currency-CH2

 - encodes a single 8-bit UTF-8 character (i.e., an ASCII character)

Currency-CH3

 - encodes a single 8-bit UTF-8 character (i.e., an ASCII character)

The concatenation of the characters encoded using CURRENCY-CH1, CURRENCY-CH2 and CURRENCY-CH3 represents an ISO 4217-2015 three letter currency code.

Index

 - An unsigned 8-bit integer represents an index

NANOS

 - An unsigned 32-bit integer representing the number of currency units, as identified by the currency-code, charged for a kilobyte (1024 bytes) of data

The number of currency units per kilobyte is calculated using the following equation:
NANOS*10e-9

Note, exceptionally, if the currency code is signalled as Venezuelan Bolivars (VES), the number of Bolivars per kilobyte shall be encoded directly in NANOS.


## WBA-Identity-Provider

The WBA-Identity-Provider VSA is used to signal a string encoding the identity of the IDP

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (16)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                      Identity-Provider
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 16

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

Identity-Provider

 - A text string encoding string encoding the identity of the IDP. The first character of the Identity-Provider string is used to encode a namespace identifier. Two namespace identifiers are defined for use in the Identity-Provider VSA:
    - “0”  (0x30)	: 	TADIG code - This identifier is used to indicate that the remaining characters of the string are used to indicate a Transferred Account Data Interchange Group (TADIG) codes, as defined by GSMA.
    - “4”  (0x34)	: 	WBAID - This identifier is used to indicate that the remaining characters of the string are used to indicate a WBAID.


## WBA-Custom-SLA

The WBA-Custom-SLA VSA is used by ANPs that operate OpenRoaming installations on moving platforms 
to signal one or more service availability/bandwidth tuples that is/are supported by the 
ANP's installation.

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (17)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| Availability  |                   Bandwidth                   | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields.

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122.

Sub-Type

 - Attribute sub-type of 17.

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields.

Availability

 - An 8-bit unsigned integer representing the percentage of time when the per-user-sustained-bandwidth is available.
 
Bandwidth

 - A 24-bit unsigned integer representing the per-user-sustained bandwidth in bits per second.


---

# Table of WBA Vendor Specific Attributes 

The following table provides a guide to which of the Vendor Specific Attributes defined
may be found in which kinds of packets, and in what quantity.

| Request | Accept | Reject | Challenge| Acct-Request| Vendor Sub-Type  | Attribute |
| ---- | ---- | ---- | ---- | ---- | ----  | ---- |
| 0-1   | 0     | 0    | 0 | 0-1  | 12 | WBA-Offered-Service|
| 0-1   | 0-1     | 0    | 0 | 0-1  | 13 | WBA-Financial-Clearing-Provider|
| 0-1   | 0-1     | 0    | 0 | 0-1  | 14 | WBA-Data-Clearing-Provider|
| 0+   | 0-1     | 0    | 0 | 0-1  | 15 | WBA-Linear-Volume-Rate|
| 0   | 0-1     | 0    | 0 | 0  | 16 | WBA-Identity-Provider|
| 0+   | 0     | 0    | 0 | 0  | 16 | WBA-Custom-SLA|


The following table defines the meaning of the above table entries.

| Entry | Meaning |
| ---- | ---- |
|0    | This attribute MUST NOT be present in packet.|
|0+   | Zero or more instances of this attribute MAY be present in packet.|
|0-1   |Zero or one instance of this attribute MAY be present in packet.|
|1    | One instance of this attribute MUST be present in packet.|

# Enhanced Reply-Message Syntax

Originally defined for being able to signal a displayable text string to authenticating users, the reply-message attribute is re-used in deployments supporting WRIX-based Passpoint networks to signal additional information from the IDP to the ANP. The enhanced reply message is encoded using UTF-8 characters. The WBA defined additional information is appended after the NUL ASCII character (0x00). 

The ABNF syntax of the Reply-message is:

~~~~~~~~~~
Reply-message      = [ displayable-string ] %x00 [ wba-info ]
displayable-string = *CHAR 
wba-info           = ”Reject-Reason=" cause-code

cause-code =  “10” ; failed user authentication
cause-code =/ “11” ; invalid user identity
cause-code =/ “12” ; expired client certificate
cause-code =/ “20” ; generic AAA failure 
cause-code =/ “21” ; backend failure
cause-code =/ “22” ; protocol timeout
cause-code =/ “30” ; failure due to badly formatted request
cause-code =/ “31” ; rejected – missing charging model
cause-code =/ “32” ; rejected – missing geospatial location
cause-code =/ “40” ; failure due to subscription - permanent
cause-code =/ “41” ; authorization rejected - no service subscription
cause-code =/ “42” ; authorization rejected - roaming not allowed in this network
cause-code =/ “43” ; authorization rejected - offered charging model not acceptable 
cause-code =/ “44” ; authorization rejected - roaming to this location not allowed
cause-code =/ “45” ; authorization rejected – offered service level not acceptable
cause-code =/ “50” ; failure due to subscription - temporary
cause-code =/ “51” ; authorization rejected - offered charging model not acceptable at this time
cause-code =/ “52” ; authorization rejected - roaming to this location not allowed at this time
~~~~~~~~~~


---
<br/><br/><br/>

# LEGACY "WISPr-" Vendor Specific Attributes

The Wireless Broadband Alliance's vendor ID 14122 was previously used to define the following RADIUS Vendor Specific Attributes (VSAs) to be used in legacy Wireless Internet Service Provider Roamining (WISPr) deployments. 

## WISPr-Location-ID

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (1) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       WISPr-Location-ID
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 1

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Location-ID

 - String encoding of a Hotspot location identifier. The WISPr-Location-ID is of the form:
isocc=<ISO_Country_Code>,cc=<E.164_Country_Code>,ac=<E.164_Area_Code>,network=<SSID/ZONE>

**This attribute is deprecated for use in Passpoint networks. WLAN implementations are recommended to use RFC 5580 to signal location information and RFC 3580 to signal SSID information.**


## WISPr-Location-Name

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (2) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       WISPr-Location-Name
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 2

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Location-Name

 - String encoding of a textual description of the Location and Operator Name
 
**This attribute is deprecated for use in Passpoint networks. WLAN implementations are recommended to use RFC 5580 to signal location and operator-name information.**


## WISPr-Logoff-URL

A text string conditionally sent by the Access Network provider.  This value is presented to allow the Home Entity to provide a link on their Start Page for the user to Logoff.

If WISPr authentication is used, then this attribute must be sent by the Access Network provider.  The Identity Provider must then include a link to this URL on the page referenced in WISPr-Redirection-URL (if WISPr-Redirection-URL is sent by the Identity Provider in an Access-Accept.

~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (3) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       WISPr-Logoff-URL
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 3

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Logoff-URL

 - A string encoding of the URL of logoff page that will be referenced by any page included in an Identity Provider’s Redirection-URL.
 
**This attribute is for use in captive portal based systems. It is not intended to be used with Passpoint based authentication.**

## WISPr-Redirection-URL

A text string optionally returned by the Ideneity Provider upon a successful authentication attempt by a roaming customer, containing the URL of a post-login “welcome” page to present to the user.

For example, T-Mobile uses “http://welcome.hotspot.t-mobile.com”.

The Access Network Provider may honour or ignore this redirection URL if it is provided, subject to technical feasibility and bilateral agreements.

~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (4) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       WISPr-Redirection-URL
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 4

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Redirection-URL

 - A string encoding of the URL of control panel/home page that will be referenced by post-login page or where customer will be redirected to.
 
**This attribute is for use in captive portal based systems. It is not intended to be used with Passpoint based authentication.**


## WISPr-Bandwidth-Min-Up

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (5) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    WISPr-Bandwidth-Min-Up                     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 5

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Bandwidth-Min-Up

 - an unsigned integer encoding of  the minimum rate in bits/s for upstream data

**This attribute is deprecated.**


## WISPr-Bandwidth-Min-Down

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (6) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                  WISPr-Bandwidth-Min-Down                     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 6

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Bandwidth-Min-Down

 - an unsigned integer encoding of the minimum rate in bits/s for downstream data

**This attribute is deprecated.**

## WISPr-Bandwidth-Max-Up

Used to signal the rate limiting to be applied to user transmitted data

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (7) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    WISPr-Bandwidth-Max-Up                     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 7

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Bandwidth-Min-Up

 - an unsigned integer encoding of the maximum rate in bits/s for upstream data

**This attribute is deprecated.**


## WISPr-Bandwidth-Max-Down

Used to signal the rate limiting to be applied to user received data

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (8) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                  WISPr-Bandwidth-Max-Down                     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 8

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Bandwidth-Min-Down

 - an unsigned integer encoding of the maximum rate in bits/s for downstream data

**This attribute is deprecated.**


### WISPr-Session-Terminate-Time

A indicates the time when the user should be disconnected from the network. 

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (9) |   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                  WISPr-Session-Terminate-Time                     
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 9

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Session-Terminate-Time

 - a stext string formatted according to ISO 8601 format YYYY-MM-DDThh:mm:ssTZD representing the time when the user should be disconnected from the network. If the TZD is not included, the user should be disconnected at the time specified in local time.
 
**This attribute is deprecated for use in Passpoint networks. It is recommended to use session-timeout (RADIUS attribute #27) to control a user's session time.**


## WISPr-Session-Terminate-End-Of-Day

An integer flag of either zero or one indicating whether the user’s connection should be terminated at the end of its billing day

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (10)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|               WISPr-Session-Terminate-End-Of-Day              |        
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 10

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Session-Terminate-End-Of-Day

 - An unisigned integer representing zero (false) or one (true) indicating termination rule.
 
**This attribute is deprecated for use in Passpoint networks.**

## WISPr-Billing-Class-Of-Service

A free-form text field. It is intended to indicate service variations that would require different charges even though they occurred at the same hotspot.

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (11)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|               WISPr-Billing-Class-Of-Service                  
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
~~~~~~~~~~

Type

 - 26 for Vendor-Specific

Length

 - Length of entire attribute including type and length fields

Vendor-ID

 - 4 octets encoding the WBA Vendor ID of 14122

Sub-Type

 - Attribute sub-type of 11

Sub-length

 - Length of the sub-attribute including the sub-type and sub-length fields

WISPr-Billing-Class-Of-Service

 - Text string indicating service type. The contents of the field should be negotiated between the Home Entity or Roaming Intermediary and the Hotspot Operator and may indicate, for example, the difference between service obtained in a hotel room versus service obtained in the lobby or conference room.
 
 
**This attribute is deprecated for use in Passpoint networks.**


# Table of WISPr Vendor Specific Attributes 

The following table provides a guide to which of the Vendor Specific Attributes defined
may be found in which kinds of packets, and in what quantity.

| Request | Accept | Reject | Challenge| Acct-Request| Vendor Sub-Type  | Attribute |
| ---- | ---- | ---- | ---- | ---- | ----  | ---- |
| 0-1   | 0     | 0    | 0 | 0-1  | 1 | WISPr-Location-ID |
| 0-1   | 0     | 0    | 0 | 0-1  | 2 | WISPr-Location-Name|
| 0-1   | 0     | 0    | 0 | 0  | 3 | WISPr-Logoff-URL |
| 0   | 0-1     | 0    | 0 | 0  | 4 | WISPr-Redirection-URL|
| 0-1   | 0     | 0    | 0 | 0-1  | 5 | WISPr-Bandwidth-Min-Up|
| 0-1   | 0     | 0    | 0 | 0-1  | 6 | WISPr-Bandwidth-Min-Down|
| 0-1   | 0     | 0    | 0 | 0-1  | 7 | WISPr-Bandwidth-Max-Up|
| 0-1   | 0    | 0    | 0 | 0-1  | 8 | WISPr-Bandwidth-Max-Down|
| 0   | 0-1     | 0    | 0 | 0  | 9 | WISPr-Session-Terminate-Time|
| 0   | 0-1     | 0    | 0 | 0  | 10 | WISPr-Session-Terminate-End-Of-Day|
| 0   | 0-1     | 0    | 0 | 0  | 11 | WISPr-Billing-Class-Of-Service|


The following table defines the meaning of the above table entries.

| Entry | Meaning |
| ---- | ---- |
|0    | This attribute MUST NOT be present in packet.|
|0+   | Zero or more instances of this attribute MAY be present in packet.|
|0-1   |Zero or one instance of this attribute MAY be present in packet.|
|1    | One instance of this attribute MUST be present in packet.|
