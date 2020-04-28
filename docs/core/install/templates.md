---
title: 安裝和管理 SDK 範本-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core 範本。
author: thraka
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 0a3c8655d55bf63de1e91337ce3a2ac399b07d0f
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200612"
---
# <a name="manage-net-project-and-item-templates"></a><span data-ttu-id="1d8bb-103">管理 .NET 專案和專案範本</span><span class="sxs-lookup"><span data-stu-id="1d8bb-103">Manage .NET project and item templates</span></span>

<span data-ttu-id="1d8bb-104">.NET Core 提供範本系統，可讓使用者從 NuGet、NuGet 套件檔案或檔案系統目錄安裝或卸載範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-104">.NET Core provides a template system that enables users to install or uninstall templates from NuGet, a NuGet package file, or a file system directory.</span></span> <span data-ttu-id="1d8bb-105">本文說明如何透過 .NET Core SDK CLI 管理 .NET Core 範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-105">This article describes how to manage .NET Core templates through the .NET Core SDK CLI.</span></span>

<span data-ttu-id="1d8bb-106">如需建立範本的詳細資訊，請參閱[教學課程：建立範本](../tutorials/cli-templates-create-item-template.md)。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-106">For more information about creating templates, see [Tutorial: Create templates](../tutorials/cli-templates-create-item-template.md).</span></span>

## <a name="install-template"></a><span data-ttu-id="1d8bb-107">安裝範本</span><span class="sxs-lookup"><span data-stu-id="1d8bb-107">Install template</span></span>

<span data-ttu-id="1d8bb-108">範本會透過具有`-i`參數的[dotnet new](../tools/dotnet-new.md) SDK 命令來安裝。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-108">Templates are installed through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-i` parameter.</span></span> <span data-ttu-id="1d8bb-109">您可以提供範本的 NuGet 套件識別碼，或包含範本檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-109">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-hosted-package"></a><span data-ttu-id="1d8bb-110">NuGet 主控的套件</span><span class="sxs-lookup"><span data-stu-id="1d8bb-110">NuGet hosted package</span></span>

