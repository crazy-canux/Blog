---
layout: post
title: Virtualization之vSphere
comments: true
date: 2016-07-20 17:10:34
updated:
tags:
- dell
- vmware
- vsphere
categories:
- Virtualization
permalink:
---

# vSphere

vmware的虚拟化平台。

pyVmomi is the Python SDK for the VMware vSphere API that allows you to manage ESX, ESXi, and vCenter.


# python

<https://github.com/vmware/pyvmomi>

    pip install pyvmomi


    from pyVmomi import vim
    from pyVim import connect
    si = connect.SmartConnect(host='hostname', user='username', pwd='password', port='port')

    def find_vm(si, name):
        ct = si.content
        ov = ct.viewManager.CreatecontainerView(ct.rootFolder, [vim.VirtualMachine], true)
        vm_list = ov.view
        for vm in vm_list:
            if vm.name == "vmname":
                return vm
        return None









