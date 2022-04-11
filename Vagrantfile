# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.6.2"

cpus = 2
description = "macOS 11.0.0 (Big Sur)"
memory = 4096

Vagrant.configure("2") do |config|

  config.ssh.password = "vagrant"
  config.ssh.username = "vagrant"

  config.vm.define "" do |os|
    os.vm.box="Megabyte/macOS-Desktop"
    os.vm.hostname = "vagrant-macos"

    os.vm.network "forwarded_port", guest: 22, host: 58022, id: "ssh", auto_correct: true
    os.vm.network "forwarded_port", guest: 80, host: 58080, id: "http", auto_correct: true
    os.vm.network "forwarded_port", guest: 443, host: 58443, id: "https", auto_correct: true
    os.vm.network "forwarded_port", guest: 3389, host: 53389, id: "rdp", auto_correct: true

    os.vm.provider "parallels" do |v|
      v.cpus = cpus
      v.memory = memory
      v.name = description
      v.update_guest_tools = true
    end

    os.vm.provider "virtualbox" do |v|
      v.check_guest_additions = true
      v.cpus = cpus
      v.customize ["modifyvm", :id, "--accelerate3d", "on"]
      v.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
      v.customize ["modifyvm", :id, "--graphicscontroller", "vmsvga"]
      v.customize ["modifyvm", :id, "--hwvirtex", "on"]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--vram", "256"]
      v.customize ["setextradata", "global", "GUI/SuppressMessages", "all"]
      v.gui = true
      v.memory = memory
      v.name = description
    end

    os.vm.provider "vmware_fusion" do |v|
      v.gui = true
      v.vmx["ethernet0.virtualDev"] = "vmxnet3"
      v.vmx["gui.fitGuestUsingNativeDisplayResolution"] = "TRUE"
      v.vmx["gui.fullScreenAtPowerOn"] = "TRUE"
      v.vmx["gui.lastPoweredViewMode"] = "fullscreen"
      v.vmx["gui.viewModeAtPowerOn"] = "fullscreen"
      v.vmx["memsize"] = memory.to_s
      v.vmx["mks.enable3d"] = "TRUE"
      v.vmx["mks.forceDiscreteGPU"] = "TRUE"
      v.vmx["numvcpus"] = cpus.to_s
      v.vmx["RemoteDisplay.vnc.enabled"] = "TRUE"
      v.vmx["RemoteDisplay.vnc.port"] = "5900"
      v.vmx["sound.autodetect"] = "TRUE"
      v.vmx["sound.present"] = "TRUE"
      v.vmx["sound.startConnected"] = "TRUE"
    end

    os.vm.provider "vmware_workstation" do |v|
      v.gui = true
      v.vmx["ethernet0.virtualDev"] = "vmxnet3"
      v.vmx["gui.fitGuestUsingNativeDisplayResolution"] = "TRUE"
      v.vmx["gui.fullScreenAtPowerOn"] = "TRUE"
      v.vmx["gui.lastPoweredViewMode"] = "fullscreen"
      v.vmx["gui.viewModeAtPowerOn"] = "fullscreen"
      v.vmx["memsize"] = memory.to_s
      v.vmx["mks.enable3d"] = "TRUE"
      v.vmx["mks.forceDiscreteGPU"] = "TRUE"
      v.vmx["numvcpus"] = cpus.to_s
      v.vmx["RemoteDisplay.vnc.enabled"] = "TRUE"
      v.vmx["RemoteDisplay.vnc.port"] = "5900"
      v.vmx["sound.autodetect"] = "TRUE"
      v.vmx["sound.present"] = "TRUE"
      v.vmx["sound.startConnected"] = "TRUE"
    end
  end
end
