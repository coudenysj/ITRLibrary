# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define :itrlib do |itrlib_config|
        itrlib_config.vm.box = "Intracto/Debian81"

        itrlib_config.vm.provider "virtualbox" do |v|
            # show a display for easy debugging
            v.gui = false

            # RAM size
            v.memory = 2048

            # Allow symlinks on the shared folder
            v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
        end

        # allow external connections to the machine
        #itrlib_config.vm.forward_port 80, 8080

        # Shared folder over NFS
        itrlib_config.vm.synced_folder ".", "/vagrant", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc', 'nolock', 'actimeo=2']

        itrlib_config.vm.network "private_network", ip: "192.168.33.79"

        # Shell provisioning
        itrlib_config.vm.provision :shell, :path => "shell_provisioner/run.sh"
    end
end
