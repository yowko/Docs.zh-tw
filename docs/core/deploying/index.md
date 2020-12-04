---
title: 應用程式發佈
description: 瞭解發佈 .NET Core 應用程式的方式。 .NET Core 可以發佈平臺特定或跨平臺應用程式。 您可以將應用程式發佈為獨立或與 framework 相依的應用程式。 每個模式都會影響使用者執行您應用程式的方式。
ms.date: 04/01/2020
ms.openlocfilehash: 03d53c8b5184d7276a69a1058d6b1b2f1e62dc81
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599573"
---
# <a name="net-core-application-publishing-overview"></a><span data-ttu-id="df42f-106">.NET Core 應用程式發行總覽</span><span class="sxs-lookup"><span data-stu-id="df42f-106">.NET Core application publishing overview</span></span>

<span data-ttu-id="df42f-107">您使用 .NET Core 建立的應用程式可以在兩種不同的模式下發行，而此模式會影響使用者執行您應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="df42f-107">Applications you create with .NET Core can be published in two different modes, and the mode affects how a user runs your app.</span></span>

<span data-ttu-id="df42f-108">將您的應用程式發佈為 *獨立* 應用程式時，會產生包含 .net Core 執行時間和程式庫的應用程式，以及您的應用程式及其相依性。</span><span class="sxs-lookup"><span data-stu-id="df42f-108">Publishing your app as *self-contained* produces an application that includes the .NET Core runtime and libraries, and your application and its dependencies.</span></span> <span data-ttu-id="df42f-109">應用程式的使用者可以在未安裝 .NET Core 執行時間的電腦上執行它。</span><span class="sxs-lookup"><span data-stu-id="df42f-109">Users of the application can run it on a machine that doesn't have the .NET Core runtime installed.</span></span>

<span data-ttu-id="df42f-110">將您的應用程式發佈為與 *framework 相依* 的專案，會產生只包含應用程式本身及其相依性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-110">Publishing your app as *framework-dependent* produces an application that includes only your application itself and its dependencies.</span></span> <span data-ttu-id="df42f-111">應用程式的使用者必須分別安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="df42f-111">Users of the application have to separately install the .NET Core runtime.</span></span>

<span data-ttu-id="df42f-112">這兩種發行模式預設都會產生平臺特定的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-112">Both publishing modes produce a platform-specific executable by default.</span></span> <span data-ttu-id="df42f-113">您可以建立不含可執行檔的 Framework 相依應用程式，而這些應用程式會跨平臺。</span><span class="sxs-lookup"><span data-stu-id="df42f-113">Framework-dependent applications can be created without an executable, and these applications are cross-platform.</span></span>

