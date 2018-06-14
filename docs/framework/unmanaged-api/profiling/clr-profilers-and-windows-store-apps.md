---
title: CLR 分析工具和 Windows 市集應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a1ed9b6b613b1e4d3e5363ab9995cc81295091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462282"
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR 分析工具和 Windows 市集應用程式
本主題討論您需要考慮當寫入診斷工具分析的受管理的 Windows 市集應用程式內部執行程式碼。  它也提供指導方針來修改現有的開發工具，讓它們繼續運作，當您執行 Windows 市集應用程式。  若要了解這項資訊，最好是如果您已熟悉通用語言執行階段程式碼剖析 API，您已經使用此應用程式開發介面中執行正確地針對 Windows 桌面應用程式，而且您正在現在想要修改工具的診斷工具若要正確地執行針對 Windows 市集應用程式。  
  
 本主題包含下列章節：  
  
 [簡介](#Intro)  
 [架構和術語](#Arch)  
 [Windows RT 裝置](#RT)  
[使用 Windows 執行階段 Api](#Consuming)  
[載入分析工具 DLL](#Loading)  
 [常見的考量，用於啟動和附加載入](#Common)  
 [啟動負載](#Startup)  
 [附加負載](#Attach)  
[在 Windows 市集應用程式內執行](#Running)  
 [Windows 市集應用程式 Api 部分吧](#APIs)  
 [降低的權限](#Permissions)  
 [處理序間通訊](#Interprocess)  
 [沒有關機通知](#Shutdown)  
[Windows 執行階段中繼資料檔案](#Metadata)  
 [Managed 和 unmanaged Winmd](#WMDs)  
 [WinMD 檔案看起來像 CLR 模組](#CLRModules)  
 [從 Winmd 讀取中繼資料](#Reading)  
 [修改 Winmd 中繼的資料](#Modifying)  
 [解析組件參考的 Winmd](#Resolving)  
[記憶體分析工具](#Profilers)  
 [ForceGC 建立 managed 的執行緒](#ForceGC)  
 [ConditionalWeakTableReferences](#WeakTable)  
[結論](#Conclusion)  
[資源](#Resources)  
  
<a name="Intro"></a>   
## <a name="introduction"></a>簡介  
 如果您已超過介紹段落，您很熟悉 CLR 程式碼剖析 API。  您已寫入一個也針對受管理的桌面應用程式的運作方式的診斷工具。  現在您已經知道要執行的工作，讓您的工具可用於受管理的 Windows 市集應用程式。  可能是您已嘗試進行這項工作，並發現不是簡單的工作。  確實，有許多可能不是所有的工具開發人員很明顯的考量。  例如:   
  
-   嚴重降低權限的內容中，執行 Windows 市集應用程式。  
  
-   Windows 中繼資料檔案有獨特的特性，相較於傳統的受管理模組。  
  
-   Windows 市集應用程式已暫停本身時效能降低的互動性的習慣。  
  
-   處理序間通訊機制基於各種原因，可能無法再運作。  
  
 本主題列出您需要注意的事項，以及如何正確處理它們。  
  
 如果您還不熟悉 CLR 分析 API，跳到本主題結尾處的資源，以尋找更好的簡介資訊。  
  
 提供特定的 Windows 應用程式開發介面和它們的使用方式的詳細資訊也是在本主題的範圍之外。  請考慮本主題的起始點，並參考 MSDN，若要深入了解此處參照任何 Windows Api。  
  
<a name="Arch"></a>   
## <a name="architecture-and-terminology"></a>架構和術語  
 一般而言，一種診斷工具的架構類似下圖所示。 它會使用詞彙 「 程式碼剖析工具 」，但許多這類工具移到一般效能或記憶體剖析成區域，例如程式碼涵蓋範圍，超過模擬物件架構、 偵錯應用程式監視，以及在時間移動。  為了簡單起見，本主題將繼續參考做為程式碼剖析工具的所有這些工具。  
  
 在本主題中，會使用下列詞彙：  
  
 應用程式  
 這是正在分析程式碼剖析工具的應用程式。  一般而言，此應用程式的開發人員正在使用程式碼剖析工具以協助診斷問題的應用程式。  傳統上，此應用程式會是 Windows 桌面應用程式，但在本主題中，我們要尋找在 Windows 市集應用程式。  
  
 分析工具 DLL  
 這是載入的應用程式所分析的處理序空間的元件。  此元件，也稱為程式碼剖析工具 「 代理程式 」 實作[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2，3，等) 的介面，並取用[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2，3，等等) 介面，以收集資料進行分析的應用程式的相關，而且可能會修改應用程式的行為方面。  
  
 分析工具 UI  
 這是程式碼剖析工具使用者互動的桌面應用程式。  它負責顯示給使用者的應用程式狀態，並讓使用者控制分析的應用程式的行為方式。  此元件一律會執行它自己的處理序空間，不同於所分析的應用程式的處理序空間中。  程式碼剖析工具 UI 也可以做為 「 附加觸發程序 」 是處理程序呼叫[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法，讓分析的應用程式載入的程式碼剖析工具 DLL，在這些情況下，分析工具 DLL 不提供支援在啟動時載入。  
  
> [!IMPORTANT]
>  您的程式碼剖析工具 UI 應保持 Windows 桌面應用程式，即使它是用來控制和 Windows 市集應用程式為基礎的報表。  不想要能夠封裝和發行您的診斷工具，Windows 市集中。  您的工具必須執行 Windows 市集應用程式無法執行，且這些事項之內您程式碼剖析工具的 UI 動作。  
  
 整份文件、 範例程式碼範例是假設：  
  
-   您的程式碼剖析工具 DLL 是以 c + + 撰寫，因為它必須進行原生 DLL，根據需求的 CLR 程式碼剖析 API。  
  
-   您的程式碼剖析工具 UI 是以 C# 撰寫。  這並非必要，但因為沒有任何需求，您的程式碼剖析工具 UI 處理程序的語言，為什麼不挑選為既簡明、 又簡單的語言？  
  
<a name="RT"></a>   
### <a name="windows-rt-devices"></a>Windows RT 裝置  
 Windows RT 裝置相當被鎖定。  協力廠商程式碼剖析工具只是無法載入對這類裝置。  本文件著重在 Windows 8 電腦上。  
  
<a name="Consuming"></a>   
## <a name="consuming-windows-runtime-apis"></a>使用 Windows 執行階段 Api  
 在下列各節所述的案例數目，需要消耗一些新的 Windows 執行階段 Api 桌面應用程式程式碼剖析工具的 UI。  您會想要參考的文件以了解哪一個 Windows 執行階段 Api 可從桌面應用程式，以及是否其行為不相同時稱為從桌面應用程式和 Windows 市集應用程式。  
  
 如果您的程式碼剖析工具 UI 以 managed 程式碼撰寫，會有幾個步驟，您必須使取用這些簡單的 Windows 執行階段 Api。  請參閱[受管理的桌面應用程式和 Windows 執行階段](http://go.microsoft.com/fwlink/?LinkID=271858)文件以取得詳細資訊。  
  
<a name="Loading"></a>   
## <a name="loading-the-profiler-dll"></a>載入分析工具 DLL  
 本章節描述您程式碼剖析工具的 UI 會如何導致 Windows 市集應用程式載入您程式碼剖析工具 DLL。  本章節所討論的程式碼所屬的程式碼剖析工具 UI 桌面應用程式，並因此牽涉到使用安全的桌面應用程式，但不一定是安全的 Windows 市集應用程式的 Windows Api。  
  
 您的程式碼剖析工具 UI 可能會造成您的程式碼剖析工具 DLL 來載入到應用程式的處理序空間中兩種方式：  
  
-   在應用程式啟動時，環境變數所控制。  
  
-   藉由附加至應用程式啟動完成之後呼叫[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法。  
  
 啟動載入和附加負載的分析工具 DLL 才能正常運作，Windows 市集應用程式，就會收到您的第一個障礙之一。  兩種形式的載入共用共同的一些特殊考量，讓我們開始使用它們。  
  
<a name="Common"></a>   
### <a name="common-considerations-for-startup-and-attach-loads"></a>常見的考量，用於啟動和附加載入  
 **簽署您的分析工具 DLL**  
 Windows 會嘗試載入您的程式碼剖析工具 DLL，它會確認正確地簽署您的程式碼剖析工具 DLL。  如果沒有，載入失敗的預設值。 執行此作業的方法有兩種：  
  
-   請確定您的程式碼剖析工具 DLL 帶正負號。  
  
-   告訴使用者他們必須安裝開發人員授權其 Windows 8 電腦上才能使用您的工具。  這可以完成自動從 Visual Studio 或以手動方式從命令提示字元。  如需詳細資訊，請參閱[取得開發人員授權](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)。  
  
 **檔案系統權限**  
 Windows 市集應用程式必須有權限來載入及執行您的程式碼剖析工具 DLL 從它所在的檔案系統上的位置。  根據預設，Windows 市集應用程式沒有這種權限用於大部分的目錄，而且任何失敗的嘗試載入您的程式碼剖析工具 DLL 將會產生 Windows 應用程式事件記錄檔，看起來像這樣的項目：  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 一般而言，Windows 市集應用程式只能存取一組有限的磁碟上的位置。  每個 Windows 市集應用程式可以存取它自己的應用程式資料資料夾，以及其他幾個領域在檔案系統中的所有 Windows 市集應用程式會授都與存取權。  最好安裝您的程式碼剖析工具 DLL 和其相依性，Program Files 或 Program Files (x86) 下的某處，因為所有的 Windows 市集應用程式有讀取和執行預設有權限。  
  
<a name="Startup"></a>   
### <a name="startup-load"></a>啟動負載  
 一般而言，在傳統型應用程式，您程式碼剖析工具的 UI 會提示啟動載入您的程式碼剖析工具 DLL 的初始化環境區塊，其中包含所需的 CLR 程式碼剖析 API 環境變數 (亦即， `COR_PROFILER`， `COR_ENABLE_PROFILING`，和`COR_PROFILER_PATH`)，以及與該環境區塊，然後建立新的處理序。  同樣適用於 Windows 市集應用程式，但是不同的機制。  
  
 **不會執行提高權限**  
 如果處理序嘗試繁衍 Windows 市集應用程式處理序 B 處理序的應該在執行中整合性層級，不是在高完整性的層級 （也就，不提高權限）。  這表示可能是您程式碼剖析工具的 UI 應執行中型完整性的層級，或它必須產生其他桌面的處理程序來負責啟動 Windows 市集應用程式中整合性層級。  
  
 **選擇 Windows 市集應用程式設定檔**  
 首先，您會想詢問您的程式碼剖析工具使用者啟動的 Windows 市集應用程式。  針對桌面應用程式，可能是您將會顯示檔案瀏覽對話方塊，和使用者會尋找並選取.exe 檔案。  但 Windows 市集應用程式不同，而且使用瀏覽對話方塊沒有意義。  相反地，最好讓使用者安裝該使用者即可從選取的 Windows 市集應用程式的清單。  
  
 您可以使用[PackageManager 類別](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx)產生這份清單。  `PackageManager` 是一個 Windows 執行階段類別，供桌面應用程式，而且事實上*只*供桌面應用程式。  
  
 下列 beethoven 的 ode 範例從撰寫為 yses C# 中的傳統型應用程式的假設分析工具 UI`PackageManager`來產生 Windows 應用程式清單：  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **指定自訂的環境區塊**  
 新的 COM 介面， [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)，可讓您自訂的 Windows 市集應用程式，若要簡化某些形式的診斷的執行行為。  其中一個方法， [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx)，可讓您將 Windows 市集應用程式的環境區塊啟動時，以及其他有用的效果類似停用自動偵測程序暫止。  環境區塊相當重要，因為這是您要指定環境變數 (`COR_PROFILER`， `COR_ENABLE_PROFILING`，和`COR_PROFILER_PATH)`) 由 CLR 載入分析工具 DLL。  
  
 請考慮下列程式碼片段：  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 有一些您需要取得正確的項目：  
  
-   `packageFullName` 反覆查看封裝及抓取時，您可以判斷`package.Id.FullName`。  
  
-   `debuggerCommandLine` 是一個位元更有趣。  若要將自訂的環境區塊傳遞至 Windows 市集應用程式，您需要撰寫您自己，最簡單的 dummy 偵錯工具。  Windows 會產生 Windows 市集應用程式暫停，而且然後再透過啟動您的偵錯工具，以在此範例中類似的命令列附加偵錯工具：  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     其中`-p 1336`表示 Windows 市集應用程式處理序識別碼 1336，和`-tid 1424`表示執行緒識別碼 1424年是暫止的執行緒。  您 dummy 偵錯工具會剖析從命令列的 ThreadID，繼續執行該執行緒，，然後結束。  
  
     以下是一些範例來執行這項操作的 c + + 程式碼 （請務必加入錯誤檢查） ！:  
  
    ```cpp  
    int wmain(int argc, wchar_t* argv[])  
    {      
        // …  
        // Parse command line here  
        // …  
  
        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,   
                                                                  FALSE /* bInheritHandle */, nThreadID);  
        ResumeThread(hThread);  
        CloseHandle(hThread);  
        return 0;  
    }  
    ```  
  
     您要部署此虛擬偵錯工具做為您的診斷工具安裝的一部分，然後指定 在這個偵錯工具的路徑`debuggerCommandLine`參數。  
  
 **啟動 Windows 市集應用程式**  
 最後到達的時間來啟動 Windows 市集應用程式。 如果您已經已經嘗試自行執行，您可能已注意到， [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425\(v=vs.85\).aspx)是不在您建立 Windows 市集應用程式程序方法。  相反地，您將需要使用[IApplicationActivationManager::ActivateApplication](https://msdn.microsoft.com/library/windows/desktop/Hh706903\(v=vs.85\).aspx)方法。  若要這樣做，請您將需要取得應用程式使用者模型識別碼，您要啟動的 Windows 市集應用程式。  這表示您將必須進行一些調查，透過在資訊清單。  
  
 反覆查看您的封裝時 (請參閱中的 「 選擇 Windows 市集應用程式來設定檔 」[啟動負載](#Startup)區段之前)，您會想要擷取的最新的套件資訊清單中包含的應用程式集：  
  
```csharp  
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";  
  
AppxPackaging.IStream manifestStream;  
SHCreateStreamOnFileEx(  
                    manifestPath,  
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE  
                    0,              // file creation attributes  
                    false,          // fCreate  
                    null,           // reserved  
                    out manifestStream);  
  
IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);  
  
IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();  
```  
  
 是，一個封裝可以有多個應用程式，且每個應用程式有自己的應用程式使用者模型識別碼。  因此，您會想詢問您的使用者設定檔，哪一個應用程式，和擷取應用程式使用者模型識別碼，從該特定應用程式：  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
…  
```  
  
 最後，您現在有您需要啟動 Windows 市集應用程式：  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **請記得要呼叫 DisableDebugging**  
 當您呼叫[IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)，您所做的承諾，您會清除之後自行呼叫[IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)方法，因此請務必執行可透過程式碼剖析工作階段時。  
  
<a name="Attach"></a>   
### <a name="attach-load"></a>附加負載  
 當您的程式碼剖析工具 UI 想要附加的程式碼剖析工具 DLL 已經開始執行的應用程式時，它會使用[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)。  同樣使用 Windows 市集應用程式。  但除了稍早所列的一般考量，請確定目標的 Windows 市集應用程式不會暫停。  
  
 **EnableDebugging**  
 如同啟動負載呼叫[IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)方法。  您不需要它將傳遞的環境區塊，但您需要的其他功能的其中一個： 停用自動偵測程序暫止。  否則，當您的程式碼剖析工具 UI 呼叫[AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)，目標的 Windows 市集應用程式可能暫止。  事實上，如果這是可能在使用者現在互動與您的程式碼剖析工具 UI 和 Windows 市集應用程式不在作用中的任何使用者的螢幕上。  如果 Windows 市集應用程式暫止，它將無法回應任何發出信號給 CLR 傳送給它來附加您的程式碼剖析工具 DLL。  
  
 因此，您會想要這麼做：  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 這是啟動負載案例中，但您未指定偵錯工具命令列或環境區塊會使相同的呼叫。  
  
 **DisableDebugging**  
 一如往常，別忘了呼叫[IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)完成您的程式碼剖析工作階段。  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>在 Windows 市集應用程式內執行  
 因此 Windows 市集應用程式最後已載入您的程式碼剖析工具 DLL。  現在您的程式碼剖析工具 DLL 必須教導如何透過 Windows 市集應用程式所需的不同規則播放，包括其中所允許的應用程式開發介面，以及如何執行與較小權限。  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Windows 市集應用程式 Api 部分吧  
 當您瀏覽 Windows 應用程式開發介面，您會發現每個應用程式開發介面已記錄為適用於桌面應用程式、 Windows 市集應用程式，或兩者。  例如，**需求**> 一節的文件[InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx)函式表示的函式適用於桌面應用程式。 相反地， [InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx)函式是適用於桌面應用程式和 Windows 市集應用程式。  
  
 在開發您的程式碼剖析工具 DLL 時，將它視為是 Windows 市集應用程式，而且只會使用 Api 所記載為可供 Windows 市集應用程式。  分析程式相依性 (例如，您可以執行`link /dump /imports`針對您要稽核的程式碼剖析工具 DLL)，然後搜尋以查看哪些程式相依性為 [確定]，而且這不是文件。  在大部分情況下，您的違規，即可修正只將其取代為較新的表單，記載成安全的 api (例如，取代[InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx)與[InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx))。  
  
 您可能會發現您的程式碼剖析工具 DLL 會呼叫桌面應用程式僅適用於某些應用程式開發介面，而且尚未似乎工作即使當您的程式碼剖析工具 DLL 載入 Windows 市集應用程式內。  請注意，是非常危險的使用未記載您的程式碼剖析工具 DLL 時載入至 Windows 市集應用程式處理序中的 Windows 市集應用程式搭配使用任何 API:  
  
-   這類應用程式開發介面不保證唯一的內容中執行 Windows 市集應用程式中呼叫時使用。  
  
-   不同的 Windows 市集應用程式處理序中呼叫時，這類應用程式開發介面可能無法一致地運作。  
  
-   這類應用程式開發介面可能會從目前版本的 Windows，Windows 市集應用程式可以正常運作，但可能會中斷或停用未來的 Windows 版本中。  
  
 最佳的建議是修正您所有的違規，並避免風險。  
  
 您可能會發現您絕對不能沒有特定的應用程式開發介面和找不到取代適用於 Windows 市集應用程式。  在此情況下，最小值：  
  
-   測試、 測試、 測試即時 daylights 超出該 API 的使用方式。  
  
-   了解 API 可能會突然中斷，或如果呼叫會消失從在 Windows 市集應用程式在未來的版本的 Windows。  這不會被視為是相容性問題的 Microsoft 和支援您的使用方式，它將不會優先。  
  
<a name="Permissions"></a>   
### <a name="reduced-permissions"></a>降低的權限  
 它已超出本主題列出 Windows 市集應用程式權限不同的桌面應用程式的所有方法的範圍。  但是一定每次您的程式碼剖析工具 DLL （載入相較於桌面應用程式的 Windows 市集應用程式） 時嘗試存取的任何資源的行為會是不同。  檔案系統是最常見的範例。  有幾個會放在指定的 Windows 市集應用程式可以存取的磁碟上 (請參閱[檔案存取和權限 (Windows 執行階段應用程式](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx))，而且您的程式碼剖析工具 DLL 會在相同的限制下。  徹底測試您的程式碼。  
  
<a name="Interprocess"></a>   
### <a name="inter-process-communication"></a>處理序間通訊  
 這份文件的開頭圖表所示，您的程式碼剖析工具 DLL （載入至 Windows 市集應用程式處理序空間中） 可能需要與您程式碼剖析工具的 UI （執行個別的傳統型應用程式處理序空間中） 執行您自己自訂的間程序進行通訊通訊 (IPC) 通道。  程式碼剖析工具 UI 將訊號傳送至程式碼剖析工具 DLL，以修改其行為，並分析工具 DLL 從分析 Windows 市集應用程式傳送資料至後續處理及顯示給使用者程式碼剖析工具分析工具 UI。  
  
 大部分的程式碼剖析工具需要這種方式，但您的程式碼剖析工具 DLL 載入至 Windows 市集應用程式時，您 IPC 機制的選擇會更多限制。  例如，具名的管道不屬於 Windows 市集應用程式 SDK，所以您無法使用它們。  
  
 但當然，檔案仍在雖然更多限制的方式。  事件也會提供。  
  
 **透過檔案進行通訊**  
 大部分的資料可能會經由檔案傳遞之間的程式碼剖析工具 DLL 和程式碼剖析工具的 UI。  索引鍵是挑選檔案位置中您的程式碼剖析工具 DLL （在 Windows 市集應用程式的內容） 和 UI 程式碼剖析工具具有讀取和寫入權限。  比方說，暫存資料夾路徑的位置，可以存取您的程式碼剖析工具 DLL 和程式碼剖析工具 UI，但沒有其他 Windows 市集應用程式封裝可以存取 （因此防護您記錄從其他 Windows 市集應用程式套件的任何資訊）。  
  
 您的程式碼剖析工具 UI 和程式碼剖析工具 DLL 可以判斷此路徑獨立。  您的程式碼剖析工具 UI，它會逐一為目前的使用者安裝的所有套件時 （請參閱稍早的範例程式碼），取得存取權`PackageId`類別，可以與這個程式碼片段類似的程式碼衍生來源的暫存資料夾路徑。  （如往常，請檢查錯誤省略為求簡單明瞭。）  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 同時，您的程式碼剖析工具 DLL 可以執行基本上相同的動作，但它可以更輕鬆地[ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx)類別使用[ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx)屬性。  
  
 **透過事件來通訊**  
 如果您希望您的程式碼剖析工具的 UI 與程式碼剖析工具 DLL 之間的簡單信號語意，您可以使用 Windows 市集應用程式，以及桌面應用程式內的事件。  
  
 從您的程式碼剖析工具 DLL，您可以直接呼叫[CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx)函式來建立具名的事件與任何您喜歡的名稱。  例如:   
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 您的程式碼剖析工具 UI 就必須找出 Windows 市集應用程式的命名空間之下的具名的事件。  例如，無法呼叫您的程式碼剖析工具 UI [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx)，指定相同的事件名稱。  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>` 為 Windows 市集應用程式的 AppContainer SID。  本主題的前一節示範了如何逐一查看目前的使用者安裝的套件。  從該範例程式碼中，您可以取得套件識別碼。  從 packageId，您可以取得`<acSid>`與下列類似的程式碼：  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
<a name="Shutdown"></a>   
### <a name="no-shutdown-notifications"></a>沒有關機通知  
 當執行 Windows 市集應用程式內，您的程式碼剖析工具 DLL 不應該依賴可能[icorprofilercallback:: Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)或甚至[DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583\(v=vs.85\).aspx) (與`DLL_PROCESS_DETACH`) 正在呼叫以通知您的程式碼剖析工具 DLL確認 Windows 市集應用程式即將結束。  事實上，您應該預期會永遠不會呼叫它們。  在過去，許多程式碼剖析工具 Dll 已經使用這些通知做為方便的位置來排清的快取到磁碟、 關閉檔案、 傳送通知回程式碼剖析工具 UI 等等。但現在需要稍有不同組織您的程式碼剖析工具 DLL。  
  
 因為它會分析工具 DLL 應該記錄資訊。  基於效能考量，您可能要批次在記憶體中的資訊和排清至磁碟隨著批次成長的大小超過某些臨界值。  但假設可能會遺失任何尚未排清至磁碟的資訊。  這表示您會想要挑選的臨界值，而且您的程式碼剖析工具 UI 需要強行寫入的程式碼剖析工具 dll 的資訊不完整處理。  
  
<a name="Metadata"></a>   
## <a name="windows-runtime-metadata-files"></a>Windows 執行階段中繼資料檔案  
 它超出範圍為詳細資料會進入此文件的檔案是在 Windows 執行階段中繼資料 (WinMD)。    本節僅限於 WinMD 檔案載入您的程式碼剖析工具 DLL 正在分析 Windows 市集應用程式時，CLR 分析 API 的回應方式。  
  
<a name="WMDs"></a>   
### <a name="managed-and-non-managed-winmds"></a>Managed 和 unmanaged Winmd  
 如果開發人員使用 Visual Studio 來建立新的 Windows 執行階段元件專案，該專案的組建會產生 WinMD 檔案，其中描述開發人員撰寫的中繼資料 （類型描述的類別、 介面、 等等）。  如果這個專案是以 C# 或 VB 撰寫的 managed 的語言專案，該相同的 WinMD 檔案也會包含這些型別 （其中包含所有從開發人員的程式碼編譯的 IL 表示） 的實作。  這類檔案稱為受管理的 WinMD 檔案。  它們有興趣，因為它們包含 Windows 執行階段中繼資料和基礎的實作。  
  
 相反地，如果開發人員針對 c + + 建立 Windows 執行階段元件專案，該專案的組建產生的 WinMD 檔案只包含中繼資料，並實作會先編譯成個別的原生 DLL。  同樣地，WinMD 檔案隨附於 Windows SDK 包含只有中繼資料，與實作編譯成個別的 Windows 隨附的原生 Dll。  
  
 以下資訊適用於這兩個受管理的 Winmd，其中包含中繼資料和實作，以及未受管理的 Winmd，包含只有中繼資料。  
  
<a name="CLRModules"></a>   
### <a name="winmd-files-look-like-clr-modules"></a>WinMD 檔案看起來像 CLR 模組  
 就 CLR 而言，所有的 WinMD 檔案都是模組。  當 WinMD 檔案載入您程式碼剖析工具 DLL 和其 ModuleIDs 為何，在其他受管理的模組一樣，因此會告知 CLR 程式碼剖析 API。  
  
 您的程式碼剖析工具 DLL 可以藉由呼叫從其他模組中區分 WinMD 檔案[icorprofilerinfo3:: Getmoduleinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)方法，並檢查`pdwModuleFlags`輸出參數[COR_PRF_MODULE_WINDOWS_執行階段](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)旗標。  （它是設定如果且只有 ModuleID 代表 WinMD）。  
  
<a name="Reading"></a>   
### <a name="reading-metadata-from-winmds"></a>從 Winmd 讀取中繼資料  
 WinMD 檔案，例如一般模組，包含中繼資料，可透過讀取[中繼資料 Api](../../../../docs/framework/unmanaged-api/metadata/index.md)。  但是，CLR Windows 執行階段將類型對應至.NET Framework 型別讀取的 WinMD 檔案，以便開發人員程式在 managed 程式碼和使用的 WinMD 檔案可以有更自然的程式設計體驗時。  如需這些對應的一些範例，請參閱[.NET Framework 支援的 Windows 市集應用程式和 Windows 執行階段](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。  
  
 因此哪些檢視您的分析工具會使用中繼資料 Api 時： 未經處理的 Windows 執行階段檢視或對應的.NET Framework 檢視？  回答： 它由您。  
  
 當您呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)方法來取得中繼資料介面，例如 WinMD [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)，您可以選擇設定[ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)中`dwOpenFlags`參數來關閉這項對應。  否則，預設會啟用對應。  一般而言，分析工具會保持啟用，對應，讓熟悉且自然的程式碼剖析工具使用者，會尋找程式碼剖析工具 DLL 會從 WinMD 中繼資料 （例如，類型的名稱） 中取得的字串。  
  
<a name="Modifying"></a>   
### <a name="modifying-metadata-from-winmds"></a>修改 Winmd 中繼的資料  
 不支援修改 Winmd 中繼資料。  如果您呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)方法 WinMD 檔案，並指定[ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)中`dwOpenFlags`參數或例如尋求可寫入的中繼資料介面[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)， [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)將會失敗。  這是要 IL 重寫的分析，需要修改中繼資料，以支援其檢測 （例如，若要新增 AssemblyRefs 或新的方法） 特別重要。  因此您應該檢查[COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)第一次 （如前一節所述），避免在這類模組要求可寫入的中繼資料介面。  
  
<a name="Resolving"></a>   
### <a name="resolving-assembly-references-with-winmds"></a>解析組件參考的 Winmd  
 許多程式碼剖析工具需要解析中繼資料參考，以手動方式，以利檢測或型別檢查。  這類程式碼剖析工具，就需要留意的 CLR 如何解析指向 Winmd 的組件參考，因為這些參考會解析完全不同的方式，比標準的組件參考。  
  
<a name="Profilers"></a>   
## <a name="memory-profilers"></a>記憶體分析工具  
 記憶體回收行程和 managed 的堆積不本質上不同的 Windows 市集應用程式和桌面應用程式中。  不過，有需要注意的分析工具作者有些微的差異。  
  
<a name="ForceGC"></a>   
### <a name="forcegc-creates-a-managed-thread"></a>ForceGC 建立 managed 的執行緒  
 在執行記憶體剖析時，您的程式碼剖析工具 DLL 通常會建立不同的執行緒用來呼叫[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)方法。  這是新的執行任何動作。  但可能意外進行記憶體回收，Windows 市集應用程式內的動作，可能會轉換成 managed 執行緒的執行緒 （例如，程式碼剖析 API ThreadID 會建立該執行緒）。  
  
 若要了解的結果，請務必了解同步和非同步呼叫之間的差異，如 CLR 分析 API 所定義。 請注意，這非常不同的 Windows 市集應用程式中的非同步呼叫的概念。  請參閱部落格文章[為什麼我們有 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/)如需詳細資訊。  
  
 相關的重點是，在您的分析工具所建立的執行緒上呼叫一律視為同步的即使這些呼叫會從您的程式碼剖析工具 DLL 的其中一個實作外進行[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)方法。  用於在至少，會發生這個情況。  現在，CLR 已轉換成 managed 執行緒分析工具的執行緒因為呼叫[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)，執行緒就不再視為分析工具的執行緒。  在這種情況，CLR 會強制執行更嚴格定義的項目會限定為該執行緒同步 — 也就是呼叫必須源自內的程式碼剖析工具 DLL 的其中一個[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)限定為同步的方法。  
  
 這代表實際上什麼？  大部分[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)方法僅提供安全同步，呼叫，否則將會立即失敗。  因此，如果您的程式碼剖析工具 DLL 會重複使用您[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)通常在分析工具建立的執行緒上進行其他呼叫的執行緒 (例如，若要[RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)， [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)，或[RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md))，您將有問題。  即使這類非同步安全函式[DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)已從 managed 執行緒呼叫時的特殊規則。 (請參閱部落格文章[分析工具堆疊查核行程： 基本概念和超越](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/)如需詳細資訊。)  
  
 因此，我們建議您的程式碼剖析工具 DLL 會呼叫建立任何執行緒[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)應該使用*只*為了觸發 Gc，然後回應 GC 回呼。  它不應該呼叫程式碼剖析 API 來執行其他工作，例如堆疊取樣或卸離。  
  
<a name="WeakTable"></a>   
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences  
 從.NET Framework 4.5 開始，沒有新的 GC 回呼， [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)，程式碼剖析工具更完整資訊的可提供*相依控制代碼*。 這些控制代碼有效地會加入從來源物件的參考到目標物件進行 GC 存留期管理。  相依控制代碼就是新的、 和開發人員以 managed 程式碼程式已能夠建立自己的相依控制代碼使用<xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType>即使在 Windows 8 和.NET Framework 4.5 之前的類別。  
  
 不過，受管理的 XAML Windows 市集應用程式現在會大量使用相依的控制代碼。  特別是，CLR 會使用它們以利管理受管理的物件及未受管理的 Windows 執行階段物件之間的參考循環。  這表示它是更重要現在比以往記憶體分析工具，了解這些相依的控制代碼，以便在堆積圖表邊緣的其餘部分一起進行視覺化。  應該使用您的程式碼剖析工具 DLL [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)， [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)，和[ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)一起以形成完整的堆積圖表檢視.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>結論  
 您可使用 CLR 分析 API 來分析 Windows 市集應用程式內執行的 managed 程式碼。  事實上，您可以使用現有的分析工具，其中您要開發並進行一些特定的變更，讓它可以針對 Windows 市集應用程式。   您的程式碼剖析工具 UI 應該使用新的應用程式開發介面啟用 Windows 市集應用程式中偵錯模式。  請確定您的程式碼剖析工具 DLL 會消耗只適用於 Windows 市集應用程式 Api。  Windows 市集應用程式的應用程式開發介面限制，請注意與得知有適用於 Windows 市集應用程式限制的使用權限的情況下，應該要撰寫您的程式碼剖析工具 DLL 和程式碼剖析工具 UI 之間的溝通機制。  您的程式碼剖析工具 DLL 應該了解如何在 CLR 處理 Winmd 和記憶體回收行程的行為的不同相對於 managed 執行緒的方式。  
  
<a name="Resources"></a>   
## <a name="resources"></a>資源  
 **Common Language Runtime**  
 -   [CLR 程式碼剖析 API 參考](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [CLR 中繼資料 API 參考](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Windows 執行階段的 CLR 的互動**  
 [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Windows 市集應用程式**  
 -   [檔案存取和權限 （Windows 執行階段應用程式](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [取得開發人員授權](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [IPackageDebugSettings 介面](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>另請參閱  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
