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
ms.openlocfilehash: 04b4b529a5a1adaa40e804988dee506942c863c4
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440076"
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR 分析工具和 Windows 市集應用程式

本主題討論當您撰寫診斷工具來分析在 Windows Store 應用程式內執行的 managed 程式碼時，所需考慮的事項。 它也提供修改現有開發工具的指導方針，以便在您針對 Windows Store 應用程式執行時繼續運作。 若要瞭解這項資訊，最好的做法是，如果您已熟悉 Common Language Runtime 分析 API，則您已在可針對 Windows 傳統型應用程式正確執行的診斷工具中使用此 API，而您現在想要修改工具以針對 Windows Store 應用程式正確執行。

## <a name="introduction"></a>簡介

如果您將它放在簡介段落之後，您就會熟悉 CLR 分析 API。 您已經撰寫一個可針對受管理的桌面應用程式順利運作的診斷工具。 現在您會想要怎麼做，讓您的工具可以搭配受控的 Windows Store 應用程式運作。 或許您已經試過這項工作，併發現它不是一項簡單的工作。 事實上，所有工具開發人員都可能不會察覺到許多考慮。 例如：

- Windows Store 應用程式會在具有嚴格減少許可權的內容中執行。

- 相較于傳統的受控模組，Windows 中繼資料檔案有獨特的特性。

- 當互動性下降時，Windows Store 應用程式習慣自行暫停。

- 基於各種原因，您的處理序間通訊機制可能不再適用。

本主題列出您需要注意的事項，以及如何適當地處理它們。

如果您不熟悉 CLR 分析 API，請跳至本主題結尾的資源，以找出更好的簡介資訊。

提供特定 Windows Api 的詳細資料，以及這些 Api 的使用方式，也不在本主題的討論範圍內。 請將此主題視為起點，並參閱 MSDN 以深入瞭解此處參考的任何 Windows Api。

## <a name="architecture-and-terminology"></a>架構和術語

通常，診斷工具具有如下圖所示的架構。 它使用「分析工具」一詞，但是許多這類工具在一般效能或記憶體分析方面，都不是在程式碼涵蓋範圍、模擬物件架構、時間移動偵錯工具、應用程式監視等範圍內。 為了簡單起見，本主題將繼續以分析工具的形式來參考這些工具。

本主題中會使用下列術語：

**應用程式**

這是分析工具所分析的應用程式。 一般來說，此應用程式的開發人員現在會流量分析工具來協助診斷應用程式的問題。 傳統上，此應用程式會是 Windows 桌面應用程式，但在本主題中，我們會查看 Windows Store 應用程式。

**Profiler DLL**

這是載入至所分析應用程式之進程空間的元件。 此元件（也稱為分析工具「代理程式」）會在 (2、3等 ) 介面上執行[ICorProfilerCallback](icorprofilercallback-interface.md)的[ICorProfilerCallback 介面](icorprofilercallback-interface.md)，並取用[ICorProfilerInfo](icorprofilerinfo-interface.md) (2、3等 ) 介面，以收集分析之應用程式的相關資料，並可能會修改應用程式行為的各個層面。

**Profiler UI**

這是分析工具使用者與之互動的桌面應用程式。 它負責向使用者顯示應用程式狀態，並讓使用者能夠控制已分析之應用程式的行為。 此元件一律會在自己的進程空間中執行，與所分析應用程式的進程空間分開。 分析工具 UI 也可以做為「附加觸發程式」，這是呼叫 [ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md) 方法的程式，可在分析工具 dll 未于啟動時載入的情況下，讓分析的應用程式載入 profiler dll。

> [!IMPORTANT]
> 您的分析工具 UI 應該保留 Windows 傳統型應用程式，即使它是用來控制和報告 Windows Store 應用程式。 不希望能夠在 Windows 市集中封裝和送出您的診斷工具。 您的工具需要進行 Windows Store 應用程式無法完成的作業，而且其中許多專案都位於分析工具 UI 內。

