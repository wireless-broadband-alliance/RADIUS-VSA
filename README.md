# RADIUS-VSA

## Wireless Broadband Alliance Defined Vendor Specific Attributes

The Wireless Broadband Alliance's vendor ID 14122 defines the following RADIUS Vendor Specific Attributes (VSAs) to be used in RADIUS signalling for Wi-Fi authentication, authorization and accounting.


### Location-ID

The Location-ID VSA uses vendor type 1

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Location-ID   | 1 | string| 0-1 |  |0-1 | Hotspot location identifier |

**This attribute is deprecated for use in Passpoint networks. WLAN implementations are recommended to use RFC 5580 to signal location information and RFC 3580 to signal SSID information.**

The Location-ID is of the form:
isocc=<ISO_Country_Code>,cc=<E.164_Country_Code>,ac=<E.164_Area_Code>,network=<SSID/ZONE>

### Location-Name

The Location-Name VSA uses vendor type 2

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Requestq | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Location-Name   | 2 | string| 0-1 |  |0-1 | Hotspot Location and Operator Name |

**This attribute is deprecated for use in Passpoint networks. WLAN implementations are recommended to use RFC 5580 to signal location and operator-name information.**

The Location-Name is a textual description of the location.

### Logoff-URL

The Logoff-URL VSA uses vendor type 3

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Redirection-URL   | 3 | string| 0-1 |  | | A string representing the URL of logoff page that will be referenced by any page included in an HSP’s Redirection-URL. |

This attribute is for use in captive portal based systems. It is not intended to be used with Passpoint based authentication.

A text string conditionally sent by the VNP.  This value is presented to allow the Home Entity to provide a link on their Start Page for the user to Logoff.

If WISPr authentication is used, then this attribute must be sent by the VNP.  The HSP must then include a link to this URL on the page referenced in Redirection-URL (if Redirection-URL is sent by the HSP in an Access-Accept.

### Redirection-URL

The Redirection-URL VSA uses vendor type 4

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Redirection-URL   | 4 | string|  | 0-1 | | A string representing the URL of control panel/home page that will be referenced by post-login page or where customer will be redirected to |

This attribute is for use in captive portal based systems. It is not intended to be used with Passpoint based authentication.

A text string optionally returned by the HSP upon a successful authentication attempt by a roaming customer, containing the URL of a post-login “welcome” page to present to the user.

For example, T-Mobile uses “http://welcome.hotspot.t-mobile.com”.

The VNP may honour or ignore this redirection URL if it is provided, subject to technical feasibility and bilateral agreements.

### Minimum-Bandwidth-Up

The Minimum-Bandwidth-Up VSA uses vendor type 5

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Minimum-Bandwidth-Up   | 5 | integer |  | 0-1 | | Specifies the minimum rate in bits/s for upstream data |

**This attribute is deprecated.**

### Minimum-Bandwidth-Down

The Minimum-Bandwidth-Down VSA uses vendor type 6

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Minimum-Bandwidth-Down   | 6 | integer |  | 0-1 | | Specifies the minimum rate in bits/s for downstream data |

**This attribute is deprecated.**

### Maximum-Bandwidth-Up

The Maximum-Bandwidth-Up VSA uses vendor type 7

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Maximum-Bandwidth-Up  | 7 | integer |  | 0-1 | | Specifies the maximum rate in bits/s for upstream data |

**This attribute is deprecated.**

The rate limiting to be applied to user transmitted data

### Maximum-Bandwidth-Down

The Maximum-Bandwidth-Down VSA uses vendor type 8

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Maximum-Bandwidth-Down   | 8 | integer |  | 0-1 | | Specifies the maximum rate in bits/s for downstream data |

**This attribute is deprecated.**

The rate limiting to be applied to user received data

### Session-Terminate-Time

The Session-Terminate-Time VSA uses vendor type 9

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Session-Terminate-Time  | 9 | string|  | 0-1 | | YYYY-MM-DDThh:mm:ssTZD  |

**This attribute is deprecated for use in Passpoint networks. It is recommended to use session-timeout (RADIUS attribute #27) to control a user's session time.**

A indicates the time when the user should be disconnected from the network. The field is a text string formatted according to ISO 8601 format YYYY-MM-DDThh:mm:ssTZD.

If the TZD is not included, the user should be disconnected at the time specified in local time.



### Session-Terminate-End-Of-Day

The Session-Terminate-End-of-Day VSA uses vendor type 10

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Session-Terminate-End-Of-Day  | 10 | integer |  | 0-1 | | Flag zero (false) or one (true) indicating termination rule.   |

**This attribute is deprecated for use in Passpoint networks.**

An integer flag of either zero or one indicating whether the user’s connection should be terminated at the end of its billing day

### Billing-Class-Of-Service

The Billing-Class-Of-Service VSA uses vendor type 11

| Attribute | # | Type | Access-Request | Access-Accept | Accounting-Request | Comment |
| --| -- | -- | -- | -- | -- | -- |
| Billing-Class-Of-Service  | 11 | string|  | 0-1 | | Text string indicating service type.  |

**This attribute is deprecated for use in Passpoint networks.**

A free-form text field. It is intended to indicate service variations that would require different charges even though they occurred at the same hotspot.

The contents of the field should be negotiated between the Home Entity or Roaming Intermediary and the Hotspot Operator and may indicate, for example, the difference between service obtained in a hotel room versus service obtained in the lobby or conference room.
