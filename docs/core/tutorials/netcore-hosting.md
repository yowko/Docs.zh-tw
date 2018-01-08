---
title: "裝載 .NET Core"
description: "從機器碼裝載 .NET Core 執行階段"
keywords: ".NET, .NET Core, 裝載, 裝載 .NET Core"
author: mjrousos
ms.author: mikerou
ms.date: 2/3/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13edec8b-614d-47ed-9e95-ed6d3b94ec0c
ms.workload: dotnetcore
ms.openlocfilehash: 2f421c72e8099a328fbc255d51f77a9cd0724e58
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="hosting-net-core"></a>裝載 .NET Core

如同所有 Managed 程式碼，.NET Core 應用程式是由主機執行。 該主機會負責啟動執行階段 (包括 JIT 和記憶體回收行程等元件)、建立 AppDomain 及叫用 Managed 進入點。

裝載 .NET Core 執行階段是進階案例，在大多數情況下，由於 .NET Core 建置程序會提供預設主機來執行 .NET Core 應用程式，因此 .NET Core 開發人員不需要擔心裝載相關事宜。 不過在某些特殊情況下，明確裝載 .NET Core 執行階段可能會很有用，像是用來叫用原生處理序中的 Managed 程式碼，或是用來增加對執行階段運作方式的更多控制。

本文概述從機器碼啟動 .NET Core 執行階段、建立初始應用程式定義域 (<xref:System.AppDomain>) 及在其中執行 Managed 程式碼的必要步驟。

## <a name="prerequisites"></a>必要條件

