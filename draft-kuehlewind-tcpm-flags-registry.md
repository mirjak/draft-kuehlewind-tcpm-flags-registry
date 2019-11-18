---
title: Registration Policy for TCP Header Flags
abbrev: Registration Policy for TCP Flags
docname: draft-kuehlewind-tcpm-flags-registry
date:
category: std

ipr: trust200902
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
  -
    ins: M. Kuehlewind
    name: Mirja Kuehlewind
    org: Ericsson
    email: mirja.kuehlewind@ericsson.com



normative:
    RFC3168:
    RFC2119:
    RFC8174:
    RFC2780:


informative:
	RFC8311:
	RFC3540:



--- abstract

RFC2780 specifies the registration policy for reserved TCP header flags as Standards Action. 
RFC3168 created an IANA registry for these header flags and registered bit 8 (CWR) and 9 (ECE).
This draft changes the registration policy of the registration to IETF Review as usually
new TCP mechanisms that could use the remaining reserved flags will be first specified as 
experimental. Not noting any of those experiments in the registry would undermine the purpose
of having a registry. However, care must be taken, as only a few reserved flags are left 
and if a new (experimental) mechanism sees deployment in the Internet, the flag cannot be
unassigned anymore or used for something else.

--- middle

# Introduction

{{RFC2780}} specifies the registration policy for reserved TCP header flags as Standards Action. 
In section 9.2 (Reserved Bits in TCP Header) is says:

	"The reserved bits in the TCP header are assigned following a Standards Action process."
	
Earlier on, in section 2 (Temporary Assignments) it also says

	"From time to time temporary assignments are made in the values for fields in these headers for use in experiments.  IESG Approval is required for any such temporary assignments."
	
However, it does not specify what exactly is meant with a temporary assignment and how this
could work for TCP header given they can hardly be re-purposed once deployed on the Internet.

{{RFC3168}} created a IANA registry for these header flags and registered bit 8 (CWR) and 9 (ECE).
{{RFC3540}} assigned bit 7 to the experimental ECN Nonce extension and {{RFC8311}} recently declared 
RFC3540 as historic and changed the assignment to reserved, as ECN Nonce was not deployed 
on the Internet. The purpose of RFC8311 was to concentrate updates to Standard Track RFCs
in one document in oder to enable new experimentation with various ECN-related mechanisms. 
However, RFC8311 does not provide any recommendation of the use of bit 7 and the TCP flags registry.


# Notation

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 {{!RFC2119}} {{!RFC8174}}
when, and only when, they appear in all capitals, as shown here.


# Registration Policy for TCP Header Flags

This draft changes the registration policy of the registration to IETF Review as usually
new TCP mechanisms that could use the remaining reserved flags will be first specified as 
experimental. Not noting any of those experiments in the registry would undermine the purpose
of having a registry. However, assignments based on experimental RFC should be marked as
such in the "Comments" field and potentially even provide hints about the nature of the 
experiment or provide a pointer to a section in an RFC where the experiment is explained. 

Further, care must be taken, when assigning TCP header flags for experimental use, as a) only a few reserved flags are left, 
and b) if a new (experimental) mechanism sees deployment in the Internet, the flag cannot be
unassigned anymore or used for something else. Therefore, any experimental RFC that registers 
a reserved flags in the TCP flags registry MUST provide ways to alter the proposed
mechanism at the end of the experimental phase without using additional TCP header flags.
E.g. it would be possible to add an additional negotiation mechanism after the TCP handshake
that would make it possible to use different versions of the general mechanism/extension
that was negotiated or indicated during the TCP handshake using the newly assigned flag. 
Further, any experimental extension
SHOULD discussion the scope of the experiment and potential failure cases or open questions
that need to be answered when running the experiment and explain how these could be addressed
in an updated version.

TCP flags can only be de-assigned if no deployment of an experimental extension happened.
This should be evaluated some years after the assignment to an experimental extension, in order to change the 
registry entry back to "RESERVED" and move the respective experimental RFC to history, or 
assign it permanently. This 
might be done by IESG Approval or based on an Standards track document. However, even when 
reversed to "RESERVED", the experiment
should still be noted (as failed and over) in the "Comments" field of the registry entry.


# IANA Considerations

IANA is requested to change the registration policy of the "TCP Header Flags" registry
(https://www.iana.org/assignments/tcp-header-flags/tcp-header-flags.xhtml) to IETF Review 
or IESG Approval and note this accordingly on the registry page.

In addition, the registry should be updated with a new column called "Comments". 
The text in the "name" field of the entry for bit 7 there should be moved into this new column
while the name will then only say "RESERVED".
Further, bits 4, 5, 6 should be
added to the registry and marked as "RESERVED".

Moreover, as a matter of cleaning-up, IANA is requested to move the registry to a sub-registry
on the Transmission Control Protocol (TCP) Parameters page 
(https://www.iana.org/assignments/tcp-parameters/tcp-parameters.xhtml). 

# Security Consideration

> TBD

# Contributors



# Acknowledgments
