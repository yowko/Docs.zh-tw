---
title: 撰寫自訂 .NET Core 執行階段主機
description: 了解如何從原生程式碼裝載 .NET Core 執行階段，以支援需要控制 .NET Core 執行階段運作方式的進階案例。
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: 9f45a75d7ec836c14a2285a1707649cc32c2a25c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537544"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>撰寫自訂 .NET Core 主機以從原生程式碼控制 .NET 執行階段

如同所有 Managed 程式碼，.NET Core 應用程式是由主機執行。 該主機會負責啟動執行階段 (包括 JIT 和記憶體回收行程等元件) 及叫用受控進入點。

裝載 .NET Core 執行階段是進階案例，在大多數情況下，由於 .NET Core 建置程序會提供預設主機來執行 .NET Core 應用程式，因此 .NET Core 開發人員不需要擔心裝載相關事宜。 不過在某些特殊情況下，明確裝載 .NET Core 執行階段可能會很有用，像是用來叫用原生處理序中的 Managed 程式碼，或是用來增加對執行階段運作方式的更多控制。

本文概述從機器碼啟動 .NET Core 執行階段及在其中執行受控碼的必要步驟。

## <a name="prerequisites"></a>Prerequisites

因為主機是原生應用程式，所以本教學課程說明如何建立 c + + 應用程式來裝載 .NET Core。 您將需要 C++ 開發環境 (例如 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 所提供的環境)。

