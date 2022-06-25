# libvirt-stealth

These configuration files can bypass common anti-vm detection

But this does not mean that all anti-vm can be bypassed

## modified

- disable all hyperv features
  ```
  <hyperv>
    <relaxed state='off'/>
    <vapic state='off'/>
    <spinlocks state='off'/>
    <vpindex state='off'/>
    <runtime state='off'/>
    <synic state='off'/>
    <stimer state='off'/>
    <reset state='off'/>
    <vendor_id state='off'/>
    <frequencies state='off'/>
    <reenlightenment state='off'/>
    <tlbflush state='off'/>
    <ipi state='off'/>
    <evmcs state='off'/>
  </hyperv>
  ```

- hide kvm state
  ```
  <kvm>
    <hidden state='on'/>
  </kvm>
  ```

- hide cpuid status and disable nested virtualization
  ```
  <cpu mode='host-passthrough' check='none'>
    <topology sockets='1' cores='2' threads='1'/>
    <feature policy='disable' name='svm'/>
    <feature policy='disable' name='vmx'/>
    <feature policy='disable' name='hypervisor'/>
  </cpu>
  ```

- remove balloon device
  ```
  <memballoon model='none'/>
  ```
