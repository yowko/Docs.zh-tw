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
ms.openlocfilehash: 8368930e60210b0cb470700e9c9470c57d536c13
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291407"
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR 分析工具和 Windows 市集應用程式

本主題討論在撰寫診斷工具來分析在 Windows Store 應用程式中執行的 managed 程式碼時，您必須考慮的事項。 它也提供修改現有開發工具的指導方針，讓它們在您對 Windows Store 應用程式執行時仍可繼續運作。 若要瞭解這項資訊，最好是您熟悉 Common Language Runtime 分析 API 時，您已經在可針對 Windows 桌面應用程式正確執行的診斷工具中使用此 API，而且您現在有興趣修改工具可針對 Windows Store 應用程式正確執行。

## <a name="introduction"></a>簡介

如果您已將它放在簡介段落之後，您就會熟悉 CLR 分析 API。 您已經撰寫一種診斷工具，適用于受管理的桌面應用程式。 現在您想知道該怎麼做，讓您的工具可與受控的 Windows Store 應用程式搭配使用。 也許您已經試過這項工作，併發現它不是一項簡單的任務。 事實上，所有工具開發人員可能都不會對您有許多考慮。 例如:

- Windows Store 應用程式會在具有嚴重降低許可權的內容中執行。

- 相較于傳統的受控模組，Windows 中繼資料檔案具有獨特的特性。

- 當互動性中斷時，Windows Store 應用程式會習慣自行暫停。

- 您的處理序間通訊機制可能因各種原因而無法再使用。

本主題列出您需要注意的事項，以及如何正確處理它們。

如果您不熟悉 CLR 分析 API，請跳到本主題結尾的資源，以尋找更好的簡介資訊。

提供有關特定 Windows Api 及其使用方式的詳細資料，也不在本主題的討論範圍內。 請考慮此主題的起點，並參閱 MSDN 以深入瞭解此處參考的任何 Windows Api。

## <a name="architecture-and-terminology"></a>架構與術語

通常，診斷工具具有如下圖所示的架構。 它會使用「分析工具」一詞，但許多這類工具會超越一般的效能或記憶體分析，使其成為程式碼涵蓋範圍、模擬物件架構、時間差的偵錯工具、應用程式監視等方面。 為了簡單起見，本主題將繼續將所有這些工具當做分析工具來參考。

本主題中使用下列術語：

**應用程式**

這是 profiler 正在分析的應用程式。 通常，此應用程式的開發人員現在會流量分析工具來協助診斷應用程式的問題。 傳統上，此應用程式會是 Windows 桌面應用程式，但在本主題中，我們會查看 Windows Store 應用程式。

**Profiler DLL**

這是載入所分析應用程式之進程空間的元件。 此元件（也稱為 profiler 「代理程式」）會執行[ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback 介面](icorprofilercallback-interface.md)（2、3等）介面，並使用[ICorProfilerInfo](icorprofilerinfo-interface.md)（2，3，等）介面來收集有關的資料。分析的應用程式，並可能修改應用程式行為的各個層面。

**Profiler UI**

這是分析工具使用者所互動的桌面應用程式。 它會負責向使用者顯示應用程式狀態，並為使用者提供控制分析應用程式行為的方法。 這個元件一律會在自己的進程空間中執行，與所分析應用程式的進程空間不同。 分析工具 UI 也可以做為「附加觸發程式」，也就是呼叫[ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)方法的進程，以便在剖析器 dll 未于啟動時載入的情況下，讓分析的應用程式載入分析工具 dll。

> [!IMPORTANT]
> 您的 Profiler UI 應該保留 Windows 桌面應用程式，即使是用來控制和報告 Windows Store 應用程式也一樣。 不希望能夠在 Windows 市集中封裝和運送您的診斷工具。 您的工具需要執行 Windows Store 應用程式無法執行的動作，而其中有許多專案都位於您的 Profiler UI 中。

在本檔中，範例程式碼假設：

- 您的 Profiler DLL 是以C++撰寫，因為它必須是原生 DLL，視 CLR 分析 API 的需求而成。

- 您的 Profiler UI 是以C#撰寫。 這並不是必要的，但因為您分析工具 UI 進程的語言沒有任何需求，所以為什麼不選擇簡潔且簡單的語言？

### <a name="windows-rt-devices"></a>Windows RT 裝置

