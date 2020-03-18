---
title: dotnet publish 命令
description: dotnet 發佈命令將 .NET Core 專案或解決方案發佈到目錄。
ms.date: 02/24/2020
ms.openlocfilehash: c34618409c9a539043c84c7e03daa8aa249d64f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146551"
---
# <a name="dotnet-publish"></a><span data-ttu-id="347b6-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="347b6-103">dotnet publish</span></span>

<span data-ttu-id="347b6-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="347b6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="347b6-105">名稱</span><span class="sxs-lookup"><span data-stu-id="347b6-105">Name</span></span>

<span data-ttu-id="347b6-106">`dotnet publish`- 將應用程式及其依賴項發佈到資料夾以部署到託管系統。</span><span class="sxs-lookup"><span data-stu-id="347b6-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="347b6-107">概要</span><span class="sxs-lookup"><span data-stu-id="347b6-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="347b6-108">描述</span><span class="sxs-lookup"><span data-stu-id="347b6-108">Description</span></span>

<span data-ttu-id="347b6-109">`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。</span><span class="sxs-lookup"><span data-stu-id="347b6-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="347b6-110">此輸出包含下列資產：</span><span class="sxs-lookup"><span data-stu-id="347b6-110">The output includes the following assets:</span></span>

- <span data-ttu-id="347b6-111">組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。</span><span class="sxs-lookup"><span data-stu-id="347b6-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="347b6-112">包含專案的所有依賴項的 *.deps.json*檔。</span><span class="sxs-lookup"><span data-stu-id="347b6-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="347b6-113">一個 *.runtimeconfig.json*檔，用於指定應用程式期望的共用運行時以及運行時的其他配置選項（例如，垃圾回收類型）。</span><span class="sxs-lookup"><span data-stu-id="347b6-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="347b6-114">應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="347b6-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="347b6-115">`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。</span><span class="sxs-lookup"><span data-stu-id="347b6-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="347b6-116">這是準備應用程式以供部署的唯一正式支援的方法。</span><span class="sxs-lookup"><span data-stu-id="347b6-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="347b6-117">根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="347b6-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="347b6-118">引數</span><span class="sxs-lookup"><span data-stu-id="347b6-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="347b6-119">要發佈的專案或解決方案。</span><span class="sxs-lookup"><span data-stu-id="347b6-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="347b6-120">`PROJECT`是[C#、F#](csproj.md)或 Visual Basic 專案檔案的路徑和檔案名，或包含 C#、F# 或 Visual Basic 專案檔案的目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="347b6-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="347b6-121">如果未指定目錄，則預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="347b6-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="347b6-122">`SOLUTION`是解決方案檔 *（.sln*副檔名） 的路徑和檔案名，或包含解決方案檔的目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="347b6-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="347b6-123">如果未指定目錄，則預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="347b6-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="347b6-124">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="347b6-124">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="347b6-125">選項。</span><span class="sxs-lookup"><span data-stu-id="347b6-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="347b6-126">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="347b6-126">Defines the build configuration.</span></span> <span data-ttu-id="347b6-127">大多數專案的預設值為 ，`Debug`但您可以覆蓋專案中的組建組態設置。</span><span class="sxs-lookup"><span data-stu-id="347b6-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="347b6-128">發行所指定[目標架構](../../standard/frameworks.md)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="347b6-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="347b6-129">您必須在專案檔中指定此目標架構。</span><span class="sxs-lookup"><span data-stu-id="347b6-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="347b6-130">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="347b6-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="347b6-131">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="347b6-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="347b6-132">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="347b6-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="347b6-133">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="347b6-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="347b6-134">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="347b6-134">For example, to complete authentication.</span></span> <span data-ttu-id="347b6-135">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="347b6-135">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="347b6-136">指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。</span><span class="sxs-lookup"><span data-stu-id="347b6-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="347b6-137">清單檔是[`dotnet store`命令](dotnet-store.md)的輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="347b6-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="347b6-138">若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。</span><span class="sxs-lookup"><span data-stu-id="347b6-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="347b6-139">不會在發佈前建置專案。</span><span class="sxs-lookup"><span data-stu-id="347b6-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="347b6-140">選項也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="347b6-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="347b6-141">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="347b6-141">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="347b6-142">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="347b6-142">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="347b6-143">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="347b6-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="347b6-144">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="347b6-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="347b6-145">指定輸出目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="347b6-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="347b6-146">如果未指定，它預設為 *./bin/[配置]/[框架]/發佈/* 對於與運行時相關的可執行和跨平臺二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="347b6-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="347b6-147">它預設為 *./bin/[配置]/[框架]/[運行時]/發佈/* 對於自包含可執行檔。</span><span class="sxs-lookup"><span data-stu-id="347b6-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="347b6-148">如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="347b6-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="347b6-149">使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。</span><span class="sxs-lookup"><span data-stu-id="347b6-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="347b6-150">預設值為`true`指定運行時識別碼。</span><span class="sxs-lookup"><span data-stu-id="347b6-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="347b6-151">有關詳細資訊，請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="347b6-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="347b6-152">相當於 `--self-contained false`。</span><span class="sxs-lookup"><span data-stu-id="347b6-152">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="347b6-153">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="347b6-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="347b6-154">發行所指定執行階段的應用程式。</span><span class="sxs-lookup"><span data-stu-id="347b6-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="347b6-155">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="347b6-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="347b6-156">有關詳細資訊，請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="347b6-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="347b6-157">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="347b6-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="347b6-158">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="347b6-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="347b6-159">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="347b6-159">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="347b6-160">定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="347b6-160">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="347b6-161">範例</span><span class="sxs-lookup"><span data-stu-id="347b6-161">Examples</span></span>

- <span data-ttu-id="347b6-162">為目前的目錄中的專案創建[與運行時相關的跨平臺二進位檔案](../deploying/index.md#produce-a-cross-platform-binary)：</span><span class="sxs-lookup"><span data-stu-id="347b6-162">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="347b6-163">從 .NET Core 3.0 SDK 開始，此示例還會為當前平臺創建[與運行時相關的可執行檔](../deploying/index.md#publish-runtime-dependent)。</span><span class="sxs-lookup"><span data-stu-id="347b6-163">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="347b6-164">為目前的目錄中的專案為特定運行時創建[自包含可執行檔](../deploying/index.md#publish-self-contained)：</span><span class="sxs-lookup"><span data-stu-id="347b6-164">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="347b6-165">RID 必須位於專案檔案中。</span><span class="sxs-lookup"><span data-stu-id="347b6-165">The RID must be in the project file.</span></span>

- <span data-ttu-id="347b6-166">為目前的目錄中的專案為特定平臺創建[與運行時相關的可執行檔](../deploying/index.md#publish-runtime-dependent)：</span><span class="sxs-lookup"><span data-stu-id="347b6-166">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="347b6-167">RID 必須位於專案檔案中。</span><span class="sxs-lookup"><span data-stu-id="347b6-167">The RID must be in the project file.</span></span> <span data-ttu-id="347b6-168">此示例適用于 .NET Core 3.0 SDK 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="347b6-168">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="347b6-169">在目前的目錄中發佈專案，用於特定運行時和目標框架：</span><span class="sxs-lookup"><span data-stu-id="347b6-169">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="347b6-170">發佈指定的專案檔案：</span><span class="sxs-lookup"><span data-stu-id="347b6-170">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="347b6-171">發佈當前應用程式，但不還原專案到專案 （P2P） 引用，只是還原操作期間的根專案：</span><span class="sxs-lookup"><span data-stu-id="347b6-171">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="347b6-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="347b6-172">See also</span></span>

- [<span data-ttu-id="347b6-173">.NET 核心應用程式發佈概述</span><span class="sxs-lookup"><span data-stu-id="347b6-173">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="347b6-174">使用 .NET 核心 CLI 發佈 .NET 核心應用</span><span class="sxs-lookup"><span data-stu-id="347b6-174">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="347b6-175">目標框架</span><span class="sxs-lookup"><span data-stu-id="347b6-175">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="347b6-176">執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="347b6-176">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="347b6-177">[使用 macOS Catalina 公證](../install/macos-notarization-issues.md)有關詳細資訊，請參閱他關注以下資源：</span><span class="sxs-lookup"><span data-stu-id="347b6-177">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="347b6-178">已發佈應用程式的目錄結構</span><span class="sxs-lookup"><span data-stu-id="347b6-178">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
