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
not necessarily reflect the rest of other ESAPI contributors or the
OWASP staff, leadership, community. --kevin wall\]

Or, specifically, "Should I use ESAPI for Java?" since that's the only
one run by OWASP that still shows any semblance of life. Maintenance
activities is down, way down in fact of its peak development activities.
Some of us are still trying and haven't given up and volunteers are
still welcome. But without active contributors, projects make slow
progress.

The first question to ask is, are you already using ESAPI in your
project, and if so, do you have a lot vested in it? If so, then the
answer to "Should I use ESAPI?" probably is "yes". The second question
you should ask, if I'm using it, why am I not contributing to it in some
manner? But we won't go there.

If you are starting out on a new project or trying for the first time to
secure an existing project, then _before_ you consider ESAPI, you
should consider these possible alternatives:

  - Output encoding: [OWASP Java Encoder Project](/www-project-java-encoder)
  - General HTML sanitization: [OWASP Java HTML Sanitizer](/www-project-java-html-sanitizer)
  - Validation: [JSR-303/JSR-349 Bean Validation](http://beanvalidation.org/)
  - Strong cryptography: [Google Tink](https://github.com/google/tink), [Keyczar](https://github.com/google/keyczar)
  - Authentication / authorization: [Apache Shiro](https://shiro.apache.org/)
  - CSRF protection: [OWASP CSRFGuard Project](/www-project-csrfguard) or [OWASP CSRFProtector Project](/www-project-csrfprotector)

Note that this is not to suggest that ESAPI is dead, but rather to
acknowledge the fact that it isn't being as well-maintained as most F500
companies would like for their enterprise software. There may be
alternatives, such as companies that you can purchase ESAPI support
from. Those are not being considered here for various reasons, not the
least of which is to remain vendor neutral. Rather, instead these
recommendations should be taken as possible alternatives to secure your
application. It is not a perfect world that we live in, but I would be
remiss as an appsec guy if I were to plug ESAPI over other good security
solutions simply because of my contributions to / involvement with
ESAPI. I think that ESAPI has it's place and I will do my best to
maintain it, but not to the exclusion of my family or day job. If you
would like to volunteer to help, you know where to find me.

\-[Kevin W. Wall](mailto:kevin.w.wall@gmail.com)
