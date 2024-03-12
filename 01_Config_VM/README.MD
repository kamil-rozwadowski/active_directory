# Configuration

1. Configured server VM as Domain Controler.
    - Rename computer:
    ```
    Rename-Computer -NewName DC1
    ```

    - Restart the server

    - Configure IPAdresses
    ```
    New-NetIPAddress –IPAddress 192.168.56.15 -DefaultGateway 192.168.56.1 -PrefixLength 24 -InterfaceIndex (Get-NetAdapter).InterfaceIndex
    ```
    - Install Active Directory Domain Services role
    ```
    Install-WindowsFeature -name AD-Domain-Services -IncludeManagementTools
    ```
    - Created a domain
    ```
    Install-ADDSForest -DomainName xyz.local -DomainNetBIOSName AD - InstallDNS
    ```
    - Configure DNSServerAdresses
    ```
    Set-DNSClientServerAddress –InterfaceIndex (Get-NetAdapter).InterfaceIndex –ServerAddresses 192.168.56.15
    ```
2. Connected Host machine to the domain.
 - Rename computer:
    ```
    Rename-Computer -NewName HOST1
    ```
    - Configure IPAdresses
    ```
    New-NetIPAddress –IPAddress 192.168.56.101 -DefaultGateway 192.168.56.1 -PrefixLength 24 -InterfaceIndex (Get-NetAdapter).InterfaceIndex
    ```
       - Configure DNSServerAdresses
    ```
    Set-DNSClientServerAddress –InterfaceIndex (Get-NetAdapter).InterfaceIndex –ServerAddresses 192.168.56.15
    ```
     - Join to the Domain:
    ```
    Add-Computer -DomainName DOMAINNAME -Restart
    ```
