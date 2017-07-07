# [Setting up two PXE servers on the same network: WDS and GNU/Linux PXE Server](#setting-up-two-pxe-servers-on-the-same-network)

Michael McMahon

Rewrite/update based on Eric Gray's 2011 article http://www.vcritical.com/2011/06/peaceful-coexistence-wds-and-linux-pxe-servers/

There are many guides on setting up a Windows Deployment Server (WDS) and GNU/Linux PXE servers.  I will not go into the specifics of setting up a general PXE server.  Setting up a WDS server or a GNU/Linux PXE server is simple by following guides availabe online, but there are very few articles about configuring multiple PXE servers on the same network.

Scenario: My organization has a WDS server configured on our network.  We use GNU/Linux regularly and want to use a GNU/Linux PXE server.  Our options are creating a new network with new cable drops or use the prexisting network.  Using the preexisting network would be easier and cheaper.

Configure and test this entire process in a test environment before implementing this on a production environment.

Requirements:

* A working WDS server with DHCP and DNS configured.  This needs to be tested with PXE booting before starting.
* Another server to configure as a GNU/Linux PXE server
* A third machine that can boot into PXE
* A switch
* Network cables to connect the four boxes
