---
title: "如何：偵錯 CLR 啟用問題 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CLR 啟動, 問題偵錯"
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：偵錯 CLR 啟用問題
如果您在以 Common Language Runtime \(CLR\) 的正確版本取得應用程式的時候遇到問題，您可以檢視並偵錯 CLR 啟動記錄檔。  。當決定啟動問題的根本原因時，這些記錄檔可能會非常有用。例如當應用程式所載入不同的 CLR 版本或根本時無法載入 CLR。  ，當 CLR 不會為應用程式時， [.NET Framework 初始化錯誤：管理使用者經驗](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) 會討論這些經驗。  
  
 您可以使用 HKEY\_LOCAL\_MACHINE 登錄機碼或系統環境變數， CLR 就會記錄可啟用整個系統。  記錄檔將會產生直到登錄項目或移除環境變數。  或者，您也可以使用使用者或處理序的環境變數以啟用具有不同的範圍和持續期間的記錄。  
  
 CLR 不應與 [組件繫結記錄檔](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)混淆啟動記錄檔，這兩者是完全不同的。  
  
## 啟用 CLR 啟動記錄  
  
#### 使用登錄  
  
1.  在 \[登錄編輯程式\]，巡覽至 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\.NETFramework \(on a 32\-bit computer\) or HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework 資料夾 \(在 64 位元電腦上\)。  
  
2.  將字串值 \(名稱為 `CLRLoadLogDir`，並將它設定為您想要儲存 CLR 啟動記錄檔現有目錄的完整路徑。  
  
 啟動啟用記錄會保持為，直到移除字串值。  
  
#### 使用環境變數  
  
-   設定 `COMPLUS_CLRLoadLogDir` 環境變數成字串來表示將用來儲存 CLR 啟動記錄檔的現有的完整目錄路徑。  
  
     如何設定環境變數來決定其範圍:  
  
    -   如果您在系統層級中啟動，在該電腦上的所有 .NET Framework 應用程式的記錄都是可查詢的，直到移除環境變數。  
  
    -   您在使用者層級，啟動記錄為目前使用者帳戶才有效。  記錄會持續進行，直到移除環境變數。  
  
    -   您將它在處理序中載入 CLR 之前，啟動記錄都是有效的，直到處理序結束。  
  
    -   假如您在在執行應用程式之前，在命令提示字元中啟動記錄，其記錄可被所有應用程式中使用。  
  
     例如，儲存啟動登入這個 c: ，在執行應用程式之前， \\clrloadlogs directory with process\-level scope， open a Command Prompt 視窗並輸入下列內容:  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## 範例  
 CLR 啟動記錄檔會記錄有關 CLR 啟動和使用的大量資料 CLR 裝載 API。  Microsoft 內部使用大部分這項資料，不過，某些資料也十分有用的開發人員，如本文所述。  
  
 這個記錄會反映 CLR 裝載 API 的呼叫順序。  它也包含了在電腦上偵測到的一組的資訊所安裝的執行階段。  CLR 啟動日誌格式本身沒有提供，，但是可以使用說明需要解決 CLR 啟動問題的開發人員。  
  
> [!NOTE]
>  您無法開啟直到使用 CLR 終止處理序的本機啟動記錄檔。  
  
> [!NOTE]
>  CLR 啟動記錄檔並未當地語系化，它們永遠會以英文版被產生。  
  
 在啟動記錄檔的下列範例中，有用的資訊在記錄檔之後被重點提示並加以說明。  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
  
```  
  
-   **CLR 載入記錄檔** 提供路徑指定要啟動的可執行檔載入 Managed 程式碼的處理序。  請注意這可能是原生主機。  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
  
    ```  
  
-   **所安裝的執行階段** 是電腦上安裝的 CLR 版本，並等候啟動的要求。  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
  
    ```  
  
-   **以版本建置** 是用來建置二進位檔的方法 [ICLRMetaHostPolicy::GetRequestedRuntime](../Topic/ICLRMetaHostPolicy::GetRequestedRuntime%20Method.md)的 CLR 版本。  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
  
    ```  
  
-   **安功能需求裝** 參考啟用 Windows 8. 的 .NET Framework 3.5。  詳細資訊請見 [.NET Framework 初始化錯誤：管理使用者經驗](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) 。  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
  
    ```  
  
## 請參閱  
 [部署](../../../docs/framework/deployment/net-framework-and-applications.md)   
 [HOW TO：設定應用程式以支援 .NET Framework 4 或 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)