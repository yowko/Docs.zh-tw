---
title: 撰寫自訂 .NET Core 執行階段主機
description: 了解如何從原生程式碼裝載 .NET Core 執行階段，以支援需要控制 .NET Core 執行階段運作方式的進階案例。
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: 6cddb6fa7dcd7a7d050749c26249f1f5d876322d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306196"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a><span data-ttu-id="f04ad-103">撰寫自訂 .NET Core 主機以從原生程式碼控制 .NET 執行階段</span><span class="sxs-lookup"><span data-stu-id="f04ad-103">Write a custom .NET Core host to control the .NET runtime from your native code</span></span>

<span data-ttu-id="f04ad-104">如同所有 Managed 程式碼，.NET Core 應用程式是由主機執行。</span><span class="sxs-lookup"><span data-stu-id="f04ad-104">Like all managed code, .NET Core applications are executed by a host.</span></span> <span data-ttu-id="f04ad-105">該主機會負責啟動執行階段 (包括 JIT 和記憶體回收行程等元件) 及叫用受控進入點。</span><span class="sxs-lookup"><span data-stu-id="f04ad-105">The host is responsible for starting the runtime (including components like the JIT and garbage collector) and invoking managed entry points.</span></span>

<span data-ttu-id="f04ad-106">裝載 .NET Core 執行階段是進階案例，在大多數情況下，由於 .NET Core 建置程序會提供預設主機來執行 .NET Core 應用程式，因此 .NET Core 開發人員不需要擔心裝載相關事宜。</span><span class="sxs-lookup"><span data-stu-id="f04ad-106">Hosting the .NET Core runtime is an advanced scenario and, in most cases, .NET Core developers don't need to worry about hosting because .NET Core build processes provide a default host to run .NET Core applications.</span></span> <span data-ttu-id="f04ad-107">不過在某些特殊情況下，明確裝載 .NET Core 執行階段可能會很有用，像是用來叫用原生處理序中的 Managed 程式碼，或是用來增加對執行階段運作方式的更多控制。</span><span class="sxs-lookup"><span data-stu-id="f04ad-107">In some specialized circumstances, though, it can be useful to explicitly host the .NET Core runtime, either as a means of invoking managed code in a native process or in order to gain more control over how the runtime works.</span></span>

<span data-ttu-id="f04ad-108">本文概述從機器碼啟動 .NET Core 執行階段及在其中執行受控碼的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="f04ad-108">This article gives an overview of the steps necessary to start the .NET Core runtime from native code and execute managed code in it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f04ad-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="f04ad-109">Prerequisites</span></span>

