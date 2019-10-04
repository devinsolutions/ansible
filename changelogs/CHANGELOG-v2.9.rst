==========================================
Ansible 2.9 "Immigrant Song" Release Notes
==========================================

.. contents:: Topics


v2.9.0rc2
=========

Release Summary
---------------

| Release Date: 2019-10-03
| `Porting Guide <https://docs.ansible.com/ansible/devel/porting_guides.html>`__


Minor Changes
-------------

- dnf - Properly handle idempotent transactions with package name wildcard globs (https://github.com/ansible/ansible/issues/62809)
- vmware_cluster_ha - Remove a wrong parameter from an example in the documentation.

Bugfixes
--------

- Fix nxos_l3_interfaces module deleting mgmt IP (https://github.com/ansible/ansible/pull/62545).
- ansible-galaxy - Default collection install path to first path in COLLECTIONS_PATHS (https://github.com/ansible/ansible/pull/62870)
- ansible-test now correctly excludes the test results temporary directory when copying files from the remote test system to the local system
- ansible-test now properly sets PYTHONPATH for tests when running from an Ansible installation
- docker_login - correct broken fix for https://github.com/ansible/ansible/pull/60381 which crashes for Python 3.
- find - clarify description of ``contains`` (https://github.com/ansible/ansible/issues/61983)
- iosxr - Fix random idempotence issues with iosxr_lag_interfaces Resource Module (https://github.com/ansible/ansible/pull/62998).
- kubevirt: apply wait_sleep fix from devel to not fail on missing param

v2.9.0rc1
=========

Release Summary
---------------

| Release Date: 2019-09-20
| `Porting Guide <https://docs.ansible.com/ansible/devel/porting_guides.html>`__


Minor Changes
-------------

- Revert apply as the default of kubernetes modules such as k8s.  This restores the 2.8 and previous behaviour as the default.  apply can still be explicitly enabled https://github.com/ansible/ansible/issues/62661
- ansible-test - Bump version of ACME test container to 1.8.0. Fixes a typo in the API and adds a newer Pebble version.
- ansible-test defaults to redacting sensitive values (disable with the ``--no-redact`` option)
- meraki_organization - Removed the absent option for state due to the possibly catastrophic mistakes. Parameter will be added in 2.10 with safeguards.
- update ansible-test default-test-container from version 1.9.1 to 1.9.2
- update ansible-test default-test-container from version 1.9.2 to 1.9.3

Bugfixes
--------

- **security issue** - Redact cloud plugin secrets in ansible-test when running integration tests using cloud plugins. Only present in 2.9.0b1.

- **security issue** - TaskExecutor - Ensure we don't erase unsafe context in TaskExecutor.run on bytes. Only present in 2.9.0beta1 (https://github.com/ansible/ansible/issues/62237)

- Add nxos_telemetry replaced state (https://github.com/ansible/ansible/pull/62368).
- AnsibleDumper - Add a representer for AnsibleUnsafeBytes (https://github.com/ansible/ansible/issues/62562).
- Change enable to enabled for junos_interfaces and junos_lldp_interfaces module (https://github.com/ansible/ansible/issues/62319)
- Check action plugin names for network (eos, ios, iosxr, junos, netconf, nxos) modules properly load with collections.
- Ensure connection with remote host is created before invoking execute_command() from module side (https://github.com/ansible/ansible/issues/61596)
- Fix delete to pass the right parameters(https://github.com/ansible/ansible/pull/62525)
- Fix for junos cli_config replace option (https://github.com/ansible/ansible/pull/62131).
- Fix ios_lldp_global enable to enabled(https://github.com/ansible/ansible/pull/62420)
- Fix issue where the collection loader tracebacks if ``collections_paths = ./`` is set in the config
- Fix loading network facts modules for smart gathering (https://github.com/ansible/ansible/pull/59856).
- Fix negated all,min for network_facts and remove choices (https://github.com/ansible/ansible/pull/61362).
- Fix nxos_bfd_global cmd order and tests (https://github.com/ansible/ansible/pull/61943).
- Fix regular expression to support parsing more than 10 network interfaces in RouterOS output (https://github.com/ansible/ansible/pull/62346)
- Fix support for Specialized images in Azure Shared Image Gallery
- Fix the upstream rpm spec file.  The ansible-test package requirement on the main ansible package was formatted incorrectly.
- Fix traceback error in IOS and IOSXR when ran with empty config (https://github.com/ansible/ansible/pull/62400)
- Fix traceback session uid error(https://github.com/ansible/ansible/pull/62523)
- Fix traceback with empty config error msg(https://github.com/ansible/ansible/pull/62538)
- Fixed intermittent "JSON object must be str, bytes or bytearray, not list" error with EOS over httpapi
- Make EOS / FRR / IOS / IOSXR bgp modules collection safe
- Remove case sensitivity on interface names from eos_interfaces, eos_l2_interfaces, eos_l3_interfaces, eos_lacp_interfaces, eos_lag_interfaces, and eos_lldp_interfaces.
- Remove unused import from iosxr l3_interfaces facts library.
- Removed unused FactArgs imports from eos / ios / iosxr / junos / vyos facts modules
- Return commands key instead of xml in result for junos resource module (https://github.com/ansible/ansible/issues/61773)
- Stabilize nxos initiated copy for nxos_file_copy plugin (https://github.com/ansible/ansible/pull/62355).
- To fix ios_l3_interfaces resource module round trip failure(https://github.com/ansible/ansible/pull/61642)
- Unit tests for cp_cp_mgmt_discard
- Unit tests for cp_mgmt_access_layer
- Unit tests for cp_mgmt_access_layer_facts
- Unit tests for cp_mgmt_access_role
- Unit tests for cp_mgmt_access_role_facts
- Unit tests for cp_mgmt_access_rule
- Unit tests for cp_mgmt_access_rule_facts
- Unit tests for cp_mgmt_address_range
- Unit tests for cp_mgmt_address_range_facts(https://github.com/ansible/ansible/pull/62338)
- Unit tests for cp_mgmt_administrator
- Unit tests for cp_mgmt_administrator_facts
- Unit tests for cp_mgmt_application_group
- Unit tests for cp_mgmt_application_group_facts
- Unit tests for cp_mgmt_application_site
- Unit tests for cp_mgmt_application_site_catagory
- Unit tests for cp_mgmt_application_site_catagory_facts
- Unit tests for cp_mgmt_application_site_facts
- Unit tests for cp_mgmt_assign_global_assignment
- Unit tests for cp_mgmt_dns_domain
- Unit tests for cp_mgmt_dns_domain_facts
- Unit tests for cp_mgmt_dynamic_object
- Unit tests for cp_mgmt_dynamic_object_facts
- Unit tests for cp_mgmt_exception_group
- Unit tests for cp_mgmt_exception_group_facts(https://github.com/ansible/ansible/pull/62216)
- Unit tests for cp_mgmt_global_assignment
- Unit tests for cp_mgmt_global_assignment
- Unit tests for cp_mgmt_global_assignment_facts
- Unit tests for cp_mgmt_global_assignment_facts
- Unit tests for cp_mgmt_group
- Unit tests for cp_mgmt_group
- Unit tests for cp_mgmt_group_facts
- Unit tests for cp_mgmt_group_facts
- Unit tests for cp_mgmt_group_with_exclusion
- Unit tests for cp_mgmt_group_with_exclusion
- Unit tests for cp_mgmt_group_with_exclusion_facts
- Unit tests for cp_mgmt_group_with_exclusion_facts
- Unit tests for cp_mgmt_host
- Unit tests for cp_mgmt_host
- Unit tests for cp_mgmt_host_facts
- Unit tests for cp_mgmt_host_facts
- Unit tests for cp_mgmt_install_policy
- Unit tests for cp_mgmt_multicast_address_range
- Unit tests for cp_mgmt_multicast_address_range_facts
- Unit tests for cp_mgmt_multicast_address_range_facts
- Unit tests for cp_mgmt_network
- Unit tests for cp_mgmt_package
- Unit tests for cp_mgmt_package
- Unit tests for cp_mgmt_package_facts
- Unit tests for cp_mgmt_package_facts
- Unit tests for cp_mgmt_publish
- Unit tests for cp_mgmt_put_file
- Unit tests for cp_mgmt_run_ips_update
- Unit tests for cp_mgmt_run_script(https://github.com/ansible/ansible/pull/62322)
- Unit tests for cp_mgmt_security_zone
- Unit tests for cp_mgmt_security_zone
- Unit tests for cp_mgmt_security_zone_facts
- Unit tests for cp_mgmt_security_zone_facts
- Unit tests for cp_mgmt_service_dce_rpc
- Unit tests for cp_mgmt_service_dce_rpc
- Unit tests for cp_mgmt_service_dce_rpc_facts
- Unit tests for cp_mgmt_service_dce_rpc_facts
- Unit tests for cp_mgmt_service_group
- Unit tests for cp_mgmt_service_group
- Unit tests for cp_mgmt_service_group_facts(https://github.com/ansible/ansible/pull/62213)
- Unit tests for cp_mgmt_service_group_facts(https://github.com/ansible/ansible/pull/62214)
- Unit tests for cp_mgmt_service_icmp
- Unit tests for cp_mgmt_service_icmp6
- Unit tests for cp_mgmt_service_icmp6_facts
- Unit tests for cp_mgmt_service_icmp_facts
- Unit tests for cp_mgmt_service_other
- Unit tests for cp_mgmt_service_other_facts
- Unit tests for cp_mgmt_service_rpc
- Unit tests for cp_mgmt_service_rpc_facts
- Unit tests for cp_mgmt_service_sctp
- Unit tests for cp_mgmt_service_sctp_facts
- Unit tests for cp_mgmt_service_tcp
- Unit tests for cp_mgmt_service_tcp_facts
- Unit tests for cp_mgmt_service_udp
- Unit tests for cp_mgmt_service_udp_facts
- Unit tests for cp_mgmt_simple_gateway
- Unit tests for cp_mgmt_simple_gateway_facts
- Unit tests for cp_mgmt_tag
- Unit tests for cp_mgmt_tag_facts(https://github.com/ansible/ansible/pull/62215)
- Unit tests for cp_mgmt_threat_exception
- Unit tests for cp_mgmt_threat_exception_facts
- Unit tests for cp_mgmt_threat_protection_override(https://github.com/ansible/ansible/pull/62328)
- Unit tests for cp_mgmt_threat_rule
- Unit tests for cp_mgmt_threat_rule_facts
- Unit tests for cp_mgmt_verfiy_policy
- Unit tests for the case with more than 10 network interfaces
- _purefa_facts - Fix missing API version check when calling I(admins) or I(all) as the subset
- allow external collections to be created in the 'ansible' collection namespace (https://github.com/ansible/ansible/issues/59988)
- ansible-connection persists even after playbook run is completed (https://github.com/ansible/ansible/pull/61591)
- ansible-doc now properly handles removed modules/plugins
- ansible-inventory - Properly hide arguments that should not be shown (https://github.com/ansible/ansible/issues/61604)
- ansible-inventory - Restore functionality to allow ``--graph`` to be limited by a host pattern
- ansible-test coverage - Fix the ``--all`` argument when generating coverage reports - https://github.com/ansible/ansible/issues/62096
- ansible-test now correctly installs the requirements specified by the collection's unit and integration tests instead of the requirements specified for Ansible's own unit and integration tests
- ansible-test now loads the collection loader plugin early enough for ansible_collections imports to work in unit test conftest.py modules
- ansible-test now properly activates the vcenter plugin for vcenter tests when docker is available
- ansible-test now properly activates virtual environments created using the --venv option
- ansible-test now properly creates a virtual environment using ``venv`` when running in a ``virtualenv`` created virtual environment
- ansible-test now properly excludes the ``tests/output/`` directory from code coverage
- ansible-test now properly handles creation of Python execv wrappers when the selected interpreter is a script
- ansible-test now properly handles warnings for removed modules/plugins
- ansible-test now properly ignores the ``tests/output//`` directory when not using git
- ansible-test now properly installs requirements for multiple Python versions when running sanity tests
- ansible-test now properly registers its own code in a virtual environment when running from an install
- ansible-test now shows sanity test doc links when installed (previously the links were only visible when running from source)
- azure - fix for specialized images in vmss
- ce_ospf - update to fix some bugs - Contrast before and after adding configuration. (https://github.com/ansible/ansible/pull/61684)
- ce_snmp_target_host - update to fix some bugs - Contrast before and after adding configuration. (https://github.com/ansible/ansible/pull/61842)
- ce_snmp_traps - update to fix some bugs - Contrast before and after adding configuration. (https://github.com/ansible/ansible/pull/61843)
- ce_static_route - update to fix some bugs - Add some update statements. (https://github.com/ansible/ansible/pull/62498)
- ce_stp - update to fix some bugs - Modify the configured query statement and replace get_config with exec_command. (https://github.com/ansible/ansible/pull/61774)
- ce_vxlan_arp - update to fix some bugs - Modifying regular expressions. (https://github.com/ansible/ansible/pull/61995)
- ce_vxlan_vap - update to fix some bugs - Modify the Operator Difference between Python 2 and Python 3. (https://github.com/ansible/ansible/pull/61996)
- cloudformation_info - Fix a KeyError returning information about the stack(s).
- collection loader - ensure Jinja function cache is fully-populated before lookup
- collection loader - fixed relative imports on Python 2.7, ensure pluginloader caches use full name to prevent names from being clobbered (https://github.com/ansible/ansible/pull/60317)
- cron and cronvar - use get_bin_path utility to locate the default crontab executable instead of the hardcoded /usr/bin/crontab. (https://github.com/ansible/ansible/pull/59765)
- cron cronvar - only run ``get_bin_path()`` once
- display - remove leading space when displaying WARNING messages
- docker_compose - fix issue where docker deprecation warning results in ansible erroneously reporting a failure
- docker_container - improve error behavior when parsing port ranges fails.
- ecs_certificate - Always specify header ``connection: keep-alive`` for ECS API connections.
- ecs_certificate - Fix formatting of contents of ``full_chain_path``.
- fix if equals error code command is not found(https://github.com/ansible/ansible/pull/62529)
- get_url - Don't treat no checksum as a checksum match (https://github.com/ansible/ansible/issues/61978)
- iosxr - support cases where a normal commit operation also throws a prompt (https://github.com/ansible/ansible/pull/62132)
- iosxr_l3_interfaces - Fixes IOSXR L3 which was having idempotent issue raised in issue #61844, also adding a RTT for iosxr_l3_interfaces resource module
- junos_config - Add commands alias to lines option to be in sync with other platforms (https://github.com/ansible/ansible/pull/62221)
- junos_config - allow validate config before committing to running configuration (https://github.com/ansible/ansible/pull/61969)
- junos_user - Add no_log=True to junos_user `encrypted_password` (https://github.com/ansible/ansible/pull/62184)
- k8s - ensure that apply works with check mode. Bumps minimum openshift version for apply to 0.9.2.
- mysql - Fix ``mysql_connect`` function's logic related to the ``cursor_class`` keyword argument (https://github.com/ansible/ansible/pull/61832).
- network_cli - ensure connection is established before returning the current prompt
- nxos_file_copy call get_capabilities to initiate device connection (https://github.com/ansible/ansible/pull/62103).
- nxos_l2_interfaces fix for integration tests failing to setup layer2 (https://github.com/ansible/ansible/pull/61887).
- nxos_lacp_interfaces fix integration test dependencies (https://github.com/ansible/ansible/pull/61947).
- openssh_keypair - public key's file attributes (permissions, owner, group, etc.) are now set to the same values as the private key.
- openssl_certificate - When provider is ``entrust``, use a ``connection: keep-alive`` header for ECS API connections.
- psexec - Fix issue where the Kerberos package was not detected as being available.
- psexec - Fix issue where the ``interactive`` option was not being passed down to the library.
- purefa_info - Fix missing API version check when calling I(admins) or I(all) as the subset
- rabbitmq lookup plugin - Fix for rabbitmq lookups failing when using pika v1.0.0 and newer.
- rabbitmq_publish - Fix to ensure the module works correctly for pika v1.0.0 and later. (https://github.com/ansible/ansible/pull/61960)
- this fix result in no more traceback on empty config when state is 'merged', 'replaced' or 'overridden'. (https://github.com/ansible/ansible/pull/62518).
- tower inventory plugin - fix TypeError when giving inventory_id as integer (https://github.com/ansible/ansible/issues/61333)
- user - update docs to reflect proper way to remove account from all groups
- vmware - Ensure we can use the modules with Python < 2.7.9 or RHEL/CentOS < 7.4, this as soon as ``validate_certs`` is disabled.
- vmware_vcenter_statistics - Fix some corner cases like increasing some interval and decreasing another at the same time.
- win_become - Do not dispose of one of the logon tokens until after the process has run
- win_exec_wrapper - Be more defensive when it comes to getting unhandled exceptions

v2.9.0b1
========

Release Summary
---------------

| Release Date: 2019-09-05
| `Porting Guide <https://docs.ansible.com/ansible/devel/porting_guides.html>`__


Minor Changes
-------------

- Add I(preferred_arrays) param to enable preferred arrays to be set in a host configuration. (https://github.com/ansible/ansible/pull/59735)
- Add ability to force a protection group snapshot to immeadiatley replicate to a remote array (if configured)
- Add date header to the email based on local time in mail module (https://github.com/ansible/ansible/issues/58808).
- Add folder option in vmware_datastore_cluster to place datastore cluster in specific folder (https://github.com/ansible/ansible/issues/48010).
- Add folder option in vmware_dvswitch to place distributed switch in a network specific folder (https://github.com/ansible/ansible/issues/54986).
- Add installation documentation for vSphere Automation SDK for Python in vmware inventory plugin docs (https://github.com/ansible/ansible/issues/57224).
- Add managed object identifier (moId) and vim reference (vimref) of virtual machine in guest facts (https://github.com/ansible/ansible/issues/53372).
- Add new option to default standard out callback plugin, ``ANSIBLE_CHECK_MODE_MARKERS``, which adds check mode markers (``DRY RUN``, ``CHECK_MODE``) to the output when running in check mode. It is off by default.
- Add support for NIS in an NFS directory service and support for specifying an OU for an SMD directory service (https://github.com/ansible/ansible/pull/59608)
- Add support for `check_mode`
- Add toggle to show per host task start on default callback
- Added C# module util that implements various access token functions
- Added a parameter to allow remounting a filesystem
- Added new `throttle` keyword, which can be used at the task, block, or play level to limit the number of workers (up to the specified forks or serial setting) allowed.
- Added new parameters hostname and subdomain to kubevirt_vm module.
- Adjusted PowerShell and C# collection util imports to use a Python package name that reflects the location of the util in the collection. This is a breaking change, for more information see :ref:`porting_2.9_guide` for more information.
- All previouslly deprecated sudo/su and module locale global settings have been removed.
- Allow ansible-doc to return JSON as output.
- Allow debugger to take a templated value (https://github.com/ansible/ansible/pull/53587)
- Allow expanded options for user to control behaviour on duplicate YAML keys.
- Allow the users to enable or disable the rescue mode on Hetzner cloud servers
- Ansible now supports relative imports of module_utils files in modules and module_utils.
- Ansible will now warn if two aliases of the same option are used for Python modules.
- Check dvs in the given portgroup before accessing any properties of dvs (https://github.com/ansible/ansible/issues/59952). This can be due to permission issue or no association between distributed virtual portgroup and dvswitch.
- Check return value of FindByInventoryPath API used for finding folder value (https://github.com/ansible/ansible/issues/54823).
- Command line argument parsing - Switch from deprecated optparse to argparse
- Corrected API call for module.fail_json in command module.
- Enable ansible-doc to work with 'adjacent' collections via --playbook-dir option.
- Fix Key Error in get_vm() api in vmware.py module util (https://github.com/ansible/ansible/issues/60129).
- Handle user unauthorization errors in VMware REST API code for tagging (https://github.com/ansible/ansible/issues/58326).
- Implement config options for ``display_ok_hosts`` and ``display_skipped_hosts`` in unixy callback plugin
- InventoryManager - Speed up host subset calculation by performing direct host uuid comparisons, instead of Host object comparisons
- Jinja tests - Remove deprecated functionality of registering tests as filters (https://github.com/ansible/ansible/issues/55319)
- Make VM name and VM UUID as mutual exclusive and required one of (https://github.com/ansible/ansible/issues/57580).
- Make ``ansible_index_var`` accessible as a magic variable.
- Meraki modules now return data in snake_case instead of camelCase. The ANSIBLE_MERAKI_FORMAT environment variable can be set to camelcase to revert back to camelcase until deprecation in Ansible 2.13.
- Now callback plugins MUST allow for setting options as deprecation period that allowed older callbacks to ignore this is over.
- Refactored ``ansible-galaxy collections`` API code to be more friendly for future bugfixes
- Remove duplicate implementation of memory reservation parameter in vmware_guest (https://github.com/ansible/ansible/issues/54335).
- Restrict vcenter_folder to vCenter only, since folder creation api is not supported on ESXi hostsystem (https://github.com/ansible/ansible/issues/49938).
- Templar - Speed up ``is_template`` by lexing the string, instead of actually templating the string (https://github.com/ansible/ansible/pull/57489)
- The ``ali_instance_facts`` module has been renamed to ``ali_instance_info``.
- The ``aws_acm_facts`` module has been renamed to ``aws_acm_info``.
- The ``aws_az_facts`` module has been renamed to ``aws_az_info``.
- The ``aws_caller_facts`` module has been renamed to ``aws_caller_info``.
- The ``aws_kms_facts`` module has been renamed to ``aws_kms_info``.
- The ``aws_region_facts`` module has been renamed to ``aws_region_info``.
- The ``aws_s3_bucket_facts`` module has been renamed to ``aws_s3_bucket_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``aws_sgw_facts`` module has been renamed to ``aws_sgw_info``.
- The ``aws_waf_facts`` module has been renamed to ``aws_waf_info``.
- The ``azure_rm_aks_facts`` module has been renamed to ``azure_rm_aks_info``.
- The ``azure_rm_aksversion_facts`` module has been renamed to ``azure_rm_aksversion_info``.
- The ``azure_rm_applicationsecuritygroup_facts`` module has been renamed to ``azure_rm_applicationsecuritygroup_info``.
- The ``azure_rm_appserviceplan_facts`` module has been renamed to ``azure_rm_appserviceplan_info``.
- The ``azure_rm_automationaccount_facts`` module has been renamed to ``azure_rm_automationaccount_info``.
- The ``azure_rm_autoscale_facts`` module has been renamed to ``azure_rm_autoscale_info``.
- The ``azure_rm_availabilityset_facts`` module has been renamed to ``azure_rm_availabilityset_info``.
- The ``azure_rm_cdnendpoint_facts`` module has been renamed to ``azure_rm_cdnendpoint_info``.
- The ``azure_rm_cdnprofile_facts`` module has been renamed to ``azure_rm_cdnprofile_info``.
- The ``azure_rm_containerinstance_facts`` module has been renamed to ``azure_rm_containerinstance_info``.
- The ``azure_rm_containerregistry_facts`` module has been renamed to ``azure_rm_containerregistry_info``.
- The ``azure_rm_cosmosdbaccount_facts`` module has been renamed to ``azure_rm_cosmosdbaccount_info``.
- The ``azure_rm_deployment_facts`` module has been renamed to ``azure_rm_deployment_info``.
- The ``azure_rm_resourcegroup_facts`` module has been renamed to ``azure_rm_resourcegroup_info``.
- The ``bigip_device_facts`` module has been renamed to ``bigip_device_info``.
- The ``bigiq_device_facts`` module has been renamed to ``bigiq_device_info``.
- The ``cloudformation_facts`` module has been renamed to ``cloudformation_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``cloudfront_facts`` module has been renamed to ``cloudfront_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``cloudwatchlogs_log_group_facts`` module has been renamed to ``cloudwatchlogs_log_group_info``.
- The ``cs_instance_facts`` module has been deprecated. Use ``cs_instance_info`` instead.
- The ``cs_zone_facts`` module has been deprecated. Use ``cs_zone_info`` instead.
- The ``digital_ocean_account_facts`` module has been renamed to ``digital_ocean_account_info``.
- The ``digital_ocean_certificate_facts`` module has been renamed to ``digital_ocean_certificate_info``.
- The ``digital_ocean_domain_facts`` module has been renamed to ``digital_ocean_domain_info``.
- The ``digital_ocean_firewall_facts`` module has been renamed to ``digital_ocean_firewall_info``.
- The ``digital_ocean_floating_ip_facts`` module has been renamed to ``digital_ocean_floating_ip_info``.
- The ``digital_ocean_image_facts`` module has been renamed to ``digital_ocean_image_info``.
- The ``digital_ocean_load_balancer_facts`` module has been renamed to ``digital_ocean_load_balancer_info``.
- The ``digital_ocean_region_facts`` module has been renamed to ``digital_ocean_region_info``.
- The ``digital_ocean_size_facts`` module has been renamed to ``digital_ocean_size_info``.
- The ``digital_ocean_snapshot_facts`` module has been renamed to ``digital_ocean_snapshot_info``.
- The ``digital_ocean_sshkey_facts`` module has been deprecated. Use ``digital_ocean_sshkey_info`` instead.
- The ``digital_ocean_tag_facts`` module has been renamed to ``digital_ocean_tag_info``.
- The ``digital_ocean_volume_facts`` module has been renamed to ``digital_ocean_volume_info``.
- The ``ec2_ami_facts`` module has been renamed to ``ec2_ami_info``.
- The ``ec2_asg_facts`` module has been renamed to ``ec2_asg_info``.
- The ``ec2_customer_gateway_facts`` module has been renamed to ``ec2_customer_gateway_info``.
- The ``ec2_eip_facts`` module has been renamed to ``ec2_eip_info``.
- The ``ec2_elb_facts`` module has been renamed to ``ec2_elb_info``.
- The ``ec2_eni_facts`` module has been renamed to ``ec2_eni_info``.
- The ``ec2_group_facts`` module has been renamed to ``ec2_group_info``.
- The ``ec2_instance_facts`` module has been renamed to ``ec2_instance_info``.
- The ``ec2_lc_facts`` module has been renamed to ``ec2_lc_info``.
- The ``ec2_placement_group_facts`` module has been renamed to ``ec2_placement_group_info``.
- The ``ec2_snapshot_facts`` module has been renamed to ``ec2_snapshot_info``.
- The ``ec2_vol_facts`` module has been renamed to ``ec2_vol_info``.
- The ``ec2_vpc_dhcp_option_facts`` module has been renamed to ``ec2_vpc_dhcp_option_info``.
- The ``ec2_vpc_endpoint_facts`` module has been renamed to ``ec2_vpc_endpoint_info``.
- The ``ec2_vpc_igw_facts`` module has been renamed to ``ec2_vpc_igw_info``.
- The ``ec2_vpc_nacl_facts`` module has been renamed to ``ec2_vpc_nacl_info``.
- The ``ec2_vpc_nat_gateway_facts`` module has been renamed to ``ec2_vpc_nat_gateway_info``.
- The ``ec2_vpc_net_facts`` module has been renamed to ``ec2_vpc_net_info``.
- The ``ec2_vpc_peering_facts`` module has been renamed to ``ec2_vpc_peering_info``.
- The ``ec2_vpc_route_table_facts`` module has been renamed to ``ec2_vpc_route_table_info``.
- The ``ec2_vpc_subnet_facts`` module has been renamed to ``ec2_vpc_subnet_info``.
- The ``ec2_vpc_vgw_facts`` module has been renamed to ``ec2_vpc_vgw_info``.
- The ``ec2_vpc_vpn_facts`` module has been renamed to ``ec2_vpc_vpn_info``.
- The ``ecs_service_facts`` module has been renamed to ``ecs_service_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ecs_taskdefinition_facts`` module has been renamed to ``ecs_taskdefinition_info``.
- The ``efs_facts`` module has been renamed to ``efs_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``elasticache_facts`` module has been renamed to ``elasticache_info``.
- The ``elb_application_lb_facts`` module has been renamed to ``elb_application_lb_info``.
- The ``elb_classic_lb_facts`` module has been renamed to ``elb_classic_lb_info``.
- The ``elb_target_facts`` module has been renamed to ``elb_target_info``.
- The ``elb_target_group_facts`` module has been renamed to ``elb_target_group_info``.
- The ``gcp_bigquery_dataset_facts`` module was renamed to ``gcp_bigquery_dataset_info``.
- The ``gcp_bigquery_table_facts`` module was renamed to ``gcp_bigquery_table_info``.
- The ``gcp_cloudbuild_trigger_facts`` module was renamed to ``gcp_cloudbuild_trigger_info``.
- The ``gcp_compute_address_facts`` module was renamed to ``gcp_compute_address_info``.
- The ``gcp_compute_backend_bucket_facts`` module was renamed to ``gcp_compute_backend_bucket_info``.
- The ``gcp_compute_backend_service_facts`` module was renamed to ``gcp_compute_backend_service_info``.
- The ``gcp_compute_disk_facts`` module was renamed to ``gcp_compute_disk_info``.
- The ``gcp_compute_firewall_facts`` module was renamed to ``gcp_compute_firewall_info``.
- The ``gcp_compute_forwarding_rule_facts`` module was renamed to ``gcp_compute_forwarding_rule_info``.
- The ``gcp_compute_global_address_facts`` module was renamed to ``gcp_compute_global_address_info``.
- The ``gcp_compute_global_forwarding_rule_facts`` module was renamed to ``gcp_compute_global_forwarding_rule_info``.
- The ``gcp_compute_health_check_facts`` module was renamed to ``gcp_compute_health_check_info``.
- The ``gcp_compute_http_health_check_facts`` module was renamed to ``gcp_compute_http_health_check_info``.
- The ``gcp_compute_https_health_check_facts`` module was renamed to ``gcp_compute_https_health_check_info``.
- The ``gcp_compute_image_facts`` module was renamed to ``gcp_compute_image_info``.
- The ``gcp_compute_instance_facts`` module was renamed to ``gcp_compute_instance_info``.
- The ``gcp_compute_instance_group_facts`` module was renamed to ``gcp_compute_instance_group_info``.
- The ``gcp_compute_instance_group_manager_facts`` module was renamed to ``gcp_compute_instance_group_manager_info``.
- The ``gcp_compute_instance_template_facts`` module was renamed to ``gcp_compute_instance_template_info``.
- The ``gcp_compute_interconnect_attachment_facts`` module was renamed to ``gcp_compute_interconnect_attachment_info``.
- The ``gcp_compute_network_facts`` module was renamed to ``gcp_compute_network_info``.
- The ``gcp_compute_region_disk_facts`` module was renamed to ``gcp_compute_region_disk_info``.
- The ``gcp_compute_route_facts`` module was renamed to ``gcp_compute_route_info``.
- The ``gcp_compute_router_facts`` module was renamed to ``gcp_compute_router_info``.
- The ``gcp_compute_ssl_certificate_facts`` module was renamed to ``gcp_compute_ssl_certificate_info``.
- The ``gcp_compute_ssl_policy_facts`` module was renamed to ``gcp_compute_ssl_policy_info``.
- The ``gcp_compute_subnetwork_facts`` module was renamed to ``gcp_compute_subnetwork_info``.
- The ``gcp_compute_target_http_proxy_facts`` module was renamed to ``gcp_compute_target_http_proxy_info``.
- The ``gcp_compute_target_https_proxy_facts`` module was renamed to ``gcp_compute_target_https_proxy_info``.
- The ``gcp_compute_target_pool_facts`` module was renamed to ``gcp_compute_target_pool_info``.
- The ``gcp_compute_target_ssl_proxy_facts`` module was renamed to ``gcp_compute_target_ssl_proxy_info``.
- The ``gcp_compute_target_tcp_proxy_facts`` module was renamed to ``gcp_compute_target_tcp_proxy_info``.
- The ``gcp_compute_target_vpn_gateway_facts`` module was renamed to ``gcp_compute_target_vpn_gateway_info``.
- The ``gcp_compute_url_map_facts`` module was renamed to ``gcp_compute_url_map_info``.
- The ``gcp_compute_vpn_tunnel_facts`` module was renamed to ``gcp_compute_vpn_tunnel_info``.
- The ``gcp_container_cluster_facts`` module was renamed to ``gcp_container_cluster_info``.
- The ``gcp_container_node_pool_facts`` module was renamed to ``gcp_container_node_pool_info``.
- The ``gcp_dns_managed_zone_facts`` module was renamed to ``gcp_dns_managed_zone_info``.
- The ``gcp_dns_resource_record_set_facts`` module was renamed to ``gcp_dns_resource_record_set_info``.
- The ``gcp_iam_role_facts`` module was renamed to ``gcp_iam_role_info``.
- The ``gcp_iam_service_account_facts`` module was renamed to ``gcp_iam_service_account_info``.
- The ``gcp_pubsub_subscription_facts`` module was renamed to ``gcp_pubsub_subscription_info``.
- The ``gcp_pubsub_topic_facts`` module was renamed to ``gcp_pubsub_topic_info``.
- The ``gcp_redis_instance_facts`` module was renamed to ``gcp_redis_instance_info``.
- The ``gcp_resourcemanager_project_facts`` module was renamed to ``gcp_resourcemanager_project_info``.
- The ``gcp_sourcerepo_repository_facts`` module was renamed to ``gcp_sourcerepo_repository_info``.
- The ``gcp_spanner_database_facts`` module was renamed to ``gcp_spanner_database_info``.
- The ``gcp_spanner_instance_facts`` module was renamed to ``gcp_spanner_instance_info``.
- The ``gcp_sql_database_facts`` module was renamed to ``gcp_sql_database_info``.
- The ``gcp_sql_instance_facts`` module was renamed to ``gcp_sql_instance_info``.
- The ``gcp_sql_user_facts`` module was renamed to ``gcp_sql_user_info``.
- The ``gcp_tpu_node_facts`` module was renamed to ``gcp_tpu_node_info``.
- The ``gcpubsub_facts`` module has been renamed to ``gcpubsub_info``.
- The ``github_webhook_facts`` module has been renamed to ``github_webhook_info``.
- The ``gluster_heal_facts`` module has been renamed to ``gluster_heal_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_datacenter_facts`` module has been renamed to ``hcloud_datacenter_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_floating_ip_facts`` module has been renamed to ``hcloud_floating_ip_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_image_facts`` module has been renamed to ``hcloud_image_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_location_facts`` module has been renamed to ``hcloud_location_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_server_facts`` module has been renamed to ``hcloud_server_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_server_type_facts`` module has been renamed to ``hcloud_server_type_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_ssh_key_facts`` module has been renamed to ``hcloud_ssh_key_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hcloud_volume_facts`` module has been renamed to ``hcloud_volume_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``hpilo_facts`` module has been renamed to ``hpilo_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``iam_mfa_device_facts`` module has been renamed to ``iam_mfa_device_info``.
- The ``iam_role_facts`` module has been renamed to ``iam_role_info``.
- The ``iam_server_certificate_facts`` module has been renamed to ``iam_server_certificate_info``.
- The ``idrac_redfish_facts`` module has been renamed to ``idrac_redfish_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``intersight_facts`` module has been renamed to ``intersight_info``.
- The ``jenkins_job_facts`` module has been renamed to ``jenkins_job_info``.
- The ``k8s_facts`` module has been renamed to ``k8s_info``.
- The ``lambda_facts`` module has been deprecated. Use ``lambda_info`` instead.
- The ``memset_memstore_facts`` module has been renamed to ``memset_memstore_info``.
- The ``memset_server_facts`` module has been renamed to ``memset_server_info``.
- The ``na_ontap_gather_facts`` module has been deprecated. Use ``na_ontap_info`` instead.
- The ``nginx_status_facts`` module has been deprecated. Use ``nginx_status_info`` instead.
- The ``one_image_facts`` module has been renamed to ``one_image_info``.
- The ``onepassword_facts`` module has been renamed to ``onepassword_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_datacenter_facts`` module has been renamed to ``oneview_datacenter_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_enclosure_facts`` module has been renamed to ``oneview_enclosure_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_ethernet_network_facts`` module has been renamed to ``oneview_ethernet_network_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_fc_network_facts`` module has been renamed to ``oneview_fc_network_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_fcoe_network_facts`` module has been renamed to ``oneview_fcoe_network_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_logical_interconnect_group_facts`` module has been renamed to ``oneview_logical_interconnect_group_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_network_set_facts`` module has been renamed to ``oneview_network_set_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``oneview_san_manager_facts`` module has been renamed to ``oneview_san_manager_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``online_server_facts`` module has been deprecated. Use ``online_server_info`` instead.
- The ``online_user_facts`` module has been deprecated. Use ``online_user_info`` instead.
- The ``os_flavor_facts`` module has been renamed to ``os_flavor_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_image_facts`` module has been renamed to ``os_image_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_keystone_domain_facts`` module has been renamed to ``os_keystone_domain_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_networks_facts`` module has been renamed to ``os_networks_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_port_facts`` module has been renamed to ``os_port_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_project_facts`` module has been renamed to ``os_project_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_server_facts`` module has been renamed to ``os_server_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_subnets_facts`` module has been renamed to ``os_subnets_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``os_user_facts`` module has been renamed to ``os_user_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_affinity_label_facts`` module has been renamed to ``ovirt_affinity_label_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_api_facts`` module has been renamed to ``ovirt_api_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_cluster_facts`` module has been renamed to ``ovirt_cluster_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_datacenter_facts`` module has been renamed to ``ovirt_datacenter_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_disk_facts`` module has been renamed to ``ovirt_disk_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_event_facts`` module has been renamed to ``ovirt_event_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_external_provider_facts`` module has been renamed to ``ovirt_external_provider_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_group_facts`` module has been renamed to ``ovirt_group_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_host_facts`` module has been renamed to ``ovirt_host_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_host_storage_facts`` module has been renamed to ``ovirt_host_storage_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_network_facts`` module has been renamed to ``ovirt_network_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_nic_facts`` module has been renamed to ``ovirt_nic_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_permission_facts`` module has been renamed to ``ovirt_permission_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_quota_facts`` module has been renamed to ``ovirt_quota_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_scheduling_policy_facts`` module has been renamed to ``ovirt_scheduling_policy_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_snapshot_facts`` module has been renamed to ``ovirt_snapshot_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_storage_domain_facts`` module has been renamed to ``ovirt_storage_domain_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_storage_template_facts`` module has been renamed to ``ovirt_storage_template_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_storage_vm_facts`` module has been renamed to ``ovirt_storage_vm_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_tag_facts`` module has been renamed to ``ovirt_tag_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_template_facts`` module has been renamed to ``ovirt_template_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_user_facts`` module has been renamed to ``ovirt_user_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_vm_facts`` module has been renamed to ``ovirt_vm_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``ovirt_vmpool_facts`` module has been renamed to ``ovirt_vmpool_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``purefa_facts`` module has been deprecated. Use ``purefa_info`` instead.
- The ``purefb_facts`` module has been deprecated. Use ``purefb_info`` instead.
- The ``python_requirements_facts`` module has been renamed to ``python_requirements_info``.
- The ``rds_instance_facts`` module has been renamed to ``rds_instance_info``.
- The ``rds_snapshot_facts`` module has been renamed to ``rds_snapshot_info``.
- The ``redfish_facts`` module has been renamed to ``redfish_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``redshift_facts`` module has been renamed to ``redshift_info``.
- The ``route53_facts`` module has been renamed to ``route53_info``.
- The ``scaleway_image_facts`` module has been deprecated. Use ``scaleway_image_info`` instead.
- The ``scaleway_ip_facts`` module has been deprecated. Use ``scaleway_ip_info`` instead.
- The ``scaleway_organization_facts`` module has been deprecated. Use ``scaleway_organization_info`` instead.
- The ``scaleway_security_group_facts`` module has been deprecated. Use ``scaleway_security_group_info`` instead.
- The ``scaleway_server_facts`` module has been deprecated. Use ``scaleway_server_info`` instead.
- The ``scaleway_snapshot_facts`` module has been deprecated. Use ``scaleway_snapshot_info`` instead.
- The ``scaleway_volume_facts`` module has been deprecated. Use ``scaleway_volume_info`` instead.
- The ``smartos_image_facts`` module has been renamed to ``smartos_image_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``vcenter_extension_facts`` module has been deprecated. Use ``vcenter_extension_info`` instead.
- The ``vertica_facts`` module has been renamed to ``vertica_info``. When called with the new name, the module no longer returns ``ansible_facts``.
- The ``vmware_about_facts`` module has been deprecated. Use ``vmware_about_info`` instead.
- The ``vmware_category_facts`` module has been deprecated. Use ``vmware_category_info`` instead.
- The ``vmware_cluster_facts`` module has been renamed to ``vmware_cluster_info``.
- The ``vmware_datastore_facts`` module has been renamed to ``vmware_datastore_info``.
- The ``vmware_drs_group_facts`` module has been deprecated. Use ``vmware_drs_group_info`` instead.
- The ``vmware_drs_rule_facts`` module has been deprecated. Use ``vmware_drs_rule_info`` instead.
- The ``vmware_dvs_portgroup_facts`` module has been deprecated. Use ``vmware_dvs_portgroup_info`` instead.
- The ``vmware_guest_boot_facts`` module has been deprecated. Use ``vmware_guest_boot_info`` instead.
- The ``vmware_guest_customization_facts`` module has been deprecated. Use ``vmware_guest_customization_info`` instead.
- The ``vmware_guest_disk_facts`` module has been deprecated. Use ``vmware_guest_disk_info`` instead.
- The ``vmware_guest_facts`` module has been renamed to ``vmware_guest_info``.
- The ``vmware_guest_snapshot_facts`` module has been renamed to ``vmware_guest_snapshot_info``.
- The ``vmware_host_capability_facts`` module has been deprecated. Use ``vmware_host_capability_info`` instead.
- The ``vmware_host_config_facts`` module has been deprecated. Use ``vmware_host_config_info`` instead.
- The ``vmware_host_dns_facts`` module has been deprecated. Use ``vmware_host_dns_info`` instead.
- The ``vmware_host_feature_facts`` module has been deprecated. Use ``vmware_host_feature_info`` instead.
- The ``vmware_host_firewall_facts`` module has been deprecated. Use ``vmware_host_firewall_info`` instead.
- The ``vmware_host_ntp_facts`` module has been deprecated. Use ``vmware_host_ntp_info`` instead.
- The ``vmware_host_package_facts`` module has been deprecated. Use ``vmware_host_package_info`` instead.
- The ``vmware_host_service_facts`` module has been deprecated. Use ``vmware_host_service_info`` instead.
- The ``vmware_host_ssl_facts`` module has been deprecated. Use ``vmware_host_ssl_info`` instead.
- The ``vmware_host_vmhba_facts`` module has been deprecated. Use ``vmware_host_vmhba_info`` instead.
- The ``vmware_host_vmnic_facts`` module has been deprecated. Use ``vmware_host_vmnic_info`` instead.
- The ``vmware_local_role_facts`` module has been deprecated. Use ``vmware_local_role_info`` instead.
- The ``vmware_local_user_facts`` module has been deprecated. Use ``vmware_local_user_info`` instead.
- The ``vmware_portgroup_facts`` module has been deprecated. Use ``vmware_portgroup_info`` instead.
- The ``vmware_resource_pool_facts`` module has been deprecated. Use ``vmware_resource_pool_info`` instead.
- The ``vmware_tag_facts`` module has been renamed to ``vmware_tag_info``.
- The ``vmware_target_canonical_facts`` module has been deprecated. Use ``vmware_target_canonical_info`` instead.
- The ``vmware_vm_facts`` module has been renamed to ``vmware_vm_info``.
- The ``vmware_vmkernel_facts`` module has been deprecated. Use ``vmware_vmkernel_info`` instead.
- The ``vmware_vswitch_facts`` module has been deprecated. Use ``vmware_vswitch_info`` instead.
- The ``vultr_account_facts`` module has been deprecated. Use ``vultr_account_info`` instead.
- The ``vultr_block_storage_facts`` module has been deprecated. Use ``vultr_block_storage_info`` instead.
- The ``vultr_dns_domain_facts`` module has been deprecated. Use ``vultr_dns_domain_info`` instead.
- The ``vultr_firewall_group_facts`` module has been deprecated. Use ``vultr_firewall_group_info`` instead.
- The ``vultr_network_facts`` module has been deprecated. Use ``vultr_network_info`` instead.
- The ``vultr_os_facts`` module has been deprecated. Use ``vultr_os_info`` instead.
- The ``vultr_plan_facts`` module has been deprecated. Use ``vultr_plan_info`` instead.
- The ``vultr_region_facts`` module has been deprecated. Use ``vultr_region_info`` instead.
- The ``vultr_server_facts`` module has been deprecated. Use ``vultr_server_info`` instead.
- The ``vultr_ssh_key_facts`` module has been deprecated. Use ``vultr_ssh_key_info`` instead.
- The ``vultr_startup_script_facts`` module has been deprecated. Use ``vultr_startup_script_info`` instead.
- The ``vultr_user_facts`` module has been deprecated. Use ``vultr_user_info`` instead.
- The ``xenserver_guest_facts`` module has been renamed to ``xenserver_guest_info``.
- The ``zabbix_group_facts`` module has been renamed to ``zabbix_group_info``.
- The ``zabbix_host_facts`` module has been renamed to ``zabbix_host_info``.
- The `podman` connection plugin now supports pipelining.
- Typecast vlan id to string in nmcli module (https://github.com/ansible/ansible/issues/58949).
- When using `fetch_nested` fetch also list of href, instead only single object hrefs.
- acme_certificate - all alternate chains can be retrieved using the new ``retrieve_all_alternates`` option.
- add purge_tags parameter to s3_bucket to allow preservation of existing tags when updating tags.
- added ``use`` option to ``hostname`` module to allow user to override autodetection.
- ansible-galaxy - Added the ``collection build`` command to build a collection tarball ready for uploading.
- ansible-galaxy - Added the ``collection init`` command to create a skeleton collection directory.
- ansible-galaxy - Added the ``collection install`` command to install collections locally.
- ansible-galaxy - Added the ``collection publish`` command to publish a collection tarball to a Galaxy server.
- apt - Remove deprecated ``installed`` and ``removed`` aliases (https://github.com/ansible/ansible/issues/55311)
- aws_eks_cluster - Ansible may now wait until an EKS cluster is fully removed before moving on.
- backports.ssl_match_hostname - Update bundled copy of backports.ssl_match_hostname from 3.4.0.2 to 3.7.0.1 (https://github.com/ansible/ansible/issues/51794)
- changed task module/action parsing to report more helpful errors
- collection role dependencies will first search for unqualified role names in the containing collection.
- cosmetic change, simplify FC WWN facts gathering on Solaris
- default collection - a playbook run inside a collection (eg, as part of a runme.sh integration test) will first search the containing collection for unqualified module/action references (https://github.com/ansible/ansible/pull/61415)
- distro - Update bundled copy of distro from 1.3.0 to 1.4.0 (https://github.com/ansible/ansible/issues/55302)
- dnf - Provide a better error message including python version info when installing python-dnf fails
- dnf - set lock_timeout to a sane default (30 seconds, as is the cli)
- docker_container - add ``mounts`` option.
- docker_container - now tests for mount endpoint collisions (for both ``mounts`` and ``volumes``) to abort early when collisions are found
- docker_image - Add ``build.target`` option.
- docker_image - added ``extra_hosts`` argument (https://github.com/ansible/ansible/issues/59233)
- docker_swarm_service - Add ``npipe`` mount support.
- docker_swarm_service - Remove requirement of ``secret_id`` on ``secrets`` and ``config_id`` on ``configs``.
- docker_swarm_service - Support passing dictionaries in ``networks`` to allow setting ``aliases`` and ``options``.
- ec2 - Remove deprecated ``device_type`` option (https://github.com/ansible/ansible/issues/55306)
- ec2_eip - Added support for BYOIP to ec2_eip module and filtering reusable addresses based on tags (https://github.com/ansible/ansible/pull/59180).
- ec2_instance - Remove deprecated ``network.ebs_optimized`` option (https://github.com/ansible/ansible/issues/55307)
- ec2_lc - Remove deprecated ``device_type`` option (https://github.com/ansible/ansible/issues/55308)
- eos_use_sessions is now type boolean instead of int.
- file - Extend ``-diff`` to return list of files and folders that will be removed in case of ``state=absent`` (https://github.com/ansible/ansible/pull/56353)
- gcp_compute - Added additional environment variables to the `gcp_compute` inventory plugin to align with the rest of the `gcp_*` modules.
- get_certificate - added ``proxy_*`` options.
- get_certificate - now works with both PyOpenSSL and cryptography Python libraries. Autodetection can be overridden with ``select_crypto_backend`` option.
- get_certificate - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- getent - add service parameter to getent to lookup specified service
- git - add a ``gpg_whitelist`` option to specify a list of trusted GPG fingerprints for when ``verify_commit`` is enabled (https://github.com/ansible/ansible/pull/55396)
- k8s - add `wait_sleep` parameter (number of seconds to sleep between checks).
- log_plays - Add a new log_folder option to the log_plays callback plugin.
- lookup_url - added ability to specify request headers
- magic variables - added a new ``ansible_parent_role_names`` magic variable that, when a role is included by another role, contains a list of all parent roles.
- magic variables - added a new ``ansible_parent_role_paths`` magic variable that, when a role is included by another role, contains a list of all parent role paths.
- meraki_* - Idempotency check has been rewritten. The new version is more thorough.
- meraki_* - Meraki modules now return data when no changes are made.
- meraki_* - Modules now respect 429 (rate limit) and 500/502 errors with a graceful backoff.
- meraki_admin - Add support for check mode.
- meraki_config_template - Enable check mode.
- meraki_content_filtering - Add support for check mode.
- meraki_mr_l3_firewall - Integration test now uses net_id in some tests for improved code coverage.
- meraki_network - Add support for disabling remote status page on a network.
- meraki_network - Add support for enabling or disabling VLANs on a network.
- meraki_snmp - Add support for check mode.
- meraki_ssid - Add examples to documentation.
- meraki_vlan - Add support for check mode.
- mysql_db - now behaves better w.r.t ``changed`` results in ``check_mode``
- mysql_db now supports creation and deletion of multiple databases (https://github.com/ansible/ansible/issues/58370)
- mysql_db now supports multiple databases in dump operation (https://github.com/ansible/ansible/issues/56059)
- openssh_keypair - add key ``comment`` to return value
- openssl_certificate - Add support for a new provider ``entrust`` (https://github.com/ansible/ansible/pull/59272).
- openssl_certificate - add support for subject key identifier and authority key identifier extensions. Subject key identifiers are created by default when not explicitly disabled.
- openssl_certificate - the ``assertonly`` provider has been deprecated. See examples in module to see how to replace it.
- openssl_certificate - the ``ownca`` provider creates authority key identifiers if not explicitly disabled with ``ownca_create_authority_key_identifier: no``.
- openssl_certificate - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- openssl_certificate_info - add ``ocsp_uri`` return value.
- openssl_certificate_info - add support for subject key identifier and authority key identifier extensions.
- openssl_certificate_info - added ``issuer_ordered`` and ``subject_ordered`` return values.
- openssl_certificate_info - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- openssl_csr - add support for subject key identifier and authority key identifier extensions.
- openssl_csr - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- openssl_csr_info - add support for subject key identifier and authority key identifier extensions.
- openssl_csr_info - added ``subject_ordered`` return value.
- openssl_csr_info - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- openssl_privatekey - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- openssl_privatekey_info - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- openssl_publickey - now works with both PyOpenSSL and cryptography Python libraries. Autodetection can be overridden with ``select_crypto_backend`` option.
- openssl_publickey - the ``pyopenssl`` backend has been deprecated, it will be removed in Ansible 2.13.
- os_network - added MTU support when creating/updating a network
- os_network - added dns_domain support when creating/updating a network
- ovirt4 inventory - Updated the dynamic inventory script for Python 3 support
- pluribus networks modules to handle empty output string.
- postgresql_ext - add version parameter to support creation / update extensions of specific versions (https://github.com/ansible/ansible/pull/58381)
- postgresql_query - Add array handling for positional_args and named_args parameters (https://github.com/ansible/ansible/issues/59955).
- postgresql_query - add autocommit parameter to support commands that can't be run inside a transaction block (https://github.com/ansible/ansible/pull/58704)
- postgresql_user - Add the new parameter ``groups`` (https://github.com/ansible/ansible/pull/60638).
- psrp - Added the ``ansible_psrp_reconnection_backoff`` variable to control the reconnection backoff setting - https://github.com/ansible/ansible/issues/58714
- purefa_ra - change resulting fact dict from I(ansible_facts) to I(ra_info)  (https://github.com/ansible/ansible/pull/61355)
- purefa_user - change module parameter I(api_token) to I(api) and to stop clash with known variable.
- purefa_user - change resulting fact dict from I(ansible_facts) to I(user_info)  (https://github.com/ansible/ansible/pull/61353)
- purefa_user - change resulting facts from I(api_token) to I(user_api) for clarity (https://github.com/ansible/ansible/pull/57588)
- purefb_fs - Deprecate I(nfs) param and replace with I(nfsv3). Add params I(user_quota) and I(group_quota) (https://github.com/ansible/ansible/pull/59559)
- purefb_s3user - change resulting fact dict from I(ansible_facts) to I(s3user_info)  (https://github.com/ansible/ansible/pull/61356)
- rabbitmq_binding - added missing SSL options for HTTP GET and DELETE requests
- redhat_subscription - allow to set syspurpose attributes (https://github.com/ansible/ansible/pull/59850)
- redhat_subscription - do not call ``subscribtion-manager`` command, when it is not necessary (https://github.com/ansible/ansible/pull/58665)
- redhat_subscription - made code more testable (https://github.com/ansible/ansible/pull/58665)
- refactor iSCSI network facts for AIX and HP-UX, add unit test, remove external grep call
- removed previously deprecated ``get_md5`` option from M(stat) module.
- roles and plugins in collections may now be stored in subdirectories under the roles or plugin-type dirs (https://github.com/ansible/ansible/pull/60682)
- roles that define a collections search list in metadata will attempt to use the defined search list when resolving unqualified role names.
- selectors2 - Update bundled copy of selectors2 from 1.1.0 to 1.1.1 (https://github.com/ansible/ansible/issues/55300)
- selinux_special_filesystems config can be specified via environment variable ``ANSIBLE_SELINUX_SPECIAL_FS``
- setup - octal escape sequences are now evaluated for mount facts pulled from /etc/mtab
- six - Update bundled copy of six from 1.11.0 to 1.12.0 (https://github.com/ansible/ansible/issues/55303)
- syslog_json - Allow configuration of the syslog_json plugin via an Ansible configuration file.
- uri - Remove deprecated ``HEADER_`` support (https://github.com/ansible/ansible/issues/55310)
- vApp setting can be set while VM creation in vmware_guest (https://github.com/ansible/ansible/issues/50617).
- validate-modules - change numeric error codes to descriptive strings (https://github.com/ansible/ansible/pull/60711)
- vcenter_folder - returns a dict instead of a string, the previous output is now in the 'msg' key
- vcenter_folder - returns now the full path of the file in the new 'path' key
- vmware - The VMware modules can now access a server behind a HTTP proxy (https://github.com/ansible/ansible/pull/52936)
- vmware - reduces the memory usage during the object lookup
- vmware_cluster - Refactor into several modules (vmware_cluster, vmware_cluster_drs, vmware_cluster_ha and vmware_cluster_vsan)
- vmware_cluster_facts now supports tag facts (https://github.com/ansible/ansible/issues/46458).
- vmware_datastore_facts - When no datastore was found, returns an empty list.
- vmware_datastore_maintenancemode - Raise an error if the datastore does not exist.
- vmware_guest_disk module supports use_instance_uuid parameter since Ansible 2.8 (https://github.com/ansible/ansible/issues/56021).
- vmware_guest_disk_facts module - added bus number of the SCSI controller to the output (https://github.com/ansible/ansible/pull/56442)
- vmware_host_datastore - Ability to directly target a ESXi.
- vmware_host_facts now supports tag facts (https://github.com/ansible/ansible/issues/46461).
- vmware_portgroup accepts list of ESXi hostsystem. Modified get_all_host_objs API to accept list of hostsystems.
- vmware_vm_facts supports folder as a filter to gather fact for VM (https://github.com/ansible/ansible/issues/56125).
- vsphere_copy - The ``host`` and ``login`` parameters are deprecated, use `hostname` and ``username`` like for the other VMware modules.
- vsphere_copy - The module can now also be used with standalone ESXi.
- vultr - the retry on failure functionality was changed to use an exponential backoff behaviour.
- vultr_server - Implemented support for using the ID instead of a name to match a resource, especially useful for region, plan and OS type.
- win_domain_user - Allow to only set password when it actually changed (https://github.com/ansible/ansible/issues/58246)
- win_domain_user - Make the query user try catch block more accurate for missing identity (https://github.com/ansible/ansible/issues/57719)
- win_domain_user and win_domain_group: add created result boolean (https://github.com/ansible/ansible/issues/57547)
- win_xml - Added 'count' module parameter which will return number of nodes matched by xpath if set to yes/true
- win_xml - Behaviour change, fragment no longer required when processing element type nodes and state=absent.
- win_xml - Behaviour change, module now processes all nodes specified by xpath, not just first encountered.
- win_xml - Some output messages worded differently now the module uses a generic method to save changes.
- xenserver_guest - wait_for_ip_address is now ignored when state=absent (https://github.com/ansible/ansible/issues/55348).
- xml - Introduce ``insertbefore`` and ``insertafter`` to specify the position (https://github.com/ansible/ansible/pull/44811)
- yum - set lock_timeout to a sane default (30 seconds, as is the cli)
- zabbix_action - ``esc_period`` is now required to reflect actual Zabbix API call
- zabbix_action - support for new condition operators (``matches``, ``does not match``, ``Yes``, ``No``) added in Zabbix 4.0 and Zabbix 4.2 (https://www.zabbix.com/documentation/4.2/manual/api/reference/action/object#action_filter_condition)
- zabbix_screen - added an option to sort hosts on a zabbix screen alphabetically
- zabbix_screen - updated documentation and module arguments
- zabbix_template - it is no longer accepted to provide parameters `template_name` and `template_groups` when using `template_json`
- zabbix_template - new parameter `dump_format` allows user to specify in which format (JSON or XML) should a template be exported from Zabbix
- zabbix_template - new parameter `template_xml` adds support for importing templates from XML documents
- zabbix_template - now allows import of multiple templates at once when using `template_json` or `template_xml` parameters
- zabbix_template - parameter `template_groups` is now required when passing `template_name` and template is being created for the fisrt time. Not required when template is being updated.
- zabbix_template - parameters `template_name`, `template_json` and `template_xml` are now mutually exclusive
- zabbix_template - template can now be updated with just a `clear_templates` parameter without requiring any additional parameters to be passed (see examples of the module)
- zfs - Remove deprecated key=value 'option' (https://github.com/ansible/ansible/issues/55318)

Deprecated Features
-------------------

- Deprecated ``net_interface``, ``net_linkagg``, ``net_lldp_interface``, ``net_l2_interface``, ``net_vlan``, ``net_l3_interface``, ``net_vrf``, ``net_lldp``, ``net_banner``, ``net_logging``, ``net_system``, ``net_user``, and ``net_static_route``. Please use either the equivalent network role or the platform-specific resource module.
- Deprecated setting the verbosity before the sub command for ``ansible-galaxy`` and ``ansible-vault``. Set the verbosity level after the sub command, e.g. do ``ansible-galaxy init -v`` and not ``ansible-galaxy -v init``.
- aws_kms - Deprecate mode, role_name, role_arn, grant_types and policy_clean_invalid_entries in favour of policy
- vmware_cluster - Deprecate DRS, HA and VSAN configuration in favour of new modules vmware_cluster_drs, vmware_cluster_ha and vmware_cluster_vsan.

Removed Features (previously deprecated)
----------------------------------------

- redis_kv - Remove deprecated lookup plugin (https://github.com/ansible/ansible/issues/59948)

Bugfixes
--------

- Add missing directory provided via ``--playbook-dir`` to adjacent collection loading
- Add no_log to credentials field to avoid disclosures, also switch type to jsonarg to avoid having users responsible for transformations.
- Allow config options that are type boolean to default to None rather than only True or False.
- AnsiballZ - Use ``importlib`` to load the module instead of ``imp`` on Python3+
- Ansible.Basic - Fix issue when deserilizing a JSON string that is not a dictionary - https://github.com/ansible/ansible/pull/55691
- Be sure to use the active state when checking for any_errors_fatal
- Clarify roles path target behaviour for ansible-galaxy
- Correctly handle delegate_to hostnames in loops (https://github.com/ansible/ansible/issues/59650)
- Do not re-use remote_user from previous loop iteration (https://github.com/ansible/ansible/issues/58876)
- Fix --diff to produce output when creating a new file (https://github.com/ansible/ansible/issues/57618)
- Fix PSLint errors regarding global vars (PSAvoidGlobalVars)
- Fix doc for proxy_username and proxy_password in yum_repository.py (https://github.com/ansible/ansible/pull/59068).
- Fix firewalld source option handling to be exclusive (https://github.com/ansible/ansible/issues/55683)
- Fix foreman inventory plugin when inventory caching is disabled
- Fix media type of RESTCONF requests.
- Fix privilege escalation support for the docker connection plugin when credentials need to be supplied (e.g. sudo with password).
- Fix regression warning on jinja2 delimiters in when statements (https://github.com/ansible/ansible/issues/56830)
- Fix regression when including a role with a custom filter (https://github.com/ansible/ansible/issues/57351)
- Fix strategy functions that update inventory and back 'add_host' and 'group_by' actions.
- Fix the issue that disk is not activated after its creation (https://github.com/ansible/ansible/issues/57412)
- Fixed a traceback in the ``git`` module when using an absolute path for the ``repo`` parameter.
- Fixed ce_bgp,first the pattern to be searched is need to change, otherwise there is no data to be found.then after running a task with this module,it will not show 'changed' correctly.
- Fixed ce_bgp_af,'changed' of module run restult is not showed, however the module run correctly,and update coommands of result is not correct.
- Fixed ce_bgp_neighbor, find specify bgp as information, as number is necessary and so on.
- Fixed ce_bgp_neighbor_af,update commands should be showed correctly, and xml for filter and edit are also re-factor as the software version upgrade and update.
- Fixed loading namespaced documentation fragments from collections.
- Fixed role's hash_params behavior to not union (https://github.com/ansible/ansible/issues/20596).
- Fixed some PSlint warnings
- For package_facts, correct information about apt being missing and fix missing attribute.
- Gather facts should use gather_subset config by default.
- Handle IndexError while parsing empty limit file (https://github.com/ansible/ansible/issues/59695).
- Handle improper variable substitution that was happening in safe_eval, it was always meant to just do 'type enforcement' and have Jinja2 deal with all variable interpolation. Also see CVE-2019-10156
- Inventory sources now respect setting ``hash_behaviour``. Previously each new inventory source would overwrite existing vars, even when ``hash_behavior`` was set to ``merge``.
- Make max_connections parameter work again in vmware_guest module (https://github.com/ansible/ansible/pull/58061).
- Module tracebacks are now recognized on stdout and stderr, intead of just on stderr.
- Only warn for bare variables if they are not type boolean (https://github.com/ansible/ansible/issues/53428)
- Pipelining now works with the buildah plugin.
- Redfish - Instead of building the Power URI from assumptions about URI structure, assemble from @odata.id information in the Chassis resource (https://github.com/ansible/ansible/issues/56137).
- Remove lingering ansible vault cipher (AES) after it beeing removed in
- SECURITY Fixed the python interpreter detection, added in 2.8.0alpha1, to properly mark the returned data as untemplatable. This prevents a malicious managed machine from running code on the controller via templating.
- TaskExecutor - Create new instance of the action plugin on each iteration when using until (https://github.com/ansible/ansible/issues/57886)
- TaskQueueManager - Ensure ``has_dead_workers`` can function, by using the correct reference, and only allow an exit code of 0. (https://github.com/ansible/ansible/issues/29124)
- To rename CheckPoint to Check_Point due to CP legal reasons. (https://github.com/ansible/ansible/pull/61172).
- Use async poll default setting for play tasks also, previouslly in only affected adhoc ansible.
- Use templated loop_var/index_var when looping include_* (https://github.com/ansible/ansible/issues/58820)
- acme_certificate - Only return challenges in ``challenge_data`` and ``challenge_data_dns`` which are not yet valid.
- acme_certificate - improve compatibility when finalizing ACME v2 orders. Fixes problem with Buypass' ACME v2 testing endpoint.
- acme_certificate - use ``ipaddress`` module bundled with Ansible for normalizations needed for OpenSSL backend.
- add options type info for Redfish modules (https://github.com/ansible/ansible/issues/54688)
- allow include_role to work with ansible command
- allow loading inventory plugins adjacent to playbooks
- allow python_requirements_facts to report on dependencies containing dashes
- ansible-galaxy - Fix url building to not truncate the URL (https://github.com/ansible/ansible/issues/61624)
- ansible-galaxy role - Fix issue where ``--server`` was not being used for certain ``ansible-galaxy role`` actions - https://github.com/ansible/ansible/issues/61609
- ansible-podman connection plugin - Fix case when mount of podman container fails and files can't be copied to/from container. Also add error handling in case of failed podman commands. (https://github.com/ansible/ansible/issues/57740)
- ansible-test now correctly enumerates submodules when a collection resides below the repository root
- ansible-test now creates output directories as needed for powershell coverage output before generating reports
- ansible-vault - fix error when multiple vault password files are specified (https://github.com/ansible/ansible/issues/57172)
- ansible.basics - fix core C# recursive call when logging fails (e.g. if insufficient permissions are held) (https://github.com/ansible/ansible/pull/59503)
- apt - Fixed the issue the cache being updated while auto-installing its dependencies even when ``update_cache`` is set to false.
- apt - fixed issue where allow_unauthenticated did not apply to dependencies when installing a deb directly
- apt - strip whitespaces in package names (https://github.com/ansible/ansible/issues/55741)
- apt_facts - fix performance regression when getting facts about apt packages (https://github.com/ansible/ansible/issues/60450)
- apt_repository - Fix crash caused by ``cache.update()`` raising an ``IOError`` due to a timeout in ``apt update`` (https://github.com/ansible/ansible/issues/51995)
- async - Fix async callback plugins to allow async output to be displayed when running command/shell (https://github.com/ansible/ansible/issues/15988)
- avoid choosing an unreadable ansible.cfg just because it exists.
- aws_ec2 inventory plugin - fixed race condition when trying to fetch IAM instance profile (role) credentials (https://github.com/ansible/ansible/pull/59638)
- aws_kms - Update key policy when key already exists
- aws_kms - Use ARN rather than ID so that cross-account changes function
- aws_kms - fix exception when only Key ID is passed
- aws_kms module ensure tag keys have their case preserved by avoiding a second unnecessary format conversion
- aws_s3 - Improve usability when the execution host lacks MD5 support (e.g. due to FIPS-140-2).
- aws_s3 - Try to wait for the bucket to exist before setting the access control list.
- aws_ses_identity module works when region is provided using config or environment variables rather than the region parameter (https://github.com/ansible/ansible/issues/51531)
- azure_rm_dnsrecordset_info - no longer returns empty ``azure_dnsrecordset`` facts when called as ``_info`` module.
- azure_rm_networkinterface_info - Fix up instances when ``ansible_facts`` is returned for the older ``_facts`` alias.
- azure_rm_resourcegroup_info - no longer returns ``azure_resourcegroups`` facts when called as ``_info`` module.
- azure_rm_securitygroup_info - Fix up instances when ``ansible_facts`` is returned for the older ``_facts`` alias.
- azure_rm_storageaccount_info - no longer returns empty ``azure_storageaccounts`` facts when called as ``_info`` module.
- azure_rm_virtualmachineimage_info - no longer returns empty ``azure_vmimages`` facts when called as ``_info`` module.
- azure_rm_virtualmachinescaleset_info - fix wrongly empty result, or ``ansible_facts`` result, when called as ``_info`` module.
- azure_rm_virtualnetwork_info - no longer returns empty ``azure_virtualnetworks`` facts when called as ``_info`` module.
- become - Provide nice error when the shell plugin is incompatible with the configured become plugin (https://github.com/ansible/ansible/issues/57770)
- ce_acl_interface - Strict regularity can't find anything.
- ce_dldp - tag named data of a xpath is unnecessay for old sotfware version to find a element from xml tree, but element can not be found with 'data' tag for new version, so remove.
- ce_dldp_interface - tag named data of a xpath is unnecessay for old sotfware version to find a element from xml tree, but element can not be found with 'data' tag for new version, so remove.
- ce_interface - It is not a good way to find data from a xml tree by regular. lin379 line405.
- ce_interface - line 750,779 Some attributes of interfaces are missing, 'ifAdminStatus', 'ifDescr', 'isL2SwitchPort'.So add them when get interface status.
- ce_snmp_location - fixed an out of array index error.
- ce_snmp_target_host - None has no 'lower()' attribute.
- ce_vxlan_arp - override 'get_config' to show specific configuration.
- ce_vxlan_gateway - override 'get_config' to show specific configuration.
- ce_vxlan_global - Netwrok_cli and netconf should be not mixed together, otherwise something bad will happen. Function get_nc_config uses netconf and load_config uses network_cli.
- ce_vxlan_global - line 242 , bd_info is a string array,and it should be 'extend' operation.
- ce_vxlan_global - line 423, 'if' and 'else' should set a different value. if 'exist', that value is 'enable'.
- ce_vxlan_global - line 477. To get state of result, if it is changed or not.
- ce_vxlan_tunnel - Netwrok_cli and netconf should be not mixed together, otherwise something bad will happen. Function get_nc_config uses netconf and load_config uses network_cli.
- ce_vxlan_vap - tag named data of a xpath is unnecessay for old sotfware version to find a element from xml tree, but element can not be found with 'data' tag for new version, so remove.
- cgroup_perf_recap - When not using file_per_task, make sure we don't prematurely close the perf files
- clarify error messages for 'auto' and missing libs, add missing lib msg for rpm.
- combine filter - Validate that undefined variables aren't used (https://github.com/ansible/ansible/issues/55810).
- constructed - Add a warning for the change in behavior in the sanitization of the groups option.
- consul_session - ``sessions`` returned value is a list even though no sessions were found
- consul_session - don't ignore ``validate_certs`` parameter
- consul_session: don't ignore ``scheme`` parameter
- cowsay - Fix issue with an empty cow_whitelist (https://github.com/ansible/ansible/issues/45631)
- crypto modules - improve error messages when required Python library is missing.
- cyberarkpassword - fix result decoding issues with Python 3 (https://github.com/ansible/ansible/issues/52625)
- digital_ocean_droplet - Fix creation of DigitalOcean droplets using digital_ocean_droplet module (https://github.com/ansible/ansible/pull/61655)
- display underlying error when reporting an invalid ``tasks:`` block.
- dnf - fix formatting of module name in error message (https://github.com/ansible/ansible/pull/58647)
- dnf - fix wildcard matching for state: absent (https://github.com/ansible/ansible/issues/55938)
- dnsmadeeasy - force the date to be rendered with C (POSIX system default) locale as English short date names are required by API
- docker connection plugin - accept version ``dev`` as 'newest version' and print warning.
- docker_* modules - behave better when requests errors are not caught by docker-py.
- docker_* modules - improve error message when docker-py is missing / has wrong version.
- docker_* modules - improve robustness when not handled Docker errors occur.
- docker_container - Add support for image lookups by digest. Fixes the detection of digest changes.
- docker_container - ``oom_killer`` and ``oom_score_adj`` options are available since docker-py 1.8.0, not 2.0.0 as assumed by the version check.
- docker_container - add support for ``nocopy`` mode for volumes.
- docker_container - correct variable used in warning message about default IP
- docker_container - fix idempotency of ``log_options`` when non-string values are used. Also warn user that this is the case.
- docker_container - fix network creation when ``networks_cli_compatible`` is enabled.
- docker_container - fix port bindings with IPv6 addresses.
- docker_container - switch to ``Config`` data source for images (API>=1.21).
- docker_container - use docker API's ``restart`` instead of ``stop``/``start`` to restart a container.
- docker_host_info - ``network_filters`` needs docker-py 2.0.2, ``disk_usage`` needs docker-py 2.2.0.
- docker_image - Add support for image lookups by digest. Fixes the detection of digest changes.
- docker_image - if ``build`` was not specified, the wrong default for ``build.rm`` is used.
- docker_image - if ``nocache`` set to ``yes`` but not ``build.nocache``, the module failed.
- docker_image - module failed when ``source: build`` was set but ``build.path`` options not specified.
- docker_image - validate ``tag`` option value.
- docker_image_info - Add support for image lookups by digest. Fixes the detection of digest changes.
- docker_login - report change on successful logout (https://github.com/ansible/ansible/issues/59232)
- docker_network module - fix idempotency when using ``aux_addresses`` in ``ipam_config``.
- docker_swarm_service - Change the type of options ``gid`` and ``uid`` on ``secrets`` and ``configs`` to ``str``.
- docker_swarm_service - allow the same port to be published both with TCP and UDP.
- docker_swarm_service - fix resource lookup if mounts.source="".
- docker_swarm_service_info - work around problems with older docker-py versions such as 2.0.2.
- documented ``ignore`` option for ``TRANSFORM_INVALID_GROUP_CHARS``
- dzdo did not work with password authentication
- ec2_group - Don't truncate the host bits off of IPv6 CIDRs. CIDRs will be passed thru to EC2 as-is provided they are valid IPv6 representations.  (https://github.com/ansible/ansible/issues/53297)
- ec2_group - Fix traceback sorting dictionaries using Python 3 and ensure rules shown by diff mode are in a consistent order.
- ec2_instance - Ensures ``ebs.volume_size`` and ``ebs.iops`` are ``int`` to avoid issues with Jinja2 templating
- ec2_instance - make Name tag idempotent (https://github.com/ansible/ansible/pull/55224)
- ec2_launch_template - Only 'volume' and 'instance' are valid resource types for tag specifications.
- ensure all cases of a None remote/become user are covered.
- ensure module results and facts are marked untrusted as templates for safer use within the same task
- ensure run_command passes bytes to Popen, which is what it expects.
- fact_cache - Define the first_order_merge method for the legacy FactCache.update(key, value).
- facts - change to use boot_time on a solaris OS to report correct uptime (https://github.com/ansible/ansible/issues/53635)
- facts - handle situation where ``ansible_architecture`` may not be defined (https://github.com/ansible/ansible/issues/55400)
- facts - properly detect is_chroot on XFS for non-root users (https://github.com/ansible/ansible/issues/56437)
- file - Fix setting relative paths for hard links (https://github.com/ansible/ansible/issues/55971)
- file - fix setting attributes for symlinked file (https://github.com/ansible/ansible/issues/56928)
- file - return more useful error message for recursion error (https://github.com/ansible/ansible/issues/56397)
- first_found - Un-deprecate ``skip``, as the alternative of ``errors`` does not work with ``with_first_found`` and only use of ``lookup`` (https://github.com/ansible/ansible/issues/58942)
- fix incorrect uses of to_native that should be to_text instead.
- fixed collection-based plugin loading in ansible-connection (eg networking plugins)
- gather_facts - Clean up tmp files upon completion (https://github.com/ansible/ansible/issues/57248)
- gather_facts - Prevent gather_facts from being verbose, just like is done in the normal action plugin for setup (https://github.com/ansible/ansible/issues/58310)
- gather_facts now correctly passes back the full output of modules on error and skipped, fixes
- gcp_compute - Speed up dynamic invetory up to 30x.
- gitlab modules - Update version deprecations to use strings instead of integers so that ``2.10`` isn't converted to ``2.1``. (https://github.com/ansible/ansible/pull/55395)
- gitlab_runner - Fix idempotency when creating runner (https://github.com/ansible/ansible/issues/57759)
- group - The group module errored of if the gid exists with the same group name. This prevents reruns of the playbook. This fixes a regression introduced by 4898b0a.
- group - properly detect duplicate GIDs when local=yes (https://github.com/ansible/ansible/issues/56481)
- handlers - Cache templated handler name on included handlers to avoid later templating errors (https://github.com/ansible/ansible/issues/58769)
- handlers - Only notify a handler if the handler is an exact match by ensuring `listen` is a list of strings. (https://github.com/ansible/ansible/issues/55575)
- hcloud_volume - Fix idempotency when attaching a server to a volume.
- hostname - Readded support for Cumulus Linux which broke in v2.8.0 (https://github.com/ansible/ansible/pull/57493)
- hostname - fix regression with Oracle Linux (https://github.com/ansible/ansible/issues/42726)
- hostname - make module work on CoreOS, Oracle Linux, Clear Linux, OpenSUSE Leap, ArchARM (https://github.com/ansible/ansible/issues/42726)
- iam_password_policy - Fix AWS/boto3 errors when setting no password expiration
- iam_password_policy no longer throws errors when you don't set pw_reuse_prevent
- iam_password_policy now only returns changed when the policy changes
- ibm_storage - Added a check for null fields in ibm_storage utils module.
- include_tasks - whitelist ``listen`` as a valid keyword (https://github.com/ansible/ansible/issues/56580)
- includes - Ensure to use the correct filename when AnsibleFileNotFound is encountered (https://github.com/ansible/ansible/issues/58436)
- ipaddr: prevent integer indices from being parsed as ip nets
- java_keystore - Use SHA256 to check the fingerprints' certs. The module is compatible with java<=8 (SHA1 by default) and Java>=9 (SHA256 by default) now.
- k8s - ensure k8s returns result of a resource update as it is at the end of the wait period
- k8s - ensure wait_condition works when Status is Unknown
- k8s - resource updates applied with force work correctly now
- k8s module - fix for case when resource definition yaml ended with 3 dashes
- keep results subset also when not no_log.
- lineinfile - fix a race / file descriptor leak when writing the file (https://github.com/ansible/ansible/issues/57327)
- lvg - Fixed warning shown when using default value for pesize about conversion from int to str.
- machinectl become plugin - correct bugs which induced errors on plugin usage
- make command module more resilient unicode errors. Also to fs errors.
- meraki_config_template - Don't query all networks unless needed.
- meraki_ssid - Improved documentation about parameter dependencies.
- meraki_ssid - Provides more accurate change results for some operations.
- meraki_static_route - Module would make unnecessary API calls to Meraki when ``net_id`` is specified in task.
- meraki_static_route - Module would make unnecessary API calls to Meraki when ``net_id`` is specified in task.
- meraki_switchport - improve reliability with native VLAN functionality.
- meraki_syslog - Module would ignore net_id parameter if passed.
- meraki_vlan - Module would make unnecessary API calls to Meraki when net_id is specified in task.
- module_defaults - Added aws_codebuild, aws_codecommit, aws_codepipeline, aws_secret, aws_ses_rule_set, cloudformation_stack_set, dms_endpoint, dms_replication_subnet_group, ec2_transit_gateway, ec2_transit_gateway_info, ecs_taskdefinition_facts, elb_target_info, iam_password_policy, redshift_cross_region_snapshots, s3_bucket_notification to the aws module_defaults group.
- module_utils - remove unused objects from dict_transformations, removed, and sys_info modules (https://github.com/ansible/ansible/pull/59570)
- mysql_user: fix regression introduced when fixing MariaDB/MySQL multiple versions handling
- nagios - Removed redundant type check which caused crashes. Guardrails added elsewhere in earlier change.
- nagios module - Fix nagios module to recognize if ``cmdfile`` exists and is fifo pipe.
- netbox - Fix missing implementation of `groups` option (https://github.com/ansible/ansible/issues/57688)
- netbox_ip_address - Fixed issue where it would create duplicate IP addresses when trying to serialize the IP address object which doesn't have the ``.serialize()`` method. This should also prevent future duplicate objects being created if they don't have the ``.serialize()`` method as well.

- new code assumed role_versions always were present event though rest of code does not.
- nmcli - fixed regression caused by commit b7724fd, github issue
- npm - Validate that all passed options have proper types.
- onepassword - fix onepassword lookup plugin failing on fields without a name or t property (https://github.com/ansible/ansible/pull/58308)
- onepassword_facts - fix onepassword_facts module failing on fields without a name or t property (https://github.com/ansible/ansible/pull/58308)
- openssh_keypair - The fingerprint return value was incorrectly returning a list of ssh-keygen output; it now returns just the fingerprint value as a string
- openssh_keypair - add public key and key comment validation on change
- openssh_keypair - make regeneration of valid keypairs with the ``force`` option possible, add better handling for invalid files
- openssl_certificate - ``invalid_at`` check was broken.
- openssl_certificate - ``key_usage`` check was broken for ``pyopenssl`` backend. Its error message was wrong for the ``cryptography`` backend.
- openssl_certificate - fix Subject Alternate Name comparison, which was broken for IPv6 addresses with PyOpenSSL, or with older cryptography versions (before 2.1).
- openssl_certificate - fix private key passphrase handling for ``cryptography`` backend.
- openssl_certificate - if both private key and CSR were specified, the idempotency check for ``selfsigned`` and ``ownca`` providers ignored the CSR.
- openssl_certificate - improve behavior when required files are missing.
- openssl_certificate - relative times did not work for ``pyopenssl`` backend under Python 3, and generally didn't work for ``valid_at`` and ``invalid_at`` for ``pyopenssl`` backend.
- openssl_csr - SAN normalization for IP addresses for the pyOpenSSL backend was broken.
- openssl_csr - the cryptography backend's idempotency checking for basic constraints was broken.
- openssl_csr, openssl_csr_info - use ``ipaddress`` module bundled with Ansible for normalizations needed for pyOpenSSL backend.
- openssl_pkcs12 - fixes crash when private key has a passphrase and the module is run a second time.
- openssl_privatekey - ``secp256r1`` got accidentally forgotten in the curve list.
- os_port - handle binding:vnic_type as optional (https://github.com/ansible/ansible/issues/55524, https://github.com/ansible/ansible/issues/55525)
- os_quota - fix failure to set compute or network quota when volume service is not available
- os_subnet - it is valid to specify an explicit ``subnetpool_id`` rather than ``use_default_subnetpool`` or ``cidr``

- ovirt_vm - fix for module failure on creation (https://github.com/ansible/ansible/issues/59385)
- pass correct loading context to persistent connections
- pass correct loading context to persistent connections other than local
- pip - Remove the unused and undocumented option ``use_mirrors``.
- pip - Validate that all items in the ``name`` option are strings.
- pkg_mgr - Ansible 2.8.0 failing to install yum packages on Amazon Linux (https://github.com/ansible/ansible/issues/56583)
- plugin loader - Restore adding plugin loader playbook dir to ``Playbook`` in addition to ``PlaybookCLI`` to solve sub directory playbook relative plugins to be located (https://github.com/ansible/ansible/issues/59548)
- podman_image - handle new output format for image build
- podman_image_facts - do not fail if invalid or non-existant image name is provided (https://github.com/ansible/ansible/issues/57899)
- postgresql modules - use ``module_utils.postgres.exec_sql`` function instead of ``__exec_sql`` method (https://github.com/ansible/ansible/pull/57674)
- postgresql_idx - remove ``__exec_sql`` method and use ``module_utils.postgres.exec_sql`` instead (https://github.com/ansible/ansible/pull/57684)
- postgresql_pg_hba - After splitting fields, merge authentication options back into a single field to prevent losing options beyond the first (https://github.com/ansible/ansible/issues/57505)
- postgresql_pg_hba - Fix TypeError after which pg_hba.conf is wiped (https://github.com/ansible/ansible/issues/56430)
- postgresql_privs - Fix incorrect views handling (https://github.com/ansible/ansible/issues/27327).
- postgresql_slot - fixed sslrootcert mapping to psycopg2 connection string
- postgresql_table - fix schema handling (https://github.com/ansible/ansible/pull/57391)
- preserve actual ssh error when we cannot connect.
- proxmox_kvm - fixed issue when vm has not yet a name item (https://github.com/ansible/ansible/issues/58194)
- psrp - Fix blank newlines appearing before ``stdout`` when using ``script`` or ``raw`` with the ``psrp`` connection plugin
- psrp - Fix issues when fetching large files causing a memory leak - https://github.com/ansible/ansible/issues/55239
- psrp - Fix issues with propagating errors back to Ansible with ``raw`` tasks
- rabbitmq_policy - Add full check for rabbit policy changes (https://github.com/ansible/ansible/issues/29264)
- rabbitmq_user - Handle non-zero rabbitmqctl exit codes (https://github.com/ansible/ansible/issues/56164)
- rds_instance - Don't hardcode the license models because there are accepted values undocumented by AWS. Rely on the exception handling instead to provide a helpful error for invalid license models.
- rds_instance no longer fails when passing neither storage_type nor iops
- re allow empty plays for now, but add deprecation msg.
- re-fix CLI help for module path, previous fix which was lost in parser switch
- redfish_command - add If-Match etag header to Redfish PATCH requests (https://github.com/ansible/ansible/issues/56050)
- redfish_command - make power commands idempotent (https://github.com/ansible/ansible/issues/55869)
- redfish_facts - add MACAddress to properties fetched by Redfish GetNicInventory command
- redhat_subscription - made code compatible with Python3 (https://github.com/ansible/ansible/pull/58665)
- refactored into function and use in some action plugins to match actual module used, made precedence very clear in code.
- regex tests - Fail with undefined error if the value is undefined (https://github.com/ansible/ansible/issues/12186)
- remove all temporary directories created by ansible-config (https://github.com/ansible/ansible/issues/56488)
- remove obsolete become mixin
- removed chdir from action plugins when using local connection, moved into plugin itself to avoid future issues with threads.
- removed_module - remove extra spaces from msg and docstring (https://github.com/ansible/ansible/pull/57209)
- resolves CVE-2019-10206, by avoiding templating passwords from prompt as it is probable they have special characters.
- route53_facts - the module did not advertise check mode support, causing it not to be run in check mode.
- setup (Windows) - prevent setup module failure if Get-MachineSid fails (https://github.com/ansible/ansible/issues/47813)
- setup.ps1 - Support non NETBIOS compliant hostnames (https://github.com/ansible/ansible/issues/54550)
- several minor fixes to ansible logging, allow deterministic log name, better level matching, leaner setup.
- show host_vars in ansible-inventory's --graph option.
- ssh connection plugin - Ensure that debug messages are properly encoded as text
- suppress "default will change" warnings for ``TRANSFORM_INVALID_GROUP_CHARS`` setting when non-default option value is chosen
- sysctl - check system values, not just sysctl.conf file, when determing state (https://github.com/ansible/ansible/pull/56153#issuecomment-514384922)
- sysctl - fix err referenced before assignment (https://github.com/ansible/ansible/issues/58158)
- sysctl: the module now also checks the output of STDERR to report if values are correctly set (https://github.com/ansible/ansible/pull/55695)
- systemd - wait for a service which is in deactivating state when using ``state=stopped`` (https://github.com/ansible/ansible/pull/59471)
- template lookup - restore variables between calls (https://github.com/ansible/ansible/issues/55113)
- tower_job_wait - Fixed wrong variable specification in examples
- tower_user - Fix to create user as a system auditor when specifying the `auditor` option (https://github.com/ansible/ansible/issues/54446)
- ufw - correctly check status when logging is off (https://github.com/ansible/ansible/issues/56674)
- uri - Handle multiple Content-Type headers correctly (https://github.com/ansible/ansible/pull/31238)
- uri - always return a value for status even during failure (https://github.com/ansible/ansible/issues/55897)
- urls - Handle redirects properly for IPv6 address by not splitting on ``:`` and rely on already parsed hostname and port values (https://github.com/ansible/ansible/issues/56258)
- use versioned link generator to link correct version for seealso
- user - allow 13 asterisk characters in password field without warning
- user - create parent directories when the specified home path has parent directiries that do not exist (https://github.com/ansible/ansible/issues/41393)
- user - do not warn when using ``local: yes`` if user already exists (https://github.com/ansible/ansible/issues/58063)
- user - omit incompatible options when operating in local mode (https://github.com/ansible/ansible/issues/48722)
- user - properly parse the shadow file on AIX (https://github.com/ansible/ansible/issues/54461)
- vault - Fix traceback using Python2 if a vault contains non-ascii characters (https://github.com/ansible/ansible/issues/58351).
- vfat - changed default value of selinux_special_filesystems to include vfat, the filesystem of ``/boot/efi`` on UEFI systems
- vmware - The VMware modules now enable the SSL certificate check unless ``validate_certs`` is ``false``.
- vmware_guest accepts 0 MB of memory reservation, fix regression introduced via 193f69064fb40a83e3e7d2112ef24868b45233b3 (https://github.com/ansible/ansible/issues/59190).
- vultr_server - Fix idempotency for options ``ipv6_enabled`` and ``private_network_enabled``.
- warn user when attempting to use service with globs in systemd module.
- we don't really need to template vars on definition as we do this on demand in templating.
- win_acl - Change special id ref recognitionto avoid language diff (https://github.com/ansible/ansible/issues/56757)
- win_acl - Fix qualifier parser when using UNC paths - https://github.com/ansible/ansible/issues/55875
- win_chocolatey - Better support detecting multiple packages installed at different versions on newer Chocolatey releases
- win_chocolatey - Install the specific Chocolatey version if the ``version`` option is set.
- win_domain - Fix checking for a domain introduced in a recent patch
- win_domain_controller - Do not fail the play without the user being able to catch dcpromo failing because of a pending reboot within a playbook using ignore_error or retry logic.
- win_domain_group_membership - Fix missing @extra_vars on Get-ADObject to support dirrent domain and credentials for retrival (https://github.com/ansible/ansible/issues/57404)
- win_domain_user - Do not hide error and stacktrace on failures
- win_dsc - Be more leniant around the accepted DateTime values for backwards compatibility - https://github.com/ansible/ansible/issues/59667
- win_firewall_rule - Fix program var not expanding %SystemRoot% type vars (https://github.com/ansible/ansible/issues/44450)
- win_get_url - Fix handling of restricted headers as per (https://github.com/ansible/ansible/issues/57880)
- win_get_url - Fix proxy_url not used correctly (https://github.com/ansible/ansible/issues/58691)
- win_hostname - Fix non netbios compliant name handling (https://github.com/ansible/ansible/issues/55283)
- win_iis_virtualdirectory - Support recursive removal (https://github.com/ansible/ansible/issues/49755)
- win_iis_website - site_id not used if no sites exist already and creating a new site (https://github.com/ansible/ansible/issues/47057)
- win_pagefile - Fix idempotency when same settings as current (https://github.com/ansible/ansible/issues/57836)
- win_pagefile - not using testPath
- win_psmodule - Missing SkipPublisherCheck in Prerq installations
- win_reboot - pass return value for ``test_command`` result when using the ``psrp`` connection plugin
- win_reg_stat - fix issue when trying to check keys in ``HKU:\`` - https://github.com/ansible/ansible/issues/59337
- win_region - Fix the check for ``format`` when running on the ``psrp`` connection plugin
- win_scheduled_task - Fix start/end bountry triggers to allow for timezone sync (https://github.com/ansible/ansible/issues/49327)
- win_shell - Fix bug when setting ``args.executable`` to an executable with a space
- win_user - Get proper error code when failing to validate the user's credentials
- winrm - Fix issue when attempting to parse CLIXML on send input failure
- xenserver_guest - fixed an issue where VM whould be powered off even though check mode is used if reconfiguration requires VM to be powered off.
- xenserver_guest - proper error message is shown when maximum number of network interfaces is reached and multiple network interfaces are added at once.
- xenserver_guest - when adding disks to a VM in powered on state, disks are now properly plugged/activated (https://github.com/ansible/ansible/issues/60693).
- yum - Fix false error message about autoremove not being supported (https://github.com/ansible/ansible/issues/56458)
- yum - gracefully handle failure case of enabling a non existent repo, as the yum cli does (Fixes https://github.com/ansible/ansible/issues/52582)
- yum - handle special "_none_" value for proxy in yum.conf and .repo files (https://github.com/ansible/ansible/issues/56538)
- yum - handle stale/invalid yum.pid lock file (https://github.com/ansible/ansible/issues/57189)

New Plugins
-----------

Cliconf
~~~~~~~

- eric_eccli - Use eccli cliconf to run command on Ericsson ECCLI platform
- icx - Use icx cliconf to run command on Ruckus ICX platform

Httpapi
~~~~~~~

- fortianalyzer - HttpApi Plugin for Fortinet FortiAnalyzer Appliance or VM
- fortios - HttpApi Plugin for Fortinet FortiOS Appliance or VM

Lookup
~~~~~~

- avi - Look up ``Avi`` objects.

New Modules
-----------

Cloud
~~~~~

amazon
^^^^^^

- aws_codebuild - Create or delete an AWS CodeBuild project
- aws_codepipeline - Create or delete AWS CodePipelines
- aws_netapp_cvs_FileSystems - NetApp AWS Cloud Volumes Service Manage FileSystem.
- aws_netapp_cvs_active_directory - NetApp AWS CloudVolumes Service Manage Active Directory.
- aws_netapp_cvs_pool - NetApp AWS Cloud Volumes Service Manage Pools.
- aws_netapp_cvs_snapshots - NetApp AWS Cloud Volumes Service Manage Snapshots.
- dms_endpoint - creates or destroys a data migration services endpoint
- dms_replication_subnet_group - creates or destroys a data migration services subnet group
- lambda_info - Gathers AWS Lambda function details
- rds_snapshot - manage Amazon RDS snapshots.
- s3_bucket_notification - Creates, updates or deletes S3 Bucket notification for lambda

azure
^^^^^

- azure_rm_aks_info - Get Azure Kubernetes Service facts
- azure_rm_aksversion_info - Get available kubernetes versions supported by Azure Kubernetes Service
- azure_rm_applicationsecuritygroup_info - Get Azure Application Security Group facts
- azure_rm_appserviceplan_info - Get azure app service plan facts
- azure_rm_automationaccount - Manage Azure Automation account
- azure_rm_automationaccount_info - Get Azure automation account facts
- azure_rm_autoscale_info - Get Azure Auto Scale Setting facts
- azure_rm_availabilityset_info - Get Azure Availability Set facts
- azure_rm_azurefirewall - Manage Azure Firewall instance.
- azure_rm_azurefirewall_info - Get AzureFirewall info.
- azure_rm_batchaccount - Manages a Batch Account on Azure.
- azure_rm_cdnendpoint_info - Get Azure CDN endpoint facts
- azure_rm_cdnprofile_info - Get Azure CDN profile facts
- azure_rm_containerinstance_info - Get Azure Container Instance facts
- azure_rm_containerregistry_info - Get Azure Container Registry facts
- azure_rm_cosmosdbaccount_info - Get Azure Cosmos DB Account facts
- azure_rm_deployment_info - Get Azure Deployment facts
- azure_rm_devtestlab_info - Get Azure DevTest Lab facts
- azure_rm_devtestlabarmtemplate_info - Get Azure DevTest Lab ARM Template facts
- azure_rm_devtestlabartifact_info - Get Azure DevTest Lab Artifact facts
- azure_rm_devtestlabartifactsource_info - Get Azure DevTest Lab Artifact Source facts
- azure_rm_devtestlabcustomimage_info - Get Azure DevTest Lab Custom Image facts
- azure_rm_devtestlabenvironment_info - Get Azure Environment facts
- azure_rm_devtestlabpolicy_info - Get Azure DTL Policy facts
- azure_rm_devtestlabschedule_info - Get Azure Schedule facts
- azure_rm_devtestlabvirtualmachine_info - Get Azure DevTest Lab Virtual Machine facts
- azure_rm_devtestlabvirtualnetwork_info - Get Azure DevTest Lab Virtual Network facts
- azure_rm_dnsrecordset_info - Get DNS Record Set facts
- azure_rm_dnszone_info - Get DNS zone facts
- azure_rm_functionapp_info - Get Azure Function App facts
- azure_rm_gallery - Manage Azure Shared Image Gallery instance.
- azure_rm_gallery_info - Get Azure Shared Image Gallery info.
- azure_rm_galleryimage - Manage Azure SIG Image instance.
- azure_rm_galleryimage_info - Get Azure SIG Image info.
- azure_rm_galleryimageversion - Manage Azure SIG Image Version instance.
- azure_rm_galleryimageversion_info - Get Azure SIG Image Version info.
- azure_rm_hdinsightcluster_info - Get Azure HDInsight Cluster facts
- azure_rm_image_info - Get facts about azure custom images
- azure_rm_iotdevice - Manage Azure IoT hub device
- azure_rm_iotdevice_info - Facts of Azure IoT hub device
- azure_rm_iotdevicemodule - Manage Azure IoT hub device module
- azure_rm_iothub - Manage Azure IoT hub
- azure_rm_iothub_info - Get IoT Hub facts
- azure_rm_iothubconsumergroup - Manage Azure IoT hub
- azure_rm_keyvault_info - Get Azure Key Vault facts
- azure_rm_keyvaultkey_info - Get Azure Key Vault key facts.
- azure_rm_loadbalancer_info - Get load balancer facts
- azure_rm_lock - Manage Azure locks
- azure_rm_lock_info - Manage Azure locks
- azure_rm_loganalyticsworkspace_info - Get facts of Azure Log Analytics workspaces
- azure_rm_manageddisk_info - Get managed disk facts
- azure_rm_mariadbconfiguration_info - Get Azure MariaDB Configuration facts
- azure_rm_mariadbdatabase_info - Get Azure MariaDB Database facts
- azure_rm_mariadbfirewallrule_info - Get Azure MariaDB Firewall Rule facts
- azure_rm_mariadbserver_info - Get Azure MariaDB Server facts
- azure_rm_monitorlogprofile - Manage Azure Monitor log profile
- azure_rm_mysqlconfiguration_info - Get Azure MySQL Configuration facts
- azure_rm_mysqldatabase_info - Get Azure MySQL Database facts
- azure_rm_mysqlfirewallrule_info - Get Azure MySQL Firewall Rule facts
- azure_rm_mysqlserver_info - Get Azure MySQL Server facts
- azure_rm_networkinterface_info - Get network interface facts
- azure_rm_postgresqlconfiguration_info - Get Azure PostgreSQL Configuration facts
- azure_rm_postgresqldatabase_info - Get Azure PostgreSQL Database facts
- azure_rm_postgresqlfirewallrule_info - Get Azure PostgreSQL Firewall Rule facts
- azure_rm_postgresqlserver_info - Get Azure PostgreSQL Server facts
- azure_rm_publicipaddress_info - Get public IP facts
- azure_rm_rediscache_info - Get Azure Cache for Redis instance facts
- azure_rm_resource_info - Generic facts of Azure resources
- azure_rm_roleassignment_info - Gets Azure Role Assignment facts
- azure_rm_roledefinition_info - Get Azure Role Definition facts
- azure_rm_routetable_info - Get route table facts
- azure_rm_securitygroup_info - Get security group facts
- azure_rm_servicebus_info - Get servicebus facts
- azure_rm_snapshot - Manage Azure Snapshot instance.
- azure_rm_sqlserver_info - Get SQL Server facts
- azure_rm_storageaccount_info - Get storage account facts
- azure_rm_trafficmanagerendpoint_info - Get Azure Traffic Manager endpoint facts
- azure_rm_trafficmanagerprofile_info - Get Azure Traffic Manager profile facts
- azure_rm_virtualmachine_info - Get virtual machine facts
- azure_rm_virtualmachineextension_info - Get Azure Virtual Machine Extension facts
- azure_rm_virtualmachineimage_info - Get virtual machine image facts
- azure_rm_virtualmachinescaleset_info - Get Virtual Machine Scale Set facts
- azure_rm_virtualmachinescalesetextension_info - Get Azure Virtual Machine Scale Set Extension facts
- azure_rm_virtualmachinescalesetinstance_info - Get Azure Virtual Machine Scale Set Instance facts
- azure_rm_virtualnetwork_info - Get virtual network facts
- azure_rm_virtualnetworkpeering_info - Get facts of Azure Virtual Network Peering
- azure_rm_webapp_info - Get Azure web app facts

cloudstack
^^^^^^^^^^

- cs_instance_info - Gathering information from the API of instances from Apache CloudStack based clouds.
- cs_zone_info - Gathering information about zones from Apache CloudStack based clouds.

digital_ocean
^^^^^^^^^^^^^

- digital_ocean_sshkey_info - Gather information about DigitalOcean SSH keys

google
^^^^^^

- gcp_appengine_firewall_rule - Creates a GCP FirewallRule
- gcp_appengine_firewall_rule_info - Gather info for GCP FirewallRule
- gcp_cloudfunctions_cloud_function - Creates a GCP CloudFunction
- gcp_cloudfunctions_cloud_function_info - Gather info for GCP CloudFunction
- gcp_cloudscheduler_job - Creates a GCP Job
- gcp_cloudscheduler_job_info - Gather info for GCP Job
- gcp_cloudtasks_queue - Creates a GCP Queue
- gcp_cloudtasks_queue_info - Gather info for GCP Queue
- gcp_compute_autoscaler - Creates a GCP Autoscaler
- gcp_compute_autoscaler_info - Gather info for GCP Autoscaler
- gcp_compute_snapshot - Creates a GCP Snapshot
- gcp_compute_snapshot_info - Gather info for GCP Snapshot
- gcp_filestore_instance - Creates a GCP Instance
- gcp_filestore_instance_info - Gather info for GCP Instance
- gcp_kms_crypto_key - Creates a GCP CryptoKey
- gcp_kms_crypto_key_info - Gather info for GCP CryptoKey
- gcp_kms_key_ring - Creates a GCP KeyRing
- gcp_kms_key_ring_info - Gather info for GCP KeyRing
- gcp_mlengine_model - Creates a GCP Model
- gcp_mlengine_model_info - Gather info for GCP Model
- gcp_mlengine_version - Creates a GCP Version
- gcp_mlengine_version_info - Gather info for GCP Version
- gcp_tpu_node - Creates a GCP Node
- gcp_tpu_node_info - Gather info for GCP Node

hcloud
^^^^^^

- hcloud_network - Create and manage cloud Networks on the Hetzner Cloud.
- hcloud_network_info - Gather info about your Hetzner Cloud networks.
- hcloud_rdns - Create and manage reverse DNS entries on the Hetzner Cloud.
- hcloud_route - Create and delete cloud routes on the Hetzner Cloud.
- hcloud_server_network - Manage the relationship between Hetzner Cloud Networks and servers
- hcloud_subnetwork - Manage cloud subnetworks on the Hetzner Cloud.

online
^^^^^^

- online_server_info - Gather information about Online servers.
- online_user_info - Gather information about Online user.

openstack
^^^^^^^^^

- os_group_info - Retrieve info about one or more OpenStack groups

ovirt
^^^^^

- ovirt_job - Module to manage jobs in oVirt/RHV

scaleway
^^^^^^^^

- scaleway_image_info - Gather information about the Scaleway images available.
- scaleway_ip_info - Gather information about the Scaleway ips available.
- scaleway_organization_info - Gather information about the Scaleway organizations available.
- scaleway_security_group_info - Gather information about the Scaleway security groups available.
- scaleway_server_info - Gather information about the Scaleway servers available.
- scaleway_snapshot_info - Gather information about the Scaleway snapshots available.
- scaleway_volume_info - Gather information about the Scaleway volumes available.

vmware
^^^^^^

- vcenter_extension_info - Gather info vCenter extensions
- vmware_about_info - Provides information about VMware server to which user is connecting to
- vmware_category_info - Gather info about VMware tag categories
- vmware_cluster_drs - Manage Distributed Resource Scheduler (DRS) on VMware vSphere clusters
- vmware_cluster_ha - Manage High Availability (HA) on VMware vSphere clusters
- vmware_cluster_vsan - Manages virtual storage area network (vSAN) configuration on VMware vSphere clusters
- vmware_content_deploy_template - Deploy Virtual Machine from template stored in content library.
- vmware_content_library_info - Gather information about VMWare Content Library
- vmware_content_library_manager - Create, update and delete VMware content library
- vmware_drs_group_info - Gathers info about DRS VM/Host groups on the given cluster
- vmware_drs_rule_info - Gathers info about DRS rule on the given cluster
- vmware_dvs_portgroup_find - Find portgroup(s) in a VMware environment
- vmware_dvs_portgroup_info - Gathers info DVS portgroup configurations
- vmware_dvswitch_nioc - Manage distributed switch Network IO Control
- vmware_evc_mode - Enable/Disable EVC mode on vCenter
- vmware_folder_info - Provides information about folders in a datacenter
- vmware_guest_boot_info - Gather info about boot options for the given virtual machine
- vmware_guest_customization_info - Gather info about VM customization specifications
- vmware_guest_disk_info - Gather info about disks of given virtual machine
- vmware_guest_network - Manage network adapters of specified virtual machine in given vCenter infrastructure
- vmware_guest_screenshot - Create a screenshot of the Virtual Machine console.
- vmware_guest_sendkey - Send USB HID codes to the Virtual Machine's keyboard.
- vmware_host_capability_info - Gathers info about an ESXi host's capability information
- vmware_host_config_info - Gathers info about an ESXi host's advance configuration information
- vmware_host_dns_info - Gathers info about an ESXi host's DNS configuration information
- vmware_host_feature_info - Gathers info about an ESXi host's feature capability information
- vmware_host_firewall_info - Gathers info about an ESXi host's firewall configuration information
- vmware_host_ntp_info - Gathers info about NTP configuration on an ESXi host
- vmware_host_package_info - Gathers info about available packages on an ESXi host
- vmware_host_service_info - Gathers info about an ESXi host's services
- vmware_host_ssl_info - Gather info of ESXi host system about SSL
- vmware_host_vmhba_info - Gathers info about vmhbas available on the given ESXi host
- vmware_host_vmnic_info - Gathers info about vmnics available on the given ESXi host
- vmware_local_role_info - Gather info about local roles on an ESXi host
- vmware_local_user_info - Gather info about users on the given ESXi host
- vmware_portgroup_info - Gathers info about an ESXi host's Port Group configuration
- vmware_resource_pool_info - Gathers info about resource pool information
- vmware_target_canonical_info - Return canonical (NAA) from an ESXi host system
- vmware_vm_storage_policy_info - Gather information about vSphere storage profile defined storage policy information.
- vmware_vmkernel_info - Gathers VMKernel info about an ESXi host
- vmware_vswitch_info - Gathers info about an ESXi host's vswitch configurations

vultr
^^^^^

- vultr_account_info - Get infos about the Vultr account.
- vultr_block_storage_info - Get infos about the Vultr block storage volumes available.
- vultr_dns_domain_info - Gather information about the Vultr DNS domains available.
- vultr_firewall_group_info - Gather information about the Vultr firewall groups available.
- vultr_network_info - Gather information about the Vultr networks available.
- vultr_os_info - Get infos about the Vultr OSes available.
- vultr_plan_info - Gather information about the Vultr plans available.
- vultr_region_info - Gather information about the Vultr regions available.
- vultr_server_info - Gather information about the Vultr servers available.
- vultr_ssh_key_info - Get infos about the Vultr SSH keys available.
- vultr_startup_script_info - Gather information about the Vultr startup scripts available.
- vultr_user_info - Get infos about the Vultr user available.

Crypto
~~~~~~

entrust
^^^^^^^

- ecs_certificate - Request SSL/TLS certificates with the Entrust Certificate Services (ECS) API

Database
~~~~~~~~

mysql
^^^^^

- mysql_info - Gather information about MySQL servers

postgresql
^^^^^^^^^^

- postgresql_copy - Copy data between a file/program and a PostgreSQL table
- postgresql_publication - Add, update, or remove PostgreSQL publication
- postgresql_sequence - Create, drop, or alter a PostgreSQL sequence

Monitoring
~~~~~~~~~~

zabbix
^^^^^^

- zabbix_mediatype - Create/Update/Delete Zabbix media types

Net Tools
~~~~~~~~~

- hetzner_failover_ip - Manage Hetzner's failover IPs
- hetzner_failover_ip_info - Retrieve information on Hetzner's failover IPs

Network
~~~~~~~

aci
^^^

- aci_interface_policy_cdp - Manage CDP interface policies (cdp:IfPol)
- aci_l3out_extepg - Manage External Network Instance Profile (ExtEpg) objects (l3extInstP:instP)
- aci_l3out_extsubnet - Manage External Subnet objects (l3extSubnet:extsubnet)
- aci_vmm_credential - Manage virtual domain credential profiles (vmm:UsrAccP)
- mso_schema_site_anp_epg_domain - Manage site-local EPG domains in schema template

avi
^^^

- avi_user - Avi User Module

check_point
^^^^^^^^^^^

- cp_mgmt_access_layer - Manages access-layer objects on Check Point over Web Services API
- cp_mgmt_access_layer_facts - Get access-layer objects facts on Check Point over Web Services API
- cp_mgmt_access_role - Manages access-role objects on Check Point over Web Services API
- cp_mgmt_access_role_facts - Get access-role objects facts on Check Point over Web Services API
- cp_mgmt_access_rule - Manages access-rule objects on Check Point over Web Services API
- cp_mgmt_access_rule_facts - Get access-rule objects facts on Check Point over Web Services API
- cp_mgmt_address_range - Manages address-range objects on Check Point over Web Services API
- cp_mgmt_address_range_facts - Get address-range objects facts on Check Point over Web Services API
- cp_mgmt_administrator - Manages administrator objects on Check Point over Web Services API
- cp_mgmt_administrator_facts - Get administrator objects facts on Check Point over Web Services API
- cp_mgmt_application_site - Manages application-site objects on Check Point over Web Services API
- cp_mgmt_application_site_category - Manages application-site-category objects on Check Point over Web Services API
- cp_mgmt_application_site_category_facts - Get application-site-category objects facts on Check Point over Web Services API
- cp_mgmt_application_site_facts - Get application-site objects facts on Check Point over Web Services API
- cp_mgmt_application_site_group - Manages application-site-group objects on Check Point over Web Services API
- cp_mgmt_application_site_group_facts - Get application-site-group objects facts on Check Point over Web Services API
- cp_mgmt_assign_global_assignment - assign global assignment on Check Point over Web Services API
- cp_mgmt_discard - All changes done by user are discarded and removed from database.
- cp_mgmt_dns_domain - Manages dns-domain objects on Check Point over Web Services API
- cp_mgmt_dns_domain_facts - Get dns-domain objects facts on Check Point over Web Services API
- cp_mgmt_dynamic_object - Manages dynamic-object objects on Check Point over Web Services API
- cp_mgmt_dynamic_object_facts - Get dynamic-object objects facts on Check Point over Web Services API
- cp_mgmt_exception_group - Manages exception-group objects on Check Point over Web Services API
- cp_mgmt_exception_group_facts - Get exception-group objects facts on Check Point over Web Services API
- cp_mgmt_global_assignment - Manages global-assignment objects on Check Point over Web Services API
- cp_mgmt_global_assignment_facts - Get global-assignment objects facts on Check Point over Web Services API
- cp_mgmt_group - Manages group objects on Check Point over Web Services API
- cp_mgmt_group_facts - Get group objects facts on Check Point over Web Services API
- cp_mgmt_group_with_exclusion - Manages group-with-exclusion objects on Check Point over Web Services API
- cp_mgmt_group_with_exclusion_facts - Get group-with-exclusion objects facts on Check Point over Web Services API
- cp_mgmt_host - Manages host objects on Check Point over Web Services API
- cp_mgmt_host_facts - Get host objects facts on Check Point over Web Services API
- cp_mgmt_install_policy - install policy on Check Point over Web Services API
- cp_mgmt_mds_facts - Get Multi-Domain Server (mds) objects facts on Check Point over Web Services API
- cp_mgmt_multicast_address_range - Manages multicast-address-range objects on Check Point over Web Services API
- cp_mgmt_multicast_address_range_facts - Get multicast-address-range objects facts on Check Point over Web Services API
- cp_mgmt_network - Manages network objects on Check Point over Web Services API
- cp_mgmt_network_facts - Get network objects facts on Check Point over Web Services API
- cp_mgmt_package - Manages package objects on Check Point over Web Services API
- cp_mgmt_package_facts - Get package objects facts on Check Point over Web Services API
- cp_mgmt_publish - All the changes done by this user will be seen by all users only after publish is called.
- cp_mgmt_put_file - put file on Check Point over Web Services API
- cp_mgmt_run_ips_update - Runs IPS database update. If "package-path" is not provided server will try to get the latest package from the User Center.
- cp_mgmt_run_script - Executes the script on a given list of targets.
- cp_mgmt_security_zone - Manages security-zone objects on Check Point over Web Services API
- cp_mgmt_security_zone_facts - Get security-zone objects facts on Check Point over Web Services API
- cp_mgmt_service_dce_rpc - Manages service-dce-rpc objects on Check Point over Web Services API
- cp_mgmt_service_dce_rpc_facts - Get service-dce-rpc objects facts on Check Point over Web Services API
- cp_mgmt_service_group - Manages service-group objects on Check Point over Web Services API
- cp_mgmt_service_group_facts - Get service-group objects facts on Check Point over Web Services API
- cp_mgmt_service_icmp - Manages service-icmp objects on Check Point over Web Services API
- cp_mgmt_service_icmp6 - Manages service-icmp6 objects on Check Point over Web Services API
- cp_mgmt_service_icmp6_facts - Get service-icmp6 objects facts on Check Point over Web Services API
- cp_mgmt_service_icmp_facts - Get service-icmp objects facts on Check Point over Web Services API
- cp_mgmt_service_other - Manages service-other objects on Check Point over Web Services API
- cp_mgmt_service_other_facts - Get service-other objects facts on Check Point over Web Services API
- cp_mgmt_service_rpc - Manages service-rpc objects on Check Point over Web Services API
- cp_mgmt_service_rpc_facts - Get service-rpc objects facts on Check Point over Web Services API
- cp_mgmt_service_sctp - Manages service-sctp objects on Check Point over Web Services API
- cp_mgmt_service_sctp_facts - Get service-sctp objects facts on Check Point over Web Services API
- cp_mgmt_service_tcp - Manages service-tcp objects on Check Point over Web Services API
- cp_mgmt_service_tcp_facts - Get service-tcp objects facts on Check Point over Web Services API
- cp_mgmt_service_udp - Manages service-udp objects on Check Point over Web Services API
- cp_mgmt_service_udp_facts - Get service-udp objects facts on Check Point over Web Services API
- cp_mgmt_session_facts - Get session objects facts on Check Point over Web Services API
- cp_mgmt_simple_gateway - Manages simple-gateway objects on Check Point over Web Services API
- cp_mgmt_simple_gateway_facts - Get simple-gateway objects facts on Check Point over Web Services API
- cp_mgmt_tag - Manages tag objects on Check Point over Web Services API
- cp_mgmt_tag_facts - Get tag objects facts on Check Point over Web Services API
- cp_mgmt_threat_exception - Manages threat-exception objects on Check Point over Web Services API
- cp_mgmt_threat_exception_facts - Get threat-exception objects facts on Check Point over Web Services API
- cp_mgmt_threat_indicator - Manages threat-indicator objects on Check Point over Web Services API
- cp_mgmt_threat_indicator_facts - Get threat-indicator objects facts on Check Point over Web Services API
- cp_mgmt_threat_layer - Manages threat-layer objects on Check Point over Web Services API
- cp_mgmt_threat_layer_facts - Get threat-layer objects facts on Check Point over Web Services API
- cp_mgmt_threat_profile - Manages threat-profile objects on Check Point over Web Services API
- cp_mgmt_threat_profile_facts - Get threat-profile objects facts on Check Point over Web Services API
- cp_mgmt_threat_protection_override - Edit existing object using object name or uid.
- cp_mgmt_threat_rule - Manages threat-rule objects on Check Point over Web Services API
- cp_mgmt_threat_rule_facts - Get threat-rule objects facts on Check Point over Web Services API
- cp_mgmt_time - Manages time objects on Check Point over Web Services API
- cp_mgmt_time_facts - Get time objects facts on Check Point over Web Services API
- cp_mgmt_verify_policy - Verifies the policy of the selected package.
- cp_mgmt_vpn_community_meshed - Manages vpn-community-meshed objects on Check Point over Web Services API
- cp_mgmt_vpn_community_meshed_facts - Get vpn-community-meshed objects facts on Check Point over Web Services API
- cp_mgmt_vpn_community_star - Manages vpn-community-star objects on Check Point over Web Services API
- cp_mgmt_vpn_community_star_facts - Get vpn-community-star objects facts on Check Point over Web Services API
- cp_mgmt_wildcard - Manages wildcard objects on Check Point over Web Services API
- cp_mgmt_wildcard_facts - Get wildcard objects facts on Check Point over Web Services API
- cp_publish - All the changes done by this user will be seen by all users only after publish is called.

eos
^^^

- eos_interfaces - Manages interface attributes of Arista EOS interfaces
- eos_l2_interfaces - Manages Layer-2 interface attributes of Arista EOS devices
- eos_l3_interfaces - Manages L3 interface attributes of Arista EOS devices.
- eos_lacp - Manage Global Link Aggregation Control Protocol (LACP) on Arista EOS devices.
- eos_lacp_interfaces - Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on Arista EOS devices.
- eos_lag_interfaces - Manages link aggregation groups on Arista EOS devices
- eos_lldp_global - Manage Global Link Layer Discovery Protocol (LLDP) settings on Arista EOS devices.
- eos_lldp_interfaces - Manage Link Layer Discovery Protocol (LLDP) attributes of interfaces on Arista EOS devices.
- eos_vlans - Manage VLANs on Arista EOS devices.

eric_eccli
^^^^^^^^^^

- eric_eccli_command - Run commands on remote devices running ERICSSON ECCLI

exos
^^^^

- exos_lldp_global - Configure and manage Link Layer Discovery Protocol(LLDP) attributes on EXOS platforms.

f5
^^

- bigip_apm_acl - Manage user-defined APM ACLs
- bigip_apm_network_access - Manage APM Network Access resource
- bigip_asm_dos_application - Manage application settings for DOS profile
- bigip_device_certificate - Manage self-signed device certificates
- bigip_firewall_log_profile - Manages AFM logging profiles configured in the system
- bigip_firewall_log_profile_network - Configures Network Firewall related settings of the log profile
- bigip_firewall_schedule - Manage BIG-IP AFM schedule configurations
- bigip_message_routing_peer - Manage peers for routing generic message protocol messages
- bigip_message_routing_protocol - Manage generic message parser profile.
- bigip_message_routing_route - Manages static routes for routing message protocol messages
- bigip_message_routing_router - Manages router profiles for message-routing protocols
- bigip_message_routing_transport_config - Manages configuration for an outgoing connection
- bigip_remote_user - Manages default settings for remote user accounts on a BIG-IP
- bigip_snat_translation - Manage SNAT Translations on a BIG-IP

fortianalyzer
^^^^^^^^^^^^^

- faz_device - Add or remove device

fortios
^^^^^^^

- fortios_alertemail_setting - Configure alert email settings in Fortinet's FortiOS and FortiGate.
- fortios_facts - Get facts about fortios devices.
- fortios_router_access_list6 - Configure IPv6 access lists in Fortinet's FortiOS and FortiGate.
- fortios_router_aspath_list - Configure Autonomous System (AS) path lists in Fortinet's FortiOS and FortiGate.
- fortios_router_community_list - Configure community lists in Fortinet's FortiOS and FortiGate.
- fortios_router_isis - Configure IS-IS in Fortinet's FortiOS and FortiGate.
- fortios_router_key_chain - Configure key-chain in Fortinet's FortiOS and FortiGate.
- fortios_router_prefix_list6 - Configure IPv6 prefix lists in Fortinet's FortiOS and FortiGate.
- fortios_router_ripng - Configure RIPng in Fortinet's FortiOS and FortiGate.
- fortios_router_route_map - Configure route maps in Fortinet's FortiOS and FortiGate.
- fortios_router_static6 - Configure IPv6 static routing tables in Fortinet's FortiOS and FortiGate.
- fortios_spamfilter_bwl - Configure anti-spam black/white list in Fortinet's FortiOS and FortiGate.
- fortios_spamfilter_bword - Configure AntiSpam banned word list in Fortinet's FortiOS and FortiGate.
- fortios_spamfilter_dnsbl - Configure AntiSpam DNSBL/ORBL in Fortinet's FortiOS and FortiGate.
- fortios_spamfilter_fortishield - Configure FortiGuard - AntiSpam in Fortinet's FortiOS and FortiGate.
- fortios_spamfilter_iptrust - Configure AntiSpam IP trust in Fortinet's FortiOS and FortiGate.
- fortios_spamfilter_mheader - Configure AntiSpam MIME header in Fortinet's FortiOS and FortiGate.
- fortios_spamfilter_options - Configure AntiSpam options in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_802_1X_settings - Configure global 802.1X settings in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_custom_command - Configure the FortiGate switch controller to send custom commands to managed FortiSwitch devices in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_igmp_snooping - Configure FortiSwitch IGMP snooping global settings in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_qos_dot1p_map - Configure FortiSwitch QoS 802.1p in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_qos_ip_dscp_map - Configure FortiSwitch QoS IP precedence/DSCP in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_qos_qos_policy - Configure FortiSwitch QoS policy in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_qos_queue_policy - Configure FortiSwitch QoS egress queue policy in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_quarantine - Configure FortiSwitch quarantine support in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_security_policy_802_1X - Configure 802.1x MAC Authentication Bypass (MAB) policies in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_security_policy_captive_portal - Names of VLANs that use captive portal authentication in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_sflow - Configure FortiSwitch sFlow in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_storm_control - Configure FortiSwitch storm control in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_stp_settings - Configure FortiSwitch spanning tree protocol (STP) in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_switch_group - Configure FortiSwitch switch groups in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_switch_interface_tag - Configure switch object tags in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_switch_log - Configure FortiSwitch logging (logs are transferred to and inserted into FortiGate event log) in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_switch_profile - Configure FortiSwitch switch profile in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_system - Configure system-wide switch controller settings in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_virtual_port_pool - Configure virtual pool in Fortinet's FortiOS and FortiGate.
- fortios_switch_controller_vlan - Configure VLANs for switch controller in Fortinet's FortiOS and FortiGate.
- fortios_system_affinity_interrupt - Configure interrupt affinity in Fortinet's FortiOS and FortiGate.
- fortios_system_affinity_packet_redistribution - Configure packet redistribution in Fortinet's FortiOS and FortiGate.
- fortios_system_alarm - Configure alarm in Fortinet's FortiOS and FortiGate.
- fortios_system_alias - Configure alias command in Fortinet's FortiOS and FortiGate.
- fortios_system_arp_table - Configure ARP table in Fortinet's FortiOS and FortiGate.
- fortios_system_auto_install - Configure USB auto installation in Fortinet's FortiOS and FortiGate.
- fortios_system_auto_script - Configure auto script in Fortinet's FortiOS and FortiGate.
- fortios_system_automation_action - Action for automation stitches in Fortinet's FortiOS and FortiGate.
- fortios_system_automation_destination - Automation destinations in Fortinet's FortiOS and FortiGate.
- fortios_system_automation_stitch - Automation stitches in Fortinet's FortiOS and FortiGate.
- fortios_system_automation_trigger - Trigger for automation stitches in Fortinet's FortiOS and FortiGate.
- fortios_system_autoupdate_push_update - Configure push updates in Fortinet's FortiOS and FortiGate.
- fortios_system_autoupdate_schedule - Configure update schedule in Fortinet's FortiOS and FortiGate.
- fortios_system_autoupdate_tunneling - Configure web proxy tunnelling for the FDN in Fortinet's FortiOS and FortiGate.
- fortios_system_cluster_sync - Configure FortiGate Session Life Support Protocol (FGSP) session synchronization in Fortinet's FortiOS and FortiGate.
- fortios_system_console - Configure console in Fortinet's FortiOS and FortiGate.
- fortios_system_csf - Add this FortiGate to a Security Fabric or set up a new Security Fabric on this FortiGate in Fortinet's FortiOS and FortiGate.
- fortios_system_custom_language - Configure custom languages in Fortinet's FortiOS and FortiGate.
- fortios_system_ddns - Configure DDNS in Fortinet's FortiOS and FortiGate.
- fortios_system_dedicated_mgmt - Configure dedicated management in Fortinet's FortiOS and FortiGate.
- fortios_system_dhcp6_server - Configure DHCPv6 servers in Fortinet's FortiOS and FortiGate.
- fortios_system_dns_database - Configure DNS databases in Fortinet's FortiOS and FortiGate.
- fortios_system_dns_server - Configure DNS servers in Fortinet's FortiOS and FortiGate.
- fortios_system_dscp_based_priority - Configure DSCP based priority table in Fortinet's FortiOS and FortiGate.
- fortios_system_email_server - Configure the email server used by the FortiGate various things. For example, for sending email messages to users to support user authentication features in Fortinet's FortiOS and FortiGate.
- fortios_system_external_resource - Configure external resource in Fortinet's FortiOS and FortiGate.
- fortios_system_fips_cc - Configure FIPS-CC mode in Fortinet's FortiOS and FortiGate.
- fortios_system_firmware_upgrade - Perform firmware upgrade on FortiGate or FortiOS (FOS) device.
- fortios_system_fm - Configure FM in Fortinet's FortiOS and FortiGate.
- fortios_system_fortiguard - Configure FortiGuard services in Fortinet's FortiOS and FortiGate.
- fortios_system_fortimanager - Configure FortiManager in Fortinet's FortiOS and FortiGate.
- fortios_system_fortisandbox - Configure FortiSandbox in Fortinet's FortiOS and FortiGate.
- fortios_system_fsso_polling - Configure Fortinet Single Sign On (FSSO) server in Fortinet's FortiOS and FortiGate.
- fortios_system_ftm_push - Configure FortiToken Mobile push services in Fortinet's FortiOS and FortiGate.
- fortios_system_geoip_override - Configure geographical location mapping for IP address(es) to override mappings from FortiGuard in Fortinet's FortiOS and FortiGate.
- fortios_system_gre_tunnel - Configure GRE tunnel in Fortinet's FortiOS and FortiGate.
- fortios_system_ha - Configure HA in Fortinet's FortiOS and FortiGate.
- fortios_system_ha_monitor - Configure HA monitor in Fortinet's FortiOS and FortiGate.
- fortios_system_ipip_tunnel - Configure IP in IP Tunneling in Fortinet's FortiOS and FortiGate.
- fortios_system_ips_urlfilter_dns - Configure IPS URL filter DNS servers in Fortinet's FortiOS and FortiGate.
- fortios_system_ips_urlfilter_dns6 - Configure IPS URL filter IPv6 DNS servers in Fortinet's FortiOS and FortiGate.
- fortios_system_ipv6_neighbor_cache - Configure IPv6 neighbor cache table in Fortinet's FortiOS and FortiGate.
- fortios_system_ipv6_tunnel - Configure IPv6/IPv4 in IPv6 tunnel in Fortinet's FortiOS and FortiGate.
- fortios_system_link_monitor - Configure Link Health Monitor in Fortinet's FortiOS and FortiGate.
- fortios_system_mac_address_table - Configure MAC address tables in Fortinet's FortiOS and FortiGate.
- fortios_system_management_tunnel - Management tunnel configuration in Fortinet's FortiOS and FortiGate.
- fortios_system_mobile_tunnel - Configure Mobile tunnels, an implementation of Network Mobility (NEMO) extensions for Mobile IPv4 RFC5177 in Fortinet's FortiOS and FortiGate.
- fortios_system_nat64 - Configure NAT64 in Fortinet's FortiOS and FortiGate.
- fortios_system_nd_proxy - Configure IPv6 neighbor discovery proxy (RFC4389) in Fortinet's FortiOS and FortiGate.
- fortios_system_netflow - Configure NetFlow in Fortinet's FortiOS and FortiGate.
- fortios_system_network_visibility - Configure network visibility settings in Fortinet's FortiOS and FortiGate.
- fortios_system_ntp - Configure system NTP information in Fortinet's FortiOS and FortiGate.
- fortios_system_object_tagging - Configure object tagging in Fortinet's FortiOS and FortiGate.
- fortios_system_password_policy - Configure password policy for locally defined administrator passwords and IPsec VPN pre-shared keys in Fortinet's FortiOS and FortiGate.
- fortios_system_password_policy_guest_admin - Configure the password policy for guest administrators in Fortinet's FortiOS and FortiGate.
- fortios_system_pppoe_interface - Configure the PPPoE interfaces in Fortinet's FortiOS and FortiGate.
- fortios_system_probe_response - Configure system probe response in Fortinet's FortiOS and FortiGate.
- fortios_system_proxy_arp - Configure proxy-ARP in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_admin - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_alertmail - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_auth - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_device_detection_portal - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_ec - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_fortiguard_wf - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_ftp - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_group - Configure replacement message groups in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_http - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_icap - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_image - Configure replacement message images in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_mail - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_nac_quar - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_nntp - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_spam - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_sslvpn - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_traffic_quota - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_utm - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_replacemsg_webproxy - Replacement messages in Fortinet's FortiOS and FortiGate.
- fortios_system_resource_limits - Configure resource limits in Fortinet's FortiOS and FortiGate.
- fortios_system_session_helper - Configure session helper in Fortinet's FortiOS and FortiGate.
- fortios_system_session_ttl - Configure global session TTL timers for this FortiGate in Fortinet's FortiOS and FortiGate.
- fortios_system_sflow - Configure sFlow in Fortinet's FortiOS and FortiGate.
- fortios_system_sit_tunnel - Configure IPv6 tunnel over IPv4 in Fortinet's FortiOS and FortiGate.
- fortios_system_sms_server - Configure SMS server for sending SMS messages to support user authentication in Fortinet's FortiOS and FortiGate.
- fortios_system_snmp_community - SNMP community configuration in Fortinet's FortiOS and FortiGate.
- fortios_system_snmp_sysinfo - SNMP system info configuration in Fortinet's FortiOS and FortiGate.
- fortios_system_snmp_user - SNMP user configuration in Fortinet's FortiOS and FortiGate.
- fortios_system_storage - Configure logical storage in Fortinet's FortiOS and FortiGate.
- fortios_system_switch_interface - Configure software switch interfaces by grouping physical and WiFi interfaces in Fortinet's FortiOS and FortiGate.
- fortios_system_tos_based_priority - Configure Type of Service (ToS) based priority table to set network traffic priorities in Fortinet's FortiOS and FortiGate.
- fortios_system_vdom_dns - Configure DNS servers for a non-management VDOM in Fortinet's FortiOS and FortiGate.
- fortios_system_vdom_exception - Global configuration objects that can be configured independently for all VDOMs or for the defined VDOM scope in Fortinet's FortiOS and FortiGate.
- fortios_system_vdom_link - Configure VDOM links in Fortinet's FortiOS and FortiGate.
- fortios_system_vdom_netflow - Configure NetFlow per VDOM in Fortinet's FortiOS and FortiGate.
- fortios_system_vdom_property - Configure VDOM property in Fortinet's FortiOS and FortiGate.
- fortios_system_vdom_radius_server - Configure a RADIUS server to use as a RADIUS Single Sign On (RSSO) server for this VDOM in Fortinet's FortiOS and FortiGate.
- fortios_system_vdom_sflow - Configure sFlow per VDOM to add or change the IP address and UDP port that FortiGate sFlow agents in this VDOM use to send sFlow datagrams to an sFlow collector in Fortinet's FortiOS and FortiGate.
- fortios_system_virtual_wire_pair - Configure virtual wire pairs in Fortinet's FortiOS and FortiGate.
- fortios_system_vxlan - Configure VXLAN devices in Fortinet's FortiOS and FortiGate.
- fortios_system_wccp - Configure WCCP in Fortinet's FortiOS and FortiGate.
- fortios_system_zone - Configure zones to group two or more interfaces. When a zone is created you can configure policies for the zone instead of individual interfaces in the zone in Fortinet's FortiOS and FortiGate.
- fortios_user_device - Configure devices in Fortinet's FortiOS and FortiGate.
- fortios_user_device_access_list - Configure device access control lists in Fortinet's FortiOS and FortiGate.
- fortios_user_device_category - Configure device categories in Fortinet's FortiOS and FortiGate.
- fortios_user_device_group - Configure device groups in Fortinet's FortiOS and FortiGate.
- fortios_user_domain_controller - Configure domain controller entries in Fortinet's FortiOS and FortiGate.
- fortios_user_fortitoken - Configure FortiToken in Fortinet's FortiOS and FortiGate.
- fortios_user_fsso - Configure Fortinet Single Sign On (FSSO) agents in Fortinet's FortiOS and FortiGate.
- fortios_user_fsso_polling - Configure FSSO active directory servers for polling mode in Fortinet's FortiOS and FortiGate.
- fortios_user_group - Configure user groups in Fortinet's FortiOS and FortiGate.
- fortios_user_krb_keytab - Configure Kerberos keytab entries in Fortinet's FortiOS and FortiGate.
- fortios_user_ldap - Configure LDAP server entries in Fortinet's FortiOS and FortiGate.
- fortios_user_local - Configure local users in Fortinet's FortiOS and FortiGate.
- fortios_user_password_policy - Configure user password policy in Fortinet's FortiOS and FortiGate.
- fortios_user_peer - Configure peer users in Fortinet's FortiOS and FortiGate.
- fortios_user_peergrp - Configure peer groups in Fortinet's FortiOS and FortiGate.
- fortios_user_pop3 - POP3 server entry configuration in Fortinet's FortiOS and FortiGate.
- fortios_user_quarantine - Configure quarantine support in Fortinet's FortiOS and FortiGate.
- fortios_user_security_exempt_list - Configure security exemption list in Fortinet's FortiOS and FortiGate.
- fortios_user_setting - Configure user authentication setting in Fortinet's FortiOS and FortiGate.
- fortios_vpn_certificate_ca - CA certificate in Fortinet's FortiOS and FortiGate.
- fortios_vpn_certificate_crl - Certificate Revocation List as a PEM file in Fortinet's FortiOS and FortiGate.
- fortios_vpn_certificate_local - Local keys and certificates in Fortinet's FortiOS and FortiGate.
- fortios_vpn_certificate_ocsp_server - OCSP server configuration in Fortinet's FortiOS and FortiGate.
- fortios_vpn_certificate_remote - Remote certificate as a PEM file in Fortinet's FortiOS and FortiGate.
- fortios_vpn_certificate_setting - VPN certificate setting in Fortinet's FortiOS and FortiGate.
- fortios_vpn_l2tp - Configure L2TP in Fortinet's FortiOS and FortiGate.
- fortios_vpn_pptp - Configure PPTP in Fortinet's FortiOS and FortiGate.
- fortios_vpn_ssl_web_host_check_software - SSL-VPN host check software in Fortinet's FortiOS and FortiGate.
- fortios_vpn_ssl_web_realm - Realm in Fortinet's FortiOS and FortiGate.
- fortios_vpn_ssl_web_user_bookmark - Configure SSL VPN user bookmark in Fortinet's FortiOS and FortiGate.
- fortios_vpn_ssl_web_user_group_bookmark - Configure SSL VPN user group bookmark in Fortinet's FortiOS and FortiGate.
- fortios_waf_main_class - Hidden table for datasource in Fortinet's FortiOS and FortiGate.
- fortios_waf_signature - Hidden table for datasource in Fortinet's FortiOS and FortiGate.
- fortios_waf_sub_class - Hidden table for datasource in Fortinet's FortiOS and FortiGate.
- fortios_wanopt_auth_group - Configure WAN optimization authentication groups in Fortinet's FortiOS and FortiGate.
- fortios_wanopt_cache_service - Designate cache-service for wan-optimization and webcache in Fortinet's FortiOS and FortiGate.
- fortios_wanopt_content_delivery_network_rule - Configure WAN optimization content delivery network rules in Fortinet's FortiOS and FortiGate.
- fortios_wanopt_peer - Configure WAN optimization peers in Fortinet's FortiOS and FortiGate.
- fortios_wanopt_remote_storage - Configure a remote cache device as Web cache storage in Fortinet's FortiOS and FortiGate.
- fortios_wanopt_webcache - Configure global Web cache settings in Fortinet's FortiOS and FortiGate.
- fortios_web_proxy_debug_url - Configure debug URL addresses in Fortinet's FortiOS and FortiGate.
- fortios_web_proxy_forward_server - Configure forward-server addresses in Fortinet's FortiOS and FortiGate.
- fortios_web_proxy_forward_server_group - Configure a forward server group consisting or multiple forward servers. Supports failover and load balancing in Fortinet's FortiOS and FortiGate.
- fortios_web_proxy_url_match - Exempt URLs from web proxy forwarding and caching in Fortinet's FortiOS and FortiGate.
- fortios_web_proxy_wisp - Configure Wireless Internet service provider (WISP) servers in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_ap_status - Configure access point status (rogue | accepted | suppressed) in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_ble_profile - Configure Bluetooth Low Energy profile in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_bonjour_profile - Configure Bonjour profiles. Bonjour is Apple's zero configuration networking protocol. Bonjour profiles allow APs and FortiAPs to connect to networks using Bonjour in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_anqp_3gpp_cellular - Configure 3GPP public land mobile network (PLMN) in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_anqp_ip_address_type - Configure IP address type availability in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_anqp_nai_realm - Configure network access identifier (NAI) realm in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_anqp_network_auth_type - Configure network authentication type in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_anqp_roaming_consortium - Configure roaming consortium in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_anqp_venue_name - Configure venue name duple in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_h2qp_conn_capability - Configure connection capability in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_h2qp_operator_name - Configure operator friendly name in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_h2qp_osu_provider - Configure online sign up (OSU) provider list in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_h2qp_wan_metric - Configure WAN metrics in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_hs_profile - Configure hotspot profile in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_icon - Configure OSU provider icon in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_hotspot20_qos_map - Configure QoS map set in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_inter_controller - Configure inter wireless controller operation in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_qos_profile - Configure WiFi quality of service (QoS) profiles in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_timers - Configure CAPWAP timers in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_vap_group - Configure virtual Access Point (VAP) groups in Fortinet's FortiOS and FortiGate.
- fortios_wireless_controller_wtp_group - Configure WTP groups in Fortinet's FortiOS and FortiGate.

icx
^^^

- icx_banner - Manage multiline banners on Ruckus ICX 7000 series switches
- icx_command - Run arbitrary commands on remote Ruckus ICX 7000 series switches
- icx_config - Manage configuration sections of Ruckus ICX 7000 series switches
- icx_copy - Transfer files from or to remote Ruckus ICX 7000 series switches
- icx_facts - Collect facts from remote Ruckus ICX 7000 series switches
- icx_interface - Manage Interface on Ruckus ICX 7000 series switches
- icx_l3_interface - Manage Layer-3 interfaces on Ruckus ICX 7000 series switches
- icx_linkagg - Manage link aggregation groups on Ruckus ICX 7000 series switches
- icx_lldp - Manage LLDP configuration on Ruckus ICX 7000 series switches
- icx_logging - Manage logging on Ruckus ICX 7000 series switches
- icx_ping - Tests reachability using ping from Ruckus ICX 7000 series switches
- icx_static_route - Manage static IP routes on Ruckus ICX 7000 series switches
- icx_system - Manage the system attributes on Ruckus ICX 7000 series switches
- icx_user - Manage the user accounts on Ruckus ICX 7000 series switches.
- icx_vlan - Manage VLANs on Ruckus ICX 7000 series switches

ios
^^^

- ios_interfaces - Manages interface attributes of Cisco IOS network devices
- ios_l2_interfaces - Manage Layer-2 interface on Cisco IOS devices.
- ios_l3_interfaces - Manage Layer-3 interface on Cisco IOS devices.
- ios_lacp - Manage Global Link Aggregation Control Protocol (LACP) on Cisco IOS devices.
- ios_lacp_interfaces - Manage Link Aggregation Control Protocol (LACP) on Cisco IOS devices interface.
- ios_lag_interfaces - Manage Link Aggregation on Cisco IOS devices.
- ios_lldp_global - Configure and manage Link Layer Discovery Protocol(LLDP) attributes on IOS platforms.
- ios_lldp_interfaces - Manage link layer discovery protocol (LLDP) attributes of interfaces on Cisco IOS devices.
- ios_vlans - Manage VLANs on Cisco IOS devices.

iosxr
^^^^^

- iosxr_interfaces - Manage interface attributes on Cisco IOS-XR network devices
- iosxr_l2_interfaces - Manage Layer-2 interface on Cisco IOS-XR devices
- iosxr_l3_interfaces - Manage Layer-3 interface on Cisco IOS-XR devices.
- iosxr_lacp - Manage Global Link Aggregation Control Protocol (LACP) on IOS-XR devices.
- iosxr_lacp_interfaces - Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on IOS-XR devices.
- iosxr_lag_interfaces - Manages attributes of LAG/Ether-Bundle interfaces on IOS-XR devices.
- iosxr_lldp_global - Manage Global Link Layer Discovery Protocol (LLDP) settings on IOS-XR devices.
- iosxr_lldp_interfaces - Manage Link Layer Discovery Protocol (LLDP) attributes of interfaces on IOS-XR devices.

junos
^^^^^

- junos_interfaces - Manages interface attributes of Juniper Junos OS network devices.
- junos_l2_interfaces - Manage Layer-2 interface on Juniper JUNOS devices
- junos_l3_interfaces - Manage Layer 3 interface on Juniper JUNOS devices
- junos_lacp - Manage Global Link Aggregation Control Protocol (LACP) on Juniper Junos devices
- junos_lacp_interfaces - Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on Juniper JUNOS devices.
- junos_lag_interfaces - Manage Link Aggregation on Juniper JUNOS devices.
- junos_lldp_global - Manage link layer discovery protocol (LLDP) attributes on Juniper JUNOS devices.
- junos_lldp_interfaces - Manage link layer discovery protocol (LLDP) attributes of interfaces on Juniper JUNOS devices
- junos_vlans - Create and manage VLAN configurations on Junos OS

meraki
^^^^^^

- meraki_firewalled_services - Edit firewall policies for administrative network services
- meraki_malware - Manage Malware Protection in the Meraki cloud
- meraki_mx_l7_firewall - Manage MX appliance layer 7 firewalls in the Meraki cloud
- meraki_nat - Manage NAT rules in Meraki cloud
- meraki_webhook - Manage webhooks configured in the Meraki cloud

netvisor
^^^^^^^^

- pn_fabric_local - CLI command to modify fabric-local
- pn_ipv6security_raguard - CLI command to create/modify/delete ipv6security-raguard
- pn_ipv6security_raguard_port - CLI command to add/remove ipv6security-raguard-port
- pn_ipv6security_raguard_vlan - CLI command to add/remove ipv6security-raguard-vlan
- pn_log_audit_exception - CLI command to create/delete an audit exception
- pn_prefix_list - CLI command to create/delete prefix-list
- pn_vrouter_bgp - CLI command to add/modify/remove vrouter-bgp
- pn_vrouter_loopback_interface - CLI command to add/remove vrouter-loopback-interface
- pn_vrouter_ospf - CLI command to add/remove vrouter-ospf
- pn_vrouter_packet_relay - CLI command to add/remove vrouter-packet-relay
- pn_vtep - CLI command to create/delete vtep

nxos
^^^^

- nxos_bfd_global - Bidirectional Forwarding Detection (BFD) global-level configuration
- nxos_bfd_interfaces - Manages BFD attributes of nxos interfaces.
- nxos_interfaces - Manages interface attributes of NX-OS Interfaces
- nxos_l2_interfaces - Manages Layer-2 Interfaces attributes of NX-OS Interfaces
- nxos_l3_interfaces - Manages Layer-3 Interfaces attributes of NX-OS Interfaces
- nxos_lacp - Manage Global Link Aggregation Control Protocol (LACP) on Cisco NX-OS devices.
- nxos_lacp_interfaces - Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on Cisco NX-OS devices.
- nxos_lag_interfaces - Manages link aggregation groups of NX-OS Interfaces
- nxos_lldp_global - Configure and manage Link Layer Discovery Protocol(LLDP) attributes on NX-OS platforms.
- nxos_telemetry - Telemetry Monitoring Service (TMS) configuration
- nxos_vlans - Create VLAN and manage VLAN configurations on NX-OS Interfaces

onyx
^^^^

- onyx_qos - Configures QoS
- onyx_traffic_class - Configures Traffic Class
- onyx_wjh - Configure what-just-happend module

vyos
^^^^

- vyos_interfaces - Manages interface attributes of VyOS network devices.
- vyos_l3_interfaces - Manages L3 interface attributes of VyOS network devices.
- vyos_lag_interfaces - Manages attributes of link aggregation groups on VyOS network devices.
- vyos_lldp_global - Manage link layer discovery protocol (LLDP) attributes on VyOS devices..
- vyos_lldp_interfaces - Manages attributes of lldp interfaces on VyOS devices.

Notification
~~~~~~~~~~~~

- snow_record_find - Search for multiple records from ServiceNow

Remote Management
~~~~~~~~~~~~~~~~~

cpm
^^^

- cpm_serial_port_config - Set Serial port parameters in WTI OOB and PDU devices
- cpm_serial_port_info - Get Serial port parameters in WTI OOB and PDU devices

dellemc
^^^^^^^

- ome_device_info - Retrieves the information about Device.

ucs
^^^

- ucs_vlan_find - Find VLANs on Cisco UCS Manager

Source Control
~~~~~~~~~~~~~~

- gitlab_project_variable - Creates/updates/deletes GitLab Projects Variables

Storage
~~~~~~~

netapp
^^^^^^

- na_ontap_firmware_upgrade - NetApp ONTAP firmware upgrade for SP, shelf, ACP, and disk.
- na_ontap_info - NetApp information gatherer
- na_ontap_ipspace - NetApp ONTAP Manage an ipspace
- na_ontap_kerberos_realm - NetApp ONTAP vserver nfs kerberos realm
- na_ontap_ldap - NetApp ONTAP LDAP
- na_ontap_ldap_client - NetApp ONTAP LDAP client
- na_ontap_ndmp - NetApp ONTAP NDMP services configuration
- na_ontap_object_store - NetApp ONTAP manage object store config.
- na_ontap_ports - NetApp ONTAP add/remove ports
- na_ontap_qos_adaptive_policy_group - NetApp ONTAP Adaptive Quality of Service policy group.
- na_ontap_volume_autosize - NetApp ONTAP manage volume autosize
- na_ontap_vscan - NetApp ONTAP Vscan enable/disable.
- na_ontap_vserver_cifs_security - NetApp ONTAP vserver CIFS security modification
- netapp_e_drive_firmware - NetApp E-Series manage drive firmware
- netapp_e_firmware - NetApp E-Series manage firmware.

purestorage
^^^^^^^^^^^

- purefa_alert - Configure Pure Storage FlashArray alert email settings
- purefa_arrayname - Configure Pure Storage FlashArray array name
- purefa_banner - Configure Pure Storage FlashArray GUI and SSH MOTD message
- purefa_connect - Manage replication connections between two FlashArrays
- purefa_info - Collect information from Pure Storage FlashArray
- purefa_phonehome - Enable or Disable Pure Storage FlashArray Phonehome
- purefa_smtp - Configure FlashArray SMTP settings
- purefa_snmp - Configure FlashArray SNMP Managers
- purefa_syslog - Configure Pure Storage FlashArray syslog settings
- purefa_vg - Manage volume groups on Pure Storage FlashArrays
- purefb_info - Collect information from Pure Storage FlashBlade
- purefb_ra - Enable or Disable Pure Storage FlashBlade Remote Assist
- purefb_smtp - Configure SMTP for Pure Storage FlashBlade

vexata
^^^^^^

- vexata_eg - Manage export groups on Vexata VX100 storage arrays

System
~~~~~~

- listen_ports_facts - Gather facts on processes listening on TCP and UDP ports.
- syspatch - Manage OpenBSD system patches

Web Infrastructure
~~~~~~~~~~~~~~~~~~

- nginx_status_info - Retrieve information on nginx status.

Windows
~~~~~~~

- win_netbios - Manage NetBIOS over TCP/IP settings on Windows.