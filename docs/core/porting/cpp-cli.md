---
title: 將C++/CLI 專案遷移到 .NET 核心
description: 瞭解有關將C++/CLI 專案移植到 .NET Core。
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964927"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a><span data-ttu-id="95faf-103">如何將C++/CLI 專案移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="95faf-103">How to port a C++/CLI project to .NET Core</span></span>

<span data-ttu-id="95faf-104">從 .NET 核心 3.1 和 Visual Studio 2019 版本 16.4 開始[，C++/CLI 專案](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp)可以定位 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="95faf-104">Beginning with .NET Core 3.1 and Visual Studio 2019 version 16.4, [C++/CLI projects](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) can target .NET Core.</span></span> <span data-ttu-id="95faf-105">通過這種支援，可以使用C++/CLI 互通層將 Windows 桌面應用程式移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="95faf-105">This support makes it possible to port Windows desktop applications with C++/CLI interop layers to .NET Core.</span></span> <span data-ttu-id="95faf-106">本文介紹如何將C++/CLI 專案從 .NET 框架移植到 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="95faf-106">This article describes how to port C++/CLI projects from .NET Framework to .NET Core 3.1.</span></span>

## <a name="ccli-net-core-limitations"></a><span data-ttu-id="95faf-107">C++/CLI .NET 核心限制</span><span class="sxs-lookup"><span data-stu-id="95faf-107">C++/CLI .NET Core limitations</span></span>

<span data-ttu-id="95faf-108">與其他語言相比，將C++/CLI 專案移植到 .NET Core 有一些重要限制：</span><span class="sxs-lookup"><span data-stu-id="95faf-108">There are some important limitations to porting C++/CLI projects to .NET Core compared to other languages:</span></span>

* <span data-ttu-id="95faf-109">C++/CLI 支援 .NET Core 僅支援 Windows。</span><span class="sxs-lookup"><span data-stu-id="95faf-109">C++/CLI support for .NET Core is Windows only.</span></span>
* <span data-ttu-id="95faf-110">C++/CLI 專案不能針對 .NET 標準，只能定位 .NET 核心（或 .NET 框架）。</span><span class="sxs-lookup"><span data-stu-id="95faf-110">C++/CLI projects can't target .NET Standard, only .NET Core (or .NET Framework).</span></span>
* <span data-ttu-id="95faf-111">C++/CLI 專案不支援新的 SDK 樣式的專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="95faf-111">C++/CLI projects don't support the new SDK-style project file format.</span></span> <span data-ttu-id="95faf-112">相反，即使以 .NET Core 為目標，C++/CLI 專案也使用現有的 vcxproj 檔案格式。</span><span class="sxs-lookup"><span data-stu-id="95faf-112">Instead, even when targeting .NET Core, C++/CLI projects use the existing vcxproj file format.</span></span>
* <span data-ttu-id="95faf-113">C++/CLI 專案不能多目標多個 .NET 平臺。</span><span class="sxs-lookup"><span data-stu-id="95faf-113">C++/CLI projects can't multitarget multiple .NET platforms.</span></span> <span data-ttu-id="95faf-114">如果需要為 .NET 框架和 .NET Core 構建C++/CLI 專案，請使用單獨的專案檔案。</span><span class="sxs-lookup"><span data-stu-id="95faf-114">If you need to build a C++/CLI project for both .NET Framework and .NET Core, use separate project files.</span></span>
* <span data-ttu-id="95faf-115">.NET Core 不支援或`-clr:pure``-clr:safe`編譯，僅支援新`-clr:netcore`選項（相當於`-clr`.NET 框架）。</span><span class="sxs-lookup"><span data-stu-id="95faf-115">.NET Core doesn't support `-clr:pure` or `-clr:safe` compilation, only the new `-clr:netcore` option (which is equivalent to `-clr` for .NET Framework).</span></span>

## <a name="port-a-ccli-project"></a><span data-ttu-id="95faf-116">移植C++/CLI 專案</span><span class="sxs-lookup"><span data-stu-id="95faf-116">Port a C++/CLI project</span></span>

