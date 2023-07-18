---
title: "RPC-SEC-OIDC - Using OpenID Connect to Authenticate Remote Procedure Call"
abbrev: "RPCSEC_OIDC"
category: std

docname: draft-tigran-nfsv4-rpcsecoidc-latest
submissiontype: IETF  # also: "independent", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Transport"
workgroup: "Network File System Version 4"
keyword:
 - RPC
 - OIDC
 - Internet-Draft

author:
 -
    ins: T. Mkrtchyan
    name: Tigran Mkrtchyan
    organization: Deutsches Elektronen-Synchrotron DESY
    abbrev: DESY
    street:
      - Notkestrasse 85
    code: 22607
    city: Hamburg
    country: Germany
    email: tigran.mkrtchyan@desy.de

normative:

informative:


--- abstract

For over two decades, Remote Procedure Call (RPC) is using Kerberos5 based GSS-API mechanism, called RPCSEC_GSS,
to provide in-transit data integrity, privacy and user authentication. With the introduction of RPC-over-TLS the
GSS-API is not required anymore for data integrity and privacy, however, to ensure user identity in a shared environment,
like public and private clouds, the Kerberos principles are still needed.

Though the RPCSEC_GSS has proven its maturity the other data access protocols, like HTTPS, rely on a different technology,
namely, TLS, which is responsible for in-transit data protection, and bearer tokens, like OAuth2 (RFC 6749 & RFC 6750), OpenID
Connect, which is responsible for user authentication and authorization.

This document describes a new authentication type for Remote Procedure Call that enables the use of OIDC tokens in combination with RPC-over-TLS.


--- middle

# Introduction

TODO Introduction


# Definitions

- OIDC: OpenID Connect, or OIDC, is an authentication protocol built on top of the OAuth 2.0 framework. It provides a standardized way for users to authenticate and authorize themselves to access web applications or APIs.

- Identity Provider (IdP): The IdP is responsible for authenticating users and issuing identity tokens. Examples of popular IdPs include Google, GitHub, and Keykloak.

- Identity Token: The identity token is a JSON Web Token (JWT) issued by the IdP. It contains claims about the user's identity, such as their username, email address, and any additional requested information.

- Access Token: In the context of OIDC, an access token is a security token issued by the identity provider (IdP) after successful authentication and authorization. It represents the user's authorization to access protected resources. The access token is a bearer token, meaning it contains the necessary information to access resources and can be presented directly to the resource server.

- Resource Server: The resource server is responsible for enforcing access control and verifying the validity and authorization of access tokens presented by clients. It holds the protected resources, such as user data, APIs, or any other restricted information.

By combining OIDC with OAuth 2.0, the access token obtained through OIDC can be used to provide both authentication (verifying the user's identity) and authorization (granting access to resources) in a secure and standardized manner.

# Flavor Number Assignment

   The RPCSEC_GSS security flavor has been assigned the value of 6:

~~~ xdr
      enum auth_flavor {
          ...
          RPCSEC_OIDC = 8      /* RPCSEC_OIDC security flavor */
      };
~~~

# Authentication

~~~ xdr

      struct opaque_auth {
         auth_flavor flavor;
         opaque body<400>;
      };
~~~

the body is the token

**FIXME**: 400 bytes is not enough to pass the token

# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
