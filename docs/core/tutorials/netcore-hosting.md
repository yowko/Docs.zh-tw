---
title: 撰寫自訂 .NET Core 執行階段主機
description: 了解如何從原生程式碼裝載 .NET Core 執行階段，以支援需要控制 .NET Core 執行階段運作方式的進階案例。
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: 03cf188fc74e8a70798c0bcc4a6940730abfc07c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180459"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a><span data-ttu-id="510ec-103">撰寫自訂 .NET Core 主機以從原生程式碼控制 .NET 執行階段</span><span class="sxs-lookup"><span data-stu-id="510ec-103">Write a custom .NET Core host to control the .NET runtime from your native code</span></span>

<span data-ttu-id="510ec-104">如同所有 Managed 程式碼，.NET Core 應用程式是由主機執行。</span><span class="sxs-lookup"><span data-stu-id="510ec-104">Like all managed code, .NET Core applications are executed by a host.</span></span> <span data-ttu-id="510ec-105">該主機會負責啟動執行階段 (包括 JIT 和記憶體回收行程等元件) 及叫用受控進入點。</span><span class="sxs-lookup"><span data-stu-id="510ec-105">The host is responsible for starting the runtime (including components like the JIT and garbage collector) and invoking managed entry points.</span></span>

<span data-ttu-id="510ec-106">裝載 .NET Core 執行階段是進階案例，在大多數情況下，由於 .NET Core 建置程序會提供預設主機來執行 .NET Core 應用程式，因此 .NET Core 開發人員不需要擔心裝載相關事宜。</span><span class="sxs-lookup"><span data-stu-id="510ec-106">Hosting the .NET Core runtime is an advanced scenario and, in most cases, .NET Core developers don't need to worry about hosting because .NET Core build processes provide a default host to run .NET Core applications.</span></span> <span data-ttu-id="510ec-107">不過在某些特殊情況下，明確裝載 .NET Core 執行階段可能會很有用，像是用來叫用原生處理序中的 Managed 程式碼，或是用來增加對執行階段運作方式的更多控制。</span><span class="sxs-lookup"><span data-stu-id="510ec-107">In some specialized circumstances, though, it can be useful to explicitly host the .NET Core runtime, either as a means of invoking managed code in a native process or in order to gain more control over how the runtime works.</span></span>

<span data-ttu-id="510ec-108">本文概述從機器碼啟動 .NET Core 執行階段及在其中執行受控碼的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="510ec-108">This article gives an overview of the steps necessary to start the .NET Core runtime from native code and execute managed code in it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="510ec-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="510ec-109">Prerequisites</span></span>