<span data-ttu-id="1d8bb-111">.NET CLI 範本會上傳至[NuGet](https://www.nuget.org/)以進行寬分佈。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-111">.NET CLI templates are uploaded to [NuGet](https://www.nuget.org/) for wide distribution.</span></span> <span data-ttu-id="1d8bb-112">您也可以從私人摘要安裝範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-112">Templates can also be installed from a private feed.</span></span> <span data-ttu-id="1d8bb-113">*Nupkg*範本檔案不會上傳至 NuGet 摘要，而是可以散發並手動安裝，如[本機 NuGet 封裝](#local-nuget-package)一節中所述。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-113">Instead of uploading a template to a NuGet feed, *nupkg* template files can be distributed and manually installed, as described in the [Local NuGet package](#local-nuget-package) section.</span></span>

<span data-ttu-id="1d8bb-114">如需有關設定 NuGet 摘要的詳細資訊，請參閱[dotnet NuGet 新增來源](../tools/dotnet-nuget-add-source.md)。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-114">For more information about configuring NuGet feeds, see [dotnet nuget add source](../tools/dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="1d8bb-115">若要從預設的 NuGet 摘要安裝範本套件，請使用`dotnet new -i {package-id}`下列命令：</span><span class="sxs-lookup"><span data-stu-id="1d8bb-115">To install a template pack from the default NuGet feed, use the `dotnet new -i {package-id}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

<span data-ttu-id="1d8bb-116">若要從具有特定版本的預設 NuGet 摘要安裝範本套件，請使用`dotnet new -i {package-id}::{version}`命令：</span><span class="sxs-lookup"><span data-stu-id="1d8bb-116">To install a template pack from the default NuGet feed with a specific version, use the `dotnet new -i {package-id}::{version}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a><span data-ttu-id="1d8bb-117">本機 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="1d8bb-117">Local NuGet package</span></span>

<span data-ttu-id="1d8bb-118">建立範本套件時，會產生*nupkg*檔案。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-118">When a template pack is created, a *nupkg* file is generated.</span></span> <span data-ttu-id="1d8bb-119">如果您有包含範本的*nupkg*檔案，您可以使用下列`dotnet new -i {path-to-package}`命令來安裝它：</span><span class="sxs-lookup"><span data-stu-id="1d8bb-119">If you have a *nupkg* file containing templates, you can install it with the `dotnet new -i {path-to-package}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a><span data-ttu-id="1d8bb-120">資料夾</span><span class="sxs-lookup"><span data-stu-id="1d8bb-120">Folder</span></span>

<span data-ttu-id="1d8bb-121">除了從*nupkg*檔案安裝範本以外，您也可以使用`dotnet new -i {folder-path}`命令直接從資料夾安裝範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-121">As an alternative to installing template from a *nupkg* file, you can also install templates from a folder directly with the `dotnet new -i {folder-path}` command.</span></span> <span data-ttu-id="1d8bb-122">指定的資料夾會被視為任何找到的範本的範本套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-122">The folder specified is treated as the template pack identifier for any template found.</span></span> <span data-ttu-id="1d8bb-123">已安裝在指定資料夾階層中找到的任何範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-123">Any template found in the specified folder's hierarchy is installed.</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

<span data-ttu-id="1d8bb-124">在`{folder-path}`命令上指定的會成為所有找到的範本的範本套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-124">The `{folder-path}` specified on the command becomes the template pack identifier for all templates found.</span></span> <span data-ttu-id="1d8bb-125">如 [[清單範本](#list-templates)] 區段中所指定，您可以使用`dotnet new -u`命令來取得已安裝的範本清單。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-125">As specified in the [List templates](#list-templates) section, you can get a list of templates installed with the `dotnet new -u` command.</span></span> <span data-ttu-id="1d8bb-126">在此範例中，範本套件識別碼會顯示為用於安裝的資料夾：</span><span class="sxs-lookup"><span data-stu-id="1d8bb-126">In this example, the template pack identifier is shown as the folder used for install:</span></span>

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a><span data-ttu-id="1d8bb-127">卸載範本</span><span class="sxs-lookup"><span data-stu-id="1d8bb-127">Uninstall template</span></span>

<span data-ttu-id="1d8bb-128">範本會透過[dotnet new](../tools/dotnet-new.md) SDK 命令與`-u`參數一起卸載。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-128">Templates are uninstalled through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-u` parameter.</span></span> <span data-ttu-id="1d8bb-129">您可以提供範本的 NuGet 套件識別碼，或包含範本檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-129">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-package"></a><span data-ttu-id="1d8bb-130">Nuget 套件</span><span class="sxs-lookup"><span data-stu-id="1d8bb-130">NuGet package</span></span>

<span data-ttu-id="1d8bb-131">安裝 NuGet 範本套件之後（從 NuGet 摘要或*nupkg*檔案），您可以藉由參考 nuget 套件識別碼來將它卸載。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-131">After a NuGet template pack is installed, either from a NuGet feed or a *nupkg* file, you can uninstall it by referencing the NuGet package identifier.</span></span>

<span data-ttu-id="1d8bb-132">若要卸載範本套件，請使用`dotnet new -u {package-id}`命令：</span><span class="sxs-lookup"><span data-stu-id="1d8bb-132">To uninstall a template pack, use the `dotnet new -u {package-id}` command:</span></span>

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a><span data-ttu-id="1d8bb-133">資料夾</span><span class="sxs-lookup"><span data-stu-id="1d8bb-133">Folder</span></span>

<span data-ttu-id="1d8bb-134">透過[資料夾路徑](#folder)安裝範本時，資料夾路徑會變成範本套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-134">When templates are installed through a [folder path](#folder), the folder path becomes the template pack identifier.</span></span>

<span data-ttu-id="1d8bb-135">若要卸載範本套件，請使用`dotnet new -u {package-folder-path}`命令：</span><span class="sxs-lookup"><span data-stu-id="1d8bb-135">To uninstall a template pack, use the `dotnet new -u {package-folder-path}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a><span data-ttu-id="1d8bb-136">列出範本</span><span class="sxs-lookup"><span data-stu-id="1d8bb-136">List templates</span></span>

<span data-ttu-id="1d8bb-137">藉由使用沒有套件識別碼的標準卸載命令，您可以查看已安裝的範本清單，以及用來卸載每個範本的命令。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-137">By using the standard uninstall command without a package identifier, you can see a list of installed templates along with the command that uninstalls each template.</span></span>

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a><span data-ttu-id="1d8bb-138">從其他 Sdk 安裝範本</span><span class="sxs-lookup"><span data-stu-id="1d8bb-138">Install templates from other SDKs</span></span>

<span data-ttu-id="1d8bb-139">如果您已依序安裝 sdk 的每個版本，例如安裝了 SDK 2.0、SDK 2.1 等等，則會安裝每個 SDK 的範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-139">If you've installed each version of the SDK sequentially, for example you installed SDK 2.0, then SDK 2.1, and so on, you'll have every SDK's templates installed.</span></span> <span data-ttu-id="1d8bb-140">不過，如果您從較新的 SDK 版本開始（例如3.1），則只會包含適用于[LTS （長期支援）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本的範本，而 sdk 3.1 版本則為 sdk 2.1 和 sdk 3.1。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-140">However, if you start with a later SDK version, like 3.1, only the templates for [LTS (long term support) releases](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) are included, which at the time of the SDK 3.1 release is SDK 2.1 and SDK 3.1.</span></span> <span data-ttu-id="1d8bb-141">不包含任何其他版本的範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-141">Templates for any other release aren't included.</span></span>

<span data-ttu-id="1d8bb-142">.NET Core 範本可在 NuGet 上取得，而且您可以像任何其他範本一樣地進行安裝。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-142">The .NET Core templates are available on NuGet, and you can install them like any other template.</span></span> <span data-ttu-id="1d8bb-143">如需詳細資訊，請參閱[安裝 NuGet 託管套件](#nuget-hosted-package)。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-143">For more information, see [Install NuGet hosted package](#nuget-hosted-package).</span></span>

| <span data-ttu-id="1d8bb-144">SDK</span><span class="sxs-lookup"><span data-stu-id="1d8bb-144">SDK</span></span>              | <span data-ttu-id="1d8bb-145">NuGet 套件識別碼</span><span class="sxs-lookup"><span data-stu-id="1d8bb-145">NuGet Package Identifier</span></span>                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1d8bb-146">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1d8bb-146">.NET Core 2.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| <span data-ttu-id="1d8bb-147">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="1d8bb-147">.NET Core 2.2</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| <span data-ttu-id="1d8bb-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1d8bb-148">.NET Core 3.0</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| <span data-ttu-id="1d8bb-149">.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="1d8bb-149">.NET Core 3.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| <span data-ttu-id="1d8bb-150">ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1d8bb-150">ASP.NET Core 2.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| <span data-ttu-id="1d8bb-151">ASP.NET Core 2。2</span><span class="sxs-lookup"><span data-stu-id="1d8bb-151">ASP.NET Core 2.2</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| <span data-ttu-id="1d8bb-152">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="1d8bb-152">ASP.NET Core 3.0</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| <span data-ttu-id="1d8bb-153">ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="1d8bb-153">ASP.NET Core 3.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

<span data-ttu-id="1d8bb-154">例如，.NET Core SDK 包含以 .NET Core 2.1 和 .NET Core 3.1 為目標之主控台應用程式的範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-154">For example, the .NET Core SDK includes templates for a console app targeting .NET Core 2.1 and .NET Core 3.1.</span></span> <span data-ttu-id="1d8bb-155">如果您想要將目標設為 .NET Core 3.0，您必須安裝3.0 範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-155">If you wanted to target .NET Core 3.0, you would need to install the 3.0 templates.</span></span>

01. <span data-ttu-id="1d8bb-156">嘗試建立以 .NET Core 3.0 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-156">Try creating an app that targets .NET Core 3.0.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="1d8bb-157">如果您看到錯誤訊息，則需要安裝範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-157">If you see an error message, you need to install the templates.</span></span>

    > <span data-ttu-id="1d8bb-158">找不到符合輸入的已安裝範本，正在線上搜尋 .。。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-158">Couldn't find an installed template that matches the input, searching online for one that does...</span></span>

01. <span data-ttu-id="1d8bb-159">安裝 .NET Core 3.0 專案範本。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-159">Install the .NET Core 3.0 project templates.</span></span>

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. <span data-ttu-id="1d8bb-160">嘗試第二次建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-160">Try creating the app a second time.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="1d8bb-161">您應該會看到一則訊息，指出已建立專案。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-161">And you should see a message indicating the project was created.</span></span>

    > <span data-ttu-id="1d8bb-162">已成功建立範本「主控台應用程式」。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-162">The template "Console Application" was created successfully.</span></span>
    >
    > <span data-ttu-id="1d8bb-163">正在處理建立後的動作 .。。正在 path-to-project-file 上執行 ' dotnet restore ' .。。正在判斷要還原的專案 .。。Path-to-project-file 的還原已于1.05 秒完成，適用于 .csproj。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-163">Processing post-creation actions... Running 'dotnet restore' on path-to-project-file.csproj... Determining projects to restore... Restore completed in 1.05 sec for path-to-project-file.csproj.</span></span>
    >
    > <span data-ttu-id="1d8bb-164">還原成功。</span><span class="sxs-lookup"><span data-stu-id="1d8bb-164">Restore succeeded.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d8bb-165">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d8bb-165">See also</span></span>

- [<span data-ttu-id="1d8bb-166">教學課程：建立專案範本</span><span class="sxs-lookup"><span data-stu-id="1d8bb-166">Tutorial: Create an item template</span></span>](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
