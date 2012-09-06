vmcfg - SmartOS zone definition file (JSON) creator
===

vmcfg is a tool that allows you to create the zone definition file
easily. It (poorly) gets its insipiration from zonecfg(1M).

## Installation and usage

Copy vmcfg to /opt

    # chmod +x /opt/vmcfg
    # /opt/vmcfg -f /tmp/riakzone.json
    /tmp/riakzone.json does not exist.
    Use 'set brand' to begin.
    zonedef> set brand=joyent
    zonedef> set image_uuid=399e09fc-c448-11e1-b3c8-a3d517dfbb07
    zonedef> set alias=riak-machine
    zonedef> set ram=1024
    zonedef> add net
    zonedef:net> set nic_tag=admin
    zonedef:net> set ip=10.88.88.55
    zonedef:net> set netmask=255.255.255.0
    zonedef:net> set gateway=10.88.88.2
    zonedef:net> end
    zonedef> info
    { brand: 'joyent',
      image_uuid: '399e09fc-c448-11e1-b3c8-a3d517dfbb07',
      alias: 'riak-machine',
      nics:
       [ { nic_tag: 'admin',
           ip: '10.88.88.55',
           netmask: '255.255.255.0',
           gateway: '10.88.88.2' } ] }
    zonedef> commit
    Succesfully written zone definition file /tmp/riakzone.json.
    zonedef> quit
    Warning, quit does not save. Really quit ? [y/N] y
    # vmadm create < /tmp/riakzone.json

The tool also provides completion:

    zonedef>[TAB]
    info                           verify                         quit                           commit
    add net                        add fs                         set brand=                     set image_uuid=
    set alias=                     set autoboot=                  set billing_id=                set brand=
    set cpu_cap=                   set cpu_shares=                set create_only=               set create_timestamp=
    set customer_metadata=         set dataset_uuid=              set delegate_dataset=          set do_not_inventory=
    set dns_domain=                set fs_allowed=                set hostname=                  set internal_metadata=
    set limit_priv=                set max_locked_memory=         set max_lwps=                  set max_physical_memory=
    set max_swap=                  set nowait=                    set owner_uuid=                set package_name=
    set package_version=           set quota=                     set ram=                       set remove_customer_metadata=
    set remove_internal_metadata=  set remove_tags=               set resolvers=                 set set_customer_metadata=
    set set_internal_metadata=     set set_tags=                  set tags=                      set tmpfs=
    set transition=                set uuid=                      set zfs_data_compression=      set zfs_data_recsize=
    set zfs_io_priority=           set zfs_root_compression=      set zfs_root_recsize=          set zfs_storage_pool_name=
    set zonename=                  set zpool=

