---
title: 撰寫自訂 .NET Core 執行階段主機
description: 了解如何從原生程式碼裝載 .NET Core 執行階段，以支援需要控制 .NET Core 執行階段運作方式的進階案例。
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: 380bfb3aa5e5715fe95e0d7772700bac9ab4a5be
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160980"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>撰寫自訂 .NET Core 主機以從原生程式碼控制 .NET 執行階段

如同所有 Managed 程式碼，.NET Core 應用程式是由主機執行。 該主機會負責啟動執行階段 (包括 JIT 和記憶體回收行程等元件) 及叫用受控進入點。

裝載 .NET Core 執行階段是進階案例，在大多數情況下，由於 .NET Core 建置程序會提供預設主機來執行 .NET Core 應用程式，因此 .NET Core 開發人員不需要擔心裝載相關事宜。 不過在某些特殊情況下，明確裝載 .NET Core 執行階段可能會很有用，像是用來叫用原生處理序中的 Managed 程式碼，或是用來增加對執行階段運作方式的更多控制。

本文概述從機器碼啟動 .NET Core 執行階段及在其中執行受控碼的必要步驟。

## <a name="prerequisites"></a>必要條件

因為主機是原生應用程式，所以本教學課程說明如何建立 c + + 應用程式來裝載 .NET Core。 您將需要 C++ 開發環境 (例如 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 所提供的環境)。

