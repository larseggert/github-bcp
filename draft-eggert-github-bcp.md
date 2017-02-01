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

# Experiences from Current WGs Actively Using GitHub

## HTTPBIS

## TLS

## ACME

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

We try to keep discussion on the mailing list (as opposed to getting
them entirely in the github issues), but may not have been very
successful in that; it definitely requires constant vigilance.

The [WG Wiki](https://trac.ietf.org/trac/core/wiki) says:

> With respect to the mode of operation of the repository, the CoRE WG
> follows the lead of the HTTPBIS WG [add link here]. Specifically
> that means that github issues are welcome to record editorial issues
> as well as technical ones; as are "pull requests" (forks of the
> repository with fixes for an issue). However, technical discussion
> should not happen in the forums implicitly created by the issues,
> but on the WG mailing list.

We currently do not have an active backup regime.

(Add similar text for 6Lo, T2TRG, LWIG, CBOR, LPWAN...)

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