<span data-ttu-id="df42f-114">當產生可執行檔時，您可以使用執行時間識別碼 (RID) 來指定目標平臺。</span><span class="sxs-lookup"><span data-stu-id="df42f-114">When an executable is produced, you can specify the target platform with a runtime identifier (RID).</span></span> <span data-ttu-id="df42f-115">如需有關 Rid 的詳細資訊，請參閱 [.Net CORE RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="df42f-115">For more information about RIDs, see [.NET Core RID Catalog](../rid-catalog.md).</span></span>

<span data-ttu-id="df42f-116">下表概述每個 SDK 版本用來將應用程式發佈為架構相依或獨立的命令：</span><span class="sxs-lookup"><span data-stu-id="df42f-116">The following table outlines the commands used to publish an app as framework-dependent or self-contained, per SDK version:</span></span>

| <span data-ttu-id="df42f-117">類型</span><span class="sxs-lookup"><span data-stu-id="df42f-117">Type</span></span>                                                                                     | <span data-ttu-id="df42f-118">SDK 2.1</span><span class="sxs-lookup"><span data-stu-id="df42f-118">SDK 2.1</span></span> | <span data-ttu-id="df42f-119">SDK 3。x</span><span class="sxs-lookup"><span data-stu-id="df42f-119">SDK 3.x</span></span> | <span data-ttu-id="df42f-120">命令</span><span class="sxs-lookup"><span data-stu-id="df42f-120">Command</span></span> |
| ---------------------------------------------------------------------------------------  | ------- | ------- | ------- |
| <span data-ttu-id="df42f-121">適用于目前平臺的[framework 相依可執行檔](#publish-framework-dependent)。</span><span class="sxs-lookup"><span data-stu-id="df42f-121">[framework-dependent executable](#publish-framework-dependent) for the current platform.</span></span> |         | <span data-ttu-id="df42f-122">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-122">✔️</span></span>      | [`dotnet publish`](../tools/dotnet-publish.md) |
| <span data-ttu-id="df42f-123">特定平臺的[framework 相依可執行檔](#publish-framework-dependent)。</span><span class="sxs-lookup"><span data-stu-id="df42f-123">[framework-dependent executable](#publish-framework-dependent) for a specific platform.</span></span>  |         | <span data-ttu-id="df42f-124">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-124">✔️</span></span>      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| <span data-ttu-id="df42f-125">[framework 相依的跨平臺二進位](#publish-framework-dependent)檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-125">[framework-dependent cross-platform binary](#publish-framework-dependent).</span></span>               | <span data-ttu-id="df42f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-126">✔️</span></span>      | <span data-ttu-id="df42f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-127">✔️</span></span>      | [`dotnet publish`](../tools/dotnet-publish.md) |
| <span data-ttu-id="df42f-128">[獨立可執行檔](#publish-self-contained)。</span><span class="sxs-lookup"><span data-stu-id="df42f-128">[self-contained executable](#publish-self-contained).</span></span>                                    | <span data-ttu-id="df42f-129">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-129">✔️</span></span>      | <span data-ttu-id="df42f-130">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-130">✔️</span></span>      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

<span data-ttu-id="df42f-131">如需詳細資訊，請參閱 [.Net Core dotnet publish 命令](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="df42f-131">For more information, see [.NET Core dotnet publish command](../tools/dotnet-publish.md).</span></span>

## <a name="produce-an-executable"></a><span data-ttu-id="df42f-132">產生可執行檔</span><span class="sxs-lookup"><span data-stu-id="df42f-132">Produce an executable</span></span>

<span data-ttu-id="df42f-133">可執行檔不是跨平臺。</span><span class="sxs-lookup"><span data-stu-id="df42f-133">Executables aren't cross-platform.</span></span> <span data-ttu-id="df42f-134">它們是專屬於作業系統和 CPU 架構所特有。</span><span class="sxs-lookup"><span data-stu-id="df42f-134">They're specific to an operating system and CPU architecture.</span></span> <span data-ttu-id="df42f-135">當您發行應用程式並建立可執行檔時，您可以將應用程式發佈為 [獨立](#publish-self-contained) 或與 [framework 相依](#publish-framework-dependent)的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-135">When publishing your app and creating an executable, you can publish the app as [self-contained](#publish-self-contained) or [framework-dependent](#publish-framework-dependent).</span></span> <span data-ttu-id="df42f-136">將應用程式發佈為獨立應用程式時，會包含 .NET Core 執行時間與應用程式，而應用程式的使用者在執行應用程式之前，不需要擔心安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="df42f-136">Publishing an app as self-contained includes the .NET Core runtime with the app, and users of the app don't have to worry about installing .NET Core before running the app.</span></span> <span data-ttu-id="df42f-137">發佈為與 framework 相依的應用程式不包含 .NET Core 執行時間和程式庫;只會包含應用程式和協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="df42f-137">Apps published as framework-dependent don't include the .NET Core runtime and libraries; only the app and 3rd-party dependencies are included.</span></span>

<span data-ttu-id="df42f-138">下列命令會產生可執行檔：</span><span class="sxs-lookup"><span data-stu-id="df42f-138">The following commands produce an executable:</span></span>

| <span data-ttu-id="df42f-139">類型</span><span class="sxs-lookup"><span data-stu-id="df42f-139">Type</span></span>                                                                                     | <span data-ttu-id="df42f-140">SDK 2.1</span><span class="sxs-lookup"><span data-stu-id="df42f-140">SDK 2.1</span></span> | <span data-ttu-id="df42f-141">SDK 3。x</span><span class="sxs-lookup"><span data-stu-id="df42f-141">SDK 3.x</span></span> | <span data-ttu-id="df42f-142">命令</span><span class="sxs-lookup"><span data-stu-id="df42f-142">Command</span></span> |
| ---------------------------------------------------------------------------------------- | ------- | ------- | ------- |
| <span data-ttu-id="df42f-143">適用于目前平臺的[framework 相依可執行檔](#publish-framework-dependent)。</span><span class="sxs-lookup"><span data-stu-id="df42f-143">[framework-dependent executable](#publish-framework-dependent) for the current platform.</span></span> |         | <span data-ttu-id="df42f-144">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-144">✔️</span></span>      | [`dotnet publish`](../tools/dotnet-publish.md) |
| <span data-ttu-id="df42f-145">特定平臺的[framework 相依可執行檔](#publish-framework-dependent)。</span><span class="sxs-lookup"><span data-stu-id="df42f-145">[framework-dependent executable](#publish-framework-dependent) for a specific platform.</span></span>  |         | <span data-ttu-id="df42f-146">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-146">✔️</span></span>      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| <span data-ttu-id="df42f-147">[獨立可執行檔](#publish-self-contained)。</span><span class="sxs-lookup"><span data-stu-id="df42f-147">[self-contained executable](#publish-self-contained).</span></span>                                    | <span data-ttu-id="df42f-148">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-148">✔️</span></span>      | <span data-ttu-id="df42f-149">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-149">✔️</span></span>      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a><span data-ttu-id="df42f-150">產生跨平臺二進位檔</span><span class="sxs-lookup"><span data-stu-id="df42f-150">Produce a cross-platform binary</span></span>

<span data-ttu-id="df42f-151">當您將應用程式發佈為與 [framework 相依](#publish-framework-dependent)的應用程式時，會建立跨平臺二進位檔（以 *dll* 檔案的形式）。</span><span class="sxs-lookup"><span data-stu-id="df42f-151">Cross-platform binaries are created when you publish your app as [framework-dependent](#publish-framework-dependent), in the form of a *dll* file.</span></span> <span data-ttu-id="df42f-152">*Dll* 檔案會以您的專案命名。</span><span class="sxs-lookup"><span data-stu-id="df42f-152">The *dll* file is named after your project.</span></span> <span data-ttu-id="df42f-153">例如，如果您有一個名為 **word_reader** 的應用程式，則會建立名為 *word_reader.dll* 的檔案。</span><span class="sxs-lookup"><span data-stu-id="df42f-153">For example, if you have an app named **word_reader**, a file named *word_reader.dll* is created.</span></span> <span data-ttu-id="df42f-154">以這種方式發佈的應用程式會使用 `dotnet <filename.dll>` 命令執行，而且可以在任何平臺上執行。</span><span class="sxs-lookup"><span data-stu-id="df42f-154">Apps published in this way are run with the `dotnet <filename.dll>` command and can be run on any platform.</span></span>

<span data-ttu-id="df42f-155">只要已安裝目標 .NET Core 執行時間，就可以在任何作業系統上執行跨平臺二進位檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-155">Cross-platform binaries can be run on any operating system as long as the targeted .NET Core runtime is already installed.</span></span> <span data-ttu-id="df42f-156">如果未安裝目標 .NET Core 執行時間，應用程式可以使用較新的執行時間執行（如果應用程式設定為向前復原）。</span><span class="sxs-lookup"><span data-stu-id="df42f-156">If the targeted .NET Core runtime isn't installed, the app may run using a newer runtime if the app is configured to roll-forward.</span></span> <span data-ttu-id="df42f-157">如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。</span><span class="sxs-lookup"><span data-stu-id="df42f-157">For more information, see [framework-dependent apps roll forward](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

<span data-ttu-id="df42f-158">下列命令會產生跨平臺二進位檔：</span><span class="sxs-lookup"><span data-stu-id="df42f-158">The following command produces a cross-platform binary:</span></span>

| <span data-ttu-id="df42f-159">類型</span><span class="sxs-lookup"><span data-stu-id="df42f-159">Type</span></span>                                                                                 | <span data-ttu-id="df42f-160">SDK 2.1</span><span class="sxs-lookup"><span data-stu-id="df42f-160">SDK 2.1</span></span> | <span data-ttu-id="df42f-161">SDK 3。x</span><span class="sxs-lookup"><span data-stu-id="df42f-161">SDK 3.x</span></span> | <span data-ttu-id="df42f-162">命令</span><span class="sxs-lookup"><span data-stu-id="df42f-162">Command</span></span> |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| <span data-ttu-id="df42f-163">[framework 相依的跨平臺二進位](#publish-framework-dependent)檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-163">[framework-dependent cross-platform binary](#publish-framework-dependent).</span></span>           | <span data-ttu-id="df42f-164">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-164">✔️</span></span>      | <span data-ttu-id="df42f-165">✔️</span><span class="sxs-lookup"><span data-stu-id="df42f-165">✔️</span></span>      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-framework-dependent"></a><span data-ttu-id="df42f-166">發佈 framework 相依</span><span class="sxs-lookup"><span data-stu-id="df42f-166">Publish framework-dependent</span></span>

<span data-ttu-id="df42f-167">發佈為與 framework 相依的應用程式是跨平臺，不包含 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="df42f-167">Apps published as framework-dependent are cross-platform and don't include the .NET Core runtime.</span></span> <span data-ttu-id="df42f-168">您應用程式的使用者必須安裝 .NET Core 執行時間。</span><span class="sxs-lookup"><span data-stu-id="df42f-168">The user of your app is required to install the .NET Core runtime.</span></span>

<span data-ttu-id="df42f-169">將應用程式發佈為與 framework 相依的應用程式，會產生 [跨平臺二進位](#produce-a-cross-platform-binary) 檔做為 *dll* 檔案，以及以您目前平臺為目標的 [平臺特定可執行](#produce-an-executable) 檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-169">Publishing an app as framework-dependent produces a [cross-platform binary](#produce-a-cross-platform-binary) as a *dll* file, and a [platform-specific executable](#produce-an-executable) that targets your current platform.</span></span> <span data-ttu-id="df42f-170">*Dll* 是跨平臺，而可執行檔則不是。</span><span class="sxs-lookup"><span data-stu-id="df42f-170">The *dll* is cross-platform while the executable isn't.</span></span> <span data-ttu-id="df42f-171">例如，如果您發行名為 **word_reader** 和目標 Windows 的應用程式，則會隨著 *word_reader.dll* 建立 *word_reader.exe* 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-171">For example, if you publish an app named **word_reader** and target Windows, a *word_reader.exe* executable is created along with *word_reader.dll*.</span></span> <span data-ttu-id="df42f-172">以 Linux 或 macOS 為目標時，會建立 *word_reader* 可執行檔以及 *word_reader.dll*。</span><span class="sxs-lookup"><span data-stu-id="df42f-172">When targeting Linux or macOS, a *word_reader* executable is created along with *word_reader.dll*.</span></span> <span data-ttu-id="df42f-173">如需有關 Rid 的詳細資訊，請參閱 [.Net CORE RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="df42f-173">For more information about RIDs, see [.NET Core RID Catalog](../rid-catalog.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df42f-174">當您發佈與應用程式架構相依的應用程式時，.NET Core SDK 2.1 不會產生平臺特定的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-174">.NET Core SDK 2.1 doesn't produce platform-specific executables when you publish an app framework-dependent.</span></span>

<span data-ttu-id="df42f-175">您可以使用命令來執行應用程式的跨平臺二進位檔 `dotnet <filename.dll>` ，並可在任何平臺上執行。</span><span class="sxs-lookup"><span data-stu-id="df42f-175">The cross-platform binary of your app can be run with the `dotnet <filename.dll>` command, and can be run on any platform.</span></span> <span data-ttu-id="df42f-176">如果應用程式使用的 NuGet 套件具有平臺特定的執行，則所有平臺的相依性都會連同應用程式一起複製到 [發佈] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="df42f-176">If the app uses a NuGet package that has platform-specific implementations, all platforms' dependencies are copied to the publish folder along with the app.</span></span>

<span data-ttu-id="df42f-177">您可以藉由將參數傳遞至命令，為特定平臺建立可執行檔 `-r <RID> --self-contained false` [`dotnet publish`](../tools/dotnet-publish.md) 。</span><span class="sxs-lookup"><span data-stu-id="df42f-177">You can create an executable for a specific platform by passing the `-r <RID> --self-contained false` parameters to the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="df42f-178">如果 `-r` 省略此參數，就會為您目前的平臺建立可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-178">When the `-r` parameter is omitted, an executable is created for your current platform.</span></span> <span data-ttu-id="df42f-179">任何具有目標平臺之平臺特定相依性的 NuGet 套件都會複製到 [發佈] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="df42f-179">Any NuGet packages that have platform-specific dependencies for the targeted platform are copied to the publish folder.</span></span> <span data-ttu-id="df42f-180">如果您不需要平臺特定的可執行檔，您可以 `<UseAppHost>False</UseAppHost>` 在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="df42f-180">If you don't need a platfrom-specific executable, you can specify `<UseAppHost>False</UseAppHost>` in the project file.</span></span> <span data-ttu-id="df42f-181">如需詳細資訊，請參閱 [.NET SDK 專案的 MSBuild 參考](../project-sdk/msbuild-props.md#useapphost)。</span><span class="sxs-lookup"><span data-stu-id="df42f-181">For more information, see [MSBuild reference for .NET SDK projects](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="advantages"></a><span data-ttu-id="df42f-182">優點</span><span class="sxs-lookup"><span data-stu-id="df42f-182">Advantages</span></span>

- <span data-ttu-id="df42f-183">**小規模部署**</span><span class="sxs-lookup"><span data-stu-id="df42f-183">**Small deployment**</span></span>\
<span data-ttu-id="df42f-184">只會發佈您的應用程式及其相依性。</span><span class="sxs-lookup"><span data-stu-id="df42f-184">Only your app and its dependencies are distributed.</span></span> <span data-ttu-id="df42f-185">使用者會安裝 .NET Core 執行時間和程式庫，而且所有應用程式會共用執行時間。</span><span class="sxs-lookup"><span data-stu-id="df42f-185">The .NET Core runtime and libraries are installed by the user and all apps share the runtime.</span></span>

- <span data-ttu-id="df42f-186">**跨平臺**</span><span class="sxs-lookup"><span data-stu-id="df42f-186">**Cross-platform**</span></span>\
<span data-ttu-id="df42f-187">您的應用程式和任何。以網路為基礎的程式庫會在其他作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="df42f-187">Your app and any .NET-based library runs on other operating systems.</span></span> <span data-ttu-id="df42f-188">您不需要為您的應用程式定義目標平臺。</span><span class="sxs-lookup"><span data-stu-id="df42f-188">You don't need to define a target platform for your app.</span></span> <span data-ttu-id="df42f-189">如需 .NET 檔案格式的詳細資訊，請參閱 [.Net 元件檔案格式](../../standard/assembly/file-format.md)。</span><span class="sxs-lookup"><span data-stu-id="df42f-189">For information about the .NET file format, see [.NET Assembly File Format](../../standard/assembly/file-format.md).</span></span>

- <span data-ttu-id="df42f-190">**使用最新的修補執行時間**</span><span class="sxs-lookup"><span data-stu-id="df42f-190">**Uses the latest patched runtime**</span></span>\
<span data-ttu-id="df42f-191">應用程式會使用最新的執行時間 (在目標系統上安裝之 .NET Core 的目標主要核心) 內。</span><span class="sxs-lookup"><span data-stu-id="df42f-191">The app uses the latest runtime (within the targeted major-minor family of .NET Core) installed on the target system.</span></span> <span data-ttu-id="df42f-192">這表示您的應用程式會自動使用 .NET Core 執行時間的最新修補版本。</span><span class="sxs-lookup"><span data-stu-id="df42f-192">This means your app automatically uses the latest patched version of the .NET Core runtime.</span></span> <span data-ttu-id="df42f-193">您可以覆寫這個預設行為。</span><span class="sxs-lookup"><span data-stu-id="df42f-193">This default behavior can be overridden.</span></span> <span data-ttu-id="df42f-194">如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。</span><span class="sxs-lookup"><span data-stu-id="df42f-194">For more information, see [framework-dependent apps roll forward](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

### <a name="disadvantages"></a><span data-ttu-id="df42f-195">缺點</span><span class="sxs-lookup"><span data-stu-id="df42f-195">Disadvantages</span></span>

- <span data-ttu-id="df42f-196">**需要預先安裝執行時間**</span><span class="sxs-lookup"><span data-stu-id="df42f-196">**Requires pre-installing the runtime**</span></span>\
<span data-ttu-id="df42f-197">只有當應用程式的目標 .NET Core 版本已安裝在主機系統上時，您的應用程式才能執行。</span><span class="sxs-lookup"><span data-stu-id="df42f-197">Your app can run only if the version of .NET Core your app targets is already installed on the host system.</span></span> <span data-ttu-id="df42f-198">您可以將應用程式的向前復原行為設定為需要特定版本的 .NET Core，或允許較新版本的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="df42f-198">You can configure roll-forward behavior for the app to either require a specific version of .NET Core or allow a newer version of .NET Core.</span></span> <span data-ttu-id="df42f-199">如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。</span><span class="sxs-lookup"><span data-stu-id="df42f-199">For more information, see [framework-dependent apps roll forward](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

- <span data-ttu-id="df42f-200">**.NET Core 可能會變更**</span><span class="sxs-lookup"><span data-stu-id="df42f-200">**.NET Core may change**</span></span>\
<span data-ttu-id="df42f-201">您可以在執行應用程式的電腦上更新 .NET Core 執行時間和程式庫。</span><span class="sxs-lookup"><span data-stu-id="df42f-201">It's possible for the .NET Core runtime and libraries to be updated on the machine where the app is run.</span></span> <span data-ttu-id="df42f-202">在罕見的情況下，如果您使用的是大部分應用程式所使用的 .NET Core 程式庫，這可能會變更您的應用程式行為。</span><span class="sxs-lookup"><span data-stu-id="df42f-202">In rare cases, this may change the behavior of your app if you use the .NET Core libraries, which most apps do.</span></span> <span data-ttu-id="df42f-203">您可以設定應用程式如何使用較新版本的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="df42f-203">You can configure how your app uses newer versions of .NET Core.</span></span> <span data-ttu-id="df42f-204">如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。</span><span class="sxs-lookup"><span data-stu-id="df42f-204">For more information, see [framework-dependent apps roll forward](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

<span data-ttu-id="df42f-205">下列缺點僅適用于 .NET Core 2.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="df42f-205">The following disadvantage only applies to .NET Core 2.1 SDK.</span></span>

- <span data-ttu-id="df42f-206">**使用 `dotnet` 命令來啟動應用程式**</span><span class="sxs-lookup"><span data-stu-id="df42f-206">**Use the `dotnet` command to start the app**</span></span>\
<span data-ttu-id="df42f-207">使用者必須執行 `dotnet <filename.dll>` 命令以啟動您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-207">Users must run the `dotnet <filename.dll>` command to start your app.</span></span> <span data-ttu-id="df42f-208">.NET Core 2.1 SDK 不會針對已發佈 framework 相依的應用程式，產生平臺特定的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-208">.NET Core 2.1 SDK doesn't produce platform-specific executables for apps published framework-dependent.</span></span>

### <a name="examples"></a><span data-ttu-id="df42f-209">範例</span><span class="sxs-lookup"><span data-stu-id="df42f-209">Examples</span></span>

<span data-ttu-id="df42f-210">發佈跨平臺架構相依的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-210">Publish an app cross-platform framework-dependent.</span></span> <span data-ttu-id="df42f-211">以目前平臺為目標的可執行檔會與 *dll* 檔案一起建立。</span><span class="sxs-lookup"><span data-stu-id="df42f-211">An executable that targets your current platform is created along with the *dll* file.</span></span>

```dotnet
dotnet publish
```

<span data-ttu-id="df42f-212">發佈跨平臺架構相依的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-212">Publish an app cross-platform framework-dependent.</span></span> <span data-ttu-id="df42f-213">Linux 64 位可執行檔會與 *dll* 檔案一起建立。</span><span class="sxs-lookup"><span data-stu-id="df42f-213">A Linux 64-bit executable is created along with the *dll* file.</span></span> <span data-ttu-id="df42f-214">此命令不適用於 .NET Core SDK 2.1。</span><span class="sxs-lookup"><span data-stu-id="df42f-214">This command doesn't work with .NET Core SDK 2.1.</span></span>

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a><span data-ttu-id="df42f-215">獨立發行</span><span class="sxs-lookup"><span data-stu-id="df42f-215">Publish self-contained</span></span>

<span data-ttu-id="df42f-216">將您的應用程式發佈為獨立應用程式，會產生平臺特定的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-216">Publishing your app as self-contained produces a platform-specific executable.</span></span> <span data-ttu-id="df42f-217">輸出發行資料夾包含應用程式的所有元件，包括 .NET Core 程式庫和目標執行時間。</span><span class="sxs-lookup"><span data-stu-id="df42f-217">The output publishing folder contains all components of the app, including the .NET Core libraries and target runtime.</span></span> <span data-ttu-id="df42f-218">應用程式會與其他 .NET Core 應用程式隔離，而且不會使用本機安裝的共用執行時間。</span><span class="sxs-lookup"><span data-stu-id="df42f-218">The app is isolated from other .NET Core apps and doesn't use a locally installed shared runtime.</span></span> <span data-ttu-id="df42f-219">您應用程式的使用者不需要下載和安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="df42f-219">The user of your app isn't required to download and install .NET Core.</span></span>

<span data-ttu-id="df42f-220">針對指定的目標平臺產生可執行檔二進位檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-220">The executable binary is produced for the specified target platform.</span></span> <span data-ttu-id="df42f-221">例如，如果您有一個名為 **word_reader** 的應用程式，而且您發行了 Windows 的獨立可執行檔，則會建立 *word_reader.exe* 檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-221">For example, if you have an app named **word_reader**, and you publish a self-contained executable for Windows, a *word_reader.exe* file is created.</span></span> <span data-ttu-id="df42f-222">針對 Linux 或 macOS 發行，會建立 *word_reader* 檔案。</span><span class="sxs-lookup"><span data-stu-id="df42f-222">Publishing for Linux or macOS, a *word_reader* file is created.</span></span> <span data-ttu-id="df42f-223">使用命令的參數指定目標平臺和架構 `-r <RID>` [`dotnet publish`](../tools/dotnet-publish.md) 。</span><span class="sxs-lookup"><span data-stu-id="df42f-223">The target platform and architecture is specified with the `-r <RID>` parameter for the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="df42f-224">如需有關 Rid 的詳細資訊，請參閱 [.Net CORE RID 目錄](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="df42f-224">For more information about RIDs, see [.NET Core RID Catalog](../rid-catalog.md).</span></span>

<span data-ttu-id="df42f-225">如果應用程式具有平臺特定的相依性（例如包含平臺特定相依性的 NuGet 套件），則會將這些相依性連同應用程式一起複製到 [發佈] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="df42f-225">If the app has platform-specific dependencies, such as a NuGet package containing platform-specific dependencies, these are copied to the publish folder along with the app.</span></span>

### <a name="advantages"></a><span data-ttu-id="df42f-226">優點</span><span class="sxs-lookup"><span data-stu-id="df42f-226">Advantages</span></span>

- <span data-ttu-id="df42f-227">**控制 .NET Core 版本**</span><span class="sxs-lookup"><span data-stu-id="df42f-227">**Control .NET Core version**</span></span>\
<span data-ttu-id="df42f-228">您可以控制您的應用程式所部署的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="df42f-228">You control which version of .NET Core is deployed with your app.</span></span>

- <span data-ttu-id="df42f-229">**平臺特定目標**</span><span class="sxs-lookup"><span data-stu-id="df42f-229">**Platform-specific targeting**</span></span>\
<span data-ttu-id="df42f-230">因為您必須為每個平臺發佈您的應用程式，所以您知道應用程式將執行的位置。</span><span class="sxs-lookup"><span data-stu-id="df42f-230">Because you have to publish your app for each platform, you know where your app will run.</span></span> <span data-ttu-id="df42f-231">如果 .NET Core 引進新平臺，使用者將無法在該平臺上執行您的應用程式，除非您發行以該平臺為目標的版本。</span><span class="sxs-lookup"><span data-stu-id="df42f-231">If .NET Core introduces a new platform, users can't run your app on that platform until you release a version targeting that platform.</span></span> <span data-ttu-id="df42f-232">您可以在使用者于新的平臺上執行應用程式之前，先測試應用程式的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="df42f-232">You can test your app for compatibility problems before your users run your app on the new platform.</span></span>

### <a name="disadvantages"></a><span data-ttu-id="df42f-233">缺點</span><span class="sxs-lookup"><span data-stu-id="df42f-233">Disadvantages</span></span>

- <span data-ttu-id="df42f-234">**較大型的部署**</span><span class="sxs-lookup"><span data-stu-id="df42f-234">**Larger deployments**</span></span>\
<span data-ttu-id="df42f-235">因為您的應用程式包含 .NET Core 執行時間和您所有的應用程式相依性，所以需要的下載大小和硬碟空間大於 [framework 相依](#publish-framework-dependent) 的版本。</span><span class="sxs-lookup"><span data-stu-id="df42f-235">Because your app includes the .NET Core runtime and all of your app dependencies, the download size and hard drive space required is greater than a [framework-dependent](#publish-framework-dependent) version.</span></span>

  > [!TIP]
  > <span data-ttu-id="df42f-236">您可以使用 .NET Core [*全球化*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)非變異模式，將 Linux 系統上的部署大小減少約 28 MB。</span><span class="sxs-lookup"><span data-stu-id="df42f-236">You can reduce the size of your deployment on Linux systems by approximately 28 MB by using .NET Core [*globalization invariant mode*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span> <span data-ttu-id="df42f-237">這會強制您的應用程式將所有文化特性視為不因 [文化](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)特性而異。</span><span class="sxs-lookup"><span data-stu-id="df42f-237">This forces your app to treat all cultures like the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).</span></span>

  > [!TIP]
  > <span data-ttu-id="df42f-238">有一 [項預覽修剪功能](trim-self-contained.md) 可進一步減少部署的大小。</span><span class="sxs-lookup"><span data-stu-id="df42f-238">There is a [preview Trim feature](trim-self-contained.md) that can further reduce the size of your deployment.</span></span>

- <span data-ttu-id="df42f-239">**較難更新 .NET Core 版本**</span><span class="sxs-lookup"><span data-stu-id="df42f-239">**Harder to update the .NET Core version**</span></span>\
<span data-ttu-id="df42f-240">.NET Core 執行時間 (隨您的應用程式散發) 只能透過發行新版的應用程式來進行升級。</span><span class="sxs-lookup"><span data-stu-id="df42f-240">.NET Core Runtime (distributed with your app) can only be upgraded by releasing a new version of your app.</span></span> <span data-ttu-id="df42f-241">不過，.NET Core 會在應用程式執行所在的電腦中，視需要更新架構程式庫所需的重大安全性修補程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-241">However, .NET Core will update critical security patches as needed for the framework library in the  machine that your app runs on.</span></span> <span data-ttu-id="df42f-242">您必須負責進行此安全性修補程式案例的端對端驗證。</span><span class="sxs-lookup"><span data-stu-id="df42f-242">You are responsible for end to end validation for this security patch scenario.</span></span>

### <a name="examples"></a><span data-ttu-id="df42f-243">範例</span><span class="sxs-lookup"><span data-stu-id="df42f-243">Examples</span></span>

<span data-ttu-id="df42f-244">發行獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-244">Publish an app self-contained.</span></span> <span data-ttu-id="df42f-245">建立 macOS 64 位可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-245">A macOS 64-bit executable is created.</span></span>

```dotnet
dotnet publish -r osx-x64
```

<span data-ttu-id="df42f-246">發行獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-246">Publish an app self-contained.</span></span> <span data-ttu-id="df42f-247">建立 Windows 64 位可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-247">A Windows 64-bit executable is created.</span></span>

```dotnet
dotnet publish -r win-x64
```

## <a name="publish-with-readytorun-images"></a><span data-ttu-id="df42f-248">使用 ReadyToRun 映射發佈</span><span class="sxs-lookup"><span data-stu-id="df42f-248">Publish with ReadyToRun images</span></span>

<span data-ttu-id="df42f-249">使用 ReadyToRun 映射發佈將可改善應用程式的啟動時間，代價是增加應用程式的大小。</span><span class="sxs-lookup"><span data-stu-id="df42f-249">Publishing with ReadyToRun images will improve the startup time of your application at the cost of increasing the size of your application.</span></span> <span data-ttu-id="df42f-250">若要使用 ReadyToRun 發佈，請參閱 [ReadyToRun](ready-to-run.md) 以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="df42f-250">In order to publish with ReadyToRun see [ReadyToRun](ready-to-run.md) for more details.</span></span>

### <a name="advantages"></a><span data-ttu-id="df42f-251">優點</span><span class="sxs-lookup"><span data-stu-id="df42f-251">Advantages</span></span>

- <span data-ttu-id="df42f-252">**改善的啟動時間**</span><span class="sxs-lookup"><span data-stu-id="df42f-252">**Improved startup time**</span></span>\
<span data-ttu-id="df42f-253">應用程式將花費較少的時間執行 JIT。</span><span class="sxs-lookup"><span data-stu-id="df42f-253">The application will spend less time running the JIT.</span></span>

### <a name="disadvantages"></a><span data-ttu-id="df42f-254">缺點</span><span class="sxs-lookup"><span data-stu-id="df42f-254">Disadvantages</span></span>

- <span data-ttu-id="df42f-255">**較大的大小**</span><span class="sxs-lookup"><span data-stu-id="df42f-255">**Larger size**</span></span>\
<span data-ttu-id="df42f-256">應用程式將會在磁片上放大。</span><span class="sxs-lookup"><span data-stu-id="df42f-256">The application will be larger on disk.</span></span>

### <a name="examples"></a><span data-ttu-id="df42f-257">範例</span><span class="sxs-lookup"><span data-stu-id="df42f-257">Examples</span></span>

<span data-ttu-id="df42f-258">發行獨立和 ReadyToRun 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-258">Publish an app self-contained and ReadyToRun.</span></span> <span data-ttu-id="df42f-259">建立 macOS 64 位可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-259">A macOS 64-bit executable is created.</span></span>

```dotnet
dotnet publish -c Release -r osx-x64 -p:PublishReadyToRun=true
```

<span data-ttu-id="df42f-260">發行獨立和 ReadyToRun 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-260">Publish an app self-contained and ReadyToRun.</span></span> <span data-ttu-id="df42f-261">建立 Windows 64 位可執行檔。</span><span class="sxs-lookup"><span data-stu-id="df42f-261">A Windows 64-bit executable is created.</span></span>

```dotnet
dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
```

## <a name="see-also"></a><span data-ttu-id="df42f-262">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df42f-262">See also</span></span>

- [<span data-ttu-id="df42f-263">使用 .NET Core CLI 部署 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-263">Deploying .NET Core Apps with .NET Core CLI.</span></span>](deploy-with-cli.md)
- [<span data-ttu-id="df42f-264">使用 Visual Studio 部署 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="df42f-264">Deploying .NET Core Apps with Visual Studio.</span></span>](deploy-with-vs.md)
- [<span data-ttu-id="df42f-265">.NET Core 執行時間識別碼 (RID) 目錄。</span><span class="sxs-lookup"><span data-stu-id="df42f-265">.NET Core Runtime Identifier (RID) catalog.</span></span>](../rid-catalog.md)
- [<span data-ttu-id="df42f-266">選取要使用的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="df42f-266">Select the .NET Core version to use.</span></span>](../versions/selection.md)