您也需要一個簡單的 .NET Core 應用程式來測試主機，因此您必須安裝 [.NET Core SDK](https://dotnet.microsoft.com/download) 並[建置一個小型的.NET Core 測試應用程式](with-visual-studio.md) (例如 'Hello World' 應用程式)。 由新的 .NET Core 主控台專案範本建立的 'Hello World' 應用程式就已足夠。

## <a name="hosting-apis"></a>裝載 API

有兩個不同的 API 可用來裝載 .NET Core。 本文 (與其相關的 [範例](https://github.com/dotnet/samples/tree/master/core/hosting)) 涵蓋這兩個選項。

* 在 .NET Core 3.0 及更新版本中裝載 .NET Core 執行階段的建議方式，是使用 `nethost` 和 `hostfxr` 程式庫的 API。 這些進入點能處理尋找及設定初始化執行階段的複雜程度，並允許啟動受控應用程式及呼叫靜態受控方法。
* 在 .NET Core 3.0 之前裝載 .NET Core 執行時間的慣用方法是使用 [`coreclrhost.h`](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API。 此 API 會公開函式，以便輕鬆地啟動和停止執行階段，以及叫用受控碼 (無論是透過啟動受控 exe 或藉由呼叫靜態受控方法)。

## <a name="sample-hosts"></a>範例主機

dotnet/samples GitHub 存放庫中提供下列示範教學課程所述步驟的[範例主機](https://github.com/dotnet/samples/tree/master/core/hosting)。 範例中註解清楚地將這些教學課程中的編號步驟與範例中的執行位置建立關聯。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#view-and-download-samples)。

請記住，範例主機是為了用於學習，因此錯誤檢查較不嚴謹，並設計成可讀性比效率更重要。

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>使用和建立主機 `nethost.h``hostfxr.h`

下列步驟詳細說明如何使用 `nethost` 和 `hostfxr` 程式庫來在原生應用程式中啟動 .NET Core 執行階段，並呼叫受控靜態方法。 此 [範例](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) 會使用 `nethost` 隨 .net SDK 安裝的標頭和程式庫，以及 [`coreclr_delegates.h`](https://github.com/dotnet/runtime/blob/master/src/installer/corehost/cli/coreclr_delegates.h) [`hostfxr.h`](https://github.com/dotnet/runtime/blob/master/src/installer/corehost/cli/hostfxr.h) [dotnet/運行](https://github.com/dotnet/runtime) 時間存放庫中和檔案的複本。

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>步驟 1-載入 `hostfxr` 和取得匯出的裝載函數

`nethost` 程式庫會提供用來找出 `hostfxr` 程式庫的 `get_hostfxr_path` 函式。 `hostfxr` 程式庫會公開用來裝載 .NET Core 執行階段的函式。 您可以在 [`hostfxr.h`](https://github.com/dotnet/runtime/blob/master/src/installer/corehost/cli/hostfxr.h) 和 [原生裝載設計檔](https://github.com/dotnet/runtime/blob/master/docs/design/features/native-hosting.md)中找到完整的函式清單。 範例和本教課程會使用下列項目：

* `hostfxr_initialize_for_runtime_config`：初始化主機內容，並準備使用指定的執行時間設定初始化 .NET Core 執行時間。
* `hostfxr_get_runtime_delegate`：取得執行時間功能的委派。
* `hostfxr_close`：關閉主機內容。

`hostfxr` 程式庫是使用 `get_hostfxr_path` 來找到。 系統接著會載入它並擷取其匯出。

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>步驟 2 - 初始化並啟動 .NET Core 執行階段

`hostfxr_initialize_for_runtime_config` 和 `hostfxr_get_runtime_delegate` 函式會使用適用於將載入之受控元件的執行階段設定，來初始化並啟動 .NET Core 執行階段。 `hostfxr_get_runtime_delegate` 函式會被用來取得能允許載入受控組件，並取得針對該組件中靜態方法之函式指標的執行階段委派。

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>步驟 3 - 載入受控組件並取得針對受控方法的函式指標

系統會呼叫執行階段委派來載入受控組件，並取得針對受控方法的函式指標。 該委派需要組件路徑、類型名稱及方法名稱作為輸入，並會傳回可用來叫用受控方法的函式指標。

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

在呼叫執行階段委派期間，透過將 `nullptr` 傳遞為委派類型名稱，範例會針對受控方法使用預設簽章：

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

若要使用不同的簽章，可以在呼叫執行階段委派時指定委派類型名稱。

### <a name="step-4---run-managed-code"></a>步驟 4 - 執行受控程式碼！

原生主機現在可以呼叫受控方法，並向它傳遞所需的參數。

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>使用建立主機 `coreclrhost.h`

下列步驟詳細說明如何使用 `coreclrhost.h` API 在原生應用程式中啟動 .Net Core 執行時間，並呼叫受控靜態方法。 本文件中的程式碼片段會使用一些 Windows 專用的 API，但[完整的範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)會顯示 Windows 和 Linux 兩者的程式碼路徑。

[Unix CoreRun 主機](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun)會顯示更複雜的主機使用範例 `coreclrhost.h` 。

### <a name="step-1---find-and-load-coreclr"></a>步驟 1 - 找到並載入 CoreCLR

.NET Core 執行階段 API 是在 *coreclr.dll* 中 (Windows)、在 *libcoreclr.so* 中 (Linux)，或是在 *libcoreclr.dylib* 中 (macOS)。 裝載 .NET Core 的第一個步驟是載入 CoreCLR 程式庫。 某些主機會探查不同的路徑，或使用輸入參數來尋找程式庫，而其他主機知道要從某個路徑 (例如，主機旁邊或從全機器位置) 進行載入。

一旦找到，就會使用 `LoadLibraryEx` Windows) 上的 (以及 `dlopen` Linux/macOS) 上的 (載入程式庫。

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>步驟 2 - 取得 .NET Core 裝載函式

CoreClrHost 有幾個可用於裝載 .NET Core 的重要方法：

* `coreclr_initialize`：啟動 .NET Core 執行時間，並設定預設 (，且僅) AppDomain。
* `coreclr_execute_assembly`：執行 managed 元件。
* `coreclr_create_delegate`：建立 managed 方法的函式指標。
* `coreclr_shutdown`：關閉 .NET Core 執行時間。
* `coreclr_shutdown_2`： Like `coreclr_shutdown` ，但也會捕獲 managed 程式碼的結束代碼。

載入 CoreCLR 程式庫之後，下一個步驟是使用 `GetProcAddress` Windows) 上的 (或 `dlsym` Linux/macOS) 上的 (來取得這些函式的參考。

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>步驟 3 - 準備執行階段屬性

啟動執行階段之前，必須準備一些屬性來指定行為 (尤其是關於組件載入器)。

常用屬性包括：

* `TRUSTED_PLATFORM_ASSEMBLIES`：這是執行階段預設能夠解析的組件路徑 (在 Windows 上會以 ';' 分隔，而在 Linux 上則以 ':' 分隔) 清單。 某些主機具有硬式編碼資訊清單，其中列出它們可以載入的組件。 其他主機則會在此清單的特定位置 (例如，*coreclr.dll* 旁邊) 放入任何程式庫。
* `APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。 因為主機可以進一步控制使用 TPA 清單載入哪些組件，所以主機最好確定它們預期載入哪些組件，並明確列出這些組件。 但是，如果需要在執行時間進行探查，則這個屬性可以啟用該案例。
* `APP_NI_PATHS`：此清單與 APP_PATHS 類似，不同之處在於其用途是作為探查原生映像的路徑。
* `NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生程式庫時，載入器應探查的路徑清單。
* `PLATFORM_RESOURCE_ROOTS` 這份清單包含在特定文化特性子目錄) 中，用於探查資源附屬元件 (的路徑。

在此範例主機中，只需列出目前目錄中的所有程式庫，即可建構 TPA 清單：

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

由於此範例很簡單，因此它只需要 `TRUSTED_PLATFORM_ASSEMBLIES` 屬性：

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>步驟 4 - 啟動執行階段

`coreclrhost.h` Api 會啟動執行時間，並使用單一呼叫來建立預設 AppDomain。 `coreclr_initialize` 函式會採用基底路徑、名稱和稍早所述的屬性，並透過 `hostHandle` 參數將控制代碼傳回到主機。

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>步驟 5 - 執行受控碼！

執行階段啟動後，主機便可以呼叫受控碼。 這可透過幾種不同的方式來完成。 連結至這個教學課程之範例程式碼使用 `coreclr_create_delegate` 函式來建立靜態受控方法的委派。 此 API 會採用[組件名稱](../../standard/assembly/names.md)、命名空間限定的類型名稱和方法名稱作為輸入，並傳回可用來叫用方法的委派。

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

在此範例中，主機現在可以呼叫 `managedDelegate` 來執行 `ManagedWorker.DoWork` 方法。

或者，`coreclr_execute_assembly` 函式可用來啟動受控可執行檔。 此 API 會採用組件路徑和引數陣列作為輸入參數。 它會載入該路徑中的組件，並叫用其 Main 方法。

```c++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>步驟 6 - 關閉並清除

最後，當主機完成受控碼的執行時，.NET Core 執行階段會使用 `coreclr_shutdown` 或 `coreclr_shutdown_2` 來關閉。

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR 不支援重新初始化或卸載。 請勿再次呼叫 `coreclr_initialize` 或卸載 CoreCLR 程式庫。

## <a name="conclusion"></a>結論
建立主機之後，您可以從命令列執行它，並傳遞主機預期的任何引數，藉以進行測試。 指定主機要執行的 .NET Core 應用程式時，請務必使用 `dotnet build` 所產生的 .dll。 `dotnet publish` 為獨立式應用程式所產生的可執行檔 (.exe 檔案)，其實就是預設 .NET Core 主機 (因此應用程式可在主要情況下從命令列直接啟動)；使用者程式碼會編譯成同名的 DLL。

如果最初無法運作，請仔細檢查主機所預期的位置中是否有可用的 *coreclr.dll* 、所有必要的架構程式庫都在 TPA 清單中，以及 CoreCLR 的位 (32 位或64位) 符合主機的建立方式。

裝載 .NET Core 執行階段是進階案例，許多開發人員並不需要，但對於需要從原生處理序啟動 Managed 程式碼的人員，或需要更能掌控 .NET Core 執行階段行為的人員而言，這項作業可能很實用。
