Controller node
~~~~~~~~~~~~~~~

Configure network interfaces
----------------------------

#. Configure the first interface as the management interface:

   IP address: 10.0.0.11

   Network mask: 255.255.255.0 (or /24)

   Default gateway: 10.0.0.1

#. The provider interface uses a special configuration without an IP
   address assigned to it. Configure the second interface as the provider
   interface:

   Replace ``INTERFACE_NAME`` with the actual interface name. For example,
   *eth1* or *ens224*.

   .. only:: ubuntu or debian

      * Edit the ``/etc/network/interfaces`` file to contain the following:

        .. path /etc/network/interfaces
        .. code-block:: bash

           # The provider network interface
           auto INTERFACE_NAME
           iface INTERFACE_NAME inet manual
           up ip link set dev $IFACE up
           down ip link set dev $IFACE down

        .. end

   .. endonly

   .. only:: rdo

      * Edit the ``/etc/sysconfig/network-scripts/ifcfg-INTERFACE_NAME`` file
        to contain the following:

        Do not change the ``HWADDR`` and ``UUID`` keys.

        .. path /etc/sysconfig/network-scripts/ifcfg-INTERFACE_NAME
        .. code-block:: ini

           DEVICE=INTERFACE_NAME
           TYPE=Ethernet
           ONBOOT="yes"
           BOOTPROTO="none"

        .. end

   .. endonly

   .. only:: obs

      * Edit the ``/etc/sysconfig/network/ifcfg-INTERFACE_NAME`` file to
        contain the following:

        .. path /etc/sysconfig/network/ifcfg-INTERFACE_NAME
        .. code-block:: ini

           STARTMODE='auto'
           BOOTPROTO='static'

        .. end

   .. endonly

#. Reboot the system to activate the changes.

Configure name resolution
-------------------------

#. Set the hostname of the node to ``controller``.

#. .. include:: shared/edit_hosts_file.txt
