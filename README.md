libvirt
=========

Install and configure libvirt on Fedora.

This role allows users to run virtual machines in userspace. It also
configures [Kernel same-page Merging (KSM)][ksm].

Requirements
------------

Your computer must have enough hardware resources to support running
virtual machines. You might also have to enable virtualization in your
computer's BIOS.

Role Variables
--------------

|name|description|type|default|
|---|---|---|---|
|ksm_max_kernel_pages|The maximum number of unswappable kernel pages which may be allocated by ksm (0 for unlimited)|int|0|
|ksm_monitor_interval|How long ksmtuned should sleep between tuning adjustments|seconds|60|
|ksm_npages_boost|Added to the `npages` value, when `free memory` is less than `thres`|int|300|
|ksm_npages_decay|The value given is subtracted from the `npages` value when `free memory` is greater than `thres`|int|-50|
|ksm_npages_min|The lower limit for the `npages` value|int|64|
|ksm_npages_max|The upper limit for the `npages` value|int|1250|
|ksm_sleep_msec|Millisecond sleep between ksm scans for 16Gb server. Smaller servers sleep more, bigger sleep less.|milliseconds|10|
|ksm_thres_coef|The RAM percentage to be calculated in parameter `thres`|int|20|
|ksm_thres_const|If this is a low memory system, and the `thres` value is less than `KSM_THRES_CONST`, then reset `thres` value to `KSM_THRES_CONST` value|int|2048|
|libvirt_pool_name|Default pool's name|string|default|
|libvirt_pool_dir|Path to default pool directory|directory path|"{{ ansible_user_dir }}/VirtualMachines"|

Example Playbook
----------------

```yaml
- hosts: workstations
  tasks:
  - import_role:
      name: libvirt
    vars:
      libvirt_pool_name: default
      libvirt_pool_dir: "{{ ansible_user_dir }}/VirtualMachines"
```

License
-------

[MIT](LICENSE)


[ksm]: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_tuning_and_optimization_guide/chap-ksm
