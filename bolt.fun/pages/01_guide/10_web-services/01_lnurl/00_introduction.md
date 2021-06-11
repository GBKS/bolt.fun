---
layout: guide
title: LNURL
parent: Web Services
description: LNURL is an open standard for communicating with a Lightning node through HTTP.
nav_order: 10
has_children: true
permalink: /guide/web-services/lnurl
main_classes: -no-top-padding
---

# LNURL - Automate invoice, channel, auth operations

LNURL allows web service providers to use Lightning Network functionality in their API endpoints that clients who have implemented one or more of the various flows can interact with autonomously. The client can be a wallet application or even another web service.

Several "Flows" are currently part of the LNURL specifications. They are; Pay, Withdraw, Channel, and Auth. These Flows automate some otherwise manual steps for certain Lightning Network-based operations and standardize the HTTP request and responses.

## URLs as Lightning invoices (bech32)

LNURL endpoints are all encoded with [bech32](https://en.bitcoin.it/wiki/Bech32) which is the same as bitcoin addresses and [standard lightning invoices]({{ "/guide/invoices" | relative_url }}). Encoding endpoints like this allows for easy integration into existing LN services/apps since most of these would already have functionality built in to receive/send and encode/decode bech32 values.

For example, this endpoint:
```
https://service.com/api?q=3fc3645b439ce8e7f2553a69e5267081d96dcd340693afabe04be7b0ccd178df
```

Would be encoded to:
```
LNURL1DP68GURN8GHJ7UM9WFMXJCM99E3K7MF0V9CXJ0M385EKVCENXC6R2C35XVUKXEFCV5MKVV34X5EKZD3EV56NYD3HXQURZEPEXEJXXEPNXSCRVWFNV9NXZCN9XQ6XYEFHVGCXXCMYXYMNSERXFQ5FNS
```

When an LNURL-enabled app receives an LNURL-specific bech32 string, it would decode the string to get the URL and then send the appropriate requests to start the relevant LNURL flow.

## Flows

There are 4 different LNURL flows that serve to expose different functionality sets to the user:

### [LNURL-pay]({{ "/guide/web-services/lnurl/pay" }})
For paying for a service

### [LNURL-withdraw]({{ "/guide/web-services/lnurl/withdraw" }})
For withdrawing funds from a service

### [LNURL-channel]({{ "/guide/web-services/lnurl/channel" }})
For requesting incoming channels from a service

### [LNURL-auth]({{ "/guide/web-services/lnurl/auth" }}) (comming soon)
For securely logging in to some service

---

**Notes:**
- _progressively implement flows a la [this playground example](https://www.oauth.com/playground/device-code.html)_