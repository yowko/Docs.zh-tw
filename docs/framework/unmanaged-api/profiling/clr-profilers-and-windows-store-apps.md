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
ms.openlocfilehash: f1747d99fbfbc31fb592aee570d10d574b8480b0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558219"
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR 分析工具和 Windows 市集應用程式

本主題討論您需要思考寫入分析的診斷工具管理的 Windows 市集應用程式內執行的程式碼時。  它也會提供指導方針來修改現有的開發工具，讓它們繼續運作，當您執行 Windows 市集應用程式。  若要了解這項資訊，最好是如果您已熟悉使用通用語言執行階段設定檔 API，您已經使用此 API 中正確地針對 Windows 桌面應用程式，而且您的執行現在想要在修改工具的診斷工具若要針對 Windows 市集應用程式正確執行。  
  
## <a name="introduction"></a>簡介

 如果您進行過簡介段落，然後您熟悉 CLR Profiling API。  您已撰寫也針對受管理的桌面應用程式的運作方式的一種診斷工具。  現在您想知道該如何使您的工具可與受管理的 Windows 市集應用程式。  或許您已經嘗試進行這項工作，並發現不是簡單的工作。  事實上，有許多可能不明顯所有的工具開發人員的考量。  例如:   
  
-   嚴重降低權限的內容中，執行 Windows 市集應用程式。  
  
-   Windows 中繼資料檔案具有獨特的特性，相較於傳統的受管理模組。  
  
-   Windows 市集應用程式已習慣在暫止自行關閉而發生的互動性。  
  
-   基於各種原因，可能無法再運作您的處理序間通訊機制。  
  
 本主題列出您要注意的事項，以及如何正確處理它們。  
  
 如果您熟悉 CLR 設定檔 API，直接跳到本主題結尾處的資源，以尋找更好的入門資訊。  
  
 提供關於特定 Windows Api 和它們的使用方式的詳細資料也已超出本主題的範圍。  請考慮本主題的起點，並參考 MSDN，若要深入了解此處參考的任何 Windows Api。  
  
## <a name="architecture-and-terminology"></a>架構和術語

 一般而言，一種診斷工具的架構，在下圖所示。 它會使用詞彙 「 程式碼剖析工具 」，但是許多這類工具遠超過一般的效能或記憶體剖析成區域，例如程式碼涵蓋範圍，模擬物件架構、 時間移動的偵錯、 監視、 等等的應用程式。  為了簡單起見，本主題將繼續參考程式碼剖析工具為所有這些工具。  
  
 在本主題中使用下列術語：  
  
**應用程式**

這是分析工具分析應用程式。  一般而言，此應用程式的開發人員正在使用的程式碼剖析工具以協助診斷應用程式的問題。  傳統上，此應用程式是 Windows 桌面應用程式，但在本主題中，我們將探討 Windows 市集應用程式。  
  
**Profiler DLL**

這是載入應用程式會被分析的處理序空間的元件。  此元件，也就是程式碼剖析工具 「 代理程式 」 會實作[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2，3，等等) 介面，並取用[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2，3，等等) 介面來收集有關分析的應用程式，以及可能的資料修改的應用程式的行為層面。  
  
**Profiler UI**

