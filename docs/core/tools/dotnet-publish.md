---
title: dotnet publish 命令
description: dotnet publish 命令會將 .NET Core 專案發行到目錄中。
ms.date: 05/29/2018
ms.openlocfilehash: 4612c8cd1f63550905ef7c6d94af050892b1620c
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117608"
---
# <a name="dotnet-publish"></a><span data-ttu-id="cd854-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="cd854-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cd854-104">名稱</span><span class="sxs-lookup"><span data-stu-id="cd854-104">Name</span></span>

<span data-ttu-id="cd854-105">`dotnet publish` - 將應用程式與其相依性封裝至資料夾中，以部署至主機系統。</span><span class="sxs-lookup"><span data-stu-id="cd854-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cd854-106">概要</span><span class="sxs-lookup"><span data-stu-id="cd854-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cd854-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd854-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cd854-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd854-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cd854-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cd854-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="cd854-110">描述</span><span class="sxs-lookup"><span data-stu-id="cd854-110">Description</span></span>

<span data-ttu-id="cd854-111">`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。</span><span class="sxs-lookup"><span data-stu-id="cd854-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="cd854-112">此輸出包含下列資產：</span><span class="sxs-lookup"><span data-stu-id="cd854-112">The output includes the following assets:</span></span>

- <span data-ttu-id="cd854-113">組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。</span><span class="sxs-lookup"><span data-stu-id="cd854-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="cd854-114">*.deps.json* 檔案，其中包含專案的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="cd854-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="cd854-115">指定應用程式預期之共用執行階段的 *.runtime.config.json* 檔案，以及適用於執行階段的其他設定選項 (例如記憶體回收類型)。</span><span class="sxs-lookup"><span data-stu-id="cd854-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="cd854-116">應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd854-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="cd854-117">`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。</span><span class="sxs-lookup"><span data-stu-id="cd854-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="cd854-118">這是準備應用程式以供部署的唯一正式支援的方法。</span><span class="sxs-lookup"><span data-stu-id="cd854-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="cd854-119">根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="cd854-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="cd854-120">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cd854-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="cd854-121">針對已發行應用程式的目錄結構，請參閱[目錄結構 (英文)](/aspnet/core/hosting/directory-structure)。</span><span class="sxs-lookup"><span data-stu-id="cd854-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="cd854-122">引數</span><span class="sxs-lookup"><span data-stu-id="cd854-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="cd854-123">要發佈的專案。</span><span class="sxs-lookup"><span data-stu-id="cd854-123">The project to publish.</span></span> <span data-ttu-id="cd854-124">它是 [C#](csproj.md)、F# 或 Visual Basic 專案檔的路徑與檔案名稱，或包含 C#、F# 或 Visual Basic 專案檔之目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="cd854-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="cd854-125">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="cd854-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="cd854-126">選項</span><span class="sxs-lookup"><span data-stu-id="cd854-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cd854-127">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd854-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="cd854-128">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="cd854-128">Defines the build configuration.</span></span> <span data-ttu-id="cd854-129">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="cd854-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cd854-130">發行所指定[目標架構](../../standard/frameworks.md)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd854-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cd854-131">您必須在專案檔中指定此目標架構。</span><span class="sxs-lookup"><span data-stu-id="cd854-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="cd854-132">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="cd854-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cd854-133">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd854-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="cd854-134">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="cd854-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="cd854-135">指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。</span><span class="sxs-lookup"><span data-stu-id="cd854-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="cd854-136">資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="cd854-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="cd854-137">若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="cd854-138">自 .NET Core 2.0 SDK 開始提供此選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="cd854-139">不會在發佈前建置專案。</span><span class="sxs-lookup"><span data-stu-id="cd854-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="cd854-140">選項也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="cd854-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="cd854-141">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="cd854-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="cd854-142">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="cd854-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cd854-143">指定輸出目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="cd854-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="cd854-144">如果未指定，預設為 *./bin/[configuration]/[framework]/publish/* (適用於架構相依的部署) 或 *./bin/[configuration]/[framework]/[runtime]/publish/* (適用於獨立部署)。</span><span class="sxs-lookup"><span data-stu-id="cd854-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="cd854-145">如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="cd854-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="cd854-146">使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。</span><span class="sxs-lookup"><span data-stu-id="cd854-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="cd854-147">如已指定執行階段識別碼，則其預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cd854-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="cd854-148">如需不同部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cd854-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="cd854-149">發行所指定執行階段的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd854-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="cd854-150">建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="cd854-151">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="cd854-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cd854-152">預設值為發行[與 Framework 相依的部署 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)。</span><span class="sxs-lookup"><span data-stu-id="cd854-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cd854-153">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="cd854-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cd854-154">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="cd854-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="cd854-155">定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="cd854-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cd854-156">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd854-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="cd854-157">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="cd854-157">Defines the build configuration.</span></span> <span data-ttu-id="cd854-158">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="cd854-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cd854-159">發行所指定[目標架構](../../standard/frameworks.md)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd854-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cd854-160">您必須在專案檔中指定此目標架構。</span><span class="sxs-lookup"><span data-stu-id="cd854-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="cd854-161">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="cd854-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cd854-162">指定這個旗標等同於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd854-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="cd854-163">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="cd854-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="cd854-164">指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。</span><span class="sxs-lookup"><span data-stu-id="cd854-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="cd854-165">資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="cd854-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="cd854-166">若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="cd854-167">自 .NET Core 2.0 SDK 開始提供此選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="cd854-168">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="cd854-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="cd854-169">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="cd854-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cd854-170">指定輸出目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="cd854-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="cd854-171">如果未指定，預設為 *./bin/[configuration]/[framework]/publish/* (適用於架構相依的部署) 或 *./bin/[configuration]/[framework]/[runtime]/publish/* (適用於獨立部署)。</span><span class="sxs-lookup"><span data-stu-id="cd854-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="cd854-172">如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="cd854-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="cd854-173">使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。</span><span class="sxs-lookup"><span data-stu-id="cd854-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="cd854-174">如已指定執行階段識別碼，則其預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cd854-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="cd854-175">如需不同部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cd854-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="cd854-176">發行所指定執行階段的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd854-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="cd854-177">建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="cd854-178">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="cd854-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cd854-179">預設值為發行[與 Framework 相依的部署 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)。</span><span class="sxs-lookup"><span data-stu-id="cd854-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cd854-180">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="cd854-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cd854-181">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="cd854-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="cd854-182">定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="cd854-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cd854-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cd854-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="cd854-184">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="cd854-184">Defines the build configuration.</span></span> <span data-ttu-id="cd854-185">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="cd854-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cd854-186">發行所指定[目標架構](../../standard/frameworks.md)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd854-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cd854-187">您必須在專案檔中指定此目標架構。</span><span class="sxs-lookup"><span data-stu-id="cd854-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="cd854-188">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="cd854-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="cd854-189">指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。</span><span class="sxs-lookup"><span data-stu-id="cd854-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="cd854-190">資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="cd854-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="cd854-191">若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="cd854-192">自 .NET Core 2.0 SDK 開始提供此選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cd854-193">指定輸出目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="cd854-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="cd854-194">如果未指定，預設為 *./bin/[configuration]/[framework]/publish/* (適用於架構相依的部署) 或 *./bin/[configuration]/[framework]/[runtime]/publish/* (適用於獨立部署)。</span><span class="sxs-lookup"><span data-stu-id="cd854-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="cd854-195">如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="cd854-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="cd854-196">發行所指定執行階段的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd854-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="cd854-197">建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="cd854-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="cd854-198">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="cd854-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cd854-199">預設值為發行[與 Framework 相依的部署 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)。</span><span class="sxs-lookup"><span data-stu-id="cd854-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cd854-200">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="cd854-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cd854-201">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="cd854-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="cd854-202">定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="cd854-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="cd854-203">範例</span><span class="sxs-lookup"><span data-stu-id="cd854-203">Examples</span></span>

<span data-ttu-id="cd854-204">發行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="cd854-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="cd854-205">使用指定的專案檔發行應用程式：</span><span class="sxs-lookup"><span data-stu-id="cd854-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="cd854-206">使用 `netcoreapp1.1` 架構發行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="cd854-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="cd854-207">使用 `netcoreapp1.1` 架構和 `OS X 10.10` 的執行階段來發行目前應用程式 (您必須在專案檔中列出這個 RID)。</span><span class="sxs-lookup"><span data-stu-id="cd854-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="cd854-208">發行目前的應用程式，但不還原專案對專案 (P2P) 的參考，還原作業期間只有根專案 (.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="cd854-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="cd854-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd854-209">See also</span></span>

- [<span data-ttu-id="cd854-210">目標架構</span><span class="sxs-lookup"><span data-stu-id="cd854-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="cd854-211">執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="cd854-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