<span data-ttu-id="f04ad-110">由於主機是原生應用程式，因此本教學課程將說明如何建構 C++ 應用程式以裝載 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f04ad-110">Because hosts are native applications, this tutorial will cover constructing a C++ application to host .NET Core.</span></span> <span data-ttu-id="f04ad-111">您將需要 C++ 開發環境 (例如 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 所提供的環境)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-111">You will need a C++ development environment (such as that provided by [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).</span></span>

<span data-ttu-id="f04ad-112">您也需要一個簡單的 .NET Core 應用程式來測試主機，因此您必須安裝 [.NET Core SDK](https://www.microsoft.com/net/core) 並[建置一個小型的.NET Core 測試應用程式](../../core/tutorials/with-visual-studio.md) (例如 'Hello World' 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-112">You will also want a simple .NET Core application to test the host with, so you should install the [.NET Core SDK](https://www.microsoft.com/net/core) and [build a small .NET Core test app](../../core/tutorials/with-visual-studio.md) (such as a 'Hello World' app).</span></span> <span data-ttu-id="f04ad-113">由新的 .NET Core 主控台專案範本建立的 'Hello World' 應用程式就已足夠。</span><span class="sxs-lookup"><span data-stu-id="f04ad-113">The 'Hello World' app created by the new .NET Core console project template is sufficient.</span></span>

## <a name="hosting-apis"></a><span data-ttu-id="f04ad-114">裝載 API</span><span class="sxs-lookup"><span data-stu-id="f04ad-114">Hosting APIs</span></span>
<span data-ttu-id="f04ad-115">有三個不同的 API 可用來裝載 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f04ad-115">There are three different APIs that can be used to host .NET Core.</span></span> <span data-ttu-id="f04ad-116">本文件 (及其相關聯的[範例](https://github.com/dotnet/samples/tree/master/core/hosting) \(英文\)) 會涵蓋所有的選項。</span><span class="sxs-lookup"><span data-stu-id="f04ad-116">This document (and its associated [samples](https://github.com/dotnet/samples/tree/master/core/hosting)) cover all options.</span></span>

* <span data-ttu-id="f04ad-117">在 .NET Core 3.0 及更新版本中裝載 .NET Core 執行階段的建議方式，是使用 `nethost` 和 `hostfxr` 程式庫的 API。</span><span class="sxs-lookup"><span data-stu-id="f04ad-117">The preferred method of hosting the .NET Core runtime in .NET Core 3.0 and above is with the `nethost` and `hostfxr` libraries' APIs.</span></span> <span data-ttu-id="f04ad-118">這些進入點能處理尋找及設定初始化執行階段的複雜性，並允許啟動受控應用程式及呼叫靜態受控方法。</span><span class="sxs-lookup"><span data-stu-id="f04ad-118">These entry points handle the complexity of finding and setting up the rutime for initialization and allow both launching a managed application and calling into a static managed method.</span></span>
* <span data-ttu-id="f04ad-119">裝載早於 .NET Core 3.0 之 .NET Core 執行階段的建議方式，是使用 [CoreClrHost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) \(英文\) API。</span><span class="sxs-lookup"><span data-stu-id="f04ad-119">The preferred method of hosting the .NET Core runtime prior to .NET Core 3.0 is with the [CoreClrHost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) API.</span></span> <span data-ttu-id="f04ad-120">此 API 會公開函式，以便輕鬆地啟動和停止執行階段，以及叫用受控碼 (無論是透過啟動受控 exe 或藉由呼叫靜態受控方法)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-120">This API exposes functions for easily starting and stopping the runtime and invoking managed code (either by launching a managed exe or by calling static managed methods).</span></span>
* <span data-ttu-id="f04ad-121">.NET Core 也可以使用 [mscoree.h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h) 中的 `ICLRRuntimeHost4` 介面進行裝載。</span><span class="sxs-lookup"><span data-stu-id="f04ad-121">.NET Core can also be hosted with the `ICLRRuntimeHost4` interface in [mscoree.h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h).</span></span> <span data-ttu-id="f04ad-122">此 API 的運行時間長於 CoreClrHost.h，因此您可能會看到舊版主機使用它。</span><span class="sxs-lookup"><span data-stu-id="f04ad-122">This API has been around longer than CoreClrHost.h, so you may have seen older hosts using it.</span></span> <span data-ttu-id="f04ad-123">它仍可運作，且比起 CoreClrHost 更能控制裝載處理序。</span><span class="sxs-lookup"><span data-stu-id="f04ad-123">It still works and allows a bit more control over the hosting process than CoreClrHost.</span></span> <span data-ttu-id="f04ad-124">不過，在大部分情況下，CoreClrHost.h 目前仍然是慣用方法，因為其 API 更為簡單。</span><span class="sxs-lookup"><span data-stu-id="f04ad-124">For most scenarios, though, CoreClrHost.h is preferred now because of its simpler APIs.</span></span>

## <a name="sample-hosts"></a><span data-ttu-id="f04ad-125">範例主機</span><span class="sxs-lookup"><span data-stu-id="f04ad-125">Sample Hosts</span></span>
<span data-ttu-id="f04ad-126">dotnet/samples GitHub 存放庫中提供下列示範教學課程所述步驟的[範例主機](https://github.com/dotnet/samples/tree/master/core/hosting)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-126">[Sample hosts](https://github.com/dotnet/samples/tree/master/core/hosting) demonstrating the steps outlined in the tutorials below are available in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="f04ad-127">範例中註解清楚地將這些教學課程中的編號步驟與範例中的執行位置建立關聯。</span><span class="sxs-lookup"><span data-stu-id="f04ad-127">Comments in the samples clearly associate the numbered steps from these tutorials with where they're performed in the sample.</span></span> <span data-ttu-id="f04ad-128">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-128">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="f04ad-129">請記住，範例主機是為了用於學習，因此錯誤檢查較不嚴謹，並設計成可讀性比效率更重要。</span><span class="sxs-lookup"><span data-stu-id="f04ad-129">Keep in mind that the sample hosts are meant to be used for learning purposes, so they are light on error checking and are designed to emphasize readability over efficiency.</span></span>

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a><span data-ttu-id="f04ad-130">使用 NetHost.h 和 HostFxr.h 建立主機</span><span class="sxs-lookup"><span data-stu-id="f04ad-130">Create a host using NetHost.h and HostFxr.h</span></span>

<span data-ttu-id="f04ad-131">下列步驟詳細說明如何使用 `nethost` 和 `hostfxr` 程式庫來在原生應用程式中啟動 .NET Core 執行階段，並呼叫受控靜態方法。</span><span class="sxs-lookup"><span data-stu-id="f04ad-131">The following steps detail how to use the `nethost` and `hostfxr` libraries to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="f04ad-132">[範例](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) \(英文\) 會使用搭配 .NET SDK 安裝的 `nethost` 標頭及程式庫，以及來自 [dotnet/core-setup](https://github.com/dotnet/core-setup) \(英文\) 存放庫的 [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) \(英文\) 及 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) \(英文\) 檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="f04ad-132">The [sample](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) uses the `nethost` header and library installed with the .NET SDK and copies of the [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) and [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) files from the [dotnet/core-setup](https://github.com/dotnet/core-setup) repository.</span></span>

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a><span data-ttu-id="f04ad-133">步驟 1 - 載入 HostFxr 並取得匯出的裝載函式</span><span class="sxs-lookup"><span data-stu-id="f04ad-133">Step 1 - Load HostFxr and get exported hosting functions</span></span>

<span data-ttu-id="f04ad-134">`nethost` 程式庫會提供用來找出 `hostfxr` 程式庫的 `get_hostfxr_path` 函式。</span><span class="sxs-lookup"><span data-stu-id="f04ad-134">The `nethost` library provides the `get_hostfxr_path` function for locating the `hostfxr` library.</span></span> <span data-ttu-id="f04ad-135">`hostfxr` 程式庫會公開用來裝載 .NET Core 執行階段的函式。</span><span class="sxs-lookup"><span data-stu-id="f04ad-135">The `hostfxr` library exposes functions for hosting the .NET Core runtime.</span></span> <span data-ttu-id="f04ad-136">函式的完整清單可在 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) \(英文\) 和[原生裝載設計文件](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="f04ad-136">The full list of functions can be found in [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) and the [native hosting design document](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md).</span></span> <span data-ttu-id="f04ad-137">範例和本教課程會使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="f04ad-137">The sample and this tutorial use the following:</span></span>
* <span data-ttu-id="f04ad-138">`hostfxr_initialize_for_runtime_config`：使用指定的執行階段設定初始化主機內容並針對 .NET Core 執行階段的初始化進行準備。</span><span class="sxs-lookup"><span data-stu-id="f04ad-138">`hostfxr_initialize_for_runtime_config`: Initializes a host context and prepares for initialization of the .NET Core runtime using the specified runtime configuration.</span></span>
* <span data-ttu-id="f04ad-139">`hostfxr_get_runtime_delegate`：取得執行階段功能的委派。</span><span class="sxs-lookup"><span data-stu-id="f04ad-139">`hostfxr_get_runtime_delegate`: Gets a delegate for runtime functionality.</span></span>
* <span data-ttu-id="f04ad-140">`hostfxr_close`：關閉主機內容。</span><span class="sxs-lookup"><span data-stu-id="f04ad-140">`hostfxr_close`: Closes a host context.</span></span>

<span data-ttu-id="f04ad-141">`hostfxr` 程式庫是使用 `get_hostfxr_path` 來找到。</span><span class="sxs-lookup"><span data-stu-id="f04ad-141">The `hostfxr` library is found using `get_hostfxr_path`.</span></span> <span data-ttu-id="f04ad-142">系統接著會載入它並擷取其匯出。</span><span class="sxs-lookup"><span data-stu-id="f04ad-142">It is then loaded and its exports are retrieved.</span></span>

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a><span data-ttu-id="f04ad-143">步驟 2 - 初始化並啟動 .NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="f04ad-143">Step 2 - Initialize and start the .NET Core runtime</span></span>

<span data-ttu-id="f04ad-144">`hostfxr_initialize_for_runtime_config` 和 `hostfxr_get_runtime_delegate` 函式會使用適用於將載入之受控元件的執行階段設定，來初始化並啟動 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="f04ad-144">The `hostfxr_initialize_for_runtime_config` and `hostfxr_get_runtime_delegate` functions initialize and start the .NET Core runtime using the runtime configuration for the managed component that will be loaded.</span></span> <span data-ttu-id="f04ad-145">`hostfxr_get_runtime_delegate` 函式會被用來取得能允許載入受控組件，並取得針對該組件中靜態方法之函式指標的執行階段委派。</span><span class="sxs-lookup"><span data-stu-id="f04ad-145">The `hostfxr_get_runtime_delegate` function is used to get a runtime delegate that allows loading a managed assembly and getting a function pointer to a static method in that assembly.</span></span>

[!code-cpp[HostFxrHost#Initialize](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a><span data-ttu-id="f04ad-146">步驟 3 - 載入受控組件並取得針對受控方法的函式指標</span><span class="sxs-lookup"><span data-stu-id="f04ad-146">Step 3 - Load managed assembly and get function pointer to a managed method</span></span>

<span data-ttu-id="f04ad-147">系統會呼叫執行階段委派來載入受控組件，並取得針對受控方法的函式指標。</span><span class="sxs-lookup"><span data-stu-id="f04ad-147">The runtime delegate is called to load the managed assembly and get a function pointer to a managed method.</span></span> <span data-ttu-id="f04ad-148">該委派需要組件路徑、類型名稱及方法名稱作為輸入，並會傳回可用來叫用受控方法的函式指標。</span><span class="sxs-lookup"><span data-stu-id="f04ad-148">The delegate requires the assembly path, type name, and method name as inputs and returns a function pointer that can be used to invoke the managed method.</span></span>

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

<span data-ttu-id="f04ad-149">在呼叫執行階段委派期間，透過將 `nullptr` 傳遞為委派類型名稱，範例會針對受控方法使用預設簽章：</span><span class="sxs-lookup"><span data-stu-id="f04ad-149">By passing `nullptr` as the delegate type name when calling the runtime delegate, the sample uses a default signature for the managed method:</span></span>

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

<span data-ttu-id="f04ad-150">若要使用不同的簽章，可以在呼叫執行階段委派時指定委派類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f04ad-150">A different signature can be used by specifying the delegate type name when calling the runtime delegate.</span></span>

### <a name="step-4---run-managed-code"></a><span data-ttu-id="f04ad-151">步驟 4 - 執行受控程式碼！</span><span class="sxs-lookup"><span data-stu-id="f04ad-151">Step 4 - Run managed code!</span></span>

<span data-ttu-id="f04ad-152">原生主機現在可以呼叫受控方法，並向它傳遞所需的參數。</span><span class="sxs-lookup"><span data-stu-id="f04ad-152">The native host can now call the managed method and pass it the desired parameters.</span></span>

[!code-cpp[HostFxrHost#CallManaged](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a><span data-ttu-id="f04ad-153">使用 CoreClrHost.h 建立主機</span><span class="sxs-lookup"><span data-stu-id="f04ad-153">Create a host using CoreClrHost.h</span></span>

<span data-ttu-id="f04ad-154">下列步驟詳細說明如何使用 CoreClrHost.h API，在原生應用程式中啟動 .NET Core 執行階段，並呼叫受控靜態方法。</span><span class="sxs-lookup"><span data-stu-id="f04ad-154">The following steps detail how to use the CoreClrHost.h API to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="f04ad-155">本文件中的程式碼片段會使用一些 Windows 專用的 API，但[完整的範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)會顯示 Windows 和 Linux 兩者的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="f04ad-155">The code snippets in this document use some Windows-specific APIs, but the [full sample host](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) shows both Windows and Linux code paths.</span></span>

<span data-ttu-id="f04ad-156">[Unix CoreRun 主機](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun) \(英文\) 能針對使用 coreclrhost.h 進行裝載，示範更加複雜的現實範例。</span><span class="sxs-lookup"><span data-stu-id="f04ad-156">The [Unix CoreRun host](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun) shows a more complex, real-world example of hosting using coreclrhost.h.</span></span>

### <a name="step-1---find-and-load-coreclr"></a><span data-ttu-id="f04ad-157">步驟 1 - 找到並載入 CoreCLR</span><span class="sxs-lookup"><span data-stu-id="f04ad-157">Step 1 - Find and load CoreCLR</span></span>

<span data-ttu-id="f04ad-158">.NET Core 執行階段 API 是在 *coreclr.dll* 中 (Windows)、在 *libcoreclr.so* 中 (Linux)，或是在 *libcoreclr.dylib* 中 (macOS)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-158">The .NET Core runtime APIs are in *coreclr.dll* (on Windows), in *libcoreclr.so* (on Linux), or in *libcoreclr.dylib* (on macOS).</span></span> <span data-ttu-id="f04ad-159">裝載 .NET Core 的第一個步驟是載入 CoreCLR 程式庫。</span><span class="sxs-lookup"><span data-stu-id="f04ad-159">The first step to hosting .NET Core is to load the CoreCLR library.</span></span> <span data-ttu-id="f04ad-160">某些主機會探查不同的路徑，或使用輸入參數來尋找程式庫，而其他主機知道要從某個路徑 (例如，主機旁邊或從全機器位置) 進行載入。</span><span class="sxs-lookup"><span data-stu-id="f04ad-160">Some hosts probe different paths or use input parameters to find the library while others know to load it from a certain path (next to the host, for example, or from a machine-wide location).</span></span>

<span data-ttu-id="f04ad-161">找到後，便會使用 `LoadLibraryEx` (在 Windows 上) 或 `dlopen` (在 Linux/Mac 上) 載入程式庫。</span><span class="sxs-lookup"><span data-stu-id="f04ad-161">Once found, the library is loaded with `LoadLibraryEx` (on Windows) or `dlopen` (on Linux/Mac).</span></span>

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a><span data-ttu-id="f04ad-162">步驟 2 - 取得 .NET Core 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f04ad-162">Step 2 - Get .NET Core hosting functions</span></span>

<span data-ttu-id="f04ad-163">CoreClrHost 有幾個可用於裝載 .NET Core 的重要方法：</span><span class="sxs-lookup"><span data-stu-id="f04ad-163">CoreClrHost has several important methods useful for hosting .NET Core:</span></span>

* <span data-ttu-id="f04ad-164">`coreclr_initialize`：啟動 .NET Core 執行階段，並設定預設的 (且唯一的) AppDomain。</span><span class="sxs-lookup"><span data-stu-id="f04ad-164">`coreclr_initialize`: Starts the .NET Core runtime and sets up the default (and only) AppDomain.</span></span>
* <span data-ttu-id="f04ad-165">`coreclr_execute_assembly`：執行受控組件。</span><span class="sxs-lookup"><span data-stu-id="f04ad-165">`coreclr_execute_assembly`: Executes a managed assembly.</span></span>
* <span data-ttu-id="f04ad-166">`coreclr_create_delegate`：建立受控方法的函式指標。</span><span class="sxs-lookup"><span data-stu-id="f04ad-166">`coreclr_create_delegate`: Creates a function pointer to a managed method.</span></span>
* <span data-ttu-id="f04ad-167">`coreclr_shutdown`：關閉 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="f04ad-167">`coreclr_shutdown`: Shuts down the .NET Core runtime.</span></span>
* <span data-ttu-id="f04ad-168">`coreclr_shutdown_2`：如同 `coreclr_shutdown`，但還會擷取受控碼的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="f04ad-168">`coreclr_shutdown_2`: Like `coreclr_shutdown`, but also retrieves the managed code's exit code.</span></span>

<span data-ttu-id="f04ad-169">載入 CoreCLR 程式庫之後，下一個步驟是使用 `GetProcAddress` (在 Windows 上) 或 `dlsym` (在 Linux/Mac 上) 取得這些函式的參考。</span><span class="sxs-lookup"><span data-stu-id="f04ad-169">After loading the CoreCLR library, the next step is to get references to these functions using `GetProcAddress` (on Windows) or `dlsym` (on Linux/Mac).</span></span>

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a><span data-ttu-id="f04ad-170">步驟 3 - 準備執行階段屬性</span><span class="sxs-lookup"><span data-stu-id="f04ad-170">Step 3 - Prepare runtime properties</span></span>

<span data-ttu-id="f04ad-171">啟動執行階段之前，必須準備一些屬性來指定行為 (尤其是關於組件載入器)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-171">Before starting the runtime, it is necessary to prepare some properties to specify behavior (especially concerning the assembly loader).</span></span>

<span data-ttu-id="f04ad-172">常用屬性包括：</span><span class="sxs-lookup"><span data-stu-id="f04ad-172">Common properties include:</span></span>

* <span data-ttu-id="f04ad-173">`TRUSTED_PLATFORM_ASSEMBLIES`：這是執行階段預設能夠解析的組件路徑 (在 Windows 上會以 ';' 分隔，而在 Linux 上則以 ':' 分隔) 清單。</span><span class="sxs-lookup"><span data-stu-id="f04ad-173">`TRUSTED_PLATFORM_ASSEMBLIES` This is a list of assembly paths (delimited by ';' on Windows and ':' on Linux) which the runtime will be able to resolve by default.</span></span> <span data-ttu-id="f04ad-174">某些主機具有硬式編碼資訊清單，其中列出它們可以載入的組件。</span><span class="sxs-lookup"><span data-stu-id="f04ad-174">Some hosts have hard-coded manifests listing assemblies they can load.</span></span> <span data-ttu-id="f04ad-175">其他主機則會在此清單的特定位置 (例如，*coreclr.dll* 旁邊) 放入任何程式庫。</span><span class="sxs-lookup"><span data-stu-id="f04ad-175">Others will put any library in certain locations (next to *coreclr.dll*, for example) on this list.</span></span>
* <span data-ttu-id="f04ad-176">`APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。</span><span class="sxs-lookup"><span data-stu-id="f04ad-176">`APP_PATHS` This is a list of paths to probe in for an assembly if it can't be found in the trusted platform assemblies (TPA) list.</span></span> <span data-ttu-id="f04ad-177">因為主機可以進一步控制使用 TPA 清單載入哪些組件，所以主機最好確定它們預期載入哪些組件，並明確列出這些組件。</span><span class="sxs-lookup"><span data-stu-id="f04ad-177">Because the host has more control over which assemblies are loaded using the TPA list, it is a best practice for hosts to determine which assemblies they expect to load and list them explicitly.</span></span> <span data-ttu-id="f04ad-178">不過，如果需要在執行階段進行探查，此屬性可用於這種情況。</span><span class="sxs-lookup"><span data-stu-id="f04ad-178">If probing at runtime is needed, however, this property can enable that scenario.</span></span>
* <span data-ttu-id="f04ad-179">`APP_NI_PATHS`：此清單與 APP_PATHS 類似，不同之處在於其用途是作為探查原生映像的路徑。</span><span class="sxs-lookup"><span data-stu-id="f04ad-179">`APP_NI_PATHS` This list is similar to APP_PATHS except that it's meant to be paths that will be probed for native images.</span></span>
* <span data-ttu-id="f04ad-180">`NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生程式庫時，載入器應探查的路徑清單。</span><span class="sxs-lookup"><span data-stu-id="f04ad-180">`NATIVE_DLL_SEARCH_DIRECTORIES` This property is a list of paths the loader should probe when looking for native libraries called via p/invoke.</span></span>
* <span data-ttu-id="f04ad-181">`PLATFORM_RESOURCE_ROOTS`：此清單包含要在其中探查資源附屬組件的路徑 (位於文化特性專屬子目錄中)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-181">`PLATFORM_RESOURCE_ROOTS` This list includes paths to probe in for resource satellite assemblies (in culture-specific sub-directories).</span></span>

<span data-ttu-id="f04ad-182">在此範例主機中，只需列出目前目錄中的所有程式庫，即可建構 TPA 清單：</span><span class="sxs-lookup"><span data-stu-id="f04ad-182">In this sample host, the TPA list is constructed by simply listing all libraries in the current directory:</span></span>

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

<span data-ttu-id="f04ad-183">由於此範例很簡單，因此它只需要 `TRUSTED_PLATFORM_ASSEMBLIES` 屬性：</span><span class="sxs-lookup"><span data-stu-id="f04ad-183">Because the sample is simple, it only needs the `TRUSTED_PLATFORM_ASSEMBLIES` property:</span></span>

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a><span data-ttu-id="f04ad-184">步驟 4 - 啟動執行階段</span><span class="sxs-lookup"><span data-stu-id="f04ad-184">Step 4 - Start the runtime</span></span>

<span data-ttu-id="f04ad-185">不同於裝載 API 的 mscoree.h (如下所述)，CoreCLRHost.h API 只需使用單一呼叫，即可啟動執行階段並建立預設的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="f04ad-185">Unlike the mscoree.h hosting API (described below), CoreCLRHost.h APIs start the runtime and create the default AppDomain all with a single call.</span></span> <span data-ttu-id="f04ad-186">`coreclr_initialize` 函式會採用基底路徑、名稱和稍早所述的屬性，並透過 `hostHandle` 參數將控制代碼傳回到主機。</span><span class="sxs-lookup"><span data-stu-id="f04ad-186">The `coreclr_initialize` function takes a base path, name, and the properties described earlier and returns back a handle to the host via the `hostHandle` parameter.</span></span>

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a><span data-ttu-id="f04ad-187">步驟 5 - 執行受控碼！</span><span class="sxs-lookup"><span data-stu-id="f04ad-187">Step 5 - Run managed code!</span></span>

<span data-ttu-id="f04ad-188">執行階段啟動後，主機便可以呼叫受控碼。</span><span class="sxs-lookup"><span data-stu-id="f04ad-188">With the runtime started, the host can call managed code.</span></span> <span data-ttu-id="f04ad-189">這可透過幾種不同的方式來完成。</span><span class="sxs-lookup"><span data-stu-id="f04ad-189">This can be done in a couple of different ways.</span></span> <span data-ttu-id="f04ad-190">連結至這個教學課程之範例程式碼使用 `coreclr_create_delegate` 函式來建立靜態受控方法的委派。</span><span class="sxs-lookup"><span data-stu-id="f04ad-190">The sample code linked to this tutorial uses the `coreclr_create_delegate` function to create a delegate to a static managed method.</span></span> <span data-ttu-id="f04ad-191">此 API 會採用[組件名稱](../../framework/app-domains/assembly-names.md)、命名空間限定的類型名稱和方法名稱作為輸入，並傳回可用來叫用方法的委派。</span><span class="sxs-lookup"><span data-stu-id="f04ad-191">This API takes the [assembly name](../../framework/app-domains/assembly-names.md), namespace-qualified type name, and method name as inputs and returns a delegate that can be used to invoke the method.</span></span>

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

<span data-ttu-id="f04ad-192">在此範例中，主機現在可以呼叫 `managedDelegate` 來執行 `ManagedWorker.DoWork` 方法。</span><span class="sxs-lookup"><span data-stu-id="f04ad-192">In this sample, the host can now call `managedDelegate` to run the `ManagedWorker.DoWork` method.</span></span>

<span data-ttu-id="f04ad-193">或者，`coreclr_execute_assembly` 函式可用來啟動受控可執行檔。</span><span class="sxs-lookup"><span data-stu-id="f04ad-193">Alternatively, the `coreclr_execute_assembly` function can be used to launch a managed executable.</span></span> <span data-ttu-id="f04ad-194">此 API 會採用組件路徑和引數陣列作為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="f04ad-194">This API takes an assembly path and array of arguments as input parameters.</span></span> <span data-ttu-id="f04ad-195">它會載入該路徑中的組件，並叫用其 Main 方法。</span><span class="sxs-lookup"><span data-stu-id="f04ad-195">It loads the assembly at that path and invokes its main method.</span></span>

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a><span data-ttu-id="f04ad-196">步驟 6 - 關閉並清除</span><span class="sxs-lookup"><span data-stu-id="f04ad-196">Step 6 - Shutdown and clean up</span></span>

<span data-ttu-id="f04ad-197">最後，當主機完成受控碼的執行時，.NET Core 執行階段會使用 `coreclr_shutdown` 或 `coreclr_shutdown_2` 來關閉。</span><span class="sxs-lookup"><span data-stu-id="f04ad-197">Finally, when the host is done running managed code, the .NET Core runtime is shut down with `coreclr_shutdown` or `coreclr_shutdown_2`.</span></span>

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

<span data-ttu-id="f04ad-198">CoreCLR 不支援重新初始化或卸載。</span><span class="sxs-lookup"><span data-stu-id="f04ad-198">CoreCLR does not support reinitialization or unloading.</span></span> <span data-ttu-id="f04ad-199">請勿再次呼叫 `coreclr_initialize` 或卸載 CoreCLR 程式庫。</span><span class="sxs-lookup"><span data-stu-id="f04ad-199">Do not call `coreclr_initialize` again or unload the CoreCLR library.</span></span>

## <a name="create-a-host-using-mscoreeh"></a><span data-ttu-id="f04ad-200">使用 Mscoree.h 建立主機</span><span class="sxs-lookup"><span data-stu-id="f04ad-200">Create a host using Mscoree.h</span></span>

<span data-ttu-id="f04ad-201">如先前所述，CoreClrHost.h 現在是裝載 .NET Core 執行階段的慣用方法。</span><span class="sxs-lookup"><span data-stu-id="f04ad-201">As mentioned previously, CoreClrHost.h is now the preferred method of hosting the .NET Core runtime.</span></span> <span data-ttu-id="f04ad-202">不過，如果 CoreClrHost.h 介面不足 (比方說，如果需要非標準啟動旗標，或如果預設定義域需要 AppDomainManager)，您仍然可以使用 `ICLRRuntimeHost4` 介面。</span><span class="sxs-lookup"><span data-stu-id="f04ad-202">The `ICLRRuntimeHost4` interface can still be used, though, if the CoreClrHost.h interfaces aren't sufficient (if non-standard startup flags are needed, for example, or if an AppDomainManager is needed on the default domain).</span></span> <span data-ttu-id="f04ad-203">這些指示會引導您使用 mscoree.h 來裝載 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f04ad-203">These instructions will guide you through hosting .NET Core using mscoree.h.</span></span>

<span data-ttu-id="f04ad-204">[CoreRun 主機](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) \(英文\) 能針對使用 mscoree.h 進行裝載，示範更加複雜的現實範例。</span><span class="sxs-lookup"><span data-stu-id="f04ad-204">The [CoreRun host](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) shows a more complex, real-world example of hosting using mscoree.h.</span></span>

### <a name="a-note-about-mscoreeh"></a><span data-ttu-id="f04ad-205">mscoree.h 的相關注意事項</span><span class="sxs-lookup"><span data-stu-id="f04ad-205">A note about mscoree.h</span></span>
<span data-ttu-id="f04ad-206">`ICLRRuntimeHost4` .NET Core 裝載介面定義於 [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-206">The `ICLRRuntimeHost4` .NET Core hosting interface is defined in [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL).</span></span> <span data-ttu-id="f04ad-207">您的主機必須參考此檔案的標頭版本 (mscoree.h)，該檔案會在建置 [.NET Core 執行階段](https://github.com/dotnet/coreclr/)時透過 MIDL 產生。</span><span class="sxs-lookup"><span data-stu-id="f04ad-207">A header version of this file (mscoree.h), which your host will need to reference, is produced via MIDL when the [.NET Core runtime](https://github.com/dotnet/coreclr/) is built.</span></span> <span data-ttu-id="f04ad-208">如果不想建置 .NET Core 執行階段，mscoree.h 也會當作 dotnet/coreclr 存放庫中[預先建立的標頭](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc)使用。</span><span class="sxs-lookup"><span data-stu-id="f04ad-208">If you do not want to build the .NET Core runtime, mscoree.h is also available as a [pre-built header](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) in the dotnet/coreclr repository.</span></span> <span data-ttu-id="f04ad-209">您可以在 GitHub 存放庫中找到[建置 .NET Core 執行階段的指示](https://github.com/dotnet/coreclr#building-the-repository)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-209">[Instructions on building the .NET Core runtime](https://github.com/dotnet/coreclr#building-the-repository) can be found in its GitHub repository.</span></span>

### <a name="step-1---identify-the-managed-entry-point"></a><span data-ttu-id="f04ad-210">步驟 1 - 識別 Managed 進入點</span><span class="sxs-lookup"><span data-stu-id="f04ad-210">Step 1 - Identify the managed entry point</span></span>
<span data-ttu-id="f04ad-211">參考必要的標頭 (例如 [mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) 和 stdio.h) 之後，.NET Core 主機必須先找出所要使用的 Managed 進入點。</span><span class="sxs-lookup"><span data-stu-id="f04ad-211">After referencing necessary headers ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) and stdio.h, for example), one of the first things a .NET Core host must do is locate the managed entry point it will be using.</span></span> <span data-ttu-id="f04ad-212">在我們的範例主機中，只要將第一個命令列引數傳遞至主機作為 Managed 二進位檔 (將執行其 `main` 方法) 的路徑，即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="f04ad-212">In our sample host, this is done by just taking the first command line argument to our host as the path to a managed binary whose `main` method will be executed.</span></span>

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a><span data-ttu-id="f04ad-213">步驟 2 - 找到並載入 CoreCLR</span><span class="sxs-lookup"><span data-stu-id="f04ad-213">Step 2 - Find and load CoreCLR</span></span>
<span data-ttu-id="f04ad-214">.NET Core 執行階段 API 位於 *CoreCLR.dll* (Windows 上)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-214">The .NET Core runtime APIs are in *CoreCLR.dll* (on Windows).</span></span> <span data-ttu-id="f04ad-215">若要取得我們的裝載介面 (`ICLRRuntimeHost4`)，您必須找到並載入 *CoreCLR.dll*。</span><span class="sxs-lookup"><span data-stu-id="f04ad-215">To get our hosting interface (`ICLRRuntimeHost4`), it's necessary to find and load *CoreCLR.dll*.</span></span> <span data-ttu-id="f04ad-216">主機會定義尋找 *CoreCLR.dll* 的方式慣例。</span><span class="sxs-lookup"><span data-stu-id="f04ad-216">It is up to the host to define a convention for how it will locate *CoreCLR.dll*.</span></span> <span data-ttu-id="f04ad-217">某些主機預期此檔案會出現在已知的全機器位置 (例如 *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-217">Some hosts expect the file to be present in a well-known machine-wide location (such as *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*).</span></span> <span data-ttu-id="f04ad-218">其他主機則預期會從主機本身或所要裝載之應用程式旁的位置載入 *CoreCLR.dll*。</span><span class="sxs-lookup"><span data-stu-id="f04ad-218">Others expect that *CoreCLR.dll* will be loaded from a location next to either the host itself or the app to be hosted.</span></span> <span data-ttu-id="f04ad-219">不過，其他主機還是可以參考環境變數以尋找程式庫。</span><span class="sxs-lookup"><span data-stu-id="f04ad-219">Still others might consult an environment variable to find the library.</span></span>

<span data-ttu-id="f04ad-220">在 Linux 或 Mac 上，Core 執行階段程式庫分別是 *libcoreclr.so* 或 *libcoreclr.dylib*。</span><span class="sxs-lookup"><span data-stu-id="f04ad-220">On Linux or Mac, the core runtime library is *libcoreclr.so* or *libcoreclr.dylib*, respectively.</span></span>

<span data-ttu-id="f04ad-221">我們的範例主機會在一些常見的位置中探查 *CoreCLR.dll*。</span><span class="sxs-lookup"><span data-stu-id="f04ad-221">Our sample host probes a few common locations for *CoreCLR.dll*.</span></span> <span data-ttu-id="f04ad-222">找到後，必須透過 `LoadLibrary` (若是 Linux/Mac 則為 `dlopen`) 載入。</span><span class="sxs-lookup"><span data-stu-id="f04ad-222">Once found, it must be loaded via `LoadLibrary` (or `dlopen` on Linux/Mac).</span></span>

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a><span data-ttu-id="f04ad-223">步驟 3 - 取得 ICLRRuntimeHost4 執行個體</span><span class="sxs-lookup"><span data-stu-id="f04ad-223">Step 3 - Get an ICLRRuntimeHost4 Instance</span></span>
<span data-ttu-id="f04ad-224">若要擷取 `ICLRRuntimeHost4` 裝載介面，請在 `GetCLRRuntimeHost` 上呼叫 `GetProcAddress` (若是 Linux/Mac 則為 `dlsym`)，然後叫用該函式。</span><span class="sxs-lookup"><span data-stu-id="f04ad-224">The `ICLRRuntimeHost4` hosting interface is retrieved by calling `GetProcAddress` (or `dlsym` on Linux/Mac) on `GetCLRRuntimeHost`, and then invoking that function.</span></span>

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a><span data-ttu-id="f04ad-225">步驟 4 - 設定啟動旗標並啟動執行階段</span><span class="sxs-lookup"><span data-stu-id="f04ad-225">Step 4 - Set startup flags and start the runtime</span></span>
<span data-ttu-id="f04ad-226">準備好 `ICLRRuntimeHost4` 之後，現在可以指定全執行階段啟動旗標並啟動執行階段。</span><span class="sxs-lookup"><span data-stu-id="f04ad-226">With an `ICLRRuntimeHost4` in-hand, we can now specify runtime-wide startup flags and start the runtime.</span></span> <span data-ttu-id="f04ad-227">啟動旗標會決定所要使用的記憶體回收行程 (GC) (並行或伺服器)，而不論使用的是單一 AppDomain 或多個 AppDomain；它也會決定 (為了以定義域中性方式載入組件) 所要使用的載入器最佳化原則。</span><span class="sxs-lookup"><span data-stu-id="f04ad-227">Startup flags determine which garbage collector (GC) to use (concurrent or server), whether we will use a single AppDomain or multiple AppDomains, and what loader optimization policy to use (for domain-neutral loading of assemblies).</span></span>

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

<span data-ttu-id="f04ad-228">呼叫 `Start` 函式以啟動執行階段。</span><span class="sxs-lookup"><span data-stu-id="f04ad-228">The runtime is started with a call to the `Start` function.</span></span>

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a><span data-ttu-id="f04ad-229">步驟 5 - 準備 AppDomain 設定</span><span class="sxs-lookup"><span data-stu-id="f04ad-229">Step 5 - Preparing AppDomain settings</span></span>
<span data-ttu-id="f04ad-230">啟動執行階段之後，我們想要設定 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="f04ad-230">Once the runtime is started, we will want to set up an AppDomain.</span></span> <span data-ttu-id="f04ad-231">不過，建立 .NET AppDomain 時必須指定一些選項，因此必須先準備這些選項。</span><span class="sxs-lookup"><span data-stu-id="f04ad-231">There are a number of options that must be specified when creating a .NET AppDomain, however, so it's necessary to prepare those first.</span></span>

<span data-ttu-id="f04ad-232">AppDomain 旗標會指定與安全性和 Interop 相關的 AppDomain 行為。</span><span class="sxs-lookup"><span data-stu-id="f04ad-232">AppDomain flags specify AppDomain behaviors related to security and interop.</span></span> <span data-ttu-id="f04ad-233">舊版的 Silverlight 主機使用這些設定來沙箱化使用者程式碼，但最新式的 .NET Core 主機則會以完全信任的方式來執行使用者程式碼並啟用 Interop。</span><span class="sxs-lookup"><span data-stu-id="f04ad-233">Older Silverlight hosts used these settings to sandbox user code, but most modern .NET Core hosts run user code as full trust and enable interop.</span></span>

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

<span data-ttu-id="f04ad-234">決定要使用的 AppDomain 旗標之後，必須定義 AppDomain 屬性。</span><span class="sxs-lookup"><span data-stu-id="f04ad-234">After deciding which AppDomain flags to use, AppDomain properties must be defined.</span></span> <span data-ttu-id="f04ad-235">這些屬性是字串的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="f04ad-235">The properties are key/value pairs of strings.</span></span> <span data-ttu-id="f04ad-236">許多屬性與 AppDomain 載入組件的方式相關。</span><span class="sxs-lookup"><span data-stu-id="f04ad-236">Many of the properties relate to how the AppDomain will load assemblies.</span></span>

<span data-ttu-id="f04ad-237">常見的 AppDomain 屬性包括：</span><span class="sxs-lookup"><span data-stu-id="f04ad-237">Common AppDomain properties include:</span></span>

* <span data-ttu-id="f04ad-238">`TRUSTED_PLATFORM_ASSEMBLIES`：這是 AppDomain 應設定載入優先權並授與完全信任 (即使是部分信任的定義域) 的組件路徑清單 (在 Windows 上會以 `;` 分隔，而在 Linux/Mac 上則以 `:` 分隔)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-238">`TRUSTED_PLATFORM_ASSEMBLIES` This is a list of assembly paths (delimited by `;` on Windows and `:` on Linux/Mac) which the AppDomain should prioritize loading and give full trust to (even in partially-trusted domains).</span></span> <span data-ttu-id="f04ad-239">此清單可用來包含 'Framework' 組件及其他信任的模組，類似於 .NET Framework 案例中的 GAC。</span><span class="sxs-lookup"><span data-stu-id="f04ad-239">This list is meant to contain 'Framework' assemblies and other trusted modules, similar to the GAC in .NET Framework scenarios.</span></span> <span data-ttu-id="f04ad-240">某些主機會將任何程式庫放在此清單中的 *coreclr.dll* 旁，其他主機則會有針對其用途列出信任組件的硬式編碼資訊清單。</span><span class="sxs-lookup"><span data-stu-id="f04ad-240">Some hosts will put any library next to *coreclr.dll* on this list, others have hard-coded manifests listing trusted assemblies for their purposes.</span></span>
* <span data-ttu-id="f04ad-241">`APP_PATHS`：這是在信賴平台組件 (TPA) 清單中找不到組件時，要在其中探查組件的路徑清單。</span><span class="sxs-lookup"><span data-stu-id="f04ad-241">`APP_PATHS` This is a list of paths to probe in for an assembly if it can't be found in the trusted platform assemblies (TPA) list.</span></span> <span data-ttu-id="f04ad-242">因為主機可以進一步控制使用 TPA 清單載入哪些組件，所以主機最好確定它們預期載入哪些組件，並明確列出這些組件。</span><span class="sxs-lookup"><span data-stu-id="f04ad-242">Because the host has more control over which assemblies are loaded using the TPA list, it is a best practice for hosts to determine which assemblies they expect to load and list them explicitly.</span></span> <span data-ttu-id="f04ad-243">不過，如果需要在執行階段進行探查，此屬性可用於這種情況。</span><span class="sxs-lookup"><span data-stu-id="f04ad-243">If probing at runtime is needed, however, this property can enable that scenario.</span></span>
* <span data-ttu-id="f04ad-244">`APP_NI_PATHS`：此清單與 APP_PATHS 非常類似，不同之處在於其用途是作為探查原生影像的路徑。</span><span class="sxs-lookup"><span data-stu-id="f04ad-244">`APP_NI_PATHS` This list is very similar to APP_PATHS except that it's meant to be paths that will be probed for native images.</span></span>
* <span data-ttu-id="f04ad-245">`NATIVE_DLL_SEARCH_DIRECTORIES`：此屬性是想要透過 p/invoke 呼叫原生 DLL 時，載入器應探查的路徑清單。</span><span class="sxs-lookup"><span data-stu-id="f04ad-245">`NATIVE_DLL_SEARCH_DIRECTORIES` This property is a list of paths the loader should probe when looking for native DLLs called via p/invoke.</span></span>
* <span data-ttu-id="f04ad-246">`PLATFORM_RESOURCE_ROOTS`：此清單包含要在其中探查資源附屬組件的路徑 (位於文化特性專屬子目錄中)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-246">`PLATFORM_RESOURCE_ROOTS` This list includes paths to probe in for resource satellite assemblies (in culture-specific sub-directories).</span></span>

<span data-ttu-id="f04ad-247">在我們的[簡單範例主機](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)中，這些屬性會設定如下：</span><span class="sxs-lookup"><span data-stu-id="f04ad-247">In our [simple sample host](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree), these properties are set up as follows:</span></span>

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a><span data-ttu-id="f04ad-248">步驟 6 - 建立 AppDomain</span><span class="sxs-lookup"><span data-stu-id="f04ad-248">Step 6 - Create the AppDomain</span></span>
<span data-ttu-id="f04ad-249">準備好所有 AppDomain 旗標和屬性之後，即可使用 `ICLRRuntimeHost4::CreateAppDomainWithManager` 來設定 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="f04ad-249">Once all AppDomain flags and properties are prepared, `ICLRRuntimeHost4::CreateAppDomainWithManager` can be used to set up the AppDomain.</span></span> <span data-ttu-id="f04ad-250">此函式會選擇性地接受完整組件名稱和類型名稱，以用作定義域的 AppDomain 管理員。</span><span class="sxs-lookup"><span data-stu-id="f04ad-250">This function optionally takes a fully qualified assembly name and type name to use as the domain's AppDomain manager.</span></span> <span data-ttu-id="f04ad-251">AppDomain 管理員可讓主機控制 AppDomain 行為的某些層面，並可在主機不想直接叫用使用者程式碼時，提供進入點以啟動 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f04ad-251">An AppDomain manager can allow a host to control some aspects of AppDomain behavior and may provide entry points for launching managed code if the host doesn't intend to invoke user code directly.</span></span>

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a><span data-ttu-id="f04ad-252">步驟 7 - 執行 Managed 程式碼！</span><span class="sxs-lookup"><span data-stu-id="f04ad-252">Step 7 - Run managed code!</span></span>
<span data-ttu-id="f04ad-253">在 AppDomain 啟動並執行之後，主機現在可以開始執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f04ad-253">With an AppDomain up and running, the host can now start executing managed code.</span></span> <span data-ttu-id="f04ad-254">最簡單的做法是使用 `ICLRRuntimeHost4::ExecuteAssembly` 叫用 Managed 組件的進入點方法。</span><span class="sxs-lookup"><span data-stu-id="f04ad-254">The easiest way to do this is to use `ICLRRuntimeHost4::ExecuteAssembly` to invoke a managed assembly's entry point method.</span></span> <span data-ttu-id="f04ad-255">請注意，此函式僅適用於單一定義域案例。</span><span class="sxs-lookup"><span data-stu-id="f04ad-255">Note that this function only works in single-domain scenarios.</span></span>

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

<span data-ttu-id="f04ad-256">如果 `ExecuteAssembly` 不符合您的主機需求，另一個選擇是使用 `CreateDelegate` 建立靜態 Managed 方法的函式指標。</span><span class="sxs-lookup"><span data-stu-id="f04ad-256">Another option, if `ExecuteAssembly` doesn't meet your host's needs, is to use `CreateDelegate` to create a function pointer to a static managed method.</span></span> <span data-ttu-id="f04ad-257">雖然此做法要求主機必須知道所呼叫的方法簽章 (以便建立函式指標類型)，但允許主機彈性地叫用組件進入點以外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f04ad-257">This requires the host to know the signature of the method it is calling into (in order to create the function pointer type) but allows hosts the flexibility to invoke code other than an assembly's entry point.</span></span> <span data-ttu-id="f04ad-258">第二個參數中提供的組件名稱為要載入之程式庫的[完整受控組件名稱](../../framework/app-domains/assembly-names.md)。</span><span class="sxs-lookup"><span data-stu-id="f04ad-258">The assembly name provided in the second parameter is the [full managed assembly name](../../framework/app-domains/assembly-names.md) of the library to load.</span></span>

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

### <a name="step-8---clean-up"></a><span data-ttu-id="f04ad-259">步驟 8 - 清除</span><span class="sxs-lookup"><span data-stu-id="f04ad-259">Step 8 - Clean up</span></span>
<span data-ttu-id="f04ad-260">最後，主機應該藉由卸載 AppDomain、停止執行階段並釋放 `ICLRRuntimeHost4` 參考來清除自身。</span><span class="sxs-lookup"><span data-stu-id="f04ad-260">Finally, the host should clean up after itself by unloading AppDomains, stopping the runtime, and releasing the `ICLRRuntimeHost4` reference.</span></span>

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

<span data-ttu-id="f04ad-261">CoreCLR 不支援卸載。</span><span class="sxs-lookup"><span data-stu-id="f04ad-261">CoreCLR does not support unloading.</span></span> <span data-ttu-id="f04ad-262">請勿卸載 CoreCLR 程式庫。</span><span class="sxs-lookup"><span data-stu-id="f04ad-262">Do not unload the CoreCLR library.</span></span>

## <a name="conclusion"></a><span data-ttu-id="f04ad-263">結論</span><span class="sxs-lookup"><span data-stu-id="f04ad-263">Conclusion</span></span>
<span data-ttu-id="f04ad-264">建置主機之後，您可以從命令列執行主機，並傳遞主機預期的任何引數 (例如要針對 mscoree 範例主機執行的受控應用程式)，藉以進行測試。</span><span class="sxs-lookup"><span data-stu-id="f04ad-264">Once your host is built, it can be tested by running it from the command line and passing any arguments the host expects (like the managed app to run for the mscoree example host).</span></span> <span data-ttu-id="f04ad-265">指定主機要執行的 .NET Core 應用程式時，請務必使用 `dotnet build` 所產生的 .dll。</span><span class="sxs-lookup"><span data-stu-id="f04ad-265">When specifying the .NET Core app for the host to run, be sure to use the .dll that is produced by `dotnet build`.</span></span> <span data-ttu-id="f04ad-266">`dotnet publish` 為獨立式應用程式所產生的可執行檔 (.exe 檔案)，其實就是預設 .NET Core 主機 (因此應用程式可在主要情況下從命令列直接啟動)；使用者程式碼會編譯成同名的 DLL。</span><span class="sxs-lookup"><span data-stu-id="f04ad-266">Executables (.exe files) produced by `dotnet publish` for self-contained applications are actually the default .NET Core host (so that the app can be launched directly from the command line in mainline scenarios); user code is compiled into a dll of the same name.</span></span>

<span data-ttu-id="f04ad-267">如果一開始未正常運作，請再確認一次主機預期的位置中有 *coreclr.dll*、所有必要的 Framework 程式庫都在 TPA 清單中，而且 CoreCLR 的位元 (32 或 64 位元) 符合主機的建立方式。</span><span class="sxs-lookup"><span data-stu-id="f04ad-267">If things don't work initially, double-check that *coreclr.dll* is available in the location expected by the host, that all necessary Framework libraries are in the TPA list, and that CoreCLR's bitness (32- or 64-bit) matches how the host was built.</span></span>

<span data-ttu-id="f04ad-268">裝載 .NET Core 執行階段是進階案例，許多開發人員並不需要，但對於需要從原生處理序啟動 Managed 程式碼的人員，或需要更能掌控 .NET Core 執行階段行為的人員而言，這項作業可能很實用。</span><span class="sxs-lookup"><span data-stu-id="f04ad-268">Hosting the .NET Core runtime is an advanced scenario that many developers won't require, but for those who need to launch managed code from a native process, or who need more control over the .NET Core runtime's behavior, it can be very useful.</span></span>
