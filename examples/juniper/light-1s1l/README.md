
This example adopts the topology with 2 instances of VQFX (light) and apply the configuration template on them.
Both VQFX will be connected back to back with IP address pre-configured on their interfaces.

```

[SPINE]
SPINE01:
  E0: VAGRANT-MGMT
  E1: LEAF01-E1
  E2: LEAF02-E1
  E3: LEAF03-E1
  E4: LEAF04-E1

[LEAF]
LEAF01:
  E0: VAGRANT-MGMT
  E1: SPINE01-E1
  E2: SPINE02-E1
  E3: SRV01-E1
  E4: LEAF02-E4

```