Windows RT 裝置已完全鎖定。 協力廠商分析工具只是無法在這類裝置上載入。 本檔著重于 Windows 8 電腦。

## <a name="consuming-windows-runtime-apis"></a>使用 Windows 執行階段 Api

在下列各節中討論的幾個案例中，您的 Profiler UI 桌面應用程式必須使用一些新的 Windows 執行階段 Api。 您會想要參考檔，以瞭解哪些 Windows 執行階段 Api 可以從桌面應用程式使用，以及從桌面應用程式和 Windows Store 應用程式呼叫時，其行為是否不同。

如果您的分析工具 UI 是以 managed 程式碼撰寫的，您將需要執行幾個步驟，才能輕鬆地使用這些 Windows 執行階段 Api。 如需詳細資訊，請參閱[受管理的桌面應用程式和 Windows 執行階段](https://go.microsoft.com/fwlink/?LinkID=271858)一文。

## <a name="loading-the-profiler-dll"></a>載入 Profiler DLL

本節說明 Profiler UI 如何讓 Windows Store 應用程式載入您的分析工具 DLL。 本節中所討論的程式碼屬於您的分析工具 UI 桌面應用程式，因此牽涉到使用適用于傳統型應用程式的 Windows Api，但不一定是 Windows Store 應用程式的安全。

您的 Profiler UI 可能會以兩種方式，將 Profiler DLL 載入應用程式的進程空間：

- 在應用程式啟動時，由環境變數所控制。

- 藉由呼叫[ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)方法，在啟動完成後附加至應用程式。

您的第一個障礙就是取得啟動載入和附加程式碼剖析工具 DLL，以便與 Windows Store 應用程式正常搭配運作。 這兩種形式的載入都共用一些特殊考慮，因此讓我們開始使用。

### <a name="common-considerations-for-startup-and-attach-loads"></a>啟動和附加負載的一般考慮

**簽署 Profiler DLL**

當 Windows 嘗試載入分析工具 DLL 時，它會驗證您的 Profiler DLL 是否已正確簽署。 如果不是，則預設載入會失敗。 執行此作業的方法有兩種：

- 請確定您的 Profiler DLL 已簽署。

- 告訴您的使用者，他們必須先在他們的 Windows 8 電腦上安裝開發人員授權，才能使用您的工具。 這可以從 Visual Studio 自動完成，或從命令提示字元手動執行。 如需詳細資訊，請參閱[取得開發人員授權](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10))。

**檔案系統許可權**

Windows Store 應用程式必須具有從檔案系統上的位置載入和執行 Profiler DLL 的許可權，而此檔案是 residesBy 預設的，Windows Store 應用程式在大部分目錄上沒有這類許可權，而且嘗試載入 Profiler DLL 失敗會在 Windows 應用程式事件記錄檔中產生專案，如下所示：

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

一般來說，Windows Store 應用程式只允許存取磁片上一組有限的位置。 每個 Windows Store 應用程式都可以存取自己的應用程式資料檔案夾，以及在檔案系統中，為所有 Windows Store 應用程式授與存取權的一些其他區域。 最佳做法是將您的 Profiler DLL 及其相依性安裝在 Program Files 或 Program Files （x86）底下，因為所有的 Windows Store 應用程式在預設情況下都有讀取和執行許可權。

### <a name="startup-load"></a>啟動載入

一般來說，在傳統型應用程式中，分析工具 UI 會藉由初始化包含必要 CLR 分析 API 環境變數（也就是 `COR_PROFILER`、`COR_ENABLE_PROFILING` 和 `COR_PROFILER_PATH`）的環境區塊，來提示您分析工具 DLL 的啟動負載，然後建立新的使用該環境區塊的處理常式。 Windows Store 應用程式也是如此，但機制不同。

**不要以提高許可權執行**

如果進程嘗試產生 Windows Store 應用程式進程 B，則應該以中度完整性層級執行進程，而不是在高完整性層級（也就是未提高許可權）。 這表示您的分析工具 UI 應該以「中」完整性層級執行，或者必須產生「中」整合層級的另一個桌面進程，以處理啟動 Windows Store 應用程式。

**選擇要分析的 Windows Store 應用程式**

