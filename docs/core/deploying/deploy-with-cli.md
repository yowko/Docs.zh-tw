---
title: 使用 .NET 核心 CLI 發佈應用
description: 瞭解如何使用 .NET 核心 CLI 命令發佈 .NET 核心應用。
author: thraka
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f4c2a4ccf551c53e4aa4e125cb5720d6f1cc9601
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399067"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a><span data-ttu-id="d9061-103">使用 .NET 核心 CLI 發佈 .NET 核心應用</span><span class="sxs-lookup"><span data-stu-id="d9061-103">Publish .NET Core apps with the .NET Core CLI</span></span>

<span data-ttu-id="d9061-104">本文示範如何從命令列發佈 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9061-104">This article demonstrates how you can publish your .NET Core application from the command line.</span></span> <span data-ttu-id="d9061-105">.NET Core 提供三種發佈應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="d9061-105">.NET Core provides three ways to publish your applications.</span></span> <span data-ttu-id="d9061-106">Framework 相依部署會產生跨平台的 .dll 檔案，以使用本機安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="d9061-106">Framework-dependent deployment produces a cross-platform .dll file that uses the locally installed .NET Core runtime.</span></span> <span data-ttu-id="d9061-107">Framework 相依可執行檔會產生平台特定的可執行檔，來使用本機安裝的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="d9061-107">Framework-dependent executable produces a platform-specific executable that uses the locally installed .NET Core runtime.</span></span> <span data-ttu-id="d9061-108">獨立式可執行檔則會產生平台特定的可執行檔，並包含 .NET Core 執行階段的本機複本。</span><span class="sxs-lookup"><span data-stu-id="d9061-108">Self-contained executable produces a platform-specific executable and includes a local copy of the .NET Core runtime.</span></span>

