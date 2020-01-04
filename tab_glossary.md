---
title: Glossary
displaytext: Glossary
layout:  null
tab: true
order: 4
tags: esapi
---

## Glossary


![Image:Asvs-letters.jpg](Asvs-letters.jpg
"Image:Asvs-letters.jpg")**ESAPI Terminology**

  - **adapter** - There are optionally your own implementations for each
    security control. There may be application logic contained in these
    classes which may be developed by or for your organization. The
    logic may be organization-specific and/or application-specific.
    There may be proprietary information or logic contained in these
    classes which may be developed by or for your organization.
  - **built-in singleton design pattern** - The "built-in" singleton
    design pattern refers to the replacement of security control
    reference implementations with your own implementations. ESAPI
    interfaces are otherwise left intact.
  - **codec** - ESAPI encoder/decoder reference implementations.
  - **core** - The ESAPI interfaces and reference implementations that
    are not intended to be replaced with enterprise-specific versions
    are called the ESAPI Core.
  - **exception** - ESAPI exception reference implementations.
  - **extended factory design pattern** - The "extended" factory design
    pattern refers to the addition of a new security control interface
    and corresponding implementation, which in turn calls ESAPI security
    control reference implementations and/or security control reference
    implementations that were replaced with your own implementations.
    The ESAPI locator class would be called in order to retrieve a
    singleton instance of your new security control, which in turn would
    call ESAPI security control reference implementations and/or
    security control reference implementations that were replaced with
    your own implementations.
  - **extended singleton design pattern** - The "extended" singleton
    pattern refers to the replacement of security control reference
    implementations with your own implementations and the
    addition/modification/subtraction of corresponding security control
    interfaces.
  - **ES-enable (or ESAPI-enable)** - Just as web applications and web
    services can be Public Key Infrastructure (PKI) enabled (PK-enabled)
    to perform for example certificate-based authentication,
    applications and services can be OWASP ESAPI-enabled (ES-enabled) to
    enable applications and services to protect themselves from
    attackers.
  - **filter** - In ESAPI for Java, there is additionally an HTTP filter
    that can be called separately from the other controls.
  - **interfaces** - There is a set of security control interfaces.
    There is no application logic contained in these interfaces. They
    define for example types of parameters that are passed to types of
    security controls. There is no proprietary information or logic
    contained in these interfaces.
  - **locator** - The ESAPI security control interfaces include an
    "ESAPI" class that is commonly referred to as a "locator" class. The
    ESAPI locator class is called in order to retrieve singleton
    instances of individual security controls, which are then called in
    order to perform security checks (such as performing an access
    control check) or that result in security effects (such as
    generating an audit record).
  - **reference implementation** - There is a reference implementation
    for each security control. There is application logic contained in
    these classes, i.e. contained in these interface implementations.
    However, the logic is not organization-specific and the logic is not
    application-specific. There is no proprietary information or logic
    contained in these reference implementation classes.
  - **Web Application Firewall (WAF)** - In ESAPI for Java, there is
    additionally a Web Application Firewall (WAF) that can be called
    separately from the other controls.