首先，您會想要要求 profiler 使用者要啟動哪個 Windows Store 應用程式。 針對桌面應用程式，您可能會顯示 [檔案] [流覽] 對話方塊，而使用者會尋找並選取 .exe 檔案。 但是，Windows Store 應用程式不同，而且使用 [流覽] 對話方塊沒有意義。 相反地，最好是向使用者顯示已安裝的 Windows Store 應用程式清單，以供該使用者選取。

您可以使用 <xref:Windows.Management.Deployment.PackageManager> 類別來產生這份清單。 `PackageManager` 是適用于桌面應用程式的 Windows 執行階段類別，事實上，它*僅*適用于桌面應用程式。

下列來自以中C#的桌面應用程式撰寫的假設分析工具 UI 的程式碼範例會使用 `PackageManager` 來產生 Windows 應用程式的清單：

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**指定自訂環境區塊**

新的 COM 介面[IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)可讓您自訂 Windows Store 應用程式的執行行為，讓某些形式的診斷變得更容易。 它的其中一個方法[EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)，可讓您在啟動時將環境區塊傳遞至 Windows Store 應用程式，以及其他實用的效果，例如停用自動進程暫止。 環境區塊很重要，因為您必須在此指定 CLR 用來載入分析工具 DLL 的環境變數（`COR_PROFILER`、`COR_ENABLE_PROFILING` 和 `COR_PROFILER_PATH)`）。

請考慮下列程式碼片段：

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

您必須先取得幾個專案：

- 在逐一查看封裝並抓取 `package.Id.FullName` 時，可以判斷 `packageFullName`。

- `debuggerCommandLine` 更有趣。 若要將自訂環境區塊傳遞至 Windows Store 應用程式，您需要撰寫您自己、簡單的虛擬偵錯工具。 Windows 會產生已暫停的 Windows Store 應用程式，然後使用命令列啟動偵錯工具（如下列範例所示）來附加偵錯工具：

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     其中 `-p 1336` 表示 Windows Store 應用程式具有處理序識別碼1336，而 `-tid 1424` 表示執行緒識別碼1424是已暫停的執行緒。 您的虛擬偵錯工具會從命令列剖析 ThreadID，繼續該執行緒，然後結束。

     以下是一些執行C++此動作的範例程式碼（請務必新增錯誤檢查！）：

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

     您必須將此虛擬偵錯工具部署為診斷工具安裝的一部分，然後在 `debuggerCommandLine` 參數中指定此偵錯工具的路徑。

**啟動 Windows Store 應用程式**

Windows Store 應用程式的啟動時間終於到達。 如果您已自行嘗試這麼做，您可能已注意到[CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa)並不是您建立 Windows Store 應用程式進程的方式。 相反地，您必須使用[IApplicationActivationManager：： ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication)方法。 若要這麼做，您必須取得您要啟動之 Windows Store 應用程式的應用程式使用者模型識別碼。 這表示您必須透過資訊清單執行一些深入探討。

