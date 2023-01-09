---
question: How is the "suite" of OpenC2 Specifications organized?
---

As described in the [_OpenC2 Architecture
Specification_](https://docs.oasis-open.org/openc2/oc2arch/v1.0/oc2arch-v1.0.html),
there are multiple types of OpenC2 specifications, meant to be
used in concert:

* The [*OpenC2 Architecture
  Specification*](https://docs.oasis-open.org/openc2/oc2arch/v1.0/oc2arch-v1.0.html)
  describes the fundamental structures of OpenC2.

* The [*OpenC2 Language
  Specification*](https://docs.oasis-open.org/openc2/oc2ls/v1.0/oc2ls-v1.0.html)
  provides the essential elements of the language, the structure
  for Commands and Responses, and the mechanisms for extending
  the OpenC2 language.

* [**OpenC2 Actuator
  Profiles**](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=openc2#technical)
  specify the subset of the OpenC2 language relevant in the
  context of specific actuator functions (e.g., [packet
  filtering](https://docs.oasis-open.org/openc2/oc2slpf/v1.0/oc2slpf-v1.0.html),
  honeypots).

* [**OpenC2 Transfer
  Specifications**](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=openc2#technical)
  utilize existing protocols and standards (e.g.,
  [HTTPS](https://docs.oasis-open.org/openc2/open-impl-https/v1.1/cs01/open-impl-https-v1.1-cs01.html),
  [MQTT](https://docs.oasis-open.org/openc2/transf-mqtt/v1.0/transf-mqtt-v1.0.html))
  to implement OpenC2 message transfer in specific environments.

