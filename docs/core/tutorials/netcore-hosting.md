---
title: 撰寫自訂 .NET Core 執行階段主機
description: 了解如何從原生程式碼裝載 .NET Core 執行階段，以支援需要控制 .NET Core 執行階段運作方式的進階案例。
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: 27717cd68d2ef7c19289a9e06f99bb8767f2f582
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654051"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>撰寫自訂 .NET Core 主機以從原生程式碼控制 .NET 執行階段

如同所有 Managed 程式碼，.NET Core 應用程式是由主機執行。 該主機會負責啟動執行階段 (包括 JIT 和記憶體回收行程等元件) 及叫用受控進入點。

裝載 .NET Core 執行階段是進階案例，在大多數情況下，由於 .NET Core 建置程序會提供預設主機來執行 .NET Core 應用程式，因此 .NET Core 開發人員不需要擔心裝載相關事宜。 不過在某些特殊情況下，明確裝載 .NET Core 執行階段可能會很有用，像是用來叫用原生處理序中的 Managed 程式碼，或是用來增加對執行階段運作方式的更多控制。

本文概述從機器碼啟動 .NET Core 執行階段及在其中執行受控碼的必要步驟。

## <a name="prerequisites"></a>必要條件

由於主機是原生應用程式，因此本教學課程將說明如何建構 C++ 應用程式以裝載 .NET Core。 您將需要 C++ 開發環境 (例如 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 所提供的環境)。