在反復執行封裝時（請參閱稍早[啟動載入](#startup-load)區段中的「選擇要分析的 Windows Store 應用程式」），您會想要抓取目前套件資訊清單中所包含的應用程式集合：

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

是，一個封裝可以有多個應用程式，而且每個應用程式都有自己的應用程式使用者模型識別碼。 因此，您會想要向使用者要求要分析的應用程式，並從該特定應用程式抓取應用程式使用者模型識別碼：

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

最後，您現在已具備啟動 Windows Store 應用程式所需的功能：

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**請記得呼叫 DisableDebugging**

當您呼叫[IPackageDebugSettings：： EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)時，您所做出的承諾是藉由呼叫[IPackageDebugSettings：:D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging)方法來自行清除，因此當分析會話結束時，請務必這麼做。

### <a name="attach-load"></a>附加負載

當您的 Profiler UI 想要將其 Profiler DLL 附加至已經開始執行的應用程式時，它會使用[ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)。 Windows Store 應用程式也是如此。 但是除了先前所列的一般考慮之外，請確定目標 Windows 儲存區應用程式未暫停。

**EnableDebugging**

如同啟動載入，請呼叫[IPackageDebugSettings：： EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)方法。 您不需要它來傳遞環境區塊，但您需要其中一個其他功能：停用自動處理常式擱置。 否則，當您的 Profiler UI 呼叫[AttachProfiler](iclrprofiling-attachprofiler-method.md)時，目標 Windows Store 應用程式可能會暫停。 事實上，如果使用者現在與您的分析工具 UI 互動，而 Windows Store 應用程式在任何使用者畫面上都不是作用中，這就很有可能。 而且，如果 Windows 儲存區應用程式已暫止，它將無法回應 CLR 傳送給它的任何信號，以附加您的分析工具 DLL。

因此，您會想要執行如下的動作：

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

這是您針對啟動載入案例所做的相同呼叫，但您不需要指定偵錯工具命令列或環境區塊。

**DisableDebugging**

一如往常，當您的分析會話完成時，別忘了呼叫[IPackageDebugSettings：:D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) 。

## <a name="running-inside-the-windows-store-app"></a>在 Windows Store 應用程式中執行

因此，Windows Store 應用程式終於已載入您的 Profiler DLL。 現在，您的分析工具 DLL 必須教您如何透過 Windows Store 應用程式所需的不同規則來播放，包括允許哪些 Api，以及如何以降低的許可權執行。

### <a name="stick-to-the-windows-store-app-apis"></a>堅持 Windows Store 應用程式 Api

當您流覽 Windows API 時，您會注意到每個 API 都記載為適用于桌面應用程式、Windows Store 應用程式或兩者。 例如， [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)函式檔的 [**需求**] 區段指出函式僅適用于桌面應用程式。 相反地，桌面應用程式和 Windows Store 應用程式都有提供[InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)函式。

開發分析工具 DLL 時，請將它視為 Windows Store 應用程式，並只使用已記載為可供 Windows Store 應用程式使用的 Api。 分析您的相依性（例如，您可以針對分析工具 DLL 執行 `link /dump /imports` 來進行審核），然後搜尋檔以查看哪些相依性是正常的，哪些不是。 在大部分的情況下，您只要以較新的 API 形式（也就是將[InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)取代為[InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)）取代，就可以修正您的違規。

您可能會注意到您的分析工具 DLL 會呼叫一些僅適用于桌面應用程式的 Api，但即使您的分析工具 DLL 載入 Windows Store 應用程式中，它們還是看起來很有作用。 請注意，當您載入 Windows Store 應用程式進程時，流量分析工具 DLL 中的 Windows Store 應用程式未記載的任何 API，會有風險：

- 在 Windows Store 應用程式執行所在的唯一內容中呼叫這類 Api 時，並不保證會運作。

- 從不同的 Windows Store 應用程式進程中呼叫時，這類 Api 可能無法一致地工作。

- 這類 Api 在目前 Windows 版本的 Windows Store 應用程式中看起來可能很正常，但在未來的 Windows 版本中可能會中斷或停用。

最佳建議是修正您所有的違規，並避免風險。

您可能會發現，在沒有特定 API 的情況下，您絕對無法執行，而且找不到適用于 Windows Store 應用程式的取代。 在這種情況下，至少：

- 測試、測試、測試您在使用該 API 時的生活 daylights。

- 瞭解在未來的 Windows 版本中，如果從 Windows Store 應用程式中呼叫，API 可能突然中斷或消失。 這不會被視為 Microsoft 的相容性問題，而且支援您的使用方式將不會是優先考慮。

### <a name="reduced-permissions"></a>降低許可權

這不在本主題的討論範圍內，以列出 Windows Store 應用程式許可權與桌面應用程式不同的所有方式。 但當然，每當您的分析工具 DLL （載入至 Windows Store 應用程式時，相較于桌面應用程式）嘗試存取任何資源時，行為會有所不同。 檔案系統是最常見的範例。 在磁片上，有幾個位置可供指定的 Windows Store 應用程式存取（請參閱檔案[存取和許可權（Windows 執行階段應用程式](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))），而您的分析工具 DLL 會受到相同的限制。 徹底測試您的程式碼。

### <a name="inter-process-communication"></a>處理序間通訊

如本文開頭的圖表所示，您的分析工具 DLL （載入至 Windows Store 應用程式進程空間）可能需要透過您自己的自訂進程間，與您的分析工具 UI 通訊（在不同的桌面應用程式進程空間中執行）通訊（IPC）通道。 分析工具 UI 會將信號傳送至 Profiler DLL 以修改其行為，而 Profiler DLL 會將資料從分析的 Windows Store 應用程式傳送回 Profiler UI，以進行後置處理，並向 profiler 使用者顯示。