在本檔中，範例程式碼假設：

- 您的分析工具 DLL 是以 c + + 撰寫，因為它必須是原生 DLL，依據 CLR 分析 API 的需求。

- 您的 Profiler UI 是以 c # 撰寫。 這並不是必要的，但因為分析工具 UI 程式的語言沒有任何需求，所以為何無法挑選簡潔又簡單的語言？

### <a name="windows-rt-devices"></a>Windows RT 裝置

Windows RT 的裝置會受到大量鎖定。 協力廠商分析工具只會在這類裝置上載入。 本檔著重于 Windows 8 電腦。

## <a name="consuming-windows-runtime-apis"></a>使用 Windows 執行階段 Api

在下列各節所討論的一些案例中，您的分析工具 UI 傳統型應用程式必須使用一些新的 Windows 執行階段 Api。 您會想要參閱檔，瞭解哪些 Windows 執行階段 Api 可從桌面應用程式使用，以及從桌面應用程式和 Windows Store 應用程式呼叫時，其行為是否不同。

如果您的分析工具 UI 是以 managed 程式碼撰寫，則您需要執行幾個步驟，才能輕鬆使用這些 Windows 執行階段 Api。 如需詳細資訊，請參閱 [受管理的桌面應用程式和 Windows 執行階段](/previous-versions/windows/apps/jj856306(v=win.10)) 文章。

## <a name="loading-the-profiler-dll"></a>載入 Profiler DLL

本節說明 Profiler UI 如何讓 Windows Store 應用程式載入 Profiler DLL。 本節中討論的程式碼屬於您的分析工具 UI 傳統型應用程式，因此需要使用適用于桌面應用程式的 Windows Api，但不一定是 Windows Store 應用程式的安全。

分析工具 UI 會以兩種方式，將您的 Profiler DLL 載入至應用程式的進程空間：

- 在應用程式啟動時，由環境變數所控制。

- 藉由呼叫 [ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md) 方法，在啟動完成之後附加至應用程式。

您的第一個障礙是將啟動載入器 DLL 和附加元件載入工具，以在 Windows Store 應用程式中正常運作。 這兩種形式的載入都會共用常見的一些特殊考慮，讓我們開始使用它們。

### <a name="common-considerations-for-startup-and-attach-loads"></a>啟動和附加載入的一般考慮

**簽署 Profiler DLL**

當 Windows 嘗試載入 Profiler DLL 時，它會驗證您的分析工具 DLL 是否已正確簽署。 如果沒有，載入預設會失敗。 作法有二：

- 確定您的 Profiler DLL 已簽署。

- 請告訴您的使用者必須先在其 Windows 8 電腦上安裝開發人員授權，才能使用您的工具。 這可以從 Visual Studio 自動完成，也可以從命令提示字元手動完成。 如需詳細資訊，請參閱 [取得開發人員授權](/previous-versions/windows/apps/hh974578(v=win.10))。

**檔案系統許可權**

Windows Store 應用程式必須有從檔案系統上 residesBy 預設值的位置載入和執行 Profiler DLL 的許可權，Windows Store 應用程式在大部分的目錄上沒有這類許可權，而且嘗試載入分析工具 DLL 的任何失敗都將會在 Windows 應用程式事件記錄檔中產生專案，如下所示：:

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

一般而言，Windows Store 應用程式只允許存取磁片上一組有限的位置。 每個 Windows Store 應用程式都可以存取自己的應用程式資料檔案夾，以及檔案系統中的一些其他區域，以授與所有 Windows Store 應用程式的存取權。 最好將程式檔或程式檔中的 Profiler DLL 及其相依性安裝 (x86) ，因為所有的 Windows Store 應用程式都有預設的 [讀取] 和 [執行] 許可權。

### <a name="startup-load"></a>啟動載入