您也需要一個簡單的 .NET Core 應用程式來測試主機，因此您必須安裝 [.NET Core SDK](https://www.microsoft.com/net/core) 並[建置一個小型的.NET Core 測試應用程式](../../core/tutorials/with-visual-studio.md) (例如 'Hello World' 應用程式)。 由新的 .NET Core 主控台專案範本建立的 'Hello World' 應用程式就已足夠。

## <a name="hosting-apis"></a>裝載 API
有兩個不同的 API 可用來裝載 .NET Core。 本文件 (及其相關聯的[範例](https://github.com/dotnet/samples/tree/master/core/hosting)) 涵蓋這兩個選項。

* 裝載 .NET Core 執行階段的慣用方法是使用 [CoreClrHost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) API。 此 API 會公開函式，以便輕鬆地啟動和停止執行階段，以及叫用受控碼 (無論是透過啟動受控 exe 或藉由呼叫靜態受控方法)。
* .NET Core 也可以使用 [mscoree.h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h) 中的 `ICLRRuntimeHost4` 介面進行裝載。 此 API 的運行時間長於 CoreClrHost.h，因此您可能會看到舊版主機使用它。 它仍可運作，且比起 CoreClrHost 更能控制裝載處理序。 不過，在大部分情況下，CoreClrHost.h 目前仍然是慣用方法，因為其 API 更為簡單。

## <a name="sample-hosts"></a>範例主機
dotnet/samples GitHub 存放庫中提供下列示範教學課程所述步驟的[範例主機](https://github.com/dotnet/samples/tree/master/core/hosting)。 範例中註解清楚地將這些教學課程中的編號步驟與範例中的執行位置建立關聯。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

請記住，範例主機是為了用於學習，因此錯誤檢查較不嚴謹，並設計成可讀性比效率更重要。 如需更多真實世界主機範例，請參閱 [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) 存放庫。 特別是 [CoreRun 主機](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) 和 [Unix CoreRun 主機](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun)，這些是適合在讀完較簡單範例之後進行研究的一般用途主機。

## <a name="create-a-host-using-coreclrhosth"></a>使用 CoreClrHost.h 建立主機

下列步驟詳細說明如何使用 CoreClrHost.h API，在原生應用程式中啟動 .NET Core 執行階段，並呼叫受控靜態方法。 本文件中的程式碼片段會使用一些 Windows 專用的 API，但[完整的範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)會顯示 Windows 和 Linux 兩者的程式碼路徑。

### <a name="step-1---find-and-load-coreclr"></a>步驟 1 - 找到並載入 CoreCLR

.NET Core 執行階段 API 是在 *coreclr.dll* 中 (Windows)、在 *libcoreclr.so* 中 (Linux)，或是在 *libcoreclr.dylib* 中 (macOS)。 裝載 .NET Core 的第一個步驟是載入 CoreCLR 程式庫。 某些主機會探查不同的路徑，或使用輸入參數來尋找程式庫，而其他主機知道要從某個路徑 (例如，主機旁邊或從全機器位置) 進行載入。

找到後，便會使用 `LoadLibraryEx` (在 Windows 上) 或 `dlopen` (在 Linux/Mac 上) 載入程式庫。

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>步驟 2 - 取得 .NET Core 裝載函式

CoreClrHost 有幾個可用於裝載 .NET Core 的重要方法：

* `coreclr_initialize`：啟動 .NET Core 執行階段，並設定預設的 (且唯一的) AppDomain。
* `coreclr_execute_assembly`：執行受控組件。
* `coreclr_create_delegate`：建立受控方法的函式指標。
* `coreclr_shutdown`：關閉 .NET Core 執行階段。
* `coreclr_shutdown_2`：如同 `coreclr_shutdown`，但還會擷取受控碼的結束代碼。

載入 CoreCLR 程式庫之後，下一個步驟是使用 `GetProcAddress` (在 Windows 上) 或 `dlsym` (在 Linux/Mac 上) 取得這些函式的參考。

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>步驟 3 - 準備執行階段屬性

啟動執行階段之前，必須準備一些屬性來指定行為 (尤其是關於組件載入器)。

常用屬性包括：

* `TRUSTED_PLATFORM_ASSEMBLIES`：這是執行階段預設能夠解析的組件路徑 (在 Windows 上會以 ';' 分隔，而在 Linux 上則以 ':' 分隔) 清單。 某些主機具有硬式編碼資訊清單，其中列出它們可以載入的組件。 其他主機則會在此清單的特定位置 (例如，*coreclr.dll* 旁邊) 放入任何程式庫。
* `APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。 因為主機可以進一步控制使用 TPA 清單載入哪些組件，所以主機最好確定它們預期載入哪些組件，並明確列出這些組件。 不過，如果需要在執行階段進行探查，此屬性可用於這種情況。
*  `APP_NI_PATHS`：此清單與 APP_PATHS 類似，不同之處在於其用途是作為探查原生映像的路徑。
*  `NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生程式庫時，載入器應探查的路徑清單。
*  `PLATFORM_RESOURCE_ROOTS`：此清單包含要在其中探查資源附屬組件的路徑 (位於文化特性專屬子目錄中)。

在此範例主機中，只需列出目前目錄中的所有程式庫，即可建構 TPA 清單：

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

由於此範例很簡單，因此它只需要 `TRUSTED_PLATFORM_ASSEMBLIES` 屬性：

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>步驟 4 - 啟動執行階段

不同於裝載 API 的 mscoree.h (如下所述)，CoreCLRHost.h API 只需使用單一呼叫，即可啟動執行階段並建立預設的 AppDomain。 `coreclr_initialize` 函式會採用基底路徑、名稱和稍早所述的屬性，並透過 `hostHandle` 參數將控制代碼傳回到主機。

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>步驟 5 - 執行受控碼！

執行階段啟動後，主機便可以呼叫受控碼。 這可透過幾種不同的方式來完成。 連結至這個教學課程之範例程式碼使用 `coreclr_create_delegate` 函式來建立靜態受控方法的委派。 此 API 會採用[組件名稱](../../framework/app-domains/assembly-names.md)、命名空間限定的類型名稱和方法名稱作為輸入，並傳回可用來叫用方法的委派。

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

在此範例中，主機現在可以呼叫 `managedDelegate` 來執行 `ManagedWorker.DoWork` 方法。

或者，`coreclr_execute_assembly` 函式可用來啟動受控可執行檔。 此 API 會採用組件路徑和引數陣列作為輸入參數。 它會載入該路徑中的組件，並叫用其 Main 方法。

```C++
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

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

請記得使用 `FreeLibrary` (在 Windows 上) 或 `dlclose` (在 Linux/Mac 上) 來卸載 CoreCLR 程式庫。

## <a name="create-a-host-using-mscoreeh"></a>使用 Mscoree.h 建立主機

如先前所述，CoreClrHost.h 現在是裝載 .NET Core 執行階段的慣用方法。 不過，如果 CoreClrHost.h 介面不足 (比方說，如果需要非標準啟動旗標，或如果預設定義域需要 AppDomainManager)，您仍然可以使用 `ICLRRuntimeHost4` 介面。 這些指示會引導您使用 mscoree.h 來裝載 .NET Core。

### <a name="a-note-about-mscoreeh"></a>mscoree.h 的相關注意事項
`ICLRRuntimeHost4` .NET Core 裝載介面定義於 [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL)。 您的主機必須參考此檔案的標頭版本 (mscoree.h)，該檔案會在建置 [.NET Core 執行階段](https://github.com/dotnet/coreclr/)時透過 MIDL 產生。 如果不想建置 .NET Core 執行階段，mscoree.h 也會當作 dotnet/coreclr 存放庫中[預先建立的標頭](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc)使用。 您可以在 GitHub 存放庫中找到[建置 .NET Core 執行階段的指示](https://github.com/dotnet/coreclr#building-the-repository)。

### <a name="step-1---identify-the-managed-entry-point"></a>步驟 1 - 識別 Managed 進入點
參考必要的標頭 (例如 [mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) 和 stdio.h) 之後，.NET Core 主機必須先找出所要使用的 Managed 進入點。 在我們的範例主機中，只要將第一個命令列引數傳遞至主機作為 Managed 二進位檔 (將執行其 `main` 方法) 的路徑，即可完成此作業。

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>步驟 2 - 找到並載入 CoreCLR
.NET Core 執行階段 API 位於 *CoreCLR.dll* (Windows 上)。 若要取得我們的裝載介面 (`ICLRRuntimeHost4`)，您必須找到並載入 *CoreCLR.dll*。 主機會定義尋找 *CoreCLR.dll* 的方式慣例。 某些主機預期此檔案會出現在已知的全機器位置 (例如 *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*)。 其他主機則預期會從主機本身或所要裝載之應用程式旁的位置載入 *CoreCLR.dll*。 不過，其他主機還是可以參考環境變數以尋找程式庫。

在 Linux 或 Mac 上，Core 執行階段程式庫分別是 *libcoreclr.so* 或 *libcoreclr.dylib*。

我們的範例主機會在一些常見的位置中探查 *CoreCLR.dll*。 找到後，必須透過 `LoadLibrary` (若是 Linux/Mac 則為 `dlopen`) 載入。

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>步驟 3 - 取得 ICLRRuntimeHost4 執行個體
若要擷取 `ICLRRuntimeHost4` 裝載介面，請在 `GetCLRRuntimeHost` 上呼叫 `GetProcAddress` (若是 Linux/Mac 則為 `dlsym`)，然後叫用該函式。

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>步驟 4 - 設定啟動旗標並啟動執行階段
準備好 `ICLRRuntimeHost4` 之後，現在可以指定全執行階段啟動旗標並啟動執行階段。 啟動旗標會決定所要使用的記憶體回收行程 (GC) (並行或伺服器)，而不論使用的是單一 AppDomain 或多個 AppDomain；它也會決定 (為了以定義域中性方式載入組件) 所要使用的載入器最佳化原則。

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

呼叫 `Start` 函式以啟動執行階段。

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>步驟 5 - 準備 AppDomain 設定
啟動執行階段之後，我們想要設定 AppDomain。 不過，建立 .NET AppDomain 時必須指定一些選項，因此必須先準備這些選項。

AppDomain 旗標會指定與安全性和 Interop 相關的 AppDomain 行為。 舊版的 Silverlight 主機使用這些設定來沙箱化使用者程式碼，但最新式的 .NET Core 主機則會以完全信任的方式來執行使用者程式碼並啟用 Interop。

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

決定要使用的 AppDomain 旗標之後，必須定義 AppDomain 屬性。 這些屬性是字串的索引鍵/值組。 許多屬性與 AppDomain 載入組件的方式相關。

常見的 AppDomain 屬性包括：

* `TRUSTED_PLATFORM_ASSEMBLIES`：這是 AppDomain 應設定載入優先權並授與完全信任 (即使是部分信任的定義域) 的組件路徑清單 (在 Windows 上會以 `;` 分隔，而在 Linux/Mac 上則以 `:` 分隔)。 此清單可用來包含 'Framework' 組件及其他信任的模組，類似於 .NET Framework 案例中的 GAC。 某些主機會將任何程式庫放在此清單中的 *coreclr.dll* 旁，其他主機則會有針對其用途列出信任組件的硬式編碼資訊清單。
* `APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。 因為主機可以進一步控制使用 TPA 清單載入哪些組件，所以主機最好確定它們預期載入哪些組件，並明確列出這些組件。 不過，如果需要在執行階段進行探查，此屬性可用於這種情況。
*  `APP_NI_PATHS`：此清單與 APP_PATHS 非常類似，不同之處在於其用途是作為探查原生影像的路徑。
*  `NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生 DLL 時，載入器應探查的路徑清單。
*  `PLATFORM_RESOURCE_ROOTS`：此清單包含要在其中探查資源附屬組件的路徑 (位於文化特性專屬子目錄中)。

在我們的[簡單範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)中，這些屬性會設定如下：

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>步驟 6 - 建立 AppDomain
準備好所有 AppDomain 旗標和屬性之後，即可使用 `ICLRRuntimeHost4::CreateAppDomainWithManager` 來設定 AppDomain。 此函式會選擇性地接受完整組件名稱和類型名稱，以用作定義域的 AppDomain 管理員。 AppDomain 管理員可讓主機控制 AppDomain 行為的某些層面，並可在主機不想直接叫用使用者程式碼時，提供進入點以啟動 Managed 程式碼。

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>步驟 7 - 執行 Managed 程式碼！
在 AppDomain 啟動並執行之後，主機現在可以開始執行 Managed 程式碼。 最簡單的做法是使用 `ICLRRuntimeHost4::ExecuteAssembly` 叫用 Managed 組件的進入點方法。 請注意，此函式僅適用於單一定義域案例。

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

如果 `ExecuteAssembly` 不符合您的主機需求，另一個選擇是使用 `CreateDelegate` 建立靜態 Managed 方法的函式指標。 雖然此做法要求主機必須知道所呼叫的方法簽章 (以便建立函式指標類型)，但允許主機彈性地叫用組件進入點以外的程式碼。 第二個參數中提供的組件名稱為要載入之程式庫的[完整受控組件名稱](../../framework/app-domains/assembly-names.md)。

```C++
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

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

## <a name="conclusion"></a>結論
建置主機之後，您可以從命令列執行主機，並傳遞主機預期的任何引數 (例如要針對 mscoree 範例主機執行的受控應用程式)，藉以進行測試。 指定主機要執行的 .NET Core 應用程式時，請務必使用 `dotnet build` 所產生的 .dll。 `dotnet publish` 為獨立式應用程式所產生的可執行檔 (.exe 檔案)，其實就是預設 .NET Core 主機 (因此應用程式可在主要情況下從命令列直接啟動)；使用者程式碼會編譯成同名的 DLL。

如果一開始未正常運作，請再確認一次主機預期的位置中有 *coreclr.dll*、所有必要的 Framework 程式庫都在 TPA 清單中，而且 CoreCLR 的位元 (32 或 64 位元) 符合主機的建立方式。

裝載 .NET Core 執行階段是進階案例，許多開發人員並不需要，但對於需要從原生處理序啟動 Managed 程式碼的人員，或需要更能掌控 .NET Core 執行階段行為的人員而言，這項作業可能很實用。