大部分的分析工具都需要以這種方式來工作，但當您的分析工具 DLL 載入至 Windows Store 應用程式時，您對 IPC 機制的選擇會更有限制。 例如，具名管道不是 Windows Store 應用程式 SDK 的一部分，因此您無法使用它們。

但當然，檔案仍在中，雖然是以較有限的方式提供。 事件也可供使用。

**透過檔案通訊**

大部分的資料可能會透過檔案在分析工具 DLL 和 Profiler UI 之間通過。 關鍵在於選擇檔案位置，讓您的分析工具 DLL （在 Windows Store 應用程式的內容中）和 Profiler UI 具有的讀取和寫入權限。 例如，暫存資料夾路徑是分析工具 DLL 和分析工具 UI 可以存取的位置，但是沒有其他 Windows 儲存區應用程式套件可以存取（因而防護您從其他 Windows Store 應用程式套件記錄的任何資訊）。

您的 Profiler UI 和 Profiler DLL 都可以獨立判斷此路徑。 分析工具 UI，當它逐一查看所有為目前使用者安裝的封裝（請參閱稍早的範例程式碼）時，會取得 `PackageId` 類別的存取權，其中暫存資料夾路徑可以使用類似于此程式碼片段的程式碼來衍生。 （一如往常，為了簡潔起見，會省略錯誤檢查）。

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

同時，您的分析工具 DLL 基本上可以執行相同的動作，不過使用[ApplicationData](xref:Windows.Storage.ApplicationData.Current%2A)屬性可以更輕鬆地取得 @no__t 0 類別。

**透過事件通訊**

如果您想要讓分析工具 UI 與 Profiler DLL 之間有簡單的信號，您可以在 Windows Store 應用程式和桌面應用程式中使用事件。

從您的分析工具 DLL，您可以直接呼叫[CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)函式，以您喜歡的任何名稱來建立名為的事件。 例如:

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