由於主機是原生應用程式，因此本教學課程將說明如何建構 C++ 應用程式以裝載 .NET Core。 您將需要 C++ 開發環境 (例如 [Visual Studio](https://www.visualstudio.com/downloads/) 所提供的環境)。

您也需要一個簡單的 .NET Core 應用程式來測試主機，因此您必須安裝 [.NET Core SDK](https://www.microsoft.com/net/core) 並[建置一個小型的.NET Core 測試應用程式](../../core/tutorials/with-visual-studio.md) (例如 'Hello World' 應用程式)。 由新的 .NET Core 主控台專案範本建立的 'Hello World' 應用程式就已足夠。

本教學課程及其相關範例會建置 Windows 主機；請參閱本文結尾有關裝載於 UNIX 的注意事項。

## <a name="creating-the-host"></a>建立主機

dotnet/docs GitHub 存放庫中提供示範本文所述步驟的[範例主機](https://github.com/dotnet/docs/tree/master/samples/core/hosting)。 範例 *host.cpp* 檔案中的註解清楚地將本教學課程中的編號步驟關聯到範例中的執行位置。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

請記住，範例主機是為了用於學習，因此錯誤檢查較不嚴謹，並設計成可讀性比效率更重要。 如需更多真實世界主機範例，請參閱 [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) 存放庫。 特別是 [CoreRun 主機](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun)，這是適合在讀完較簡單範例之後進行研究的一般用途主機。

### <a name="a-note-about-mscoreeh"></a>mscoree.h 的相關注意事項
主要的 .NET Core 裝載介面 (`ICLRRuntimeHost2`) 定義於 [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL)。 您的主機必須參考此檔案的標頭版本 (mscoree.h)，該檔案會在建置 [.NET Core 執行階段](https://github.com/dotnet/coreclr/)時透過 MIDL 產生。 如果不想建置 .NET Core 執行階段，mscoree.h 也會當作 dotnet/coreclr 存放庫中[預先建立的標頭](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc)使用。 您可以在 GitHub 存放庫中找到[建置 .NET Core 執行階段的指示](https://github.com/dotnet/coreclr#building-the-repository)。 

### <a name="step-1---identify-the-managed-entry-point"></a>步驟 1 - 識別 Managed 進入點
參考必要的標頭 (例如 [mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) 和 stdio.h) 之後，.NET Core 主機必須先找出所要使用的 Managed 進入點。 在我們的範例主機中，只要將第一個命令列引數傳遞至主機作為 Managed 二進位檔 (將執行其 `main` 方法) 的路徑，即可完成此作業。

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>步驟 2 - 找到並載入 CoreCLR.dll
.NET Core 執行階段 API 位於 *CoreCLR.dll* (Windows 上)。 若要取得我們的裝載介面 (`ICLRRuntimeHost2`)，您必須找到並載入 *CoreCLR.dll*。 主機會定義尋找 *CoreCLR.dll* 的方式慣例。 某些主機預期此檔案會出現在已知的全機器位置 (例如 %programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0)。 其他主機則預期會從主機本身或所要裝載之應用程式旁的位置載入 *CoreCLR.dll*。 不過，其他主機還是可以參考環境變數以尋找程式庫。

在 Linux 或 Mac 上，Core 執行階段程式庫分別是 *libcoreclr.so* 或 *libcoreclr.dylib*。

我們的範例主機會在一些常見的位置中探查 *CoreCLR.dll*。 找到後，必須透過 `LoadLibrary` (若是 Linux/Mac 則為 `dlopen`) 載入。

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>步驟 3 - 取得 ICLRRuntimeHost2 執行個體
若要擷取 `ICLRRuntimeHost2` 裝載介面，請在 `GetCLRRuntimeHost` 上呼叫 `GetProcAddress` (若是 Linux/Mac 則為 `dlsym`)，然後叫用該函式。 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>步驟 4 - 設定啟動旗標並啟動執行階段
準備好 `ICLRRuntimeHost2` 之後，現在可以指定全執行階段啟動旗標並啟動執行階段。 啟動旗標會決定所要使用的記憶體回收行程 (GC) (並行或伺服器)，而不論使用的是單一 AppDomain 或多個 AppDomain；它也會決定 (為了以定義域中性方式載入組件) 所要使用的載入器最佳化原則。

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

呼叫 `Start` 函式以啟動執行階段。

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>步驟 5 - 準備 AppDomain 設定
啟動執行階段之後，我們想要設定 AppDomain。 不過，建立 .NET AppDomain 時必須指定一些選項，因此必須先準備這些選項。

AppDomain 旗標會指定與安全性和 Interop 相關的 AppDomain 行為。 舊版的 Silverlight 主機使用這些設定來沙箱化使用者程式碼，但最新式的 .NET Core 主機則會以完全信任的方式來執行使用者程式碼並啟用 Interop。

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

決定要使用的 AppDomain 旗標之後，必須定義 AppDomain 屬性。 這些屬性是字串的索引鍵/值組。 許多屬性與 AppDomain 載入組件的方式相關。

常見的 AppDomain 屬性包括：

* `TRUSTED_PLATFORM_ASSEMBLIES`：這是 AppDomain 應設定載入優先權並授與完全信任 (即使是部分信任的定義域) 的組件路徑清單 (在 Windows 上會以 ';' 分隔，而在 Unix 上則以 ':' 分隔)。 此清單可用來包含 'Framework' 組件及其他信任的模組，類似於 .NET Framework 案例中的 GAC。 某些主機會將任何程式庫放在此清單中的 *coreclr.dll* 旁，其他主機則會有針對其用途列出信任組件的硬式編碼資訊清單。
* `APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。 這些路徑會是使用者組件所在的位置。 在沙箱化 AppDomain 中，從這些路徑載入的組件只會被授與部分信任。 常見的 APP_PATH 路徑包括載入目標應用程式的來源路徑，或使用者資產已知存留的其他位置。
*  `APP_NI_PATHS`：此清單與 APP_PATHS 非常類似，不同之處在於其用途是作為探查原生影像的路徑。
*  `NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生 DLL 時，載入器應探查的路徑清單。
*  `PLATFORM_RESOURCE_ROOTS`：此清單包含要在其中探查資源附屬組件的路徑 (位於文化特性專屬子目錄中)。
*  `AppDomainCompatSwitch`：此字串指定針對沒有明確目標 Framework Moniker (指出組件要執行之架構的組件層級屬性) 的組件，所應使用的相容性 Quirks。 一般而言，這應該設定為 `"UseLatestBehaviorWhenTFMNotSpecified"`，但某些主機可能會想要改為取得舊版 Silverlight 或 Windows Phone 相容性 Quirks。

在我們的[簡單範例主機](https://github.com/dotnet/docs/tree/master/samples/core/hosting)中，這些屬性會設定如下：

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>步驟 6 - 建立 AppDomain
準備好所有 AppDomain 旗標和屬性之後，即可使用 `ICLRRuntimeHost2::CreateAppDomainWithManager` 來設定 AppDomain。 此函式會選擇性地接受完整組件名稱和類型名稱，以用作定義域的 AppDomain 管理員。 AppDomain 管理員可讓主機控制 AppDomain 行為的某些層面，並可在主機不想直接叫用使用者程式碼時，提供進入點以啟動 Managed 程式碼。   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>步驟 7 - 執行 Managed 程式碼！
在 AppDomain 啟動並執行之後，主機現在可以開始執行 Managed 程式碼。 最簡單的做法是使用 `ICLRRuntimeHost2::ExecuteAssembly` 叫用 Managed 組件的進入點方法。 請注意，此函式僅適用於單一定義域案例。

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

如果 `ExecuteAssembly` 不符合您的主機需求，另一個選擇是使用 `CreateDelegate` 建立靜態 Managed 方法的函式指標。 雖然此做法要求主機必須知道所呼叫的方法簽章 (以便建立函式指標類型)，但允許主機彈性地叫用組件進入點以外的程式碼。

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",  // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                  // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>步驟 8 - 清除
最後，主機應該藉由卸載 AppDomain、停止執行階段並釋放 `ICLRRuntimeHost2` 參考來清除自身。

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>關於在 Unix 上裝載 .NET Core
.NET Core 是在 Windows、Linux 和 Mac 作業系統上執行的跨平台產品。 不過如同原生應用程式，不同平台的主機之間會有一些差異。 上述使用 `ICLRRuntimeHost2` 啟動執行階段、建立 AppDomain 及執行 Managed 程式碼的程序，在任何支援的作業系統上都應該正常運作。 不過，由於 mscoree 提出許多 Win32 假設，因此定義於 mscoree.h 的介面可能很難搭配 Unix 平台使用。

為了讓 Unix 平台上的裝載作業更容易，[coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) 中提供由多個非平台相關的裝載 API 包裝函式組成的集合。

您可以在 [UnixCoreRun 主機](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts)中查看使用 coreclrhost.h (而不是直接使用 mscoree.h) 的範例。 從 coreclrhost.h 使用 API 裝載執行階段的步驟，類似於使用 mscoree.h 時的步驟：

1. 識別要執行的 Managed 程式碼 (例如從命令列參數)。 
2. 載入 CoreCLR 程式庫。
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. 使用 `dlsym` 取得 CoreCLR 之 `coreclr_initialize`、`coreclr_create_delegate`、`coreclr_execute_assembly` 和 `coreclr_shutdown` 的函式指標
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. 設定 AppDomain 屬性 (例如 TPA 清單)。 這會與上述 mscoree 工作流程的步驟 5 相同。
5. 使用 `coreclr_initialize` 啟動執行階段並建立 AppDomain。 這也會建立將在未來裝載呼叫中使用的 `hostHandle` 指標。
    1. 請注意，此函式會執行上一個工作流程之步驟 4 和 6 的角色。 
6. 使用 `coreclr_execute_assembly` 或 `coreclr_create_delegate` 執行 Managed 程式碼。 這些函式類似於上一個工作流程的步驟 7 中 mscoree 的 `ExecuteAssembly` 和 `CreateDelegate` 函式。
7. 使用 `coreclr_shutdown` 卸載 AppDomain 並關閉執行階段。 

## <a name="conclusion"></a>結論
建立主機之後，您可以藉由從命令列執行主機，並傳遞主機預期的任何引數 (例如所要執行的 Managed 應用程式)，來進行測試。 指定主機要執行的 .NET Core 應用程式時，請務必使用 `dotnet build` 所產生的 .dll。 針對獨立性應用程式執行 `dotnet publish` 所產生的可執行檔，其實就是預設 .NET Core 主機 (因此應用程式可在主要情況下從命令列直接啟動)；使用者程式碼會編譯成同名的 DLL。 

如果一開始未正常運作，請再確認一次主機預期的位置中有 *coreclr.dll*、所有必要的 Framework 程式庫都在 TPA 清單中，而且 CoreCLR 的位元 (32 或 64 位元) 符合主機的建立方式。

裝載 .NET Core 執行階段是進階案例，許多開發人員並不需要，但對於需要從原生處理序啟動 Managed 程式碼的人員，或需要更能掌控 .NET Core 執行階段行為的人員而言，這項作業可能很實用。 由於 .NET Core 能夠與本身並存執行，因此您甚至可以建立主機，以初始化並啟動多個版本的 .NET Core 執行階段，並在相同處理序的這些執行階段上執行應用程式。 
