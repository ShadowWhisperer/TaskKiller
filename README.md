# TaskKiller

(Safely) force close all running proccesses, and services.   
I call this script from a custom cleanup script, on infected or just slow running computers.  
Build a list of running processes, sort by unique, check if it's required, then force kill it.  

```diff
- Dell / Alienware systems can cause BSOD with some pre-installed applications.
- I work on a ton of Dells, but don't see many Alienware systems.
```
<br>  

    [Processes]
    ==================================================================================================================
    AWCC.Service.exe                         (
    cmd.exe                                  (Windows Command Prompt)                - This script
    CMGShieldSvc.exe                         (
    conhost.exe                              (Console Window Host)                   - 
    csrss.exe                                (Client Server Runtime Process Server)  - 
    Dell.SecurityFramework.Agent.exe         (Dell SecurityFramework)                - BSOD
    Dell.SecurityFramework.Console.exe       (Dell SecurityFramework)                - BSOD
    Dell.SecurityFramework.LocalServer.exe   (Dell SecurityFramework)                - BSOD
    devmonsrv.exe                            (Intel Wifi Driver)                     - Denied
    DFSSvc.exe                               (Dell Foundation Services)              - BSOD
    dllhost.exe                              (Controls DLL Files)                    - 
    dwm.exe                                  (Desktop Window Manager)                - Windows Themes crash loop
    EmsService.exe                           (
    EmsServiceHelper.exe                     (
    explorer.exe                             (Windows Explorer)                      - Windows GUI Stops
    fontdrvhost.exe                          (
    LsaIso.exe                               (
    lsass.exe                                (
    lsm.exe                                  (
    MDLCSvc.exe                              (My Dell Learning Center)               - BSOD
    MsMpEng.exe                              (Windows Defender)                      - Denied / BSOD on Vista
    NisSrv.exe                               (
    obexsrv.exe                              ()                                      - BSOD
    PRSvc.exe                                (Dell Product Registration)             - BSOD
    sc.exe                                   (Service Manager)                       - Used by this script
    services.exe                             (
    sihost.exe                               (Shell Experience Host)                 - Start Menu crash loop
    smss.exe                                 (
    taskhost.exe                             (
    taskmgr.exe                              (Task Manager)                          - All versions before Windows 8
    Taskmgr.exe                              (Task Manager)                          - All versions after Windows 8
    wininit.exe                              (
    winlogon.exe                             (
    WMIC.exe                                 (
    WmiPrvSE.exe                             (Win Manage Instrumentation)            - 
    
    
    
    
    [Services]
    ==================================================================================================================                  
    Appinfo                                  (Application Information)       - Breaks UAC Admin
    BFE                                      (
    BITS                                     (
    BrokerInfrastructure                     (
    Browser                                  (Computer Browser)              - Takes a very long time to stop
    camsvc                                   (
    CDPSvc                                   (
    ClipSVC                                  (
    CoreMessagingRegistrar                   (
    CryptSvc                                 (Cryptographic Sercice)         - 
    DcomLaunch                               (DCOM Server Process Launcher)  - 
    Dhcp                                     (DHCP Client)                   - Needed to get ip address
    DiagTrack                                (
    DispBrokerDesktopSvc                     (
    DisplayEnhancementService                (
    Dnscache                                 (
    DoSvc                                    (
    DPS                                      (
    DsmSvc                                   (
    DusmSvc                                  (
    eventlog                                 (Windows Event Log)
    EventSystem                              (
    FontCache                                (Windows Font Cache Service)
    gpsvc                                    (Group Policy Client)
    IBMPMSVC                                 (Lenovo Power Manager)          - IBM Power Management (Windows 10)
    ibmpmsvc                                 (Lenovo Power Manager)          - IBM Power Management
    iphlpsvc                                 (
    KeyIso                                   (
    LanmanServer                             (
    LanmanWorkstation                        (
    lfsvc                                    (
    LicenseManager                           (
    lmhosts                                  (
    LSM                                      (
    mpssvc                                   (
    NcbService                               (
    Netman                                   (
    netprofm                                 (Network List Service)          - Network activity icon in tray stops working
    NlaSvc                                   (Network Location Awareness)   
    nsi                                      (Network Store Interface Svs)   - Needed for networking
    PcaSvc                                   (
    PlugPlay                                 (Plug and Play)                 - Need for adding additional hardware/devices
    Power                                    (Power)                         - Manages Power Settings
    ProfSvc                                  (User Profile Service)          - Programs error out when opening as 'Admin'
    PushToInstall                            (
    RasMan                                   (
    RpcEptMapper                             (RPC Endpoint Mapper)           - 
    RpcSs                                    (Remote Procedure Call)         - 
    SamSs                                    (Security Accounts Manager)     - 
    Schedule                                 (Task Scheduler)                - 
    SEMgrSvc                                 (
    SENS                                     (
    SensrSvc                                 (
    servicesAppXSvc                          (
    SgrmBroker                               (
    SSDPSRV                                  (
    SstpSvc                                  (
    StateRepository                          (
    SysMain                                  (
    SystemEventsBroker                       (
    Themes                                   (Themes)                        - Windows Themes Stops
    TimeBrokerSvc                            (
    TokenBroker                              (
    TrkWks                                   (
    UserManager                              (
    UsoSvc                                   (
    VaultSvc                                 (
    Wcmsvc                                   (
    WdiServiceHost                           (
    WinHttpAutoProxySvc                      (
    Winmgmt                                  (Win Man Instrumentation)       - 
    Wlansvc                                  (WLAN AutoConfig)               - Wifi networking stops working (Windows 7)
    WlanSvc                                  (WLAN AutoConfig)               - Wifi networking stops working (Windows 8)
    WPDBusEnum                               (
    WpnService                               (
    wscsvc                                   (
    wudfsvc                                  (Windows Driver Foundation)     - Cannot be stopped
