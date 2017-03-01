---
coding: utf-8

title: Using GitHub for IETF Working Groups
docname: draft-eggert-github-bcp-latest
category: bcp
ipr: trust200902

stand_alone: yes
pi: [toc, sortrefs, symrefs, comments]

author:
  -
    ins: L. Eggert
    name: Lars Eggert
    org: NetApp
    street: Sonnenallee 1
    city: Kirchheim bei München
    code: 85551
    country: Germany
    phone: +49 151 120 55791
    email: lars@netapp.com


informative:
    ID-TEMPLATE:
        title: martinthomson/i-d-template
        author:
            ins: M. Thomson
        target: https://github.com/martinthomson/i-d-template
    REPO:
        title: larseggert/github-bcp
        author:
            ins: L. Eggert
        target: https://github.com/larseggert/github-bcp
    KRAMDOWN-RFC2629:
        title: cabo/kramdown-rfc2629
        author:
            ins: C. Bormann
        target: https://github.com/cabo/kramdown-rfc2629


--- abstract

This document describes the best current practices on using the GitHub web
service to support the operation of IETF Working Groups.

--- middle

# Introduction

# Experiences from Working Groups

<!-- ## HTTPBIS -->

<!-- ## TLS -->

<!-- ## ACME -->

## CORE

\[blame Carsten Bormann for this subsection]

The CoRE WG (Constrained RESTful Environments) has been actively using
the Trac/SVN combination offered by the Tools Team for its older
drafts.
Some newer drafts (including some drafts that are not yet WG drafts
but could be considered candidates for that) are now being worked on
in the `core-wg` github organization.

These drafts generally use Martin Thomson's template, except where the
build process (examples, grammars) is much more complicated than can
easily be supported by this template.
For most repos, a CI (continuous integration) process is set up that
generates a readable editor's copy (in HTML form) as well as a diff
from the most recent submitted version (tools TXT diff), linked from
the README; both have turned out to be very valuable.  (Unfortunately, the
travis-based CI process is somewhat brittle, so there is an
appreciable failure rate.)

We try to keep discussion on the mailing list (as opposed to getting
them entirely in the github issues), but may not have been very
successful in that; it definitely requires constant vigilance.

