# Intro to frameworks

There is no universally accepted definition of the word "framework" in
the context of web development.

According to Merriam-Webster, the word "framework" refers to "a basic
conceptual structure" (e.g., the *framework* of the U.S. Constitution).
It can also point to "a skeletal, openwork, or structural frame" (e.g.,
an iron *framework* surrounding a sculpture).

In the same way, web frameworks are third-party code whose interface
dictates the overall structure of a project. They offer a standardized
approach (i.e., a skeleton) to build and deploy web applications,
automating common activities such as database management, templating,
authentication, internationalization, etc. Common frameworks include
Django, Laravel, Ruby on Rails, and Next.

In theory, frameworks differ from libraries in that the latter do not
significantly influence the overall structure of a project. Libraries
are third-party modules that applications use here and there. They can
be easily replaced without impacting the rest of the codebase. To cite
[Alexander Petros][], "a library is a cog that you add to your machine,
a framework is a pre-built machine that you control by customizing its
cogs".

[Alexander Petros]: https://htmx.org/essays/is-htmx-another-javascript-framework/

In practice, the distinction between the two is more ambiguous. There is
no strict rule determining when third-party code transitions from being
a library to becoming a framework. Many libraries in the aforementioned
sense, including React, Flask, or HTMX, often label themselves as
frameworks.

## A word of caution

To use frameworks is to abstract parts of your application. It means
operating at a "higher level" than you might have otherwise, employing
code that you did not write, and may not fully comprehend. Frameworks
often accelerate the speed of development, especially at the start, but
they are not free of compromises. They come with conventions and
concepts you need to learn, but cannot generalize. They free you from
having to make many decisions, but limit flexibility. They offer
ressources and community, but increase debugging complexity. Part of
being a good web developper is knowing when these tradeoffs are worth
it, and when they are not.
