# Wireless Broadband Alliance Defined Vendor Specific Attributes

The Wireless Broadband Alliance's vendor ID 14122 defines the following RADIUS Vendor Specific Attributes (VSAs) to be used in RADIUS signalling for Wi-Fi authentication, authorization and accounting.

---

# CURRENT WBA Vendor Specific Attributes


## WBA-Offered-Service

~~~~~~~~~~
0                   1                   2                   3
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Type      |  Length       |        Vendor-ID = 14122   
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   Vendor-ID = 14122 (cont)     |  sub-type (12)|   Sub-Length  | 
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       WBA-Offered-Service
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

WBA-Offered-Service

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
|                 WBA-Financial-Clearing-Provider
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

WBA-Financial-Clearing-Provider

 - A UTF-8 encoded string encoding the identity of the provider of financial clearing services. The first character of the WBA-Financial-Clearing-Provider string is used to encode a namespace identifier. A single namespace identifier is defined for use in the Financial-Clearing-Provider VSA:
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
|                   WBA-Data-Clearing-Provider
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

WBA-Data-Clearing-Provider

 - A UTF-8 encoded string encoding the identity of the provider of data clearing services. The first character of the WBA-Data-Clearing-Provider string is used to encode a namespace identifier. A single namespace identifier is defined for use in the Financial-Clearing-Provider VSA:
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
|                      WBA-Identity-Provider
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

WBA-Identity-Provider

 - A text string encoding string encoding the identity of the IDP. The first character of the WBA-Identity-Provider string is used to encode a namespace identifier. Two namespace identifiers are defined for use in the Identity-Provider VSA:
    - “0”  (0x30)	: 	TADIG code - This identifier is used to indicate that the remaining characters of the string are used to indicate a Transferred Account Data Interchange Group (TADIG) codes, as defined by GSMA.
    - “4”  (0x34)	: 	WBAID - This identifier is used to indicate that the remaining characters of the string are used to indicate a WBAID.


---

# LEGACY WISPr Vendor Specific Attributes

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

