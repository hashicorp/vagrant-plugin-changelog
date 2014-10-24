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