一般來說，在傳統型應用程式中，您的分析工具 UI 會藉由初始化包含所需 CLR 分析 API 環境變數的環境區塊，來提示您分析工具 DLL 的啟動載入 (例如、、 `COR_PROFILER` `COR_ENABLE_PROFILING` 和 `COR_PROFILER_PATH`) ，然後使用該環境區塊建立新的進程。 這同樣適用于 Windows Store 應用程式，但不同的機制也是如此。

**未提高許可權執行**

如果進程嘗試產生 Windows Store 應用程式進程 B，進程 A 應該在中完整性層級執行，而不是在高完整性層級上執行， (也就是不會提高) 的許可權。 這表示您的分析工具 UI 應該以中度的完整性層級執行，或者必須在中等完整性層級產生另一個桌面進程，以負責啟動 Windows Store 應用程式。

**選擇要分析的 Windows Store 應用程式**

首先，您會想要要求分析工具使用者啟動哪個 Windows Store 應用程式。 若為傳統型應用程式，您可能會顯示檔案流覽對話方塊，而且使用者會尋找並選取 .exe 檔案。 但 Windows Store 應用程式不同，而使用 [流覽] 對話方塊並不合理。 相反地，最好是向使用者顯示安裝的 Windows Store 應用程式清單，讓該使用者從中選取。

您可以使用 <xref:Windows.Management.Deployment.PackageManager> 類別來產生這份清單。 `PackageManager` 是適用于桌面應用程式的 Windows 執行階段類別，事實上它 *只* 適用于桌面應用程式。

下列程式碼範例取自以 c # 撰寫為傳統型應用程式的假想分析工具 UI，會使用 `PackageManager` 來產生 Windows 應用程式清單：

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**指定自訂環境區塊**

新的 COM 介面 [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)可讓您自訂 Windows Store 應用程式的執行行為，讓某些形式的診斷變得更容易。 其中一個方法（ [EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)）可讓您在啟動時，將環境區塊傳遞給 Windows Store 應用程式，以及其他有用的效果，例如停用自動處理常式擱置。 環境區塊很重要，因為這是您需要指定環境變數 (`COR_PROFILER` 、 `COR_ENABLE_PROFILING` 和 `COR_PROFILER_PATH)`) CLR 用來載入 Profiler DLL 的位置。

請考慮下列程式碼片段：

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

有幾個您必須正確的專案：

- `packageFullName` 可以在逐一查看封裝和抓取時進行判斷 `package.Id.FullName` 。

- `debuggerCommandLine` 有點有趣。 為了將自訂環境區塊傳遞給 Windows Store 應用程式，您必須撰寫自己的簡單虛擬偵錯工具。 Windows 會使用類似下列範例的命令列來啟動您的偵錯工具，以產生暫停的 Windows Store 應用程式，然後附加您的偵錯工具：

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     其中， `-p 1336` 表示 Windows Store 應用程式具有處理序識別碼1336， `-tid 1424` 表示執行緒識別碼1424是擱置的執行緒。 您的虛擬偵錯工具會從命令列剖析 ThreadID、繼續該執行緒，然後結束。

     以下是執行此作業的一些 c + + 程式碼範例 (請務必新增錯誤檢查！ ) ：

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

     您必須將此虛擬偵錯工具部署為診斷工具安裝的一部分，然後在參數中指定這個偵錯工具的路徑 `debuggerCommandLine` 。

**啟動 Windows Store 應用程式**

Windows Store 應用程式的啟動時間終於到達了。 如果您已經試過這項作業，您可能已經注意到 [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) 不是您建立 Windows Store 應用程式進程的方式。 相反地，您必須使用 [IApplicationActivationManager：： ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) 方法。 若要這樣做，您必須取得您要啟動之 Windows Store 應用程式的應用程式使用者模型識別碼。 這表示您必須透過資訊清單執行一點深入探討。

