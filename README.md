# tips
useful or useless tips
# notice for installing mac series os via vmware #
- close vmware service and install unlocker208 so vmware can recognize mac series os
- it is a pity that .iso may not be supported, only .crf is supported, which should be generated from .dmg
- after setting mac vm, open vm dic and find .vmx, after `smc.present = "TRUE"` modify `smc.version = 0`
- then it may be easier to finish the installation
- after getting into mac vm, it may be slow, download [beamoff](http://files.cnblogs.com/files/yipu/beamoff.zip) and install it to address the problem
