---
title: Facilities
description: Resources available at BNL and JLab
name: facilities
layout: default

tables:
  cpu:
    headers:
      - BNL
      - JLab
    rows:
      - [
      "Dedicated EIC resources: 7 machines with 64 core,
      6 * 64 batch slots = 384 slots and one for interactive use (VMs).
      Each node have dual CPU AMD EPYC 7351.",

      "JLab operates a common cluster. 25k job slots. Delivering ~ 76M core hours per year normalized to dual CPU AMD EPYC 7351."
      ]

      - [
      "1,000 slots allocated from a variety of CPUs (Intel(R) Xeon(R) and AMD EPYC)",
      
      "EIC is currently one of ten projects sharing a 10% fair-share of the cluster.
      So guaranteed 7.6M core hours if the other nine are idle 0.8M if all are busy"
      ]

      - [
      "31k slots available to all experiments that can be dynamically allocated upon priorities (358 M core hours per year).",

      "A further 4MCH/yr dedicated to EIC will be added when demand requires it."
      ]

---
{% include layouts/title.md %}

BNL and JLab provide computing resources for the worldwide EIC community:

{% include layouts/big_table.md width="80%" headers=page.tables.cpu.headers rows=page.tables.cpu.rows %}