<span data-ttu-id="510ec-110">因為主機是原生應用程式，所以本教學課程說明如何建立 c + + 應用程式來裝載 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="510ec-110">Because hosts are native applications, this tutorial covers constructing a C++ application to host .NET Core.</span></span> <span data-ttu-id="510ec-111">您將需要 C++ 開發環境 (例如 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 所提供的環境)。</span><span class="sxs-lookup"><span data-stu-id="510ec-111">You will need a C++ development environment (such as that provided by [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).</span></span>

<span data-ttu-id="510ec-112">您也需要一個簡單的 .NET Core 應用程式來測試主機，因此您必須安裝 [.NET Core SDK](https://dotnet.microsoft.com/download) 並[建置一個小型的.NET Core 測試應用程式](with-visual-studio.md) (例如 'Hello World' 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="510ec-112">You will also want a simple .NET Core application to test the host with, so you should install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [build a small .NET Core test app](with-visual-studio.md) (such as a 'Hello World' app).</span></span> <span data-ttu-id="510ec-113">由新的 .NET Core 主控台專案範本建立的 'Hello World' 應用程式就已足夠。</span><span class="sxs-lookup"><span data-stu-id="510ec-113">The 'Hello World' app created by the new .NET Core console project template is sufficient.</span></span>

## <a name="hosting-apis"></a><span data-ttu-id="510ec-114">裝載 API</span><span class="sxs-lookup"><span data-stu-id="510ec-114">Hosting APIs</span></span>

<span data-ttu-id="510ec-115">有三個不同的 API 可用來裝載 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="510ec-115">There are three different APIs that can be used to host .NET Core.</span></span> <span data-ttu-id="510ec-116">本文 (與其相關的 [範例](https://github.com/dotnet/samples/tree/master/core/hosting)) 涵蓋所有選項。</span><span class="sxs-lookup"><span data-stu-id="510ec-116">This article (and its associated [samples](https://github.com/dotnet/samples/tree/master/core/hosting)) covers all options.</span></span>

* <span data-ttu-id="510ec-117">在 .NET Core 3.0 及更新版本中裝載 .NET Core 執行階段的建議方式，是使用 `nethost` 和 `hostfxr` 程式庫的 API。</span><span class="sxs-lookup"><span data-stu-id="510ec-117">The preferred method of hosting the .NET Core runtime in .NET Core 3.0 and above is with the `nethost` and `hostfxr` libraries' APIs.</span></span> <span data-ttu-id="510ec-118">這些進入點能處理尋找及設定初始化執行階段的複雜程度，並允許啟動受控應用程式及呼叫靜態受控方法。</span><span class="sxs-lookup"><span data-stu-id="510ec-118">These entry points handle the complexity of finding and setting up the runtime for initialization and allow both launching a managed application and calling into a static managed method.</span></span>
* <span data-ttu-id="510ec-119">在 .NET Core 3.0 之前裝載 .NET Core 執行時間的慣用方法是使用 [`coreclrhost.h`](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API。</span><span class="sxs-lookup"><span data-stu-id="510ec-119">The preferred method of hosting the .NET Core runtime prior to .NET Core 3.0 is with the [`coreclrhost.h`](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API.</span></span> <span data-ttu-id="510ec-120">此 API 會公開函式，以便輕鬆地啟動和停止執行階段，以及叫用受控碼 (無論是透過啟動受控 exe 或藉由呼叫靜態受控方法)。</span><span class="sxs-lookup"><span data-stu-id="510ec-120">This API exposes functions for easily starting and stopping the runtime and invoking managed code (either by launching a managed exe or by calling static managed methods).</span></span>

## <a name="sample-hosts"></a><span data-ttu-id="510ec-121">範例主機</span><span class="sxs-lookup"><span data-stu-id="510ec-121">Sample Hosts</span></span>

<span data-ttu-id="510ec-122">dotnet/samples GitHub 存放庫中提供下列示範教學課程所述步驟的[範例主機](https://github.com/dotnet/samples/tree/master/core/hosting)。</span><span class="sxs-lookup"><span data-stu-id="510ec-122">[Sample hosts](https://github.com/dotnet/samples/tree/master/core/hosting) demonstrating the steps outlined in the tutorials below are available in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="510ec-123">範例中註解清楚地將這些教學課程中的編號步驟與範例中的執行位置建立關聯。</span><span class="sxs-lookup"><span data-stu-id="510ec-123">Comments in the samples clearly associate the numbered steps from these tutorials with where they're performed in the sample.</span></span> <span data-ttu-id="510ec-124">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#view-and-download-samples)。</span><span class="sxs-lookup"><span data-stu-id="510ec-124">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

<span data-ttu-id="510ec-125">請記住，範例主機是為了用於學習，因此錯誤檢查較不嚴謹，並設計成可讀性比效率更重要。</span><span class="sxs-lookup"><span data-stu-id="510ec-125">Keep in mind that the sample hosts are meant to be used for learning purposes, so they are light on error checking and are designed to emphasize readability over efficiency.</span></span>

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a><span data-ttu-id="510ec-126">使用和建立主機 `nethost.h``hostfxr.h`</span><span class="sxs-lookup"><span data-stu-id="510ec-126">Create a host using `nethost.h` and `hostfxr.h`</span></span>

<span data-ttu-id="510ec-127">下列步驟詳細說明如何使用 `nethost` 和 `hostfxr` 程式庫來在原生應用程式中啟動 .NET Core 執行階段，並呼叫受控靜態方法。</span><span class="sxs-lookup"><span data-stu-id="510ec-127">The following steps detail how to use the `nethost` and `hostfxr` libraries to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="510ec-128">[範例](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) \(英文\) 會使用搭配 .NET SDK 安裝的 `nethost` 標頭及程式庫，以及來自 [dotnet/core-setup](https://github.com/dotnet/core-setup) \(英文\) 存放庫的 [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) \(英文\) 及 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) \(英文\) 檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="510ec-128">The [sample](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) uses the `nethost` header and library installed with the .NET SDK and copies of the [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) and [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) files from the [dotnet/core-setup](https://github.com/dotnet/core-setup) repository.</span></span>

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a><span data-ttu-id="510ec-129">步驟 1-載入 `hostfxr` 和取得匯出的裝載函數</span><span class="sxs-lookup"><span data-stu-id="510ec-129">Step 1 - Load `hostfxr` and get exported hosting functions</span></span>

<span data-ttu-id="510ec-130">`nethost` 程式庫會提供用來找出 `hostfxr` 程式庫的 `get_hostfxr_path` 函式。</span><span class="sxs-lookup"><span data-stu-id="510ec-130">The `nethost` library provides the `get_hostfxr_path` function for locating the `hostfxr` library.</span></span> <span data-ttu-id="510ec-131">`hostfxr` 程式庫會公開用來裝載 .NET Core 執行階段的函式。</span><span class="sxs-lookup"><span data-stu-id="510ec-131">The `hostfxr` library exposes functions for hosting the .NET Core runtime.</span></span> <span data-ttu-id="510ec-132">您可以在 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) 和 [原生裝載設計檔](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md)中找到完整的函式清單。</span><span class="sxs-lookup"><span data-stu-id="510ec-132">The full list of functions can be found in [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) and the [native hosting design document](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md).</span></span> <span data-ttu-id="510ec-133">範例和本教課程會使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="510ec-133">The sample and this tutorial use the following:</span></span>

* <span data-ttu-id="510ec-134">`hostfxr_initialize_for_runtime_config`：初始化主機內容，並準備使用指定的執行時間設定初始化 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="510ec-134">`hostfxr_initialize_for_runtime_config`: Initializes a host context and prepares for initialization of the .NET Core runtime using the specified runtime configuration.</span></span>
* <span data-ttu-id="510ec-135">`hostfxr_get_runtime_delegate`：取得執行時間功能的委派。</span><span class="sxs-lookup"><span data-stu-id="510ec-135">`hostfxr_get_runtime_delegate`: Gets a delegate for runtime functionality.</span></span>
* <span data-ttu-id="510ec-136">`hostfxr_close`：關閉主機內容。</span><span class="sxs-lookup"><span data-stu-id="510ec-136">`hostfxr_close`: Closes a host context.</span></span>

<span data-ttu-id="510ec-137">`hostfxr` 程式庫是使用 `get_hostfxr_path` 來找到。</span><span class="sxs-lookup"><span data-stu-id="510ec-137">The `hostfxr` library is found using `get_hostfxr_path`.</span></span> <span data-ttu-id="510ec-138">系統接著會載入它並擷取其匯出。</span><span class="sxs-lookup"><span data-stu-id="510ec-138">It is then loaded and its exports are retrieved.</span></span>

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a><span data-ttu-id="510ec-139">步驟 2 - 初始化並啟動 .NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="510ec-139">Step 2 - Initialize and start the .NET Core runtime</span></span>

<span data-ttu-id="510ec-140">`hostfxr_initialize_for_runtime_config` 和 `hostfxr_get_runtime_delegate` 函式會使用適用於將載入之受控元件的執行階段設定，來初始化並啟動 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="510ec-140">The `hostfxr_initialize_for_runtime_config` and `hostfxr_get_runtime_delegate` functions initialize and start the .NET Core runtime using the runtime configuration for the managed component that will be loaded.</span></span> <span data-ttu-id="510ec-141">`hostfxr_get_runtime_delegate` 函式會被用來取得能允許載入受控組件，並取得針對該組件中靜態方法之函式指標的執行階段委派。</span><span class="sxs-lookup"><span data-stu-id="510ec-141">The `hostfxr_get_runtime_delegate` function is used to get a runtime delegate that allows loading a managed assembly and getting a function pointer to a static method in that assembly.</span></span>

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a><span data-ttu-id="510ec-142">步驟 3 - 載入受控組件並取得針對受控方法的函式指標</span><span class="sxs-lookup"><span data-stu-id="510ec-142">Step 3 - Load managed assembly and get function pointer to a managed method</span></span>

<span data-ttu-id="510ec-143">系統會呼叫執行階段委派來載入受控組件，並取得針對受控方法的函式指標。</span><span class="sxs-lookup"><span data-stu-id="510ec-143">The runtime delegate is called to load the managed assembly and get a function pointer to a managed method.</span></span> <span data-ttu-id="510ec-144">該委派需要組件路徑、類型名稱及方法名稱作為輸入，並會傳回可用來叫用受控方法的函式指標。</span><span class="sxs-lookup"><span data-stu-id="510ec-144">The delegate requires the assembly path, type name, and method name as inputs and returns a function pointer that can be used to invoke the managed method.</span></span>

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

<span data-ttu-id="510ec-145">在呼叫執行階段委派期間，透過將 `nullptr` 傳遞為委派類型名稱，範例會針對受控方法使用預設簽章：</span><span class="sxs-lookup"><span data-stu-id="510ec-145">By passing `nullptr` as the delegate type name when calling the runtime delegate, the sample uses a default signature for the managed method:</span></span>

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

<span data-ttu-id="510ec-146">若要使用不同的簽章，可以在呼叫執行階段委派時指定委派類型名稱。</span><span class="sxs-lookup"><span data-stu-id="510ec-146">A different signature can be used by specifying the delegate type name when calling the runtime delegate.</span></span>

### <a name="step-4---run-managed-code"></a><span data-ttu-id="510ec-147">步驟 4 - 執行受控程式碼！</span><span class="sxs-lookup"><span data-stu-id="510ec-147">Step 4 - Run managed code!</span></span>

<span data-ttu-id="510ec-148">原生主機現在可以呼叫受控方法，並向它傳遞所需的參數。</span><span class="sxs-lookup"><span data-stu-id="510ec-148">The native host can now call the managed method and pass it the desired parameters.</span></span>

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a><span data-ttu-id="510ec-149">使用建立主機 `coreclrhost.h`</span><span class="sxs-lookup"><span data-stu-id="510ec-149">Create a host using `coreclrhost.h`</span></span>

<span data-ttu-id="510ec-150">下列步驟詳細說明如何使用 `coreclrhost.h` API 在原生應用程式中啟動 .Net Core 執行時間，並呼叫受控靜態方法。</span><span class="sxs-lookup"><span data-stu-id="510ec-150">The following steps detail how to use the `coreclrhost.h` API to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="510ec-151">本文件中的程式碼片段會使用一些 Windows 專用的 API，但[完整的範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)會顯示 Windows 和 Linux 兩者的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="510ec-151">The code snippets in this document use some Windows-specific APIs, but the [full sample host](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) shows both Windows and Linux code paths.</span></span>

<span data-ttu-id="510ec-152">[Unix CoreRun 主機](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun)會顯示更複雜的主機使用範例 `coreclrhost.h` 。</span><span class="sxs-lookup"><span data-stu-id="510ec-152">The [Unix CoreRun host](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun) shows a more complex, real-world example of hosting using `coreclrhost.h`.</span></span>

### <a name="step-1---find-and-load-coreclr"></a><span data-ttu-id="510ec-153">步驟 1 - 找到並載入 CoreCLR</span><span class="sxs-lookup"><span data-stu-id="510ec-153">Step 1 - Find and load CoreCLR</span></span>

<span data-ttu-id="510ec-154">.NET Core 執行階段 API 是在 *coreclr.dll* 中 (Windows)、在 *libcoreclr.so* 中 (Linux)，或是在 *libcoreclr.dylib* 中 (macOS)。</span><span class="sxs-lookup"><span data-stu-id="510ec-154">The .NET Core runtime APIs are in *coreclr.dll* (on Windows), in *libcoreclr.so* (on Linux), or in *libcoreclr.dylib* (on macOS).</span></span> <span data-ttu-id="510ec-155">裝載 .NET Core 的第一個步驟是載入 CoreCLR 程式庫。</span><span class="sxs-lookup"><span data-stu-id="510ec-155">The first step to hosting .NET Core is to load the CoreCLR library.</span></span> <span data-ttu-id="510ec-156">某些主機會探查不同的路徑，或使用輸入參數來尋找程式庫，而其他主機知道要從某個路徑 (例如，主機旁邊或從全機器位置) 進行載入。</span><span class="sxs-lookup"><span data-stu-id="510ec-156">Some hosts probe different paths or use input parameters to find the library while others know to load it from a certain path (next to the host, for example, or from a machine-wide location).</span></span>

<span data-ttu-id="510ec-157">一旦找到，就會使用 `LoadLibraryEx` Windows) 上的 (以及 `dlopen` Linux/macOS) 上的 (載入程式庫。</span><span class="sxs-lookup"><span data-stu-id="510ec-157">Once found, the library is loaded with `LoadLibraryEx` (on Windows) or `dlopen` (on Linux/macOS).</span></span>

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a><span data-ttu-id="510ec-158">步驟 2 - 取得 .NET Core 裝載函式</span><span class="sxs-lookup"><span data-stu-id="510ec-158">Step 2 - Get .NET Core hosting functions</span></span>

<span data-ttu-id="510ec-159">CoreClrHost 有幾個可用於裝載 .NET Core 的重要方法：</span><span class="sxs-lookup"><span data-stu-id="510ec-159">CoreClrHost has several important methods useful for hosting .NET Core:</span></span>

* <span data-ttu-id="510ec-160">`coreclr_initialize`：啟動 .NET Core 執行時間，並設定預設 (，且僅) AppDomain。</span><span class="sxs-lookup"><span data-stu-id="510ec-160">`coreclr_initialize`: Starts the .NET Core runtime and sets up the default (and only) AppDomain.</span></span>
* <span data-ttu-id="510ec-161">`coreclr_execute_assembly`：執行 managed 元件。</span><span class="sxs-lookup"><span data-stu-id="510ec-161">`coreclr_execute_assembly`: Executes a managed assembly.</span></span>
* <span data-ttu-id="510ec-162">`coreclr_create_delegate`：建立 managed 方法的函式指標。</span><span class="sxs-lookup"><span data-stu-id="510ec-162">`coreclr_create_delegate`: Creates a function pointer to a managed method.</span></span>
* <span data-ttu-id="510ec-163">`coreclr_shutdown`：關閉 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="510ec-163">`coreclr_shutdown`: Shuts down the .NET Core runtime.</span></span>
* <span data-ttu-id="510ec-164">`coreclr_shutdown_2`： Like `coreclr_shutdown` ，但也會捕獲 managed 程式碼的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="510ec-164">`coreclr_shutdown_2`: Like `coreclr_shutdown`, but also retrieves the managed code's exit code.</span></span>

<span data-ttu-id="510ec-165">載入 CoreCLR 程式庫之後，下一個步驟是使用 `GetProcAddress` Windows) 上的 (或 `dlsym` Linux/macOS) 上的 (來取得這些函式的參考。</span><span class="sxs-lookup"><span data-stu-id="510ec-165">After loading the CoreCLR library, the next step is to get references to these functions using `GetProcAddress` (on Windows) or `dlsym` (on Linux/macOS).</span></span>

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a><span data-ttu-id="510ec-166">步驟 3 - 準備執行階段屬性</span><span class="sxs-lookup"><span data-stu-id="510ec-166">Step 3 - Prepare runtime properties</span></span>

<span data-ttu-id="510ec-167">啟動執行階段之前，必須準備一些屬性來指定行為 (尤其是關於組件載入器)。</span><span class="sxs-lookup"><span data-stu-id="510ec-167">Before starting the runtime, it is necessary to prepare some properties to specify behavior (especially concerning the assembly loader).</span></span>

<span data-ttu-id="510ec-168">常用屬性包括：</span><span class="sxs-lookup"><span data-stu-id="510ec-168">Common properties include:</span></span>

* <span data-ttu-id="510ec-169">`TRUSTED_PLATFORM_ASSEMBLIES`：這是執行階段預設能夠解析的組件路徑 (在 Windows 上會以 ';' 分隔，而在 Linux 上則以 ':' 分隔) 清單。</span><span class="sxs-lookup"><span data-stu-id="510ec-169">`TRUSTED_PLATFORM_ASSEMBLIES` This is a list of assembly paths (delimited by ';' on Windows and ':' on Linux) which the runtime will be able to resolve by default.</span></span> <span data-ttu-id="510ec-170">某些主機具有硬式編碼資訊清單，其中列出它們可以載入的組件。</span><span class="sxs-lookup"><span data-stu-id="510ec-170">Some hosts have hard-coded manifests listing assemblies they can load.</span></span> <span data-ttu-id="510ec-171">其他主機則會在此清單的特定位置 (例如，*coreclr.dll* 旁邊) 放入任何程式庫。</span><span class="sxs-lookup"><span data-stu-id="510ec-171">Others will put any library in certain locations (next to *coreclr.dll*, for example) on this list.</span></span>
* <span data-ttu-id="510ec-172">`APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。</span><span class="sxs-lookup"><span data-stu-id="510ec-172">`APP_PATHS` This is a list of paths to probe in for an assembly if it can't be found in the trusted platform assemblies (TPA) list.</span></span> <span data-ttu-id="510ec-173">因為主機可以進一步控制使用 TPA 清單載入哪些組件，所以主機最好確定它們預期載入哪些組件，並明確列出這些組件。</span><span class="sxs-lookup"><span data-stu-id="510ec-173">Because the host has more control over which assemblies are loaded using the TPA list, it is a best practice for hosts to determine which assemblies they expect to load and list them explicitly.</span></span> <span data-ttu-id="510ec-174">但是，如果需要在執行時間進行探查，則這個屬性可以啟用該案例。</span><span class="sxs-lookup"><span data-stu-id="510ec-174">If probing at run time is needed, however, this property can enable that scenario.</span></span>
* <span data-ttu-id="510ec-175">`APP_NI_PATHS`：此清單與 APP_PATHS 類似，不同之處在於其用途是作為探查原生映像的路徑。</span><span class="sxs-lookup"><span data-stu-id="510ec-175">`APP_NI_PATHS` This list is similar to APP_PATHS except that it's meant to be paths that will be probed for native images.</span></span>
* <span data-ttu-id="510ec-176">`NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生程式庫時，載入器應探查的路徑清單。</span><span class="sxs-lookup"><span data-stu-id="510ec-176">`NATIVE_DLL_SEARCH_DIRECTORIES` This property is a list of paths the loader should probe when looking for native libraries called via p/invoke.</span></span>
* <span data-ttu-id="510ec-177">`PLATFORM_RESOURCE_ROOTS` 這份清單包含在特定文化特性子目錄) 中，用於探查資源附屬元件 (的路徑。</span><span class="sxs-lookup"><span data-stu-id="510ec-177">`PLATFORM_RESOURCE_ROOTS` This list includes paths to probe in for resource satellite assemblies (in culture-specific subdirectories).</span></span>

<span data-ttu-id="510ec-178">在此範例主機中，只需列出目前目錄中的所有程式庫，即可建構 TPA 清單：</span><span class="sxs-lookup"><span data-stu-id="510ec-178">In this sample host, the TPA list is constructed by simply listing all libraries in the current directory:</span></span>

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

<span data-ttu-id="510ec-179">由於此範例很簡單，因此它只需要 `TRUSTED_PLATFORM_ASSEMBLIES` 屬性：</span><span class="sxs-lookup"><span data-stu-id="510ec-179">Because the sample is simple, it only needs the `TRUSTED_PLATFORM_ASSEMBLIES` property:</span></span>

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a><span data-ttu-id="510ec-180">步驟 4 - 啟動執行階段</span><span class="sxs-lookup"><span data-stu-id="510ec-180">Step 4 - Start the runtime</span></span>

<span data-ttu-id="510ec-181">`coreclrhost.h` Api 會啟動執行時間，並使用單一呼叫來建立預設 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="510ec-181">`coreclrhost.h` APIs start the runtime and create the default AppDomain all with a single call.</span></span> <span data-ttu-id="510ec-182">`coreclr_initialize` 函式會採用基底路徑、名稱和稍早所述的屬性，並透過 `hostHandle` 參數將控制代碼傳回到主機。</span><span class="sxs-lookup"><span data-stu-id="510ec-182">The `coreclr_initialize` function takes a base path, name, and the properties described earlier and returns back a handle to the host via the `hostHandle` parameter.</span></span>

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a><span data-ttu-id="510ec-183">步驟 5 - 執行受控碼！</span><span class="sxs-lookup"><span data-stu-id="510ec-183">Step 5 - Run managed code!</span></span>

<span data-ttu-id="510ec-184">執行階段啟動後，主機便可以呼叫受控碼。</span><span class="sxs-lookup"><span data-stu-id="510ec-184">With the runtime started, the host can call managed code.</span></span> <span data-ttu-id="510ec-185">這可透過幾種不同的方式來完成。</span><span class="sxs-lookup"><span data-stu-id="510ec-185">This can be done in a couple of different ways.</span></span> <span data-ttu-id="510ec-186">連結至這個教學課程之範例程式碼使用 `coreclr_create_delegate` 函式來建立靜態受控方法的委派。</span><span class="sxs-lookup"><span data-stu-id="510ec-186">The sample code linked to this tutorial uses the `coreclr_create_delegate` function to create a delegate to a static managed method.</span></span> <span data-ttu-id="510ec-187">此 API 會採用[組件名稱](../../standard/assembly/names.md)、命名空間限定的類型名稱和方法名稱作為輸入，並傳回可用來叫用方法的委派。</span><span class="sxs-lookup"><span data-stu-id="510ec-187">This API takes the [assembly name](../../standard/assembly/names.md), namespace-qualified type name, and method name as inputs and returns a delegate that can be used to invoke the method.</span></span>

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

<span data-ttu-id="510ec-188">在此範例中，主機現在可以呼叫 `managedDelegate` 來執行 `ManagedWorker.DoWork` 方法。</span><span class="sxs-lookup"><span data-stu-id="510ec-188">In this sample, the host can now call `managedDelegate` to run the `ManagedWorker.DoWork` method.</span></span>

<span data-ttu-id="510ec-189">或者，`coreclr_execute_assembly` 函式可用來啟動受控可執行檔。</span><span class="sxs-lookup"><span data-stu-id="510ec-189">Alternatively, the `coreclr_execute_assembly` function can be used to launch a managed executable.</span></span> <span data-ttu-id="510ec-190">此 API 會採用組件路徑和引數陣列作為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="510ec-190">This API takes an assembly path and array of arguments as input parameters.</span></span> <span data-ttu-id="510ec-191">它會載入該路徑中的組件，並叫用其 Main 方法。</span><span class="sxs-lookup"><span data-stu-id="510ec-191">It loads the assembly at that path and invokes its main method.</span></span>

```c++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a><span data-ttu-id="510ec-192">步驟 6 - 關閉並清除</span><span class="sxs-lookup"><span data-stu-id="510ec-192">Step 6 - Shutdown and clean up</span></span>

<span data-ttu-id="510ec-193">最後，當主機完成受控碼的執行時，.NET Core 執行階段會使用 `coreclr_shutdown` 或 `coreclr_shutdown_2` 來關閉。</span><span class="sxs-lookup"><span data-stu-id="510ec-193">Finally, when the host is done running managed code, the .NET Core runtime is shut down with `coreclr_shutdown` or `coreclr_shutdown_2`.</span></span>

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

<span data-ttu-id="510ec-194">CoreCLR 不支援重新初始化或卸載。</span><span class="sxs-lookup"><span data-stu-id="510ec-194">CoreCLR does not support reinitialization or unloading.</span></span> <span data-ttu-id="510ec-195">請勿再次呼叫 `coreclr_initialize` 或卸載 CoreCLR 程式庫。</span><span class="sxs-lookup"><span data-stu-id="510ec-195">Do not call `coreclr_initialize` again or unload the CoreCLR library.</span></span>

## <a name="conclusion"></a><span data-ttu-id="510ec-196">結論</span><span class="sxs-lookup"><span data-stu-id="510ec-196">Conclusion</span></span>
<span data-ttu-id="510ec-197">建立主機之後，您可以從命令列執行它，並傳遞主機預期的任何引數，藉以進行測試。</span><span class="sxs-lookup"><span data-stu-id="510ec-197">Once your host is built, it can be tested by running it from the command line and passing any arguments the host expects.</span></span> <span data-ttu-id="510ec-198">指定主機要執行的 .NET Core 應用程式時，請務必使用 `dotnet build` 所產生的 .dll。</span><span class="sxs-lookup"><span data-stu-id="510ec-198">When specifying the .NET Core app for the host to run, be sure to use the .dll that is produced by `dotnet build`.</span></span> <span data-ttu-id="510ec-199">`dotnet publish` 為獨立式應用程式所產生的可執行檔 (.exe 檔案)，其實就是預設 .NET Core 主機 (因此應用程式可在主要情況下從命令列直接啟動)；使用者程式碼會編譯成同名的 DLL。</span><span class="sxs-lookup"><span data-stu-id="510ec-199">Executables (.exe files) produced by `dotnet publish` for self-contained applications are actually the default .NET Core host (so that the app can be launched directly from the command line in mainline scenarios); user code is compiled into a dll of the same name.</span></span>

<span data-ttu-id="510ec-200">如果最初無法運作，請仔細檢查主機所預期的位置中是否有可用的 *coreclr.dll* 、所有必要的架構程式庫都在 TPA 清單中，以及 CoreCLR 的位 (32 位或64位) 符合主機的建立方式。</span><span class="sxs-lookup"><span data-stu-id="510ec-200">If things don't work initially, double-check that *coreclr.dll* is available in the location expected by the host, that all necessary Framework libraries are in the TPA list, and that CoreCLR's bitness (32-bit or 64-bit) matches how the host was built.</span></span>

<span data-ttu-id="510ec-201">裝載 .NET Core 執行階段是進階案例，許多開發人員並不需要，但對於需要從原生處理序啟動 Managed 程式碼的人員，或需要更能掌控 .NET Core 執行階段行為的人員而言，這項作業可能很實用。</span><span class="sxs-lookup"><span data-stu-id="510ec-201">Hosting the .NET Core runtime is an advanced scenario that many developers won't require, but for those who need to launch managed code from a native process, or who need more control over the .NET Core runtime's behavior, it can be very useful.</span></span>