<span data-ttu-id="d9061-109">如需這些發佈模式的概觀，請參閱 [.NET Core 應用程式部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-109">For an overview of these publishing modes, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="d9061-110">需要一些使用 CLI 的快速說明嗎？</span><span class="sxs-lookup"><span data-stu-id="d9061-110">Looking for some quick help on using the CLI?</span></span> <span data-ttu-id="d9061-111">下表顯示一些如何發佈應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="d9061-111">The following table shows some examples of how to publish your app.</span></span> <span data-ttu-id="d9061-112">您可以使用 `-f <TFM>` 參數或藉由編輯專案檔來指定目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="d9061-112">You can specify the target framework with the `-f <TFM>` parameter or by editing the project file.</span></span> <span data-ttu-id="d9061-113">如需詳細資訊，請參閱[發佈基本概念](#publishing-basics)。</span><span class="sxs-lookup"><span data-stu-id="d9061-113">For more information, see [Publishing basics](#publishing-basics).</span></span>

| <span data-ttu-id="d9061-114">發佈模式</span><span class="sxs-lookup"><span data-stu-id="d9061-114">Publish Mode</span></span> | <span data-ttu-id="d9061-115">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="d9061-115">SDK Version</span></span> | <span data-ttu-id="d9061-116">Command</span><span class="sxs-lookup"><span data-stu-id="d9061-116">Command</span></span> |
| ------------ | ----------- | ------- |
| <span data-ttu-id="d9061-117">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="d9061-117">Framework-dependent deployment</span></span> | <span data-ttu-id="d9061-118">2.x</span><span class="sxs-lookup"><span data-stu-id="d9061-118">2.x</span></span> | `dotnet publish -c Release` |
| <span data-ttu-id="d9061-119">Framework 相依可執行檔</span><span class="sxs-lookup"><span data-stu-id="d9061-119">Framework-dependent executable</span></span> | <span data-ttu-id="d9061-120">2.2</span><span class="sxs-lookup"><span data-stu-id="d9061-120">2.2</span></span> | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | <span data-ttu-id="d9061-121">3.0</span><span class="sxs-lookup"><span data-stu-id="d9061-121">3.0</span></span> | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | <span data-ttu-id="d9061-122">3.0\*</span><span class="sxs-lookup"><span data-stu-id="d9061-122">3.0\*</span></span> | `dotnet publish -c Release` |
| <span data-ttu-id="d9061-123">自封式部署</span><span class="sxs-lookup"><span data-stu-id="d9061-123">Self-contained deployment</span></span>      | <span data-ttu-id="d9061-124">2.1</span><span class="sxs-lookup"><span data-stu-id="d9061-124">2.1</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | <span data-ttu-id="d9061-125">2.2</span><span class="sxs-lookup"><span data-stu-id="d9061-125">2.2</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | <span data-ttu-id="d9061-126">3.0</span><span class="sxs-lookup"><span data-stu-id="d9061-126">3.0</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |

<span data-ttu-id="d9061-127">\* 使用 SDK 3.0 版時，相依於架構的可執行檔是執行基本 `dotnet publish` 命令時的預設發佈模式。</span><span class="sxs-lookup"><span data-stu-id="d9061-127">\* When using SDK version 3.0, framework-dependent executable is the default publishing mode when running the basic `dotnet publish` command.</span></span> <span data-ttu-id="d9061-128">這只適用於以 **.NET Core 2.1** 或 **.NET Core 3.0** 為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="d9061-128">This only applies when the project targets either **.NET Core 2.1** or **.NET Core 3.0**.</span></span>

## <a name="publishing-basics"></a><span data-ttu-id="d9061-129">發佈基本概念</span><span class="sxs-lookup"><span data-stu-id="d9061-129">Publishing basics</span></span>

<span data-ttu-id="d9061-130">專案檔的 `<TargetFramework>` 設定會指定發佈應用程式時的預設目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="d9061-130">The `<TargetFramework>` setting of the project file specifies the default target framework when you publish your app.</span></span> <span data-ttu-id="d9061-131">您可以將目標 Framework 變更為任何有效的[目標 Framework Moniker (TFM)](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-131">You can change the target framework to any valid [Target Framework Moniker (TFM)](../../standard/frameworks.md).</span></span> <span data-ttu-id="d9061-132">例如，如果您的專案使用 `<TargetFramework>netcoreapp2.2</TargetFramework>`，就會建立以 .NET Core 2.2 為目標的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="d9061-132">For example, if your project uses `<TargetFramework>netcoreapp2.2</TargetFramework>`, a binary that targets .NET Core 2.2 is created.</span></span> <span data-ttu-id="d9061-133">此設置中指定的 TFM 是[`dotnet publish`](../tools/dotnet-publish.md)命令使用的預設目標。</span><span class="sxs-lookup"><span data-stu-id="d9061-133">The TFM specified in this setting is the default target used by the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="d9061-134">如果您想要以多個 Framework 為目標，則可以將 `<TargetFrameworks>` 設定設為以分號隔開的多個 TFM 值。</span><span class="sxs-lookup"><span data-stu-id="d9061-134">If you want to target more than one framework, you can set the `<TargetFrameworks>` setting to more than one TFM value separated by a semicolon.</span></span> <span data-ttu-id="d9061-135">您可以使用 `dotnet publish -f <TFM>` 命令來發佈其中一個 Framework。</span><span class="sxs-lookup"><span data-stu-id="d9061-135">You can publish one of the frameworks with the `dotnet publish -f <TFM>` command.</span></span> <span data-ttu-id="d9061-136">例如，如果您的專案具有 `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` 並執行 `dotnet publish -f netcoreapp2.1`，就會建立以 .NET Core 2.1 為目標的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="d9061-136">For example, if you have `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` and run `dotnet publish -f netcoreapp2.1`, a binary that targets .NET Core 2.1 is created.</span></span>

<span data-ttu-id="d9061-137">除非另行設置，否則命令的[`dotnet publish`](../tools/dotnet-publish.md)輸出目錄為`./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`。</span><span class="sxs-lookup"><span data-stu-id="d9061-137">Unless otherwise set, the output directory of the [`dotnet publish`](../tools/dotnet-publish.md) command is `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`.</span></span> <span data-ttu-id="d9061-138">除非使用 `-c` 參數加以變更，否則預設的**組建組態**模式為 [偵錯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9061-138">The default **BUILD-CONFIGURATION** mode is **Debug** unless changed with the `-c` parameter.</span></span> <span data-ttu-id="d9061-139">例如，`dotnet publish -c Release -f netcoreapp2.1` 會發佈至 `myfolder/bin/Release/netcoreapp2.1/publish/`。</span><span class="sxs-lookup"><span data-stu-id="d9061-139">For example, `dotnet publish -c Release -f netcoreapp2.1` publishes to `myfolder/bin/Release/netcoreapp2.1/publish/`.</span></span>

<span data-ttu-id="d9061-140">如果使用 .NET Core SDK 3.0 或更高版本，則針對 .NET Core 版本 2.1、2.2、3.0 或更高版本的應用的預設發佈模式是依賴于框架的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d9061-140">If you use .NET Core SDK 3.0 or later, the default publish mode for apps that target .NET Core versions 2.1, 2.2, 3.0, or a later version, is framework-dependent executable.</span></span>

<span data-ttu-id="d9061-141">如果使用 .NET Core SDK 2.1，則針對 .NET Core 版本 2.1 和 2.2 的應用的預設發佈模式與框架相關的部署。</span><span class="sxs-lookup"><span data-stu-id="d9061-141">If you use .NET Core SDK 2.1, the default publish mode for apps that target .NET Core versions 2.1 and 2.2 is framework-dependent deployment.</span></span>

### <a name="native-dependencies"></a><span data-ttu-id="d9061-142">原生相依性</span><span class="sxs-lookup"><span data-stu-id="d9061-142">Native dependencies</span></span>

<span data-ttu-id="d9061-143">如果您的應用程式具有原生相依性，它可能無法在不同的作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="d9061-143">If your app has native dependencies, it may not run on a different operating system.</span></span> <span data-ttu-id="d9061-144">例如，如果您的應用程式使用原生 Windows API，它就不會在 macOS 或 Linux 上執行。</span><span class="sxs-lookup"><span data-stu-id="d9061-144">For example, if your app uses the native Windows API, it won't run on macOS or Linux.</span></span> <span data-ttu-id="d9061-145">您必須提供平台特定程式碼，並為每個平台編譯可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d9061-145">You would need to provide platform-specific code and compile an executable for each platform.</span></span>

<span data-ttu-id="d9061-146">另外，請考慮如果您參考的程式庫具有原生相依性，您的應用程式可能無法在每個平台上執行。</span><span class="sxs-lookup"><span data-stu-id="d9061-146">Consider also, if a library you referenced has a native dependency, your app may not run on every platform.</span></span> <span data-ttu-id="d9061-147">不過，您參考的 NuGet 套件可能包含了平台特定版本，以便為您處理必要的原生相依性。</span><span class="sxs-lookup"><span data-stu-id="d9061-147">However, it's possible a NuGet package you're referencing has included platform-specific versions to handle the required native dependencies for you.</span></span>

<span data-ttu-id="d9061-148">散發具有原生相依性的應用程式時，您可能需要使用 `dotnet publish -r <RID>` 參數來指定想要為其發佈的目標平台。</span><span class="sxs-lookup"><span data-stu-id="d9061-148">When distributing an app with native dependencies, you may need to use the `dotnet publish -r <RID>` switch to specify the target platform you want to publish for.</span></span> <span data-ttu-id="d9061-149">如需執行階段識別碼清單，請參閱[執行階段識別碼 (RID) 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-149">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

<span data-ttu-id="d9061-150">平台特定二進位檔的詳細資訊涵蓋在 [Framework 相依可執行檔](#framework-dependent-executable)和[獨立式部署](#self-contained-deployment)章節中。</span><span class="sxs-lookup"><span data-stu-id="d9061-150">More information about platform-specific binaries is covered in the [Framework-dependent executable](#framework-dependent-executable) and [Self-contained deployment](#self-contained-deployment) sections.</span></span>

## <a name="sample-app"></a><span data-ttu-id="d9061-151">範例應用程式</span><span class="sxs-lookup"><span data-stu-id="d9061-151">Sample app</span></span>

<span data-ttu-id="d9061-152">您可以使用以下應用來流覽發佈命令。</span><span class="sxs-lookup"><span data-stu-id="d9061-152">You can use the following app to explore the publishing commands.</span></span> <span data-ttu-id="d9061-153">在終端機中執行下列命令即可建立此應用程式：</span><span class="sxs-lookup"><span data-stu-id="d9061-153">The app is created by running the following commands in your terminal:</span></span>

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

<span data-ttu-id="d9061-154">主控台範本所產生的 `Program.cs` 或 `Program.vb` 檔案必須變更如下：</span><span class="sxs-lookup"><span data-stu-id="d9061-154">The `Program.cs` or `Program.vb` file that is generated by the console template needs to be changed to the following:</span></span>

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

<span data-ttu-id="d9061-155">運行應用時 （），[`dotnet run`](../tools/dotnet-run.md)將顯示以下輸出：</span><span class="sxs-lookup"><span data-stu-id="d9061-155">When you run the app ([`dotnet run`](../tools/dotnet-run.md)), the following output is displayed:</span></span>

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a><span data-ttu-id="d9061-156">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="d9061-156">Framework-dependent deployment</span></span>

<span data-ttu-id="d9061-157">若為 .NET Core SDK 2.x CLI，Framework 相依部署 (FDD) 是基本 `dotnet publish` 命令的預設模式。</span><span class="sxs-lookup"><span data-stu-id="d9061-157">For the .NET Core SDK 2.x CLI, framework-dependent deployment (FDD) is the default mode for the basic `dotnet publish` command.</span></span>

<span data-ttu-id="d9061-158">當您將應用程式發佈為 FDD 時，就會在 `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` 資料夾中建立 `<PROJECT-NAME>.dll` 檔案。</span><span class="sxs-lookup"><span data-stu-id="d9061-158">When you publish your app as an FDD, a `<PROJECT-NAME>.dll` file is created in the `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` folder.</span></span> <span data-ttu-id="d9061-159">若要執行您的應用程式，請巡覽至輸出資料夾，並使用 `dotnet <PROJECT-NAME>.dll` 命令。</span><span class="sxs-lookup"><span data-stu-id="d9061-159">To run your app, navigate to the output folder and use the `dotnet <PROJECT-NAME>.dll` command.</span></span>

<span data-ttu-id="d9061-160">您的應用程式會設定為以 .NET Core 特定版本為目標。</span><span class="sxs-lookup"><span data-stu-id="d9061-160">Your app is configured to target a specific version of .NET Core.</span></span> <span data-ttu-id="d9061-161">目標 .NET 核心運行時必須在應用運行的任何電腦上。</span><span class="sxs-lookup"><span data-stu-id="d9061-161">That targeted .NET Core runtime is required to be on any machine where your app runs.</span></span> <span data-ttu-id="d9061-162">例如，如果您的應用程式以 .NET Core 2.2 為目標，則應用程式執行所在的任何電腦都必須已安裝 .NET Core 2.2 執行階段。</span><span class="sxs-lookup"><span data-stu-id="d9061-162">For example, if your app targets .NET Core 2.2, any machine that your app runs on must have the .NET Core 2.2 runtime installed.</span></span> <span data-ttu-id="d9061-163">依照[發佈基本概念](#publishing-basics)一節中所述，您可以編輯專案檔來變更預設的目標 Framework，或以多個 Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="d9061-163">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="d9061-164">發佈 FDD 會建立一個應用程式，以自動向前復原到應用程式執行所在系統上可用的最新 .NET Core 安全性修補程式。</span><span class="sxs-lookup"><span data-stu-id="d9061-164">Publishing an FDD creates an app that automatically rolls-forward to the latest .NET Core security patch available on the system that runs the app.</span></span> <span data-ttu-id="d9061-165">如需編譯時期版本繫結的詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md#framework-dependent-apps-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="d9061-165">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

## <a name="framework-dependent-executable"></a><span data-ttu-id="d9061-166">Framework 相依可執行檔</span><span class="sxs-lookup"><span data-stu-id="d9061-166">Framework-dependent executable</span></span>

<span data-ttu-id="d9061-167">對於 .NET 核心 SDK 3.x CLI，與框架相關的可執行性 （FDE）`dotnet publish`是基本命令的預設模式。</span><span class="sxs-lookup"><span data-stu-id="d9061-167">For the .NET Core SDK 3.x CLI, framework-dependent executable (FDE) is the default mode for the basic `dotnet publish` command.</span></span> <span data-ttu-id="d9061-168">只要您想要針對當前作業系統，就不需要指定任何其他參數。</span><span class="sxs-lookup"><span data-stu-id="d9061-168">You don't need to specify any other parameters, as long as you want to target the current operating system.</span></span>

<span data-ttu-id="d9061-169">在此模式中，將會建立平台特定可執行檔主機來裝載您的跨平台應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9061-169">In this mode, a platform-specific executable host is created to host your cross-platform app.</span></span> <span data-ttu-id="d9061-170">此模式類似于 FDD，因為 FDD 需要`dotnet`命令形式的主機。</span><span class="sxs-lookup"><span data-stu-id="d9061-170">This mode is similar to FDD, as FDD requires a host in the form of the `dotnet` command.</span></span> <span data-ttu-id="d9061-171">主機可執行檔名因平臺而異，並且命名為類似`<PROJECT-FILE>.exe`。</span><span class="sxs-lookup"><span data-stu-id="d9061-171">The host executable filename varies per platform and is named something similar to `<PROJECT-FILE>.exe`.</span></span> <span data-ttu-id="d9061-172">您可以直接運行此可執行檔，而不是調用`dotnet <PROJECT-FILE>.dll`，這仍然是運行應用的可接受方式。</span><span class="sxs-lookup"><span data-stu-id="d9061-172">You can run this executable directly instead of calling `dotnet <PROJECT-FILE>.dll`, which is still an acceptable way to run the app.</span></span>

<span data-ttu-id="d9061-173">您的應用程式會設定為以 .NET Core 特定版本為目標。</span><span class="sxs-lookup"><span data-stu-id="d9061-173">Your app is configured to target a specific version of .NET Core.</span></span> <span data-ttu-id="d9061-174">目標 .NET 核心運行時必須在應用運行的任何電腦上。</span><span class="sxs-lookup"><span data-stu-id="d9061-174">That targeted .NET Core runtime is required to be on any machine where your app runs.</span></span> <span data-ttu-id="d9061-175">例如，如果您的應用程式以 .NET Core 2.2 為目標，則應用程式執行所在的任何電腦都必須已安裝 .NET Core 2.2 執行階段。</span><span class="sxs-lookup"><span data-stu-id="d9061-175">For example, if your app targets .NET Core 2.2, any machine that your app runs on must have the .NET Core 2.2 runtime installed.</span></span> <span data-ttu-id="d9061-176">依照[發佈基本概念](#publishing-basics)一節中所述，您可以編輯專案檔來變更預設的目標 Framework，或以多個 Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="d9061-176">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="d9061-177">發佈 FDE 會建立一個應用程式，以自動向前復原到應用程式執行所在系統上可用的最新 .NET Core 安全性修補程式。</span><span class="sxs-lookup"><span data-stu-id="d9061-177">Publishing an FDE creates an app that automatically rolls-forward to the latest .NET Core security patch available on the system that runs the app.</span></span> <span data-ttu-id="d9061-178">如需編譯時期版本繫結的詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md#framework-dependent-apps-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="d9061-178">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

<span data-ttu-id="d9061-179">對於 .NET Core 2.2 及更早版本，必須使用以下帶有`dotnet publish`命令的開關來發佈 FDE：</span><span class="sxs-lookup"><span data-stu-id="d9061-179">For .NET Core 2.2 and earlier, you must use the following switches with the `dotnet publish` command to publish an FDE:</span></span>

- <span data-ttu-id="d9061-180">`-r <RID>` 此參數會使用識別碼 (RID) 來指定目標平台。</span><span class="sxs-lookup"><span data-stu-id="d9061-180">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="d9061-181">如需執行階段識別碼清單，請參閱[執行階段識別碼 (RID) 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-181">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="d9061-182">`--self-contained false` 此參數會指示 .NET Core SDK 將可執行檔建立為 FDE。</span><span class="sxs-lookup"><span data-stu-id="d9061-182">`--self-contained false` This switch tells the .NET Core SDK to create an executable as an FDE.</span></span>

<span data-ttu-id="d9061-183">只要您使用 `-r` 參數，輸出資料夾路徑就會變更為： `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`</span><span class="sxs-lookup"><span data-stu-id="d9061-183">Whenever you use the `-r` switch, the output folder path changes to: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`</span></span>

<span data-ttu-id="d9061-184">如果您使用[範例應用程式](#sample-app)，請執行 `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`。</span><span class="sxs-lookup"><span data-stu-id="d9061-184">If you use the [example app](#sample-app), run `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`.</span></span> <span data-ttu-id="d9061-185">此命令會建立下列可執行檔： `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`</span><span class="sxs-lookup"><span data-stu-id="d9061-185">This command creates the following executable: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="d9061-186">您可以啟用**全域無差異模式**來減少您部署的大小總計。</span><span class="sxs-lookup"><span data-stu-id="d9061-186">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="d9061-187">此模式適用於非全域應用程式，其能使用格式化慣例、大小寫慣例及字串比較，還有[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)的排序次序。</span><span class="sxs-lookup"><span data-stu-id="d9061-187">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="d9061-188">有關**全球化不變模式**以及如何啟用它的詳細資訊，請參閱[.NET 核心全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-188">For more information about **globalization invariant mode** and how to enable it, see [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

## <a name="self-contained-deployment"></a><span data-ttu-id="d9061-189">自封式部署</span><span class="sxs-lookup"><span data-stu-id="d9061-189">Self-contained deployment</span></span>

<span data-ttu-id="d9061-190">當您發佈獨立式部署 (SCD) 時，.NET Core SDK 會建立平台特定的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d9061-190">When you publish a self-contained deployment (SCD), the .NET Core SDK creates a platform-specific executable.</span></span> <span data-ttu-id="d9061-191">發佈 SCD 包括運行應用所需的所有 .NET Core 檔，但它不包括[.NET Core 的本機依賴項](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-191">Publishing an SCD includes all required .NET Core files to run your app but it doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span> <span data-ttu-id="d9061-192">在執行應用程式之前，系統上必須具有這些相依性。</span><span class="sxs-lookup"><span data-stu-id="d9061-192">These dependencies must be present on the system before the app runs.</span></span>

<span data-ttu-id="d9061-193">發佈 SCD 會創建一個不會向前滾動到最新可用的 .NET Core 安全修補程式的應用。</span><span class="sxs-lookup"><span data-stu-id="d9061-193">Publishing an SCD creates an app that doesn't roll forward to the latest available .NET Core security patch.</span></span> <span data-ttu-id="d9061-194">如需編譯時期版本繫結的詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md#self-contained-deployments-include-the-selected-runtime)。</span><span class="sxs-lookup"><span data-stu-id="d9061-194">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).</span></span>

<span data-ttu-id="d9061-195">您必須使用下列參數搭配 `dotnet publish` 命令來發佈 SCD：</span><span class="sxs-lookup"><span data-stu-id="d9061-195">You must use the following switches with the `dotnet publish` command to publish an SCD:</span></span>

- <span data-ttu-id="d9061-196">`-r <RID>` 此參數會使用識別碼 (RID) 來指定目標平台。</span><span class="sxs-lookup"><span data-stu-id="d9061-196">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="d9061-197">如需執行階段識別碼清單，請參閱[執行階段識別碼 (RID) 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-197">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="d9061-198">`--self-contained true` 此參數會指示 .NET Core SDK 將可執行檔建立為 SCD。</span><span class="sxs-lookup"><span data-stu-id="d9061-198">`--self-contained true` This switch tells the .NET Core SDK to create an executable as an SCD.</span></span>

> [!NOTE]
> <span data-ttu-id="d9061-199">您可以啟用**全域無差異模式**來減少您部署的大小總計。</span><span class="sxs-lookup"><span data-stu-id="d9061-199">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="d9061-200">此模式適用於非全域應用程式，其能使用格式化慣例、大小寫慣例及字串比較，還有[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)的排序次序。</span><span class="sxs-lookup"><span data-stu-id="d9061-200">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="d9061-201">有關**全球化不變模式**以及如何啟用它的詳細資訊，請參閱[.NET 核心全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d9061-201">For more information about **globalization invariant mode** and how to enable it, see [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9061-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9061-202">See also</span></span>

- [<span data-ttu-id="d9061-203">.NET Core 應用程式部署概觀</span><span class="sxs-lookup"><span data-stu-id="d9061-203">.NET Core Application Deployment Overview</span></span>](index.md)
- [<span data-ttu-id="d9061-204">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="d9061-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
