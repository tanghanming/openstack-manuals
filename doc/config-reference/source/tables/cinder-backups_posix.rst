..
    Warning: Do not edit this file. It is automatically generated from the
    software project's code and your changes will be overwritten.

    The tool to generate this file lives in openstack-doc-tools repository.

    Please make any changes needed in the code, then run the
    autogenerate-config-doc tool from the openstack-doc-tools repository, or
    ask for help on the documentation mailing list, IRC channel or meeting.

.. _cinder-backups_posix:

.. list-table:: Description of POSIX backup driver configuration options
   :header-rows: 1
   :class: config-ref-table

   * - Configuration option = Default value
     - Description
   * - **[DEFAULT]**
     -
   * - ``backup_container`` = ``None``
     - (String) Custom directory to use for backups.
   * - ``backup_enable_progress_timer`` = ``True``
     - (Boolean) Enable or Disable the timer to send the periodic progress notifications to Ceilometer when backing up the volume to the backend storage. The default value is True to enable the timer.
   * - ``backup_file_size`` = ``1999994880``
     - (Integer) The maximum size in bytes of the files used to hold backups. If the volume being backed up exceeds this size, then it will be backed up into multiple files.backup_file_size must be a multiple of backup_sha_block_size_bytes.
   * - ``backup_posix_path`` = ``$state_path/backup``
     - (String) Path specifying where to store backups.
   * - ``backup_sha_block_size_bytes`` = ``32768``
     - (Integer) The size in bytes that changes are tracked for incremental backups. backup_file_size has to be multiple of backup_sha_block_size_bytes.
