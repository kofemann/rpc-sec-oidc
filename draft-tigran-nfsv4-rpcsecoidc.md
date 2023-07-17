---
title: "RPC-SEC-OIDC - Using OpenID Connect to Authenticate Remote Procedure Call"
abbrev: "RPCSEC_OIDC"
category: info

docname: draft-tigran-nfsv4-rpcsecoidc-latest-latest
submissiontype: IETF  # also: "independent", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: Transport
workgroup: Internet-Draft
keyword:
 - RPC
 - OIDC
 - Internet-Draft

author:
 -
    ins: T. Mkrtchyan
    name: Tigran Mkrtchyan
    organization: Deutsches Elektronen-Synchrotron DESY
    email: tigran.mkrtchyan@desy.de

normative:

informative:


--- abstract

For over two decades, Remote Procedure Call (RPC) is using Kerberos5 based GSS-API mechanism, called RPCSEC_GSS,
to provide in-transit data integrity, privacy and user authentication. With the introduction of RPC-over-TLS the
GSS-API is not required anymore for data integrity and privacy, however, to ensure user identity in a shared environment,
like public and private clouds, the Kerberos principles are still needed.

Though the RPCSEC_GSS has proven it's maturity the other data access protocols, like HTTPS, rely on a different technology,
namely, TLS, which is responsible for in-transit data protection, and bearer tokens, like OAuth2 (RFC 6749 & RFC 6750), OpenID
Connect, which is responsible for user authentication and authorization.

This document describes a new authentication type for Remote Procedure Call that enables the use of OIDC tokens in combination with RPC-over-TLS.


--- middle

# Introduction

TODO Introduction


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