<span data-ttu-id="95faf-117">要將C++/CLI 專案移植到 .NET Core，對 vcxproj 檔進行以下更改。</span><span class="sxs-lookup"><span data-stu-id="95faf-117">To port a C++/CLI project to .NET Core, make the following changes to the vcxproj file.</span></span> <span data-ttu-id="95faf-118">這些遷移步驟與其他專案類型所需的步驟不同，因為C++/CLI 專案不使用 SDK 樣式的專案檔案。</span><span class="sxs-lookup"><span data-stu-id="95faf-118">These migration steps differ from the steps needed for other project types because C++/CLI projects don't use SDK-style project files.</span></span>

1. <span data-ttu-id="95faf-119">將`<CLRSupport>true</CLRSupport>`屬性替換為`<CLRSupport>NetCore</CLRSupport>`。</span><span class="sxs-lookup"><span data-stu-id="95faf-119">Replace `<CLRSupport>true</CLRSupport>` properties with `<CLRSupport>NetCore</CLRSupport>`.</span></span> <span data-ttu-id="95faf-120">此屬性通常位於特定于配置的屬性組中，因此您可能需要在多個位置替換它。</span><span class="sxs-lookup"><span data-stu-id="95faf-120">This property is often in configuration-specific property groups, so you may need to replace it in multiple places.</span></span>
2. <span data-ttu-id="95faf-121">將`<TargetFrameworkVersion>`屬性替換為`<TargetFramework>netcoreapp3.1</TargetFramework>`。</span><span class="sxs-lookup"><span data-stu-id="95faf-121">Replace `<TargetFrameworkVersion>` properties with `<TargetFramework>netcoreapp3.1</TargetFramework>`.</span></span>
3. <span data-ttu-id="95faf-122">刪除任何 .NET 框架引用`<Reference Include="System" />`（如 ）。</span><span class="sxs-lookup"><span data-stu-id="95faf-122">Remove any .NET Framework references (like `<Reference Include="System" />`).</span></span> <span data-ttu-id="95faf-123">.NET 核心 SDK 程式集在使用`<CLRSupport>NetCore</CLRSupport>`時會自動引用。</span><span class="sxs-lookup"><span data-stu-id="95faf-123">.NET Core SDK assemblies are automatically referenced when using `<CLRSupport>NetCore</CLRSupport>`.</span></span>
4. <span data-ttu-id="95faf-124">根據需要更新 cpp 檔中的 API 使用方式，以刪除對 .NET Core 不可用的 API。</span><span class="sxs-lookup"><span data-stu-id="95faf-124">Update API usage in cpp files, as necessary, to remove APIs unavailable to .NET Core.</span></span> <span data-ttu-id="95faf-125">由於C++/CLI 專案往往相當薄的交互操作層，因此通常不需要太多的更改。</span><span class="sxs-lookup"><span data-stu-id="95faf-125">Because C++/CLI projects tend to be fairly thin interop layers, there are often not many changes needed.</span></span> <span data-ttu-id="95faf-126">[.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)可用於識別C++/CLI 二進位檔案使用的不支援的 .NET API，就像與純託管二進位檔案一樣。</span><span class="sxs-lookup"><span data-stu-id="95faf-126">The [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) can be used to identify unsupported .NET APIs used by C++/CLI binaries just as with purely managed binaries.</span></span> <span data-ttu-id="95faf-127">[庫移植指南](./libraries.md#determine-portability)中提供了確定代碼可攜性和更新專案以使用 .NET Core API 的指南。</span><span class="sxs-lookup"><span data-stu-id="95faf-127">Guidelines for determining code portability and updating projects to work with .NET Core APIs are available in the [library porting guidance](./libraries.md#determine-portability).</span></span>

### <a name="wpf-and-windows-forms-usage"></a><span data-ttu-id="95faf-128">WPF 和 Windows 表單使用方式</span><span class="sxs-lookup"><span data-stu-id="95faf-128">WPF and Windows Forms usage</span></span>

<span data-ttu-id="95faf-129">.NET 核心C++/CLI 專案可以使用 Windows 表單和 WPF API。</span><span class="sxs-lookup"><span data-stu-id="95faf-129">.NET Core C++/CLI projects can use Windows Forms and WPF APIs.</span></span> <span data-ttu-id="95faf-130">要使用這些 Windows 桌面 API，您需要向 UI 庫添加顯式框架引用。</span><span class="sxs-lookup"><span data-stu-id="95faf-130">To use these Windows desktop APIs, you need to add explicit framework references to the UI libraries.</span></span> <span data-ttu-id="95faf-131">使用 Windows 桌面 API 的 SDK 樣式專案使用`Microsoft.NET.Sdk.WindowsDesktop`SDK 自動引用必要的框架庫。</span><span class="sxs-lookup"><span data-stu-id="95faf-131">SDK-style projects that use Windows desktop APIs reference the necessary framework libraries automatically by using the `Microsoft.NET.Sdk.WindowsDesktop` SDK.</span></span> <span data-ttu-id="95faf-132">由於C++/CLI 專案不使用 SDK 風格的專案格式，因此在定位 .NET Core 時，需要添加顯式框架引用。</span><span class="sxs-lookup"><span data-stu-id="95faf-132">Because C++/CLI projects don't use the SDK-style project format, they need to add explicit framework references when targeting .NET Core.</span></span>

<span data-ttu-id="95faf-133">要使用 Windows 表單 API，添加此引用到 vcxproj 檔：</span><span class="sxs-lookup"><span data-stu-id="95faf-133">To use Windows Forms APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

<span data-ttu-id="95faf-134">要使用 WPF API，添加此引用到 vcxproj 檔：</span><span class="sxs-lookup"><span data-stu-id="95faf-134">To use WPF APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

<span data-ttu-id="95faf-135">要同時使用 Windows 表單和 WPF API，請使用此引用添加到 vcxproj 檔：</span><span class="sxs-lookup"><span data-stu-id="95faf-135">To use both Windows Forms and WPF APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

<span data-ttu-id="95faf-136">目前，無法使用 Visual Studio 的參考管理器添加這些引用。</span><span class="sxs-lookup"><span data-stu-id="95faf-136">Currently, it's not possible to add these references using Visual Studio's reference manager.</span></span> <span data-ttu-id="95faf-137">而是手動更新專案檔案。</span><span class="sxs-lookup"><span data-stu-id="95faf-137">Instead, update the project file manually.</span></span> <span data-ttu-id="95faf-138">此更新可以通過卸載專案然後編輯專案檔案在 Visual Studio 中完成。</span><span class="sxs-lookup"><span data-stu-id="95faf-138">This update can be done in Visual Studio by unloading the project and then editing the project file.</span></span> <span data-ttu-id="95faf-139">您還可以使用其他編輯器，如 VS 代碼。</span><span class="sxs-lookup"><span data-stu-id="95faf-139">You can also use another editor like VS Code.</span></span>

## <a name="build-without-msbuild"></a><span data-ttu-id="95faf-140">無需 MSBuild 即可生成</span><span class="sxs-lookup"><span data-stu-id="95faf-140">Build without MSBuild</span></span>

<span data-ttu-id="95faf-141">無需使用 MSBuild 即可構建C++/CLI 專案。</span><span class="sxs-lookup"><span data-stu-id="95faf-141">It's also possible to build C++/CLI projects without using MSBuild.</span></span> <span data-ttu-id="95faf-142">按照以下步驟直接使用*cl.exe*和*link.exe*為 .NET Core 構建C++/CLI 專案：</span><span class="sxs-lookup"><span data-stu-id="95faf-142">Follow these steps to build a C++/CLI project for .NET Core directly with *cl.exe* and *link.exe*:</span></span>

1. <span data-ttu-id="95faf-143">編譯時，將傳遞給`-clr:netcore` *cl.exe*。</span><span class="sxs-lookup"><span data-stu-id="95faf-143">When compiling, pass `-clr:netcore` to *cl.exe*.</span></span>
2. <span data-ttu-id="95faf-144">引用必需 .NET 核心引用程式集。</span><span class="sxs-lookup"><span data-stu-id="95faf-144">Reference necessary .NET Core reference assemblies.</span></span>
3. <span data-ttu-id="95faf-145">連結時，將 .NET Core 應用主機目錄`LibPath`作為 （以便可以找到*ijwhost.lib）* 。</span><span class="sxs-lookup"><span data-stu-id="95faf-145">When linking, provide the .NET Core app host directory as a `LibPath` (so that *ijwhost.lib* can be found).</span></span>
4. <span data-ttu-id="95faf-146">將*ijwhost.dll（* 從 .NET Core 應用主機目錄）複製到專案的輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="95faf-146">Copy *ijwhost.dll* (from the .NET Core app host directory) to the project's output directory.</span></span>
5. <span data-ttu-id="95faf-147">確保運行託管代碼的應用程式的第一個元件存在[運行時 config.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)檔。</span><span class="sxs-lookup"><span data-stu-id="95faf-147">Make sure a [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) file exists for the first component of the application that will run managed code.</span></span> <span data-ttu-id="95faf-148">如果應用程式具有託管進入點，將自動創建和`runtime.config`複製檔。</span><span class="sxs-lookup"><span data-stu-id="95faf-148">If the application has a managed entry point, a `runtime.config` file will be created and copied automatically.</span></span> <span data-ttu-id="95faf-149">但是，如果應用程式具有本機進入點，則需要為第一個C++/CLI 庫創建一個`runtimeconfig.json`檔才能使用 .NET Core 運行時。</span><span class="sxs-lookup"><span data-stu-id="95faf-149">If the application has a native entry point, though, you need to create a `runtimeconfig.json` file for the first C++/CLI library to use the .NET Core runtime.</span></span>

## <a name="known-issues"></a><span data-ttu-id="95faf-150">已知問題</span><span class="sxs-lookup"><span data-stu-id="95faf-150">Known issues</span></span>

<span data-ttu-id="95faf-151">在以 .NET Core 為目標C++/CLI 專案時，有幾個已知問題需要關注。</span><span class="sxs-lookup"><span data-stu-id="95faf-151">There are a couple known issues to look out for when working with C++/CLI projects targeting .NET Core.</span></span>

* <span data-ttu-id="95faf-152">.NET Core C++/CLI 專案中的 WPF 框架引用當前會導致一些有關無法導入符號的無關警告。</span><span class="sxs-lookup"><span data-stu-id="95faf-152">A WPF framework reference in .NET Core C++/CLI projects currently causes some extraneous warnings about being unable to import symbols.</span></span> <span data-ttu-id="95faf-153">可以安全地忽略這些警告，並且應該儘快修復。</span><span class="sxs-lookup"><span data-stu-id="95faf-153">These warnings can be safely ignored and should be fixed soon.</span></span>
* <span data-ttu-id="95faf-154">如果應用程式具有本機進入點，則首先執行託管代碼C++/CLI 庫需要[運行時 config.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)檔。</span><span class="sxs-lookup"><span data-stu-id="95faf-154">If the application has a native entry point, the C++/CLI library that first executes managed code needs a [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) file.</span></span> <span data-ttu-id="95faf-155">當 .NET 核心運行時啟動時，使用此設定檔。</span><span class="sxs-lookup"><span data-stu-id="95faf-155">This config file is used when the .NET Core runtime starts.</span></span> <span data-ttu-id="95faf-156">C++/CLI 專案尚未在生成`runtimeconfig.json`時自動創建檔，因此必須手動生成該檔。</span><span class="sxs-lookup"><span data-stu-id="95faf-156">C++/CLI projects don't create `runtimeconfig.json` files automatically at build time yet, so the file must be generated manually.</span></span> <span data-ttu-id="95faf-157">如果從託管進入點調用C++/CLI 庫，則C++/CLI 庫不需要`runtimeconfig.json`檔（因為進入點程式集將在啟動運行時時使用）。</span><span class="sxs-lookup"><span data-stu-id="95faf-157">If a C++/CLI library is called from a managed entry point, then the C++/CLI library doesn't need a `runtimeconfig.json` file (since the entry point assembly will have one that is used when starting the runtime).</span></span> <span data-ttu-id="95faf-158">下面顯示了一`runtimeconfig.json`個簡單的示例檔。</span><span class="sxs-lookup"><span data-stu-id="95faf-158">A simple sample `runtimeconfig.json` file is shown below.</span></span> <span data-ttu-id="95faf-159">有關詳細資訊，請參閱[GitHub 上的規範](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="95faf-159">For more information, see the [spec on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
