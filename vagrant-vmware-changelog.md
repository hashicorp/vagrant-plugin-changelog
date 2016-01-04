## 4.0.4 (December 21, 2015)

  - core: perform a normal VM clone if the linked clone fails - this
    accounts for the case where the user does not have a VMware
    product that supports linked clones (such as the non-PRO versions)

## 4.0.3 (December 14, 2015)

  - core: run provisioner cleanup tasks
  - core: add support for encoding on Ruby 2.1 and 2.2

## 4.0.2 (October 12, 2015)

  - core: fix a nil exception that can happen when the user interrupts
    (ctrl + c)
  - workstation: fix a bug that would cause an exception to be printed
    when the version of Workstation was newer than what the license
    permitted

## 4.0.1 (August 25, 2015)

  - workstation: fix for version parsing code preventing the plugin from
    booting with Workstation 12 on Windows

## 4.0.0 (August 25, 2015)

  - fusion: enable Fusion 8 support with valid license
  - workstation: enable Workstation 12 with valid license

## 3.2.12 (August 17, 2015)

  - core: Increase retries when looking up guest IP address for communicator
    info from 5 to 10. We continue to do linear backoff, meaning we'll wait for
    up to 55 seconds for an IP to be available.

## 3.2.11 (July 29, 2015)

  - hgfs: fall back to legacy `:group` behavior when `getent` based lookup
    does not succeed

## 3.2.10 (July 27, 2015)

  - core: adjust timeout to 45 seconds and raise a more human-friendly error
  - core: do not error when trying to destroy a non-created VM
  - core: allow users to use `VAGRANT_VMWARE_FUSION_EXP` for experimental VMware
    Fusion support again

## 3.2.9 (June 17, 2015)

 - hgfs: fix an issue with the `:group` option of HGFS `synced_folder`s, which
   was causing it to only work with group names that were also usernames.

## 3.2.8 (June 1, 2015)

 - nat_conf: detect and repair a type of nat conf corruption caused by certain
   combinations of previously released versions of VMware, Vagrant, and the
   Vagrant VMware plugin (See: https://github.com/mitchellh/vagrant/issues/5600)

## 3.2.7 (May 29, 2015)

 - core: fix public networks with static ips; they were incorrectly being marked
     as `type: :dhcp`, causing the assigned IP not to be respected
 - synced_folders: improve error message when ssh info cannot be determined

## 3.2.6 (March 23, 2015)

 - nfs: modify the strategy for choosing the guest / host IP address for NFS
     configuration to avoid issues selecting the proper IP address when using
     NFS synced_folders with private_networks

## 3.2.5 (March 23, 2015)

 - workstation-linux: properly reconfigure host `vmnet` devices; fixes
     incorrect VMware configs being generated when Vagrant needed to add a
     network device to the host.

## 3.2.4 (February 26, 2015)

 - workstation-windows: fix another port-forwarding bug causing issues with
   port collisions on subsequent boots

## 3.2.3 (February 17, 2015)

 - core: additional sanity checks during box clone

## 3.2.2 (February 12, 2015)

 - synced_folders: revert symlink-specific code; recent versions of Fusion and
     Workstation handle symlinks properly without any additional configuration;
     incorporating workaround docs for users on older versions of VMWare
     software that have trouble with symlinks
 - workstation-windows: fix slash mismatch preventing multi-vm port forwarding
     from working properly

## 3.2.1 (February 6, 2015)

  - core: (OS X) fall back to sudo if osascript-based privilege escalation
      for installing `sudo_helper` fails for any reason
  - fusion,workstation: fix addSharedFolder side-effect causing symlinks to
      become disabled when multiple shared folders are used
  - fusion,workstation: new provider config `enable_vmrun_ip_lookup`, defaults
      to `true`, allows `vmrun getGuestIpAddress` to be manually skipped to
      work around cases where it returns an incorrect address

## 3.2.0 (January 5, 2015)

  - core: invalid IP addresses returned by `vmrun` are ignored
  - core: static IPs work for _public_ networks (private networks have
      always works)
  - fusion,workstation: symlinks are always enabled on shared folders
  - fusion,workstation: support UDP forwarded ports

## 3.1.2 (November 14, 2014)

  - core: Fix a bug where IPV6 addresses were parsed as IPV4

## 3.1.1 (November 14, 2014)

  - core: Fix a logging bug that was producing misleading information during
    debugging
  - core: More gracefully handle invalid IP addresses returned from VMware

## 3.1.0 (October 24, 2014)

  - core: Cleaner exiting when interrupted.
  - core: Fix infinite vmnet retry loop on route conflict.
  - core: Halt, suspend, etc. will not fatally error if the VM is not
      created.
  - core: On OS X, ask for admin privs using the dialog rather than sudo.
  - fusion: Upgrade dialog will not appear anymore for VMware.
  - fusion: Try DHCP leases backup file to detect IP as well.
  - workstation: Not an error on Linux if the vmware-networks script doesn't
      support the --configure flag.

## 3.0.1 (September 4, 2014)

  - core: Attempt to use `vmrun` to find guest IP address in parallel to
      watching the DHCP leases file. The result is more robust IP
      detection.

## 3.0.0 (September 3, 2014)

  - fusion: enable Fusion 7 support with valid license
  - workstation: groundwork for Workstation 11

## 2.5.0 (August 5, 2014)

  - core: Vagrantfiles with private networks with string "type" values
      will no longer crash.
  - fusion: Groundwork for Fusion 7
  - fusion: Fusion Tech Preview support for Yosemite

## 2.4.0 (May 1, 2014)

  - core: Improve parallelism under Vagrant 1.6 with process-level locking
      for certain situations.
  - core: Remove some custom locking if Vagrant 1.6+ is being used, since
      Vagrant 1.6 does this automatically in core.
  - core: Priority is higher than VirtualBox so it defaults to that
      in Vagrant 1.6.

## 2.3.6 (April 5, 2014)

  - workstation/linux: Look for required binaries on PATH, not just hardcoded
      to `/usr/bin`.

## 2.3.5 (April 2, 2014)

  - Fix issue where synced folders would sometimes not properly
    get SSH info.
  - Emit "vagrant-mounted" event for synced folders.

## Old Versions

  - A public CHANGELOG was not maintained prior to the versions above.
