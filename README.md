# kite-testbed

Let's run your cloud test on AWS EC2, VMWare ESXi, OpenStack here. `kite-testbed` is just a testbed and provides a test environment for you.

## How does `kite-testbed` work?

* `kite-testbed` depends on [Github Actions](https://docs.github.com/en/actions) as CI. All tests will be run in [self-hosted runner](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners).

* `kite-testbed` does not provide test code and deployment code. Test code `kite-testbed` used will be fetched from [kite-test](https://github.com/virt-s1/kite-test.git) repository. Deploying VM/Instance/Guest on cloud platform with [kite-deploy](https://github.com/virt-s1/kite-deploy.git).

* `kite-testbed` workflow:
  * listening Pull Request
  * checkout [kite-test](https://github.com/virt-s1/kite-test.git) repository
  * checkout [kite-deploy](https://github.com/virt-s1/kite-deploy.git) repository
  * run deployment code
  * download and update application, like kernel
  * run test code

## How to run test?

Currently, `kite-testbed` only supports kernel test. To run a kernel test, what you need to do is sending a Pull Request and put your kernel download URL into `kernel/rhel-8`. `kite-testbed` will finish the rest of things for you.

## Supported scenarios:

### cloud platforms:

* AWS EC2
  * `t2.medium` (`Xen` based instance with `xen_netfront` interface)
  * `t3.medium` (`KVM` based instance with `Elastic Network Adapter` - `ENA`)
  * `t3a.medium` (`KVM` based instance with `AMD` CPU)
  * `m4.large` (`Xen` based instance with the `Intel 82599 VF` interface - `SRIOV`)

* ESXi
  * `ESXi 7.0`
    * `BIOS` (AMD CPU with `VMXNET 3` interface)
    * `EFI` (AMD CPU with `VMXNET 3` interface)

* OpenStack

### applications:

* `kernel`

### Linux distros:

* [Red Hat Enterprise Linux 8](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux)
