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

    zonedef>
    info    verify  quit    commit  add     set

    zonedef> set
    brand                     image_uuid                alias
    autoboot                  billing_id                brand
    cpu_cap                   cpu_shares                create_only
    create_timestamp          customer_metadata         dataset_uuid
    delegate_dataset          do_not_inventory          dns_domain
    fs_allowed                hostname                  internal_metadata
    limit_priv                max_locked_memory         max_lwps
    max_physical_memory       max_swap                  nowait
    owner_uuid                package_name              package_version
    quota                     ram                       remove_customer_metadata
    remove_internal_metadata  remove_tags               resolvers
    set_customer_metadata     set_internal_metadata     set_tags
    tags                      tmpfs                     transition
    uuid                      zfs_data_compression      zfs_data_recsize
    zfs_io_priority           zfs_root_compression      zfs_root_recsize
    zfs_storage_pool_name     zonename                  zpool

    zonedef> set image_uuid=
    9012a9c2-f15d-11e1-a33a-afaec53ebde9  3390ca7c-f2e7-11e1-8818-c36e0b12e58b

