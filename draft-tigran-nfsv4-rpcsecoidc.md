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

This draft considers the problem of using token-based authentication with network attached storage systems, in particular
with NFS servers. This problem exist due to wide adoption of token based authentication for majority of services
provided by private and public clouds. Due to lack of common security infrastructure between storage and other services,
the end users forced either to completely disable authentication and rely on network isolation or introduce a custom,
non standard and, probably, faulty, workarounds. This problem has become aggravated in recent years with high adoption
of OpenID Connect technology to authenticate and delegate access to various could-based resources for large user communities.

Though, Remote Procedure Call (RPC) protocol, which is the underlying transport for NFS support multiple authentication
mechanisms supports GSSAPI, that aims to address this issues, the lacks of integration with other cloud services makes it
insufficient as a general purpose solution.

--- middle

# Introduction

For over two decades, Remote Procedure Call (RPC) is using Kerberos5 based GSS-API mechanism,
called RPCSEC_GSS, to provide in-transit data integrity, privacy and user authentication. With the introduction of RPC-over-TLS the
GSS-API is not required any more for data integrity and privacy, however, to ensure user identity in a shared environment,
like public and private clouds, the Kerberos principles are still needed.

Though the RPCSEC_GSS has proven its maturity the other data access protocols, like HTTPS, rely on a different technology,
namely, TLS, which is responsible for in-transit data protection, and bearer tokens, like OAuth2 (RFC 6749 & RFC 6750), OpenID
Connect, which is responsible for user authentication and authorization. The adoption of those technologies for RPC protocol will
provide direct NFS access to storage servers from token-enabed CPU clusters.

The token-based access is rapidly enters into many online services, from simply reading e-mails to starting complex applications
in large scientific environments. Moreover, one of the benefits of token-based access is a possibility to delegate
authorization decisions to identity provides that are not required to run locally at the sites, thus allows a decentralized access
control in a distributed environments. This makes token-based authentication and authorization very attractive to large multisite users
communities, like scientist at Large Hadron Collider (LHC) or Square Kilometer Array(SKA) telescope, who typically need to be
authorized by their home institutions but get an access to shared resources available at other universities or private/public clouds.

Since 2017 the computing specialists at Worldwide LHC Computing Grid (WLCG) has been working towards enabling token based authentication
and authorization throughout its entire middleware stack, including storage access through HTTPs protocol, which is used for date exchange
between laboratories. However, those efforts doesn't cover data access from CPU clusters to locally available storage services. One
on the reasons is the lack of standard access protocols that provide token-based access to storage.


# Definitions

- OIDC: OpenID Connect, or OIDC, is an authentication protocol built on top of the OAuth 2.0 framework. It provides a standardized way for users to authenticate and authorize themselves to access web applications or APIs.

- Identity Provider (IdP): The IdP is responsible for authenticating users and issuing identity tokens. Examples of popular IdPs include Google, GitHub, and Keykloak.

- Identity Token: The identity token is a JSON Web Token (JWT) issued by the IdP. It contains claims about the user's identity, such as their username, email address, and any additional requested information.

- Access Token: In the context of OIDC, an access token is a security token issued by the identity provider (IdP) after successful authentication and authorization. It represents the user's authorization to access protected resources. The access token is a bearer token, meaning it contains the necessary information to access resources and can be presented directly to the resource server.

- Resource Server: The resource server is responsible for enforcing access control and verifying the validity and authorization of access tokens presented by clients. It holds the protected resources, such as user data, APIs, or any other restricted information.

By combining OIDC with OAuth 2.0, the access token obtained through OIDC can be used to provide both authentication (verifying the user's identity) and authorization (granting access to resources) in a secure and standardized manner.

# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
