Configuring a Windows Server
=================================

Windows server 2012 R2 (Win8.1)

- Login as PSMS user
- Pwd is D*****9


OpenSSH
-----------

- Configuration file `sshd_config` here `C:\ProgramData\ssh\sshd_config`

.. code-block:: shell

    Port 8010
    #AddressFamily any
    #ListenAddress 0.0.0.0
    #ListenAddress ::

    # The default is to check both .ssh/authorized_keys and .ssh/authorized_keys2
    # but this is overridden so installations will only check .ssh/authorized_keys
    AuthorizedKeysFile	.ssh/authorized_keys


    # override default of no subsystems
    Subsystem	sftp	sftp-server.exe

    Match Group administrators
        AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys
    ```

    - Create a file `administrators_authorized_keys` to contain `public keys` for password-less SSH authentication


nginx
------------------

nginx is a light-weight front-end web server application.
Compared to alternatives such as ``Apache HTTP`` or ``Microsoft IIS``, ``nginx``
is a much easiler to configure and deploy. It can support many request asynchronously, 
widely use (means very robust in security) which is why it is very widely used in 
the industry.

Program directory: ``C:\Program Files\nginx``


nssm
------------------

https://nssm.cc/

nssm is a service helper which doesn't suck. srvany and other service helper programs suck because 
they don't handle failure of the application running as a service. If you use such a program 
you may see a service listed as started when in fact the application has died. nssm monitors 
the running service and will restart it if it dies. With nssm you know that if a service says it's running, 
it really is. Alternatively, if your application is well-behaved you can configure nssm to absolve all 
responsibility for restarting it and let Windows take care of recovery actions.

nssm logs its progress to the system Event Log so you can get some idea of why an application isn't 
behaving as it should.

nssm also features a graphical service installation and removal facility. 
Prior to version 2.19 it did suck. Now it's quite a bit better.


.. code-block:: powershell

    cd "C:\Program Files\nssm\win64"
    .\nssm.exe 