反復查看套件時 (請參閱) 先前的 [啟動載入](#startup-load) 區段中的「選擇要分析的 Windows Store 應用程式」，您會想要抓取目前套件資訊清單中包含的應用程式集：

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

是，一個封裝可以有多個應用程式，而每個應用程式都有自己的應用程式使用者模型識別碼。 因此，您會想要詢問使用者要分析的應用程式，並從該特定應用程式抓取應用程式使用者模型識別碼：

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

最後，您現在已擁有啟動 Windows Store 應用程式所需的內容：

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**請記得呼叫 DisableDebugging**

當您呼叫 [IPackageDebugSettings：： EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)時，您所做的承諾會藉由呼叫 [IPackageDebugSettings：:D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) 方法自行清除，因此請務必在分析會話結束時執行此動作。

### <a name="attach-load"></a>附加負載

當分析工具 UI 想要將其 Profiler DLL 附加至已經開始執行的應用程式時，它會使用 [ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)。 這同樣適用于 Windows Store 應用程式。 但除了先前所列的一般考慮之外，請確定目標 Windows Store 應用程式未暫停。

**EnableDebugging**

如同啟動載入，請呼叫 [IPackageDebugSettings：： EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) 方法。 您不需要它來傳遞環境區塊，但您需要其中一個其他功能：停用自動進程擱置。 否則，當分析工具 UI 呼叫 [AttachProfiler](iclrprofiling-attachprofiler-method.md)時，目標 Windows Store 應用程式可能會被擱置。 事實上，如果使用者現在與您的分析工具 UI 互動，而且 Windows Store 應用程式在任何使用者的畫面上都不在使用中，則可能會發生這種情況。 而且，如果 Windows Store 應用程式已暫止，它將無法回應 CLR 傳送給它以附加分析工具 DLL 的任何信號。

因此，您會想要執行如下所示的內容：

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

這與您在啟動載入案例中所做的相同呼叫相同，不同之處在于您未指定偵錯工具命令列或環境區塊。

**DisableDebugging**

在程式碼剖析會話完成時，請記得一律呼叫 [IPackageDebugSettings：:D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) 。

## <a name="running-inside-the-windows-store-app"></a>在 Windows Store 應用程式內執行

因此，Windows Store 應用程式終於載入了 Profiler DLL。 現在，您的分析工具 DLL 必須教授如何以 Windows Store 應用程式所需的不同規則來播放，包括允許哪些 Api，以及如何以降低的許可權執行。

### <a name="stick-to-the-windows-store-app-apis"></a>前往 Windows Store 應用程式 Api

當您流覽 Windows API 時，您會發現每個 API 都記載為適用于桌面應用程式、Windows Store 應用程式或兩者。 例如， [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)函式檔的 [ **需求** ] 區段指出此函式僅適用于桌面應用程式。 相反地， [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) 函式適用于桌面應用程式和 Windows Store 應用程式。

開發 Profiler DLL 時，請將它視為 Windows Store 應用程式，並只使用 Windows Store 應用程式所記載的 Api。 分析您的相依性 (例如，您可以 `link /dump /imports` 針對分析工具 DLL 執行以 audit) ，然後搜尋檔以查看哪些相依性正常，哪些不是。 在大多數情況下，您的違規可以藉由將其取代為安全 (的較新形式的 API 來修正，例如，將 [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) 取代為 [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)) 。

您可能會注意到，分析工具 DLL 會呼叫僅適用于桌面應用程式的某些 Api，但即使您的 Profiler DLL 是在 Windows 市集中應用程式中載入，它們仍可正常運作。 請注意，將任何未記載的 API 載入至 Windows Store 應用程式處理常式時，會在您的 Profiler DLL 中使用任何未記載的 API：

- 在 Windows Store 應用程式執行所在的唯一內容中呼叫這類 Api 時，並不保證可正常運作。

- 從不同的 Windows Store 應用程式處理常式中呼叫這類 Api 時，可能無法一致地運作。

- 這類 Api 可能會在目前 Windows 版本的 Windows Store 應用程式中正常運作，但在未來的 Windows 版本中可能會中斷或停用。

最佳建議是修正您的所有違規，並避免風險。

您可能會發現，在沒有特定 API 的情況下，您絕對不能這樣做，而且找不到適用于 Windows Store 應用程式的取代。 在這種情況下，至少：

- 測試、測試、測試使用該 API 時的 daylights。

- 瞭解 API 可能會在未來的 Windows 版本中，從 Windows Store 應用程式內部呼叫，突然中斷或消失。 這不會被視為 Microsoft 的相容性問題，而且支援您的使用方式不會是優先考慮。

### <a name="reduced-permissions"></a>降低許可權

這不在本主題的討論範圍內，可列出 Windows Store 應用程式許可權與傳統型應用程式不同的所有方式。 但是，每次您的 Profiler DLL (載入至 Windows Store 應用程式時，相較于桌面應用程式) 嘗試存取任何資源，其行為會有所不同。 檔案系統是最常見的範例。 磁片上有幾個位置可供指定的 Windows Store 應用程式存取 (請參閱 [ (Windows 執行階段應用程式) 的檔案存取和許可權](/previous-versions/windows/apps/hh967755(v=win.10)) ，而且您的分析工具 DLL 會受到相同的限制。 徹底測試您的程式碼。

### <a name="inter-process-communication"></a>內含式通訊

如本文開頭的圖表所示，您的 Profiler DLL (載入至 Windows Store 應用程式的進程空間) 可能需要與您的分析工具 UI 進行通訊， (在個別的桌面應用程式進程空間中執行) 透過您自己的自訂處理序間通訊 (IPC) 通道。 分析工具 UI 會將信號傳送給 Profiler DLL 以修改其行為，而分析工具 DLL 會將資料從已分析的 Windows Store 應用程式傳送回分析工具 UI，以進行後置處理，並顯示給 profiler 使用者。

大部分的分析工具都必須以這種方式運作，但是當您的 Profiler DLL 載入至 Windows Store 應用程式時，您的 IPC 機制選擇會更受限制。 例如，具名管道不是 Windows Store app SDK 的一部分，因此無法使用。

當然，檔案仍在使用中，雖然更有限制。 也可以使用事件。

**透過檔案進行通訊**

大部分的資料可能會透過檔案在分析工具 DLL 和 Profiler UI 之間傳遞。 關鍵是挑選您的分析工具 DLL 在 Windows Store 應用程式內容中 (的檔案位置) 和 Profiler UI 具有的讀取和寫入存取權。 例如，暫存資料夾路徑是您分析工具 DLL 和 Profiler UI 可以存取的位置，但是沒有其他的 Windows Store 應用程式套件可以存取 (因此會防護您從其他 Windows Store 應用程式套件) 記錄的任何資訊。

分析工具 UI 和 Profiler DLL 都可以獨立判斷此路徑。 當您的分析工具 UI 逐一查看為目前使用者安裝的所有套件時 (請參閱稍早) 的範例程式碼，取得類別的存取權， `PackageId` 該類別可讓您使用類似于此程式碼片段的程式碼來衍生暫存資料夾路徑。  (為一律，為了簡潔起見，會省略錯誤檢查。 ) 

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

同時，分析工具 DLL 可以進行相同的作業，不過使用 ApplicationData 屬性可以更輕鬆地取得 <xref:Windows.Storage.ApplicationData> 類別。 [ApplicationData.Current](xref:Windows.Storage.ApplicationData.Current%2A)

**透過事件進行通訊**

如果您想要在分析工具 UI 和 Profiler DLL 之間進行簡單的信號語義，您可以使用 Windows Store 應用程式內的事件，以及桌面應用程式。

您可以從程式碼剖析工具 DLL 呼叫 [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) 函式，使用您喜歡的任何名稱來建立名為的事件。 例如：

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

您的分析工具 UI 接著需要在 Windows Store 應用程式的命名空間下找出該名為的事件。 例如，您的分析工具 UI 可能會呼叫 [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)，並將事件名稱指定為

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>` 是 Windows Store 應用程式的 AppContainer SID。 本主題的先前章節示範如何逐一查看針對目前使用者所安裝的封裝。 從該範例程式碼中，您可以取得 packageId。 從 packageId，您可以 `<acSid>` 使用類似下列的程式碼來取得：

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>沒有關機通知

在 Windows Store 應用程式內執行時，分析工具 DLL 不應依賴 [ICorProfilerCallback：： Shutdown](icorprofilercallback-shutdown-method.md) 或甚至是 [DllMain](/windows/desktop/Dlls/dllmain) (與 `DLL_PROCESS_DETACH`) 呼叫，以通知分析工具 dll Windows Store 應用程式即將結束。 事實上，您應該預期永遠不會呼叫它們。 在過去，許多分析工具 Dll 都已使用這些通知做為方便的位置，可將快取排清至磁片、關閉檔案、將通知傳送回分析工具 UI 等等。但現在您的 Profiler DLL 必須以不同的方式組織。

分析工具 DLL 應記錄資訊。 基於效能考慮，您可能會想要在記憶體中批次處理資訊，並在批次成長的大小超過某個臨界值時將其排清到磁片。 但假設任何尚未排清到磁片的資訊都可能遺失。 這表示您會想要明智地挑選您的閾值，並且必須強化分析工具 UI，才能處理分析工具 DLL 所寫入的不完整資訊。

## <a name="windows-runtime-metadata-files"></a>Windows 執行階段中繼資料檔案

本檔的範圍外，會詳細說明 (WinMD) 檔 Windows 執行階段的中繼資料。 當您分析工具 DLL 正在分析的 Windows Store 應用程式載入 WinMD 檔案時，此區段僅限於 CLR 分析 API 的回應方式。

### <a name="managed-and-non-managed-winmds"></a>受控和非受控 Winmd

如果開發人員使用 Visual Studio 建立新的 Windows 執行階段元件專案，則該專案的組建會產生 WinMD 檔案，該檔案會描述 (開發人員所撰寫的中繼資料、類別、介面 ) 等的類型描述。 如果此專案是以 c # 或 Visual Basic 撰寫的 managed 語言專案，則相同的 WinMD 檔案也會包含這些類型的實 (表示它包含從開發人員的原始程式碼) 編譯的所有 IL。 這類檔案稱為 managed WinMD 檔案。 這些都很有趣，因為它們同時包含 Windows 執行階段中繼資料和基礎執行。

相反地，如果開發人員建立 c + + 的 Windows 執行階段元件專案，則該專案的組建會產生只包含中繼資料的 WinMD 檔案，而且會將該執行編譯成不同的原生 DLL。 同樣地，隨附于 Windows SDK 中的 WinMD 檔案只包含中繼資料，並編譯成獨立的原生 Dll （隨附于 Windows 的一部分）。

下列資訊適用于包含中繼資料和實作為的 managed Winmd，以及僅包含中繼資料的非受控 Winmd。

### <a name="winmd-files-look-like-clr-modules"></a>WinMD 檔案看起來像 CLR 模組

至於 CLR 的考慮，所有 WinMD 檔案都是模組。 因此，CLR 分析 API 會在 WinMD 檔案載入時告訴 Profiler DLL，以及其 ModuleIDs 的方式，與其他受控模組的方式相同。

分析工具 DLL 可以藉由呼叫[ICorProfilerInfo3：： GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)方法，並檢查 COR_PRF_MODULE_WINDOWS_RUNTIME 旗標的 output 參數，來區別其他模組的 WinMD 檔案 `pdwModuleFlags` 。 [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md)  (只有在 ModuleID 代表 WinMD 時，才會設定此設定。 ) 

### <a name="reading-metadata-from-winmds"></a>從 Winmd 讀取中繼資料

WinMD 檔案（如一般模組）包含可透過 [中繼資料 api](../metadata/index.md)讀取的中繼資料。 不過，當 CLR 讀取 WinMD 檔案時，CLR 會將 Windows 執行階段型別對應到 .NET Framework 型別，讓以 managed 程式碼進行程式設計和取用 WinMD 檔案的開發人員可以有更自然的程式設計經驗。 如需這些對應的一些範例，請參閱 [.NET Framework 支援 Windows Store 應用程式和 Windows 執行階段](../../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。

如此一來，當分析工具使用中繼資料 Api 時，您的分析工具會取得：原始 Windows 執行階段視圖或對應的 .NET Framework 視圖？  答案：由您負責。

當您在 WinMD 上呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)方法來取得中繼資料介面（例如[IMetaDataImport](../metadata/imetadataimport-interface.md)）時，您可以選擇在參數[ofNoTransform](../metadata/coropenflags-enumeration.md)中設定 ofNoTransform `dwOpenFlags` 來關閉此對應。 否則，預設會啟用對應。 分析工具通常會讓對應保持啟用狀態，讓分析工具 DLL 從 WinMD 中繼資料取得的字串 (例如，) 類型的名稱將會對分析工具使用者感到陌生且自然。

### <a name="modifying-metadata-from-winmds"></a>修改 Winmd 的中繼資料

不支援在 Winmd 中修改中繼資料。 如果您針對 WinMD 檔案呼叫 [ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) 方法，並在參數中指定 [ofWrite](../metadata/coropenflags-enumeration.md) `dwOpenFlags` 或要求可寫入的中繼資料介面（例如 [IMetaDataEmit](../metadata/imetadataemit-interface.md)）， [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) 將會失敗。 這對 IL 重寫分析工具特別重要，因為這需要修改中繼資料以支援其檢測 (例如，將 AssemblyRefs 或新方法) 。 因此，您應該檢查上一節中所討論的 [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) 第一個 () 並避免在這類別模組上要求可寫入的中繼資料介面。

### <a name="resolving-assembly-references-with-winmds"></a>使用 Winmd 解析元件參考

許多分析工具需要手動解析中繼資料參考，以協助檢測或類型檢查。 這類分析工具必須知道 CLR 如何解析指向 Winmd 的元件參考，因為這些參考的解析方式與標準元件參考完全不同。

## <a name="memory-profilers"></a>記憶體分析工具

在 Windows Store 應用程式和傳統型應用程式中，垃圾收集行程和受控堆積本質上並不相同。 不過，profiler 作者必須留意一些微妙的差異。

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC 會建立受控執行緒

進行記憶體分析時，分析工具 DLL 通常會建立要呼叫 [ForceGC 方法](icorprofilerinfo-forcegc-method.md) 方法的個別執行緒。 這是新功能。 但可能會令人驚訝的是，在 Windows Store 應用程式中進行垃圾收集的動作可能會將您的執行緒轉換成 managed 執行緒 (例如，將會為該執行緒) 建立分析 API ThreadID。

若要瞭解這項功能的後果，請務必瞭解同步和非同步呼叫之間的差異，如 CLR 分析 API 所定義。 請注意，這與 Windows Store 應用程式中的非同步呼叫概念非常不同。 如需詳細資訊，請參閱 blog 文章的 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) 。

相關的重點是，在分析工具所建立的執行緒上所進行的呼叫一律會被視為同步，即使這些呼叫是從程式碼剖析工具 DLL 的其中一個 [ICorProfilerCallback](icorprofilercallback-interface.md) 方法以外的地方進行。 至少就是這種情況。 既然 CLR 已將您的分析工具執行緒轉換成 managed 執行緒，因為您呼叫 [ForceGC 方法](icorprofilerinfo-forcegc-method.md)，該執行緒不再被視為 profiler 的執行緒。 如此一來，CLR 會強制較嚴格的定義做為該執行緒的同步，也就是說，呼叫必須來自您分析工具 DLL 的其中一個 [ICorProfilerCallback](icorprofilercallback-interface.md) 方法，才能限定為同步。

這在實務上的意義為何？ 大部分的 [ICorProfilerInfo](icorprofilerinfo-interface.md) 方法僅安全地以同步方式呼叫，並且會立即失敗。 因此，如果您的分析工具 DLL 重複使用您的 [ForceGC 方法](icorprofilerinfo-forcegc-method.md) 執行緒進行通常在分析工具建立的執行緒上進行的其他呼叫 (例如， [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)、 [RequestReJIT](icorprofilerinfo4-requestrejit-method.md)或 [RequestRevert](icorprofilerinfo4-requestrevert-method.md)) ，您就會遇到問題。 即使是非同步安全的函式（例如 [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) ），也會在從 managed 執行緒呼叫時具有特殊的規則。 如需詳細資訊， (查看 blog 文章分析工具 [堆疊逐步解說：基本和](/archive/blogs/davbr/profiler-stack-walking-basics-and-beyond) 其他資訊。 ) 

因此，我們建議您分析工具 DLL 所建立的任何執行緒呼叫 [ForceGC 方法](icorprofilerinfo-forcegc-method.md) ， *只能* 用來觸發 GC，然後回應 gc 回呼。 它不應該呼叫分析 API 來執行其他工作，例如堆疊取樣或卸離。

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

從 .NET Framework 4.5 開始，有一個新的 GC 回呼 [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)，可讓分析工具更完整的 *相依控制碼* 相關資訊。 由於 GC 存留期管理的目的，這些處理常式可有效地將來源物件的參考新增至目標物件。 相依的控制碼不是新的，而且在 managed 程式碼中撰寫程式的開發人員可以使用類別來建立自己的相依控制碼， <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> 即使在 Windows 8 和 .NET Framework 4.5。

不過，managed XAML Windows Store 應用程式現在會大量使用相依的控制碼。 尤其是，CLR 會使用它們來協助管理 managed 物件與非受控 Windows 執行階段物件之間的參考迴圈。 這表示，比以往更重要的是，它比以往更重要的是，記憶體分析工具會收到這些相依控制碼的通知，以便與堆積圖形中的其餘邊緣進行視覺化。 分析工具 DLL 應使用 [RootReferences2](icorprofilercallback2-rootreferences2-method.md)、 [ObjectReferences](icorprofilercallback-objectreferences-method.md)和 [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) ，以形成堆積圖形的完整觀點。

## <a name="conclusion"></a>結論

您可以使用 CLR 分析 API 來分析在 Windows Store 應用程式內執行的 managed 程式碼。 事實上，您可以取得正在開發的現有分析工具，並進行一些特定的變更，讓它能夠以 Windows Store 應用程式為目標。 分析工具 UI 應該使用新的 Api，以在偵測模式中啟用 Windows Store 應用程式。 請確定您的分析工具 DLL 只會取用適用于 Windows Store 應用程式的 Api。 分析工具 DLL 和分析工具 UI 之間的通訊機制應以 Windows Store 應用程式 API 限制來撰寫，並留意 Windows Store 應用程式的限制許可權。 分析工具 DLL 應留意 CLR 如何處理 Winmd，以及垃圾收集行程的行為與 managed 執行緒的不同之處。

## <a name="resources"></a>資源

**Common Language Runtime**

- [程式碼剖析 (非受控 API 參考) ](index.md)

- [中繼資料 (非受控 API 參考) ](../metadata/index.md)

**CLR 與 Windows 執行階段的互動**

- [適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Windows 市集應用程式**

- [ (Windows 執行階段應用程式的檔案存取和許可權](/previous-versions/windows/apps/hh967755(v=win.10))

- [取得開發人員授權](/previous-versions/windows/apps/hh974578(v=win.10))

- [IPackageDebugSettings 介面](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
