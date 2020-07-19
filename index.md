---

layout: col-sidebar
title: OWASP Enterprise Security API (ESAPI)
tags: esapi
project: true
level: 3
type: code

---
[![OWASP Lab](https://img.shields.io/badge/owasp-lab%20project-yellow)](https://owasp.org/projects#div-lab)

## What is ESAPI?
ESAPI (The OWASP Enterprise Security API) is a free, open source, web application security control library that makes it easier for programmers to write lower-risk applications. The ESAPI libraries are designed to make it easier for programmers to retrofit security into existing applications. The ESAPI libraries also serve as a solid foundation for new development.

Allowing for language-specific differences, all OWASP ESAPI versions have the same basic design:

* <strong>There is a set of security control interfaces.</strong> They define for example types of parameters that are passed to types of security controls.
* <strong>There is a reference implementation for each security control.</strong> The logic is not organization‐specific and the logic is not application‐specific. An example: string‐based input validation. (Note that some of the reference implementations are simply "toy" examples to illustrate how to implement a specific interface [e.g., ESAPI for Java's <code>org.owasp.esapi.reference.FileBasedAuthenticator</code>] whereas others are full-fledged enterprise ready reference implementations [e.g., <code>org.owasp.esapi.reference.DefaultEncoder</code> or <code>org.owasp.esapi.reference.DefaultValidator</code>].)
* <strong>There are optionally your own implementations for each security control.</strong> There may be application logic contained in these classes which may be developed by or for your organization. An example: enterprise authentication.
