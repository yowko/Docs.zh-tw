---
title: "dotnet publish 命令 - .NET Core CLI"
description: "dotnet publish 命令會將 .NET Core 專案發行到目錄中。"
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2aa69217e949b970b632c4fad72838b63c2a8988
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="dotnet-publish"></a><span data-ttu-id="5ab84-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5ab84-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5ab84-104">名稱</span><span class="sxs-lookup"><span data-stu-id="5ab84-104">Name</span></span>

<span data-ttu-id="5ab84-105">`dotnet publish` - 將應用程式與其相依性封裝至資料夾中，以部署至主機系統。</span><span class="sxs-lookup"><span data-stu-id="5ab84-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5ab84-106">概要</span><span class="sxs-lookup"><span data-stu-id="5ab84-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5ab84-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="5ab84-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5ab84-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5ab84-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="5ab84-109">描述</span><span class="sxs-lookup"><span data-stu-id="5ab84-109">Description</span></span>

<span data-ttu-id="5ab84-110">`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。</span><span class="sxs-lookup"><span data-stu-id="5ab84-110">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="5ab84-111">輸出會包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="5ab84-111">The output will contain the following:</span></span>

* <span data-ttu-id="5ab84-112">組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。</span><span class="sxs-lookup"><span data-stu-id="5ab84-112">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="5ab84-113">*.deps.json* 檔案，其中包含專案的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5ab84-113">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="5ab84-114">*.runtime.config.json* 檔案，指定應用程式預期的共用執行階段，以及執行階段的其他組態選項 (例如記憶體回收類型)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-114">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="5ab84-115">應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="5ab84-115">The application's dependencies.</span></span> <span data-ttu-id="5ab84-116">這些相依性會從 NuGet 快取複製到輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="5ab84-116">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="5ab84-117">`dotnet publish` 命令的輸出已準備好部署至主機系統 (例如，伺服器、電腦、Mac、膝上型電腦) 以執行，且是準備要進行部署之應用程式的唯一正式支援方式。</span><span class="sxs-lookup"><span data-stu-id="5ab84-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="5ab84-118">根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。</span><span class="sxs-lookup"><span data-stu-id="5ab84-118">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="5ab84-119">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-119">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="5ab84-120">針對已發行應用程式的目錄結構，請參閱[目錄結構 (英文)](/aspnet/core/hosting/directory-structure)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-120">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="5ab84-121">引數</span><span class="sxs-lookup"><span data-stu-id="5ab84-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="5ab84-122">要發行的專案，如果未指定，則預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="5ab84-122">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="5ab84-123">選項</span><span class="sxs-lookup"><span data-stu-id="5ab84-123">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5ab84-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="5ab84-124">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5ab84-125">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="5ab84-125">Defines the build configuration.</span></span> <span data-ttu-id="5ab84-126">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="5ab84-126">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5ab84-127">發行所指定[目標架構](../../standard/frameworks.md)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ab84-127">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5ab84-128">您必須在專案檔中指定此目標架構。</span><span class="sxs-lookup"><span data-stu-id="5ab84-128">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="5ab84-129">即使最後的還原成功，仍強制解析所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5ab84-129">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5ab84-130">這相當於刪除 *project.assets.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="5ab84-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="5ab84-131">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5ab84-131">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="5ab84-132">指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。</span><span class="sxs-lookup"><span data-stu-id="5ab84-132">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="5ab84-133">資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="5ab84-133">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="5ab84-134">若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。</span><span class="sxs-lookup"><span data-stu-id="5ab84-134">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="5ab84-135">自 .NET Core 2.0 SDK 開始提供此選項。</span><span class="sxs-lookup"><span data-stu-id="5ab84-135">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="5ab84-136">忽略專案對專案參考，並且只還原根專案。</span><span class="sxs-lookup"><span data-stu-id="5ab84-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="5ab84-137">執行命令時，不執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="5ab84-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5ab84-138">指定輸出目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="5ab84-138">Specifies the path for the output directory.</span></span> <span data-ttu-id="5ab84-139">如果未指定，則預設為 *./bin/[configuration]/[framework]/* (與 Framework 相依的部署) 或 *./bin/[configuration]/[framework]/[runtime]* (獨立部署)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-139">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="5ab84-140">如果提供相對路徑，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="5ab84-140">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="5ab84-141">使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。</span><span class="sxs-lookup"><span data-stu-id="5ab84-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="5ab84-142">如已指定執行階段識別碼，則其預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="5ab84-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="5ab84-143">如需不同部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-143">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="5ab84-144">發行所指定執行階段的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ab84-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="5ab84-145">建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5ab84-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="5ab84-146">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="5ab84-147">預設值為發行[與 Framework 相依的部署 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5ab84-148">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="5ab84-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5ab84-149">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="5ab84-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="5ab84-150">定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="5ab84-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5ab84-151">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5ab84-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5ab84-152">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="5ab84-152">Defines the build configuration.</span></span> <span data-ttu-id="5ab84-153">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="5ab84-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5ab84-154">發行所指定[目標架構](../../standard/frameworks.md)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ab84-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5ab84-155">您必須在專案檔中指定此目標架構。</span><span class="sxs-lookup"><span data-stu-id="5ab84-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="5ab84-156">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5ab84-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="5ab84-157">指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。</span><span class="sxs-lookup"><span data-stu-id="5ab84-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="5ab84-158">資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="5ab84-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="5ab84-159">若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。</span><span class="sxs-lookup"><span data-stu-id="5ab84-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="5ab84-160">自 .NET Core 2.0 SDK 開始提供此選項。</span><span class="sxs-lookup"><span data-stu-id="5ab84-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5ab84-161">指定輸出目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="5ab84-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="5ab84-162">如果未指定，則預設為 *./bin/[configuration]/[framework]/* (與 Framework 相依的部署) 或 *./bin/[configuration]/[framework]/[runtime]* (獨立部署)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-162">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="5ab84-163">如果提供相對路徑，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="5ab84-163">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="5ab84-164">發行所指定執行階段的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ab84-164">Publishes the application for a given runtime.</span></span> <span data-ttu-id="5ab84-165">建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5ab84-165">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="5ab84-166">如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="5ab84-167">預設值為發行[與 Framework 相依的部署 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-167">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5ab84-168">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="5ab84-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5ab84-169">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="5ab84-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="5ab84-170">定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。</span><span class="sxs-lookup"><span data-stu-id="5ab84-170">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5ab84-171">範例</span><span class="sxs-lookup"><span data-stu-id="5ab84-171">Examples</span></span>

<span data-ttu-id="5ab84-172">發行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="5ab84-172">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="5ab84-173">使用指定的專案檔發行應用程式：</span><span class="sxs-lookup"><span data-stu-id="5ab84-173">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="5ab84-174">使用 `netcoreapp1.1` 架構發行目前目錄中的專案：</span><span class="sxs-lookup"><span data-stu-id="5ab84-174">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="5ab84-175">使用 `netcoreapp1.1` 架構和 `OS X 10.10` 的執行階段來發行目前應用程式 (您必須在專案檔中列出這個 RID)。</span><span class="sxs-lookup"><span data-stu-id="5ab84-175">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="5ab84-176">發行目前的應用程式，但不還原專案對專案 (P2P) 的參考，還原作業期間只有根專案 (.NET Core SDK 2.0 及更新版本)：</span><span class="sxs-lookup"><span data-stu-id="5ab84-176">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="5ab84-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ab84-177">See also</span></span>

* [<span data-ttu-id="5ab84-178">目標架構</span><span class="sxs-lookup"><span data-stu-id="5ab84-178">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="5ab84-179">執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="5ab84-179">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)