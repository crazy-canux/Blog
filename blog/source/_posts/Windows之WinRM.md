---
layout: post
title: Windows之WinRM
comments: true
date: 2016-07-17 08:36:36
updated:
tags:
- winrm
categories:
- Windows
permalink:
---

# WinRM

Windows Remote Management

WinRM是WSMAN(WS-Management Protocol)的增强版。

WinRM是基于SOAP的防火墙友好的远程协议。

<https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx>

windows自带winrm，但是需要设置一个listener, 默认端口5985,建立一个http的连接。

<https://msdn.microsoft.com/en-us/library/aa384372(v=vs.85).aspx>

检查winrm状态：

    cmd> winrm get winrm/config

快速设置winrm：

    cmd> winrm quickconfig
    cmd> winrm quickconfig -transport:https

查看listener配置：

    cmd> winrm enumerate winrm/config/listener

设置auth：

    cmd> winrm set winrm/config/client/auth @{Basic="true"}
    cmd> winrm set winrm/config/service/auth @{Basic="true"}
    cmd> winrm set winrm/config/service @{AllowUnencrypted="true"}

查看auth配置：

    cmd> winrm get winrm/config/service

# ntlm和kerberos

windows的网络安全协议。

# python

使用basic auth和NTLM：

    pip install pywinrm

使用kerberos需要安装：

    sudo apt-get install libkrb5-dev
    pip install pywinrm[kerberos] ?

Session使用：

    import winrm
    Session(target, auth, **kwargs)
    run_cmd(self, command, args=())
    run_ps(self, script)

    # domain 用户使用 ntlm
    s = winrm.Session('127.0.0.1', auth=('domain\user', 'password'), transport='ntlm', server_cert_validation='ignore')
    r = s.run_cmd('ipconfig', ['/all'])
    return_code = r.status_code
    output = r.std_out
    error = r.std_err

Protocol使用：

    import winrm
    Protocol(endpoint, transport=u'plaintext', username=None, password=None, realm=None, service=None, keytab=None, ca_trust_path=None, cert_pem=None, cert_key_pem=None, server_cert_validation=u'validate', kerberos_delegation=False, read_timeout_sec=30, operation_timeout_sec=20, kerberos_hostname_override=None)
    # @param string transport: transport type, one of 'plaintext' (default), 'ntlm', 'kerberos', 'ssl'  # NOQA
    open_shell(self, i_stream=u'stdin', o_stream=u'stdout stderr',
    run_command(self, shell_id, command, arguments=(), console_mode_stdin=True,
    get_command_output(self, shell_id, command_id)
    working_directory=None, env_vars=None, noprofile=False, codepage=437,
    lifetime=None, idle_timeout=None)
    skip_cmd_shell=False)
    send_message(self, message)
    cleanup_command(self, shell_id, command_id)
    close_shell(self, shell_id)

    # domain 用户使用 ntlm
    p = winrm.Protocol(endpoint='http://127.0.0.1:5985/wsman', transport='ntlm', username=r'DOMAIN\user', password='password',server_cert_validation='ignore')
    shell_id = p.open_shell()
    command_id = p.run_command(shell_id, 'ipconfig', ['/all'])
    std_out, std_err, status_code = p.get_command_output(shell_id, command_id)
    p.cleanup_command(shell_id, command_id)
    p.close_shell(shell_id)
