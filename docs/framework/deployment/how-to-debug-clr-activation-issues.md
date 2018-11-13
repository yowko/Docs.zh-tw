---
title: 如何：偵錯 CLR 啟用問題
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89724e9a322f2f28dbe5d18ae697acbdd0a32d8e
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744466"
---
# <a name="how-to-debug-clr-activation-issues"></a>如何：偵錯 CLR 啟用問題
如果以正確的通用語言執行平台 (CLR) 版本執行應用程式時發生問題，您可以檢視並偵錯 CLR 啟用記錄。 當您的應用程式載入不符預期的 CLR 版本，或完全不載入 CLR 時，這些記錄檔對判斷啟動問題的根本原因非常有幫助。 [NET Framework 初始化錯誤：管理使用者經驗](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) 會討論應用程式找不到任何 CLR 時的經驗。  
  
 使用 HKEY_LOCAL_MACHINE 登錄機碼或系統環境變數可以啟用全系統的 CLR 啟動記錄。 登錄項目或環境變數移除之前會一直產生記錄檔。 或者，您可以使用使用者或處理序本機環境變數，啟用不同範圍和持續時間的記錄。  
  
 CLR 啟動記錄檔不應該與[assembly binding logs組件繫結記錄檔](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)相混淆，兩者截然不同。  
  
## <a name="to-enable-clr-activation-logging"></a>啟用 CLR 啟動記錄  
  
#### <a name="using-the-registry"></a>使用登錄  
  
1.  在登錄編輯器中瀏覽至 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (32 位元電腦) 或 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 資料夾 (64 位元電腦)。  
  
2.  新增名為 `CLRLoadLogDir` 的字串值，將它設為現有目錄的完整路徑，這是您要儲存 CLR 啟動記錄的目錄。  
  
 啟動記錄會一直保持啟用，直到您移除字串值為止。  
  
#### <a name="using-an-environment-variable"></a>使用環境變數  
  
-   將 `COMPLUS_CLRLoadLogDir` 環境變數設為字串，代表現有目錄的完整路徑，這是您要儲存 CLR 啟動記錄的目錄。  
  
     環境變數的設定方式會決定其範圍︰  
  
    -   如果設定在系統層級，就會為該電腦上的所有 .NET Framework 應用程式啟用啟動記錄，直到移除環境變數為止。  
  
    -   如果設定在使用者層級，就只為目前的使用者帳戶啟用啟動記錄。 環境變數移除之前，會一直記錄。  
  
    -   如果載入 CLR 之前，從處理序中設定它，就會啟用啟動記錄直到處理序終止為止。  
  
    -   如果執行應用程式之前，在命令提示字元中設定它，就會啟用從該命令提示字元執行的所有應用程式的啟動記錄。  
  
     例如，您要先啟動記錄儲存在處理序層級範圍的 c:\clrloadlogs 目錄中，開啟 [命令提示字元] 視窗並鍵入下列命令，才能執行應用程式︰  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a>範例  
 CLR 啟動記錄檔會提供大量有關 CLR 啟動的資料和裝載 API 的 CLR 用法。 此資料大部分是由 Microsoft 內部使用，但某些部分也對開發人員很有用，如本文所述。  
  
 記錄會反映裝載 API 之 CLR 的呼叫順序。 它也包含電腦上偵測到有關已安裝執行階段組的有用資料。 CLR 啟動記錄格式不是其本身的記錄，但可用來協助需要解決 CLR 啟動問題的開發人員。  
  
> [!NOTE]
>  您無法開啟啟動記錄，直到使用 CLR 的處理序終止為止。  
  
> [!NOTE]
>  CLR 啟動記錄不會當地語系化，一律以英文產生。  
  
 在下例的啟動記錄中，最有用的資訊會在記錄後反白顯示及描述。  
  
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
  
-   **CLR 載入記錄**提供可執行檔路徑，啟動載入 Managed 程式碼的處理序。 請注意，這可能是原生的主機。  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   **已安裝的執行階段**是安裝在電腦上用來啟動要求的一組備選 CLR 版本。  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   **以版本建置**是建置二進位檔所用的 CLR 版本，二進位檔會提供給類似 [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) 的方法。  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   **功能隨選安裝**指的是在 Windows 8 上啟用 .NET Framework 3.5。 如需此案例的詳細資訊，請參閱 [.NET Framework 初始化錯誤：管理使用者經驗](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)。  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a>請參閱  
- [部署](../../../docs/framework/deployment/index.md)  
- [操作說明：設定應用程式以支援 .NET Framework 4 或 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
