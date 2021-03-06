..
    Warning: Do not edit this file. It is automatically generated from the
    software project's code and your changes will be overwritten.

    The tool to generate this file lives in openstack-doc-tools repository.

    Please make any changes needed in the code, then run the
    autogenerate-config-doc tool from the openstack-doc-tools repository, or
    ask for help on the documentation mailing list, IRC channel or meeting.

.. _keystone-mapping:

.. list-table:: Description of mapping configuration options
   :header-rows: 1
   :class: config-ref-table

   * - Configuration option = Default value
     - Description
   * - **[identity_mapping]**
     -
   * - ``driver`` = ``sql``
     - (String) Entry point for the identity mapping backend driver in the `keystone.identity.id_mapping` namespace. Keystone only provides a `sql` driver, so there is no reason to change this unless you are providing a custom entry point.
   * - ``generator`` = ``sha256``
     - (String) Entry point for the public ID generator for user and group entities in the `keystone.identity.id_generator` namespace. The Keystone identity mapper only supports generators that produce 64 bytes or less. Keystone only provides a `sha256` entry point, so there is no reason to change this value unless you're providing a custom entry point.
   * - ``backward_compatible_ids`` = ``True``
     - (Boolean) The format of user and group IDs changed in Juno for backends that do not generate UUIDs (for example, LDAP), with keystone providing a hash mapping to the underlying attribute in LDAP. By default this mapping is disabled, which ensures that existing IDs will not change. Even when the mapping is enabled by using domain-specific drivers (`[identity] domain_specific_drivers_enabled`), any users and groups from the default domain being handled by LDAP will still not be mapped to ensure their IDs remain backward compatible. Setting this value to false will enable the new mapping for all backends, including the default LDAP driver. It is only guaranteed to be safe to enable this option if you do not already have assignments for users and groups from the default LDAP domain, and you consider it to be acceptable for Keystone to provide the different IDs to clients than it did previously (existing IDs in the API will suddenly change). Typically this means that the only time you can set this value to false is when configuring a fresh installation, although that is the recommended value.
