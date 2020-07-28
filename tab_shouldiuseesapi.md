---
title: shouldiuseesapi
displaytext: Should I use ESAPI?
layout:  null
tab: true
order: 3
tags: esapi
---

## Should I use ESAPI?

\[NOTE: The heretical opinions on this ESAPI tab are 100% my own and do
not necessarily reflect the rest of other ESAPI contributors / creators, or the
OWASP Foundation staff, leadership, community. --kevin wall\]

Or, specifically, "Should I use ESAPI for Java (Legacy)?" since that's the only
one run by OWASP that still shows any semblance of life. While maintenance
activities are down compared to ESAPI's peak development years and there is
no new significant functionality planned (although we did recently add support
for SLF4J in the ESAPI Logger), it is not completely abandoned as rumor would
have it.  A few of us are still regularly working on ESAPI and haven't given up,
although we certain could use some additional volunteers to help out.  But without
additional active contributors, ESAPI makes slow progress in terms of bug fixing.

The first question to ask is, are you already using ESAPI in your
project, and if so, do you have a lot vested in it? If so, then the
answer to "Should I use ESAPI?" probably is "yes". The second question
you should ask, if I'm using it, why am I not contributing to it in some
manner? But we won't go there. ;-)

### Potential alternatives to ESAPI
If you are starting out on a new project or trying for the first time to
secure an existing project, then _before_ you consider ESAPI, you
should consider these possible alternatives:

  - Output encoding: [OWASP Java Encoder Project](/www-project-java-encoder)
  - General HTML sanitization: [OWASP Java HTML Sanitizer](/www-project-java-html-sanitizer)
  - Validation: [JSR-303/JSR-349 Bean Validation](http://beanvalidation.org/)
  - Strong cryptography: [Google Tink](https://github.com/google/tink), [Keyczar](https://github.com/google/keyczar)
  - Authentication / authorization: [Apache Shiro](https://shiro.apache.org/), [Authentication using Spring Security](https://duckduckgo.com/?q=using+%22spring+security%22+authentication&atb=v203-1&ia=web)
  - CSRF protection: [OWASP CSRFGuard Project](/www-project-csrfguard) or [OWASP CSRFProtector Project](/www-project-csrfprotector)

if _might_ make sense to use ESAPI if you plan use multiple security controls
provided by ESAPI (e.g., you plan on using an output encoder to prevent XSS,
data validation, HTML sanitization, and safe logging), then ESAPI possibly makes
more sense to use than 3 or 4 other disparate class libraries, which provide but
a single security control. That is an engineering decision your development team
will need to make.

But most (perhaps 90% or more) of the ESAPI use which I have observed was solely
limited to using ESAPI's Encoder to remediate XSS vulnerabilities. If that is
all that you intend to do with ESAPI, steer clear and use
[OWASP Java Encoder Project](/www-project-java-encoder) instead.


A final note: If you want to use ESAPI for authentication / authorization, keep
in mind that ESAPI's reference implementation of those are "flat file based" and will
not scale to enterprise levels. Those 2 reference implementations are more or
less intended as 1) instructional models so show fundamental implementation
ideas, and 2) provided so we could do unit testing that we otherwise would not
be able to accomplishment without some reference implementation. That said,
writing a RDBMS implementation or an LDAP implementation should not be rocket
science.

### Is ESAPI "safe" to use?

#### A brief history
Note that none of the above recommended alternatives are meant to
suggest that ESAPI is dead, but rather to acknowledge the fact that
it isn't being as well-maintained as most F500 companies would
like for their enterprise software.

In the past, ESAPI had gathered the reputation that it was not well maintained,
but that's not the whole story. There were a few of us who were actively
fixing bugs (including updating dependencies), but because no one had
instructions of how to upload a new release to Maven Central, we couldn't make
official releases available to the public unless they were willing to get them
from our GitHub 'develop' branch where the fixes were being applied. Despite
me pleading for help, none arrived until 2Q2019. Since that time, there have
been 3 releases (2.2.0.0, 2.2.1.0, and 2.2.1.1).

#### Concerns about vulnerable ESAPI dependencies are usually over-hyped
Despite that, I still see objections that the ESAPI development team is still
not responsive enough to new vulnerabilities discovered in its dependencies.
Let me respond to that.

1. I get security alerts from both Snyk and GitHub as well as regularly using OWASP Dependency Check in our build process to stay on top of vulnerabilities in library dependencies. In addition, the ever astute ESAPI user community regularly emails the ESAPI co-leaders notices of new CVEs that might affect ESAPI.
2. When I become aware of a new CVE in an ESAPI dependency, whether that it is in a direct or transitive dependency, I attempt to research it to see if it leads to an _exploitable_ path to those using ESAPI. Usually that means digging through the source code of the affected dependency and looking at the commits that fixed the problem. As it turns out, vulnerabilities in ESAPI dependencies rarely to lead to exploitable paths via ESAPI, but if it does, the ESAPI team discusses it, and either upgrades or prepares a workaround. And if that is not possible, we will put usually will put out an announcement on our Google groups mailing lists and prepare a security bulletin, such as this [one](https://github.com/ESAPI/esapi-java-legacy/blob/develop/documentation/ESAPI-security-bulletin2.pdf) for CVE-2019-17571 in Log4J 1.x.
3. If users of ESAPI are overly concerned, then can generally edit their Maven or Gradle, etc. configuration file to exclude the vulnerable dependency and use an updated one that has patched whatever CVE. This does not require a Ph.D. in quantum physics; any developer with a clue (or knowing how to use Stack Overflow :) ought to be able to figure this out. There may be some rare cases where this is not possible and breaks their tests, but if that is the case, it means that ESAPI generally would not be able to upgrade either. (Note because ESAPI currently has a minimal baseline dependency of Java 7, there are times when we cannot upgrade to later versions of dependencies because they require Java 8 or later. That is rare, but could happen. Of course, if your application is stuck using Java 7, then CVEs in ESAPI dependencies probably should be the least of your worries.)

#### If you are still concerned about support...
There used to be, and probably still are, companies from which you can purchase ESAPI support.
I am not going to list such companies here in order to remain vendor neutral. If you are searching
for, and unable to locate, one, then contact me privately via email and I will provide you with
a few pointers.

### So why then are you against recommending ESAPI?
At one point when I originally created this 'tab' on the OWASP ESAPI 'wiki', 
my primary motivation of recommending other security alternatives to ESAPI
was indeed because I felt that we could not adequately support it because I
had not yet figured out how to do a release, but having now done a couple
of releases to Maven Central and having written down detailed documentation, 
that is no longer my concern for recommending alternatives.

So if not that, then why steer people clear of ESAPI 2.x? Glad you asked.
There are two primary reasons:
1. ESAPI's monolithic architecture means that your project will probably unnecessarily pull in lots of dependencies that are not actually needed, which in turn leads to more bloated application deployments. Maybe that's not an issue everywhere, especially if your application war file is in the GB range, but I grew up in the day when Bill Gates told us that 640Kb ought to be enough RAM for anybody and I foolishly believed him. Given that the latest ESAPI jar is a tad over 450Kb, that doesn't leave much room for  its dependent jars, much less for the rest of your application. :) So, in part, its a personal crusade against software bloat.
2. It is going to be a difficult path forward to ESAPI 3 for those applications using ESAPI 2.x. To decouple things and be able to package major functionality into separate ESAPI jars (for instance, there likely will be an esapi3-core jar and an esapi3-encoder jar, etc.), we likely will break some existing interfaces. We won't do that intentionally, but the main goal will not be to preserve backward compatibility. The fact of the matter is, I don't think any of the active ESAPI 2.x contributors wants to spend their time on mailing lists or Stack Overflow or at their companies advising application development teams on the best way of migrating from ESAPI 2.x to ESAPI 3. So the less projects that are on ESAPI 2 now, the better it will be for us when ESAPI 3 finally does arrive. It's somewhat of a selfish reason, but application developers themselves should be selfish in the same sense about the future maintainability of their code. We certainly will not needlessly (at least as I'm a project co-lead) deviate from the ESAPI 2.x interfaces and its current semantic behavior, but at this point, I cannot promise anything. I personally think many of the current ESAPI 2 interfaces are too bloated and confusing and need to be "broken apart" because the current structure ultimately leads to confusion on the part of developers and is an impediment to learning the ESAPI SDK. Therefore we will, in fact, not be hesitant to change such things. In the end, the transition from ESAPI 2 to ESAPI 3 may be easy, but it almost certainly will NOT be seamless and could end up being a royal PITA, much like the transition from Struts 1 to Struts 2. No promises at this point.


### Closing thoughts
It is not a perfect world that we live in, but I would be
remiss as an AppSec guy if I were to plug ESAPI over other good security
solutions simply because of my contributions to / involvement with
ESAPI. I think that ESAPI has its place and I will do my best to
maintain it, but not to the exclusion of my family or day job and I don't
expect that of the other ESAPI contributors either. However, if you
would like to volunteer to help, you know where to find me.

\-[Kevin W. Wall](mailto:kevin.w.wall@gmail.com), ESAPI project co-lead
(last updated July 2020)
