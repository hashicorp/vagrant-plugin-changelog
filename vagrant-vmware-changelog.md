## 5.0.4

  - core: Include VMware path validations
  - core: Prevent helper task AC requirement on Windows
  - core: Update username filtering during Windows installations

## 5.0.3

  - core: Resolve cross-link errors on installation

## 5.0.2

  - core: Remove osascript usage on darwin
  - core: Fix username pathing issues on Windows
  - core: Fix installation setup on some Linux platforms

## 5.0.1

  - core: Provide useful error when VMware utility task fails on Windows
  - core: Fix executable path generation on Windows
  - core: Automatically fix data and lock file permissions if encountered
  - core: Use local port forward for SSH connect

## 5.0.0

  - core: Add support for VMware Fusion 10 and VMware Workstation 14

## 4.0.25

  - core: Update sudo helper implementation to restrict access
  - core: Update Windows to no longer require Administrator privileges
    for normal usage.
  - core: Fix port forward collision bugs where deleted ports are
    automatically re-added to the nat configuration.

## 4.0.23

  - core: Prevent loading of user defined files within sudo helper.

## 4.0.22

  - core: Fixes plugin startup failure on macOS 10.12

## 4.0.21

  - core: Fix privilege escalation issue within sudo helper
    Thanks to Mark Wadham (https://m4.rkw.io/blog.html) for
    identifying and reporting this issue.

## 4.0.20

  - core: Detect Bundler in sudo wrapper and run setup
  - core: Wait for network to become available when forwarding ports
  - core: Add configurable option to wait for network stabilization

## 4.0.18 (March 3, 2017)

  - core: Disable ethernet VMX whitelist and enable warnings

## 4.0.17 (February 28, 2017)

  - core: Fix file access issue on certain installations

## 4.0.16 (February 27, 2017)

  - core: Persist NAT configuration and repair if rewritten
  - core: Check IP address returned from vmrun and discard if invalid
  - core: Support linked clones

## 4.0.15 (November 28, 2016)

  - core: properly load in Vagrant versions >= 1.9.0

## 4.0.14 (October 14, 2016)

  - linux/shared_folders: Only emit upstart event on mount if upstart is in use.
  - linux/shared_folders: Update hgfs mount strategy for open-vm-tools to properly
    handle symlink usage.
    (See: https://github.com/mitchellh/vagrant/issues/7599 https://github.com/mitchellh/vagrant/issues/5474)
  - linux/shared_folders: Automatically unmount `/mnt/hgfs` if present on guest. Include
    configuration option to disable (`config.vm.unmount_default_hgfs = false`).

## 4.0.13 (September 30, 2016)

  - core: fix setuid usage within sudo wrapper.
    (See: https://github.com/mitchellh/vagrant/issues/7839)

## 4.0.12 (September 27, 2016)

  - core: rebuild go binaries with go 1.7 to properly support macOS Sierra.

## 4.0.11 (August 29, 2016)

  - core: use consistent path formatting to properly match results provided within
    `vmrun list` output.
    (See: https://github.com/mitchellh/vagrant/issues/5838)

## 4.0.8 (February 17, 2016)

  - core: Implement `nic_mac_addresses` provider capability, enables support
    for Darwin guests on Vagrant 1.8+.
    (See: https://github.com/mitchellh/vagrant/issues/6792)

## 4.0.7 (February 8, 2016)

  - core: correct default for `verify_vmnet` boolean provider config option. In
    4.0.6 it was incorrectly defaulted to `false`. It now defaults to `true`.

## 4.0.6 (January 6, 2016)

  - core: add `verify_vmnet` boolean provider config option. Disabling vmnet device verification might in some cases allow Vagrant to boot machines in a mostly-working state, skipping checks that would proactively bail out. This is an advanced option for which HashiCorp can only provide limited support.

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