您也需要一個簡單的 .NET Core 應用程式來測試主機，因此您必須安裝 [.NET Core SDK](https://dotnet.microsoft.com/download) 並[建置一個小型的.NET Core 測試應用程式](with-visual-studio.md) (例如 'Hello World' 應用程式)。 由新的 .NET Core 主控台專案範本建立的 'Hello World' 應用程式就已足夠。

## <a name="hosting-apis"></a>裝載 API
有三個不同的 API 可用來裝載 .NET Core。 本文 (與其相關的 [範例](https://github.com/dotnet/samples/tree/master/core/hosting)) 涵蓋所有選項。

* 在 .NET Core 3.0 及更新版本中裝載 .NET Core 執行階段的建議方式，是使用 `nethost` 和 `hostfxr` 程式庫的 API。 這些進入點能處理尋找及設定初始化執行階段的複雜程度，並允許啟動受控應用程式及呼叫靜態受控方法。
* 裝載早於 .NET Core 3.0 之 .NET Core 執行階段的建議方式，是使用 [CoreClrHost.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) \(英文\) API。 此 API 會公開函式，以便輕鬆地啟動和停止執行階段，以及叫用受控碼 (無論是透過啟動受控 exe 或藉由呼叫靜態受控方法)。
* .NET Core 也可以使用 [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) 中的 `ICLRRuntimeHost4` 介面進行裝載。 此 API 的運行時間長於 CoreClrHost.h，因此您可能會看到舊版主機使用它。 它仍可運作，且比起 CoreClrHost 更能控制裝載處理序。 不過，在大部分情況下，CoreClrHost.h 目前仍然是慣用方法，因為其 API 更為簡單。

## <a name="sample-hosts"></a>範例主機

dotnet/samples GitHub 存放庫中提供下列示範教學課程所述步驟的[範例主機](https://github.com/dotnet/samples/tree/master/core/hosting)。 範例中註解清楚地將這些教學課程中的編號步驟與範例中的執行位置建立關聯。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#view-and-download-samples)。

請記住，範例主機是為了用於學習，因此錯誤檢查較不嚴謹，並設計成可讀性比效率更重要。

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>使用 NetHost.h 和 HostFxr.h 建立主機

下列步驟詳細說明如何使用 `nethost` 和 `hostfxr` 程式庫來在原生應用程式中啟動 .NET Core 執行階段，並呼叫受控靜態方法。 [範例](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) \(英文\) 會使用搭配 .NET SDK 安裝的 `nethost` 標頭及程式庫，以及來自 [dotnet/core-setup](https://github.com/dotnet/core-setup) \(英文\) 存放庫的 [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) \(英文\) 及 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) \(英文\) 檔案的複本。

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>步驟 1 - 載入 HostFxr 並取得匯出的裝載函式

`nethost` 程式庫會提供用來找出 `hostfxr` 程式庫的 `get_hostfxr_path` 函式。 `hostfxr` 程式庫會公開用來裝載 .NET Core 執行階段的函式。 您可以在 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) 和 [原生裝載設計檔](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md)中找到完整的函式清單。 範例和本教課程會使用下列項目：

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

## <a name="create-a-host-using-coreclrhosth"></a>使用 CoreClrHost.h 建立主機

下列步驟詳細說明如何使用 CoreClrHost.h API，在原生應用程式中啟動 .NET Core 執行階段，並呼叫受控靜態方法。 本文件中的程式碼片段會使用一些 Windows 專用的 API，但[完整的範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)會顯示 Windows 和 Linux 兩者的程式碼路徑。

[Unix CoreRun 主機](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun) \(英文\) 能針對使用 coreclrhost.h 進行裝載，示範更加複雜的現實範例。

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

不同於裝載 API 的 mscoree.h (如下所述)，CoreCLRHost.h API 只需使用單一呼叫，即可啟動執行階段並建立預設的 AppDomain。 `coreclr_initialize` 函式會採用基底路徑、名稱和稍早所述的屬性，並透過 `hostHandle` 參數將控制代碼傳回到主機。

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

## <a name="create-a-host-using-mscoreeh"></a>使用 Mscoree.h 建立主機

如先前所述，CoreClrHost.h 現在是裝載 .NET Core 執行階段的慣用方法。 不過，如果 CoreClrHost.h 介面不足 (比方說，如果需要非標準啟動旗標，或如果預設定義域需要 AppDomainManager)，您仍然可以使用 `ICLRRuntimeHost4` 介面。 這些指示會引導您使用 mscoree.h 來裝載 .NET Core。

[CoreRun 主機](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/corerun) \(英文\) 能針對使用 mscoree.h 進行裝載，示範更加複雜的現實範例。

### <a name="a-note-about-mscoreeh"></a>mscoree.h 的相關注意事項
`ICLRRuntimeHost4` .NET Core 裝載介面定義於 [MSCOREE.IDL](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/inc/MSCOREE.IDL)。 您的主機必須參考此檔案的標頭版本 (mscoree.h)，該檔案會在建置 [.NET Core 執行階段](https://github.com/dotnet/runtime/)時透過 MIDL 產生。 如果您不想要建立 .NET Core 執行時間，mscoree.dll 也可做為 dotnet/執行時間存放庫中 [預先建立的標頭](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/) 。

### <a name="step-1---identify-the-managed-entry-point"></a>步驟 1 - 識別 Managed 進入點
參考必要的標頭 (例如 [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) 和 stdio.h) 之後，.NET Core 主機必須先找出所要使用的 Managed 進入點。 在我們的範例主機中，只要採用主機的第一個命令列引數做為 managed 二進位檔的路徑，就會 `main` 執行其方法。

[!code-cpp[NetCoreHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>步驟 2 - 找到並載入 CoreCLR
.NET Core 執行階段 API 位於 *CoreCLR.dll* (Windows 上)。 若要取得我們的裝載介面 (`ICLRRuntimeHost4`)，您必須找到並載入 *CoreCLR.dll*。 主機會定義尋找 *CoreCLR.dll* 的方式慣例。 某些主機預期此檔案會出現在已知的全機器位置 (例如 *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*)。 其他主機則預期會從主機本身或所要裝載之應用程式旁的位置載入 *CoreCLR.dll*。 不過，其他主機還是可以參考環境變數以尋找程式庫。

在 Linux 或 macOS 上，核心執行時間程式庫分別是*libcoreclr.so*或 *>libcoreclr.dylib。*

我們的範例主機會在一些常見的位置中探查 *CoreCLR.dll*。 一旦找到，就必須透過 `LoadLibrary` (或 `dlopen` Linux/macOS) 載入。

[!code-cpp[NetCoreHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>步驟 3 - 取得 ICLRRuntimeHost4 執行個體
藉 `ICLRRuntimeHost4` 由呼叫 `GetProcAddress` (或 `dlsym` 上的 Linux/macOS) ，然後叫用該函式，即可抓取裝載介面 `GetCLRRuntimeHost` 。

[!code-cpp[NetCoreHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>步驟 4 - 設定啟動旗標並啟動執行階段
準備好 `ICLRRuntimeHost4` 之後，現在可以指定全執行階段啟動旗標並啟動執行階段。 啟動旗標會決定所要使用的記憶體回收行程 (GC) (並行或伺服器)，而不論使用的是單一 AppDomain 或多個 AppDomain；它也會決定 (為了以定義域中性方式載入組件) 所要使用的載入器最佳化原則。

[!code-cpp[NetCoreHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#4)]

呼叫 `Start` 函式以啟動執行階段。

```c++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>步驟 5 - 準備 AppDomain 設定
啟動執行階段之後，我們想要設定 AppDomain。 不過，建立 .NET AppDomain 時必須指定一些選項，因此必須先準備這些選項。

AppDomain 旗標會指定與安全性和 Interop 相關的 AppDomain 行為。 舊版的 Silverlight 主機使用這些設定來沙箱化使用者程式碼，但最新式的 .NET Core 主機則會以完全信任的方式來執行使用者程式碼並啟用 Interop。

[!code-cpp[NetCoreHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#5)]

決定要使用的 AppDomain 旗標之後，必須定義 AppDomain 屬性。 這些屬性是字串的索引鍵/值組。 許多屬性與 AppDomain 載入組件的方式相關。

常見的 AppDomain 屬性包括：

* `TRUSTED_PLATFORM_ASSEMBLIES` 這是在 Windows 和 Linux/) macOS 上分隔的元件路徑清單 (， `;` `:` AppDomain 應該優先載入，並將完全信任授與 (，即使在部分信任的網域) 中也是如此。 此清單可用來包含 'Framework' 組件及其他信任的模組，類似於 .NET Framework 案例中的 GAC。 某些主機會將任何程式庫放在此清單中的 *coreclr.dll* 旁，其他主機則會有針對其用途列出信任組件的硬式編碼資訊清單。
* `APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。 因為主機可以進一步控制使用 TPA 清單載入哪些組件，所以主機最好確定它們預期載入哪些組件，並明確列出這些組件。 但是，如果需要在執行時間進行探查，則這個屬性可以啟用該案例。
* `APP_NI_PATHS`：此清單與 APP_PATHS 非常類似，不同之處在於其用途是作為探查原生影像的路徑。
* `NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生 DLL 時，載入器應探查的路徑清單。
* `PLATFORM_RESOURCE_ROOTS` 這份清單包含在特定文化特性子目錄) 中，用於探查資源附屬元件 (的路徑。

在我們的[簡單範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)中，這些屬性會設定如下：

[!code-cpp[NetCoreHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>步驟 6 - 建立 AppDomain
準備好所有 AppDomain 旗標和屬性之後，即可使用 `ICLRRuntimeHost4::CreateAppDomainWithManager` 來設定 AppDomain。 此函式會選擇性地接受完整組件名稱和類型名稱，以用作定義域的 AppDomain 管理員。 AppDomain 管理員可讓主機控制 AppDomain 行為的某些層面，並可在主機不想直接叫用使用者程式碼時，提供進入點以啟動 Managed 程式碼。

[!code-cpp[NetCoreHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>步驟 7 - 執行 Managed 程式碼！
在 AppDomain 啟動並執行之後，主機現在可以開始執行 Managed 程式碼。 最簡單的做法是使用 `ICLRRuntimeHost4::ExecuteAssembly` 叫用 Managed 組件的進入點方法。 請注意，此函式僅適用於單一定義域案例。

[!code-cpp[NetCoreHost#8](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#8)]

如果 `ExecuteAssembly` 不符合您的主機需求，另一個選擇是使用 `CreateDelegate` 建立靜態 Managed 方法的函式指標。 雖然此做法要求主機必須知道所呼叫的方法簽章 (以便建立函式指標類型)，但允許主機彈性地叫用組件進入點以外的程式碼。 第二個參數中提供的組件名稱為要載入之程式庫的[完整受控組件名稱](../../standard/assembly/names.md)。

```c++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
    domainId,
    L"HW, Version=1.0.0.0, Culture=neutral", // Target managed assembly
    L"ConsoleApplication.Program",           // Target managed type
    L"Main",                                 // Target entry point (static method)
    (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>步驟 8 - 清除
最後，主機應該藉由卸載 AppDomain、停止執行階段並釋放 `ICLRRuntimeHost4` 參考來清除自身。

[!code-cpp[NetCoreHost#9](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#9)]

CoreCLR 不支援卸載。 請勿卸載 CoreCLR 程式庫。

## <a name="conclusion"></a>結論
建置主機之後，您可以從命令列執行主機，並傳遞主機預期的任何引數 (例如要針對 mscoree 範例主機執行的受控應用程式)，藉以進行測試。 指定主機要執行的 .NET Core 應用程式時，請務必使用 `dotnet build` 所產生的 .dll。 `dotnet publish` 為獨立式應用程式所產生的可執行檔 (.exe 檔案)，其實就是預設 .NET Core 主機 (因此應用程式可在主要情況下從命令列直接啟動)；使用者程式碼會編譯成同名的 DLL。

如果最初無法運作，請仔細檢查主機所預期的位置中是否有可用的 *coreclr.dll* 、所有必要的架構程式庫都在 TPA 清單中，以及 CoreCLR 的位 (32 位或64位) 符合主機的建立方式。

裝載 .NET Core 執行階段是進階案例，許多開發人員並不需要，但對於需要從原生處理序啟動 Managed 程式碼的人員，或需要更能掌控 .NET Core 執行階段行為的人員而言，這項作業可能很實用。