接著，您的分析工具 UI 就必須在 Windows Store 應用程式的命名空間下尋找該命名事件。 例如，您的 Profiler UI 可以呼叫[CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)，並將事件名稱指定為

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>` 是 Windows Store 應用程式的 AppContainer SID。 本主題稍早的章節示範如何逐一查看針對目前使用者所安裝的套件。 從該範例程式碼中，您可以取得 packageId。 而從 packageId，您可以使用與下列類似的程式碼取得 `<acSid>`：

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>沒有關機通知

在 Windows Store 應用程式中執行時，您的分析工具 DLL 不應依賴[ICorProfilerCallback：： Shutdown](icorprofilercallback-shutdown-method.md) ，[或甚至是](/windows/desktop/Dlls/dllmain)使用 `DLL_PROCESS_DETACH`）來通知分析工具 dll，Windows Store 應用程式即將結束。 事實上，您應該預期它們永遠不會被呼叫。 在過去，許多 Profiler Dll 已使用這些通知做為方便的位置，可將快取快取到磁片、關閉檔案、將通知傳送回分析工具 UI 等等。但現在您的 Profiler DLL 必須以不同的方式組織。

分析工具 DLL 應記錄資訊。 基於效能的考慮，您可能會想要在記憶體中批次處理資訊，並在批次大小超過某個臨界值時將資料排清到磁片。 但假設尚未排清到磁片的任何資訊都可能遺失。 這表示您會想要明智地挑選您的臨界值，而且您的分析工具 UI 必須強化，才能處理 Profiler DLL 所寫入的不完整資訊。

## <a name="windows-runtime-metadata-files"></a>Windows 執行階段中繼資料檔案

本檔不在本文的討論範圍內，以詳細瞭解 Windows 執行階段中繼資料（WinMD）檔案。 本節僅限於當 WinMD 檔案是由 Profiler DLL 正在分析的 Windows Store 應用程式載入時，CLR 分析 API 的回應方式。

### <a name="managed-and-non-managed-winmds"></a>受控和非受控 Winmd

如果開發人員使用 Visual Studio 建立新的 Windows 執行階段元件專案，則該專案的組建會產生 WinMD 檔案，以描述開發人員所撰寫的中繼資料（類別、介面等的類型描述）。 如果此專案是以C#或 VB 撰寫的 managed 語言專案，則相同的 WinMD 檔案也會包含這些類型的實作為（表示它包含從開發人員的原始程式碼所編譯的所有 IL）。 這類檔案稱為受控 WinMD 檔案。 它們很有趣，因為它們同時包含 Windows 執行階段中繼資料和基礎執行。

相反地，如果開發人員建立的 Windows 執行階段元件專案C++，則該專案的組建會產生僅包含中繼資料的 WinMD 檔案，並將此實編譯成個別的原生 DLL。 同樣地，隨附于 Windows SDK 中的 WinMD 檔案只包含中繼資料，並編譯成個別的原生 Dll，並隨附于 Windows 中。

下列資訊適用于 managed Winmd，其中包含中繼資料和實作為，以及僅包含中繼資料的非受控 Winmd。

### <a name="winmd-files-look-like-clr-modules"></a>WinMD 檔案看起來像 CLR 模組

就 CLR 的顧慮而言，所有 WinMD 檔案都是模組。 因此，CLR 分析 API 會在 WinMD 檔案載入及其 ModuleIDs 時，告訴您的 Profiler DLL，其方式與其他受控模組相同。

您的分析工具 DLL 可以藉由呼叫[ICorProfilerInfo3：： GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)方法，並檢查[COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md)旗標的 `pdwModuleFlags` 輸出參數，來區分 WinMD 檔案與其他模組。 （只有在 ModuleID 代表 WinMD 時才會設定）。

### <a name="reading-metadata-from-winmds"></a>從 Winmd 讀取中繼資料

WinMD 檔案（例如一般模組）包含可以透過[中繼資料 api](../../../../docs/framework/unmanaged-api/metadata/index.md)讀取的中繼資料。 不過，CLR 會在讀取 WinMD 檔案時，將 Windows 執行階段型別對應到 .NET Framework 型別，以便在 managed 程式碼中設計和取用 WinMD 檔案的開發人員可以擁有更自然的程式設計經驗。 如需這些對應的一些範例，請參閱[.NET Framework 支援 Windows Store 應用程式和 Windows 執行階段](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。

當 profiler 使用中繼資料 Api 時，您的分析工具會取得哪一個視圖：原始 Windows 執行階段視圖或對應的 .NET Framework 視圖？  答：這是由您自行來。

當您在 WinMD 上呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)方法來取得中繼資料介面（例如[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)）時，您可以選擇在 `dwOpenFlags` 參數中設定[ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) ，以關閉這個對應。 否則，根據預設，將會啟用對應。 一般來說，分析工具會讓對應保持啟用狀態，讓分析工具 DLL 從 WinMD 中繼資料（例如，類型的名稱）取得的字串看起來會對分析工具使用者感到熟悉且自然。

### <a name="modifying-metadata-from-winmds"></a>修改 Winmd 的中繼資料

不支援在 Winmd 中修改中繼資料。 如果您針對 WinMD 檔案呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)方法，並在 `dwOpenFlags` 參數中指定[ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) ，或要求可寫入的中繼資料介面（例如[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)）， [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)將會失敗。 這對於 IL 重寫分析工具而言特別重要，這需要修改中繼資料以支援其檢測（例如，新增 AssemblyRefs 或新方法）。 因此，您應該先檢查[COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) （如上一節所述），並避免在這類別模組上要求可寫入的中繼資料介面。

### <a name="resolving-assembly-references-with-winmds"></a>使用 Winmd 解析元件參考

許多分析工具必須以手動方式解析中繼資料參考，以協助檢測或型別檢查。 這類分析工具必須知道 CLR 如何解析指向 Winmd 的元件參考，因為這些參考是以與標準元件參考完全不同的方式來解析。

## <a name="memory-profilers"></a>記憶體分析工具

在 Windows Store 應用程式和傳統型應用程式中，垃圾收集行程和受控堆積的本質並不相同。 不過，profiler 作者必須注意一些細微的差異。

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC 會建立受控執行緒

進行記憶體分析時，您的 Profiler DLL 通常會建立另一個執行緒，以呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)方法。 這不是新的內容。 但可能會令人驚訝的是，在 Windows Store 應用程式中執行垃圾收集的動作可能會將您的執行緒轉換成受控執行緒（例如，將會為該執行緒建立分析 API ThreadID）。

若要瞭解這項功能的結果，請務必瞭解 CLR 分析 API 所定義的同步和非同步呼叫之間的差異。 請注意，這與 Windows Store 應用程式中非同步呼叫的概念非常不同。 如需詳細資訊，請參閱 blog 文章[為什麼會 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) 。

相關的重點是，您的分析工具所建立之執行緒上的呼叫一律會視為同步，即使這些呼叫是從您的其中一個 Profiler DLL 的[ICorProfilerCallback](icorprofilercallback-interface.md)方法以外的地方進行。 至少，這是用來做為案例的情況。 既然 CLR 已將分析工具的執行緒轉換成 managed 執行緒，因為您呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)，該執行緒就不再被視為分析工具的執行緒。 因此，CLR 會針對該執行緒強制執行更嚴格的定義，亦即呼叫必須源自其中一個分析工具 DLL 的[ICorProfilerCallback](icorprofilercallback-interface.md)方法，才能限定為同步。

這在實務上的意義為何？ 大部分的[ICorProfilerInfo](icorprofilerinfo-interface.md)方法都只能以同步方式呼叫，否則會立即失敗。 因此，如果您的分析工具 DLL 重複使用[ForceGC 方法](icorprofilerinfo-forcegc-method.md)執行緒，以進行通常在分析工具建立的執行緒上進行的其他呼叫（例如， [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)、 [RequestReJIT](icorprofilerinfo4-requestrejit-method.md)或[RequestRevert](icorprofilerinfo4-requestrevert-method.md)），您就會遇到問題. 即使是非同步安全的函式（例如[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) ），從 managed 執行緒呼叫時也有特殊的規則。 （請參閱 @no__t 0Profiler 堆疊演練的 blog 文章：除了 @ no__t-0 以外的基本知識，以取得詳細資訊）。

因此，我們建議您 Profiler DLL 所建立的任何執行緒呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)，都應該*僅*用於觸發 GC，然後回應 gc 回呼的目的。 它不應該呼叫分析 API 來執行其他工作，例如堆疊取樣或卸離。

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

從 .NET Framework 4.5 開始，有新的 GC 回呼[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)，可讓分析工具更完整地取得*相依控制碼*的相關資訊。 這些控制碼可有效地將來源物件的參考新增至目標物件，以進行 GC 存留期管理。 相依控制碼並不是新的，而且以 managed 程式碼撰寫程式的開發人員也能夠在 Windows 8 和 .NET Framework 4.5 之前，使用 <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> 類別來建立自己的相依控制碼。

不過，受控 XAML Windows Store 應用程式現在會大量使用相依的控制碼。 特別是，CLR 會使用它們來協助管理 managed 物件與非受控 Windows 執行階段物件之間的參考迴圈。 這表示，比以往更重要的是，要知道這些相依控制碼的記憶體分析工具，讓它們可以與堆積圖形中的其餘邊緣進行視覺化。 您的分析工具 DLL 應該一起使用[RootReferences2](icorprofilercallback2-rootreferences2-method.md)、 [ObjectReferences](icorprofilercallback-objectreferences-method.md)和[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)來形成堆積圖表的完整視圖。

## <a name="conclusion"></a>結論

您可以使用 CLR 分析 API 來分析在 Windows Store 應用程式中執行的受控碼。 事實上，您可以採用您正在開發的現有 profiler，並進行一些特定的變更，讓它能夠以 Windows Store 應用程式為目標。 您的 Profiler UI 應使用新的 Api，以在偵錯工具模式中啟用 Windows Store 應用程式。 請確定您的 Profiler DLL 只會使用適用于 Windows Store 應用程式的 Api。 分析工具 DLL 和分析工具 UI 之間的通訊機制，應以 Windows Store 應用程式 API 限制來撰寫，並留意適用于 Windows Store 應用程式的限制許可權。 您的分析工具 DLL 應該知道 CLR 如何處理 Winmd，以及垃圾收集行程的行為與 managed 執行緒的不同之處。

## <a name="resources"></a>資源

**Common Language Runtime**

- [分析（非受控 API 參考）](index.md)

- [中繼資料（非受控 API 參考）](../metadata/index.md)

**CLR 與 Windows 執行階段的互動**

- [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Windows 市集應用程式**

- [檔案存取和許可權（Windows 執行階段應用程式](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [取得開發人員授權](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [IPackageDebugSettings 介面](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