The [WG Wiki](https://trac.ietf.org/trac/core/wiki) says:

> With respect to the mode of operation of the repository, the CoRE WG
> follows the lead of the [HTTPBIS WG](http://httpwg.org/). Specifically
> that means that github issues are welcome to record editorial issues
> as well as technical ones; as are "pull requests" (forks of the
> repository with fixes for an issue). However, technical discussion
> should not happen in the forums implicitly created by the issues,
> but on the WG mailing list.

We currently do not have an active backup regime; we would expect the
IETF to come up with one that we can share.

As the contributors to CoRE are not necessarily deeply involved in
software projects that already make use of github, moving work to
github may create a sudden barrier of entry for some contributors at
the same time as other contributors report that
the work got much easier for them.
Also, accidents do happen (such as committing versions of a text that
suddenly have CRLF line endings), and some authors may not know how to
fix them.

(There is a separate, chairs-only github organization for chair materials.)

(Add similar text for 6Lo, T2TRG, LWIG, CBOR, LPWAN...)


## QUIC

The [QUIC WG](https://datatracker.ietf.org/wg/quic/charter/) was chartered in
October 2016, and has been using GitHub very intensively.

We created a GitHub organization called ["quicwg"](https://github.com/quicwg),
which the WG chairs administer. Under than organization, we set up two teams,
one for [WG document editors](https://github.com/orgs/quicwg/teams/editors) and
one for [regular
contributors](https://github.com/orgs/quicwg/teams/contributors). Membership in
the former team is contingent on being chosen as an editor for a WG deliverable.
The latter team is more open, and consists of people that the chairs and editors
want to assign reviews or issues to. Obviously, anyone can raise issues, comment
on them, submit pull requests, etc. The benefit of the "contributors" team
really lies in allowing the assignment of tasks to individuals, which is
otherwise not possible.

Underneath the "quicwg" organization, we created two repositories, one for [WG
materials](https://github.com/quicwg/wg-materials) and one for our [base WG
drafts](https://github.com/quicwg/base-drafts). Only the chairs have commit
permissions to the WG materials repo, which is mostly used to hold presentations
and other materials from our various meetings. This repo is configured to not
allow issues to be raised or have a wiki (we instead store Markdown files inside
the repo.)

Our second repo, for "base drafts", is where most of the work occurs. The
decision to use a common repo for several drafts was deliberate. QUIC is a
complex protocol with a complex specification, text moves between different
documents and issues can affect several. Maintaining each draft in a separate
repo, while "cleaner" on first impression, actually complicates this workflow.
When the WG adopts additional drafts, we will decide on a case-by-case basis
whether they will be made part of the "base drafts" or if we create a new repo
underneath the organization. Since Martin Thomson is an editor, we use his setup
[I-D template](#ID-TEMPLATE) to rapidly publish HTML editor copies of the specs.

The "base drafts" repo is configured to allow issues to be raised, and its wiki
is enabled (but rarely used.) Editors (and chairs) have commit rights to this
repo.

We use sets of labels to tag issues that are raised. One set simply indicates
which draft(s) an issue applies to, or whether it is potentially of broad
"design" impact, or "editorial" in nature so that an editor can use his or her
own discretion to resolve it without WG consensus. A second set is used to track
the WG consensus on each issue (with states that currently include
"needs-discussion", "confirm-consensus", "notify-consensus" and "editor-ready").
Issues progress from "needs-discussion" to either "confirm-consensus" or
"notify-consensus". The former is entered when consensus amongst the
participants in the discussion has emerged, and the WG needs to confirm this
consensus on the list. The latter is entered when a consensus call happened at a
WG meeting, and the mailing list needs to confirm this consensus. (It is not
clear if two separate labels actually make all that much sense here.) Once WG
consensus has been established, an issue is labeled "editor-ready".

Although the QUIC WG has only been chartered for a few months, we have already
had ~250 issues raised, many of which have attracted dozens of comments. Good
issue topics and actively searching for prior issues before opening new ones is
essential to manage the workflow.

In order to allow WG participants to follow the activity on GitHub without
needing to check the GitHub web site, we have set up a separate
["quic-issues"](https://www.ietf.org/mailman/listinfo/quic-issues) mailing list
at the IETF. It was a deliberate decision to use a list other than the regular
WG mailing list. First, because we are intensively using GitHub, a lot of
notifications get generated (dozens per day), which would drown out other list
traffic, Second, the issues list is configured as a read-only list, where all
incoming email is rejected, except for some whitelisted senders. The intent is
to keep all discussion on the regular WG mailing list, or on GitHub tickets.
(While GitHub will correctly reflect email replies to issue notifications, they
seem to loose sender information, which is useless.)

Getting GitHub notifications to go to this list was mildly painful, and involved
creating a dummy ["IETF QUIC WG" GitHub user
account](https://github.com/orgs/quicwg/people/quic-issues), whose subscription
email address is the quic-issues list address. The dummy user was made a member
of the QUIC GitHub organization, and will therefore by default "track" all repo
activity. This will cause GitHub to create the desired stream of notification
emails to an IETF list. One caveat here is that GitHub uses the email address
associated with the user who is interacting with the web site as the sender
address of notification emails, which requires regular whitelisting in mailman.
It also means that these users are allowed to otherwise email the issues list;
we trust they don't. This email integration is rather dissatisfyingly complex;
we'd be interested to learn of a better way.


# Security Considerations

This document raises no security considerations.


# IANA Considerations

This document has no IANA considerations.


# Acknowledgments

Carsten Borman and Paul Hoffman have contributed text to this document.

Lars Eggert has received funding from the European Union's Horizon 2020 research
and innovation program 2014-2018 under grant agreement 644866 ("SSICLOPS"). This
document reflects only the authors' views and the European Commission is not
responsible for any use that may be made of the information it contains.

This document is being prepared in a [Github repository](#REPO) using Martin
Thomson's [I-D template](#ID-TEMPLATE) and Carsten Bormann's
[kramdown-rfc2629](#KRAMDOWN-RFC2629).