這是程式碼剖析工具的使用者互動的桌面應用程式。  它負責向使用者顯示應用程式狀態，並提供使用者的方式來控制分析的應用程式的行為。  此外，此元件一律會在它自己的處理序空間，與正在分析之應用程式的處理序空間分開執行。  Profiler UI 也可以做為連結觸發程序 」 處理程序，呼叫[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法，讓分析的應用程式，以載入 Profiler DLL 在這些情況下，分析工具 DLL 不提供支援在啟動時載入。  
  
> [!IMPORTANT]
> Profiler UI 應保持 Windows 桌面應用程式，即使它是用來控制和報告上的 Windows 市集應用程式。  未預期要能夠封裝並寄送您的診斷工具，在 Windows 市集中。  您的工具必須執行 Windows 市集應用程式無法執行，且許多這些項目之內 Profiler UI 動作。  
  
 整份文件、 範例程式碼會假設：  
  
- Profiler DLL 是以 c + + 撰寫的因為它必須是原生 DLL，根據 CLR Profiling API 的需求。  
  
- Profiler UI 是以 C# 撰寫的。  這並非必要，但因為沒有任何需求 Profiler UI 的程序的語言，為什麼不選擇精簡、 簡單的語言？  
  
### <a name="windows-rt-devices"></a>Windows RT 裝置

Windows RT 裝置相當已鎖定。  協力廠商程式碼剖析工具只是無法載入這類裝置。  本文件著重在 Windows 8 電腦上。  
  
## <a name="consuming-windows-runtime-apis"></a>使用 Windows 執行階段 Api

 在下列各節所述的案例數目，Profiler UI 桌面應用程式需要使用一些新的 Windows 執行階段 Api。  您會想要參考的文件以了解哪些 Windows 執行階段 Api 可從桌面應用程式，以及其行為是否不同時稱為從桌面應用程式和 Windows 市集應用程式。  
  
 如果您的 Profiler UI 以 managed 程式碼撰寫，會有幾個步驟，您需要如何讓您使用這些簡單的 Windows 執行階段 Api。  請參閱[受管理的傳統型應用程式和 Windows 執行階段](https://go.microsoft.com/fwlink/?LinkID=271858)文件，如需詳細資訊。  
  
## <a name="loading-the-profiler-dll"></a>正在載入 Profiler DLL

 本章節描述如何 Profiler UI 會導致 Windows 市集應用程式載入 Profiler DLL。  本章節所討論的程式碼位於您 Profiler UI 的桌面應用程式，並因此牽涉到使用安全的桌面應用程式，但不一定是安全的 Windows 市集應用程式的 Windows Api。  
  
 Profiler UI 可能會造成您 Profiler DLL 載入至應用程式的處理序空間有兩種：  
  
-   在應用程式啟動時，環境變數來控制。  
  
-   藉由附加至應用程式，啟動完成之後呼叫[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法。  
  
 啟動載入和附加負載的 Profiler DLL 才能正常運作，使用 Windows 市集應用程式，將會出現您的第一個障礙之一。  這兩種形式的載入共用共同的一些特殊考量，我們現在就開始使用它們。  
  
### <a name="common-considerations-for-startup-and-attach-loads"></a>常見的考量，啟動並附加載入

 **簽署您 Profiler DLL**  
 當 Windows 嘗試載入 Profiler DLL 時，它會確認已正確簽署您 Profiler 的 DLL。  如果沒有，則預設的載入會失敗。 執行此作業的方法有兩種：  
  
-   請確定您 Profiler 的 DLL 帶正負號。  
  
-   告訴您的使用者，他們必須使用您的工具之前在其 Windows 8 電腦上安裝開發人員授權。  這可自動從 Visual Studio 或以手動方式從命令提示字元。  如需詳細資訊，請參閱 <<c0> [ 取得開發人員授權](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)。  
  
 **檔案系統權限**  
 Windows 市集應用程式必須具有權限，以載入和執行 Profiler DLL 從它所在的檔案系統上的位置。  根據預設，Windows 市集應用程式不會對大部分的目錄，此類權限，而且任何失敗的嘗試載入 Profiler DLL 將會產生看起來類似下面的 Windows 應用程式事件記錄檔中的項目：  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 一般而言，Windows 市集應用程式只能存取一組有限的磁碟上的位置。  每一個 Windows 市集應用程式可以存取自己的應用程式資料資料夾，以及少數的其他區域，為其授與所有 Windows 市集應用程式存取的檔案系統中。  最好的方式是安裝 Profiler DLL 和其相依性，Program Files 或 Program Files (x86) 下的某處，因為所有的 Windows 市集應用程式具有讀取和執行預設的權限。  
  
### <a name="startup-load"></a>啟動負載

 一般而言，在傳統型應用程式，Profiler UI 會提示啟動負載 Profiler DLL 的初始化環境區塊，其中包含必要的 CLR 程式碼剖析 API 環境變數 (亦即`COR_PROFILER`， `COR_ENABLE_PROFILING`，和`COR_PROFILER_PATH`)，以及然後使用該環境區塊中建立新的處理序。  同樣適用於 Windows 市集應用程式，但機制並不相同。  
  
 **不會執行提高權限**  
 如果處理序嘗試繁衍 （spawn） Windows 市集應用程式處理序 B 程序的應執行在中度完整性層級，不是在高整合層級 （亦即未提高權限）。  這表示，應該執行 Profiler UI，在中度完整性層級，或它必須繁衍 （spawn） 負責啟動 Windows 市集應用程式中整合性層級的另一個桌面程序。  
  
 **選擇 Windows 市集應用程式設定檔**  
 首先，您會想詢問您程式碼剖析工具的使用者若要啟動哪一個 Windows 市集應用程式。  傳統型應用程式，或許您會顯示檔案瀏覽對話方塊中，，而且使用者會尋找並選取 .exe 檔案。  Windows 市集應用程式各不相同，但使用 瀏覽對話方塊沒有任何意義。  相反地，最好是對使用者顯示安裝該使用者即可從選取的 Windows 市集應用程式的清單。  
  
 您可以使用[PackageManager 類別](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx)來產生這份清單。  `PackageManager` 是適用於桌面應用程式，Windows 執行階段類別，而且事實上*只*用於桌面應用程式。  
  
 下列程式碼範例從撰寫為傳統型應用程式在 C# yses 假設 Profiler UI`PackageManager`來產生 Windows 應用程式清單：  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **指定自訂的環境區塊**  
 新的 COM 介面， [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)，可讓您自訂的 Windows 市集應用程式，以便於某些形式的診斷的執行行為。  其中一個方法中， [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx)，可讓您傳遞給 Windows 市集應用程式的環境區塊，當它啟動時，以及其他有用的效果，例如停用自動程序暫止。  環境區塊是很重要，因為這是您要指定環境變數 (`COR_PROFILER`， `COR_ENABLE_PROFILING`，和`COR_PROFILER_PATH)`) 載入 Profiler DLL 使用 CLR。  
  
 請考慮下列程式碼片段：  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 有一些您必須取得適當的項目：  
  
-   `packageFullName` 可以逐一查看封裝，並同時決定`package.Id.FullName`。  
  
-   `debuggerCommandLine` 更有趣的是。  若要為 Windows 市集應用程式中傳遞自訂的環境區塊，您要撰寫您自己的圖片，最簡單的 dummy 偵錯工具。  Windows 會產生暫止的 Windows 市集應用程式，並再啟動您的偵錯工具，包含類似的命令列，在此範例中，以將附加偵錯工具：  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     何處`-p 1336`表示的 Windows 市集應用程式處理序識別碼 1336，和`-tid 1424`表示執行緒 ID 1424 是暫止的執行緒。  虛擬偵錯工具會剖析從命令列 ThreadID，繼續執行該執行緒，，然後結束。  
  
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
  
     您要部署此虛擬偵錯工具為您的診斷工具安裝的一部分，然後指定 在這個偵錯工具的路徑`debuggerCommandLine`參數。  
  
 **啟動 Windows 市集應用程式**  
 若要啟動的 Windows 市集應用程式目前最後到達。 如果您已經已經嘗試自行執行，您可能已經注意[CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa)是不在您建立 Windows 市集應用程式處理序方法。  相反地，您必須使用[IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication)方法。  若要這樣做，您必須取得您要啟動的 Windows 市集應用程式的應用程式使用者模型識別碼。  這表示您必須執行一些探查的資訊清單。  
  
 逐一查看您的套件時 (請參閱中的 「 選擇 Windows 市集應用程式來設定檔 」[啟動負載](#Startup)稍早一節)，您會想要擷取目前的封裝資訊清單中包含的應用程式集：  
  
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
  
 是，一個封裝可以有多個應用程式，以及每個應用程式有自己的應用程式使用者模型識別碼。  因此，您會想要詢問您的使用者設定檔，哪一個應用程式，並抓取應用程式使用者模型識別碼，從該特定應用程式：  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
    //...
}
```  
  
 最後，您現在有您要啟動的 Windows 市集應用程式：  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **務必要記得呼叫 DisableDebugging**  
 當您呼叫[IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)，您所做的承諾，您會自行善後藉由呼叫[IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)方法，因此請務必執行可透過程式碼剖析工作階段時。  
  
### <a name="attach-load"></a>將連接負載

 當 Profiler UI 會想要將其 Profiler DLL 附加至已經開始執行的應用程式時，它會使用[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)。  這同樣適用 Windows 市集應用程式。  但除了稍早所列的一般考量，請確定目標 Windows 市集應用程式不會遭擱置。  
  
 **EnableDebugging**  
 如同啟動載入、 呼叫[IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)方法。  您不需要它來傳遞環境區塊，但您需要其中一個其他功能： 停用自動程序暫止。  否則，當您 Profiler UI 會呼叫[AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)，目標 Windows 市集應用程式可能會暫止。  事實上，這可能是如果使用者現在互動 Profiler UI，並為 Windows 市集應用程式不會啟動任何使用者的畫面。  如果 Windows 市集應用程式暫停的情況下，它將無法回應任何表示 CLR 傳送給它來附加您 Profiler 的 DLL。  
  
 因此，您會想要這麼做：  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 這是除了您未指定偵錯工具命令列或環境區塊，則會進行啟動載入案例中，相同的呼叫。  
  
 **DisableDebugging**  
 一如往常，別忘了呼叫[IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)完成您的程式碼剖析工作階段。  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>在 Windows 市集應用程式中執行  
 因此 Windows 市集應用程式最後已載入您 Profiler 的 DLL。  現在您 Profiler 的 DLL 必須接受教導，學習如何播放 Windows 市集應用程式所需的不同規則，包括其中所允許的 Api，以及如何執行與較小權限。  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>堅持在 Windows 市集應用程式 api  
 當您瀏覽 Windows API，您會發現每一種 API 會記載為適用於傳統型應用程式、 Windows 市集應用程式，或兩者。  例如，**需求**的文件 區段[InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)函式可讓您指出函式適用於傳統型應用程式。 相反地， [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)函式是適用於傳統型應用程式和 Windows 市集應用程式。  
  
 在開發 Profiler DLL 時，將它視為是 Windows 市集應用程式，而且只會使用記載為可供 Windows 市集應用程式的 Api。  分析相依性 (比方說，您可以執行`link /dump /imports`針對您要稽核的 Profiler DLL)，然後搜尋 若要查看哪些相依性為 確定，這不是文件。  在大部分情況下，您的違規可藉由直接取代為較新表單時，就安全的 api (例如，取代[InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)使用[InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex))。  
  
 您可能會發現您 Profiler 的 DLL 會呼叫適用於桌面應用程式，某些 Api，而且尚未似乎運作甚至 Profiler DLL 載入時的 Windows 市集應用程式內。  請注意，它是非常危險的使用與載入 Windows 市集應用程式的程序時在 Profiler DLL 中的 Windows 市集應用程式搭配使用未記載的任何 API:  
  
-   這類 Api 不保證能夠在執行 Windows 市集應用程式的唯一內容中呼叫時。  
  
-   從不同的 Windows 市集應用程式處理序內呼叫，這類 Api 可能不一致的方式運作。  
  
-   這類 Api 可能會看似正常運作，從 Windows 市集應用程式的目前版本的 Windows，但可能會中斷或停用 Windows 的未來版本中。  
  
 若要修正您所有的違規，並避免風險，是的最佳建議。  
  
 您可能會發現您絕對的工作需要特定的 API 並無法找到適用於 Windows 市集應用程式的替代項目。  在此情況下，最小值：  
  
-   測試、 測試、 測試即時 daylights 超出該 API 的使用方式。  
  
-   了解此 API 可能會突然中斷或消失如果呼叫從 Windows 市集內的應用程式在未來的版本的 Windows。  這不會由 Microsoft 視為相容性問題，支援您的使用量，它將不會優先使用。  
  
### <a name="reduced-permissions"></a>降低權限

 它已超出本主題列出 Windows 市集應用程式權限不同於傳統型應用程式的所有方法的範圍。  但，當然每次您 Profiler 的 DLL （載入 Windows 市集應用程式相較於傳統型應用程式） 時嘗試存取的任何資源的行為會有所差異。  檔案系統是最常見的範例。  有一些會放在指定的 Windows 市集應用程式是否可存取的磁碟上 (請參閱[檔案存取和權限 (Windows 執行階段應用程式](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx))，而且您 Profiler 的 DLL 會在相同的限制下。  徹底測試您的程式碼。  
  
### <a name="inter-process-communication"></a>處理序間通訊

 在這份文件開頭的圖表所示，Profiler DLL （載入至 Windows 市集應用程式處理序空間中） 可能需要與 Profiler UI （執行個別的桌面應用程式處理序空間中） 透過您自己自訂處理序間通訊通訊 (IPC) 通道。  Profiler UI 會將訊號傳送至 Profiler DLL，以修改其行為，和 Profiler DLL 從已分析的 Windows 市集應用程式傳送資料至 Profiler UI 來後置處理和顯示程式碼剖析工具的使用者。  
  
 大部分的程式碼剖析工具需要使用這種方式，但您 Profiler 的 DLL 載入 Windows 市集應用程式時，您的選擇，IPC 機制有更多限制。  比方說，具名的管道不屬於 Windows 市集應用程式 SDK，因此您無法使用它們。  
  
 但當然，檔案仍在儘管在更多限制的方式。  事件也會提供。  
  
 **透過檔案進行通訊**  
 大部分的資料可能會透過檔案傳遞 Profiler DLL 和 Profiler UI 之間。  索引鍵是挑選檔案位置，您 （在 Windows 市集應用程式的內容） 的 Profiler DLL 和 Profiler UI 具有讀取和寫入權限。  例如，暫存資料夾的路徑是您 Profiler DLL 和 Profiler UI 可以存取的位置，但沒有其他的 Windows 市集應用程式封裝可以存取 （因此防護您記錄從其他 Windows 市集應用程式套件的任何資訊）。  
  
 您的 Profiler UI 和 Profiler DLL 可以判斷此路徑獨立。  Profiler UI，它會逐一為目前的使用者安裝的所有套件時 （請參閱稍早的範例程式碼），取得存取權`PackageId`類別，可以使用此程式碼片段的程式碼衍生來源的暫存資料夾路徑。  （如往常，錯誤檢查省略以求簡單扼要。）  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 同時，Profiler DLL 基本上相同，但它可以更輕鬆地[ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx)類別[ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx)屬性。  
  
 **透過事件進行通訊**  
 如果您想在 Profiler UI 與 Profiler DLL 之間的簡單訊號語意，您可以使用 Windows 市集應用程式，以及桌面應用程式內的事件。  
  
 從您 Profiler 的 DLL，您可以直接呼叫[CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)函式來建立具名的事件，您想要的任何名稱。  例如:   
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Profiler UI 則需要尋找 Windows 市集應用程式的命名空間下該具名的事件。  例如，無法呼叫 Profiler UI [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)，指定做為事件名稱  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>` 為 Windows 市集應用程式的 AppContainer SID。  本主題稍早章節說明如何以逐一查看目前的使用者安裝的套件。  您可以從該範例程式碼中，取得 packageId。  從 packageId 中，您可以取得和`<acSid>`與下列類似的程式碼：  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
### <a name="no-shutdown-notifications"></a>沒有關機通知

 執行時的 Windows 市集應用程式內，Profiler DLL 不應該仰賴依據其中一個[icorprofilercallback:: Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)甚至[DllMain](/windows/desktop/Dlls/dllmain) (與`DLL_PROCESS_DETACH`) 正在呼叫以通知您 Profiler 的 DLL正在結束的 Windows 市集應用程式。  事實上，您應該預期它們將永遠不可叫用。  在過去，許多 Profiler Dll 使用這些通知便利的地方來排清至磁碟、 關閉檔案，將通知傳回到的 Profiler UI 等等的快取。但現在您 Profiler 的 DLL 必須稍有不同的組織。  
  
 Profiler DLL 應該是它會記錄資訊。  基於效能考量，您可能想要批次在記憶體中的資訊和排清到磁碟隨著批次的成長的大小超過某個臨界值。  但假設可能會遺失任何尚未排清至磁碟的資訊。  這表示您會想要明智的做法，挑選您的閾值和 Profiler UI 需要強行寫入的 Profiler dll 的資訊不完整處理。  
  
## <a name="windows-runtime-metadata-files"></a>Windows 執行階段中繼資料檔案

 它超出範圍的詳細說明此文件檔案是在 Windows 執行階段中繼資料 (WinMD)。    本章節僅限於 WinMD 檔案載入的 Profiler DLL 正在分析 Windows 市集應用程式時，CLR Profiling API 的回應方式。  
  
### <a name="managed-and-non-managed-winmds"></a>受控和非受控 Winmd

 如果開發人員會使用 Visual Studio 來建立新的 Windows 執行階段元件專案，該專案的組建會產生 WinMD 檔案，描述開發人員所撰寫的中繼資料 （型別描述的類別、 介面等）。  如果這個專案是以 C# 或 VB 撰寫的 managed 的語言專案，該相同的 WinMD 檔案也會包含這些類型 （亦即，它包含所有由開發人員的原始程式碼所編譯的 IL） 的實作。  這類檔案稱為受管理的 WinMD 檔案。  它們有趣，因為它們包含 Windows 執行階段中繼資料和基礎實作。  
  
 相反地，如果開發人員的 c + + 建立 Windows 執行階段元件專案，該專案的組建產生 WinMD 檔案，僅包含中繼資料，並實作會編譯成不同的原生 DLL。  同樣地，隨附於 Windows SDK 的 WinMD 檔案會包含只有中繼資料，實作編譯成不同的原生 Dll 隨附為 Windows 的一部分。  
  
 以下資訊適用於這兩個受管理的 Winmd，包含中繼資料和實作，以及未受管理的 Winmd，包含只有中繼資料。  
  
### <a name="winmd-files-look-like-clr-modules"></a>WinMD 檔案看起來像 CLR 模組

 就 CLR 而言，所有的 WinMD 檔案都是模組。  當 WinMD 檔案載入您 Profiler DLL 和其 Moduleid 為何，相同的方式，與其他受管理的模組，因此會告訴 CLR Profiling API。  
  
 Profiler DLL 可以區分來自其他模組 WinMD 檔案藉由呼叫[ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)方法，並檢查`pdwModuleFlags`輸出參數[COR_PRF_MODULE_WINDOWS_執行階段](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)旗標。  （它是設定才 ModuleID 代表 WinMD）。  
  
### <a name="reading-metadata-from-winmds"></a>從 Winmd 讀取中繼資料

 WinMD 檔案，例如一般模組，包含中繼資料，可以透過讀取[中繼資料 Api](../../../../docs/framework/unmanaged-api/metadata/index.md)。  不過，CLR 將 Windows 執行階段型別至.NET Framework 型別時它會讀取 WinMD 檔案，讓開發人員以 managed 程式碼程式，並使用 WinMD 檔案可以有更自然的程式設計體驗。  如需這些對應的一些範例，請參閱[.NET Framework 支援的 Windows 市集應用程式和 Windows 執行階段](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。  
  
 因此何種檢視您的分析工具會使用中繼資料 Api 時： 原始的 Windows 執行階段檢視中或對應的.NET Framework 檢視？  答案： 它是由您。  
  
 當您呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)方法來取得中繼資料介面，例如 WinMD [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)，您可以選擇設定[ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)在`dwOpenFlags`參數來關閉這項對應。  否則，根據預設，會啟用對應。  通常，分析工具會保留啟用，對應，使 Profiler DLL 取得從 WinMD 中繼資料 （例如，類型的名稱） 的字串會看起來就熟悉且自然的程式碼剖析工具的使用者。  
  
### <a name="modifying-metadata-from-winmds"></a>修改從 Winmd 中繼資料

 不支援修改 Winmd 中繼資料。  如果您呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)方法對 WinMD 的檔案，並指定[ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)中`dwOpenFlags`參數或例如尋求可寫入的中繼資料介面[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)， [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)將會失敗。  這是以 IL 重寫的分析，需要修改中繼資料，以支援其檢測 （例如，若要新增 AssemblyRefs 或新的方法） 的特別重要。  因此您應檢查有無[COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)第一次 （如前一節所述） 並避免這類模組在要求可寫入的中繼資料介面。  
  
### <a name="resolving-assembly-references-with-winmds"></a>解析組件參考 Winmd

 許多程式碼剖析工具需要解析中繼資料參考，以手動方式來協助與檢測或型別檢查。  這類程式碼剖析工具必須要了解 CLR 如何解析指向 Winmd 的組件參考，因為這些參考會解析以完全不同的方式，比標準的組件參考。  
  
## <a name="memory-profilers"></a>記憶體分析工具

 Managed 的堆積的記憶體回收行程不完全不同的 Windows 市集應用程式和傳統型應用程式中。  不過，有程式碼剖析工具作者需要留意的某些細微的差異。  
  
### <a name="forcegc-creates-a-managed-thread"></a>ForceGC 建立 managed 的執行緒

 在執行記憶體分析時，Profiler DLL 通常會建立個別的執行緒，要呼叫[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)方法。  這是什麼新玩意兒。  但可能會令人意外執行廢棄項目集合內的 Windows 市集應用程式的動作，可能會轉換成 managed 執行緒的執行緒 （例如，程式碼剖析 API ThreadID 會建立該執行緒）。  
  
 若要瞭解這個結果，就一定要了解同步和非同步呼叫之間的差異，CLR Profiling API 所定義。 請注意，這是非常不同於 Windows 市集應用程式中的非同步呼叫的概念。  請參閱部落格文章[為什麼我們 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/)如需詳細資訊。  
  
 相關的點是，在您的分析工具所建立的執行緒上所做的呼叫一律是同步的即使這些呼叫會從外部 Profiler DLL 的其中一項的實作進行[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)方法。  至少，用這種情況。  現在，CLR 已轉換成 managed 執行緒分析工具的執行緒因為呼叫[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)，執行緒不會再視為您的分析工具執行緒。  因此，CLR 會強制執行更嚴格定義的項目會限定為該執行緒同步 — 也就是呼叫必須來自 Profiler DLL 的其中一項[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)限定為同步的方法。  
  
 這代表在實務上什麼？  大部分[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)方法僅提供以同步方式呼叫的安全，否則將會立即失敗。  因此，如果您 Profiler 的 DLL 會重複使用您[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)通常做程式碼剖析工具所建立執行緒上的其他呼叫的執行緒 (例如，若要[RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)， [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)，或[RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md))，您要有問題。  即使這類非同步安全函式[DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)已從受管理的執行緒呼叫時的特殊規則。 (請參閱部落格文章[Profiler 堆疊查核行程： 基礎及更新版本](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/)如需詳細資訊。)  
  
 因此，我們建議您 Profiler 的 DLL 會呼叫建立任何執行緒[ForceGC 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)應*只*為了觸發 Gc，然後回應 GC 回呼。  它不應該呼叫程式碼剖析 API 來執行其他工作，例如 stack 取樣或中斷連結。  
  
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

 從.NET Framework 4.5 開始，沒有新的 GC 回呼[ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)，提供程式碼剖析工具更完整資訊*相依控制代碼*。 這些控制代碼有效地會加入從來源物件的參考到目標物件為了 GC 存留期管理。  相依控制代碼已經不新奇，但開發人員以 managed 程式碼程式還能建立自己的相依控制代碼使用<xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType>甚至是在 Windows 8 和.NET Framework 4.5 之前的類別。  
  
 不過，受管理的 XAML Windows 市集應用程式現在會使大量使用相依的控制代碼。  特別是，CLR 會使用它們來協助管理受管理的物件和未受管理的 Windows 執行階段物件之間的參考循環。  這表示它是更重要現在比以往記憶體分析工具，以了解這些相依的控制代碼，讓他們可以視覺化以及剩餘的堆積圖形中的邊緣。  應該使用 Profiler DLL [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)， [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)，並[ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)一起以形成完整的堆積圖形檢視.  
  
## <a name="conclusion"></a>結論

 您可使用 CLR Profiling API 來分析 Windows 市集應用程式內執行的 managed 程式碼。  事實上，您可以採用現有的剖析您正在開發的工具，並進行一些特定的變更，以便它可以針對 Windows 市集應用程式。   Profiler UI 應該用來啟用 Windows 市集應用程式偵錯模式中的使用新的 Api。  請確定您 Profiler 的 DLL 會使用僅適用於 Windows 市集應用程式的 Api。  應該寫入您 Profiler DLL 和 Profiler UI 之間的通訊機制，記住的 Windows 市集應用程式 API 限制與受限的權限，可供 Windows 市集應用程式的認知。  Profiler DLL 應該留意 CLR 如何處理 Winmd 和記憶體回收行程的行為有何不同方面 managed 執行緒。  
  
## <a name="resources"></a>資源

 **通用語言執行平台**  
 -   [CLR 程式碼剖析 API 參考](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [CLR 中繼資料 API 參考](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Windows 執行階段的 CLR 的互動**  
 [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Windows 市集應用程式**  
 -   [檔案存取權和權限 （Windows 執行階段應用程式](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [取得開發人員授權](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [IPackageDebugSettings 介面](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>另請參閱

[程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)  
