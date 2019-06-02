---
title: 建立 dotnet new 的自訂範本
description: 了解如何在此好玩的教學課程中建立 dotnet new 命令的自訂範本。
author: mairaw
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: e47da048584ec31c275ff9c122d157f34556268a
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299963"
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="4f1b3-103">建立 dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-103">Create a custom template for dotnet new</span></span>

<span data-ttu-id="4f1b3-104">本教學課程會示範如何：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="4f1b3-105">從現有的專案或新的主控台應用程式專案建立基本範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-105">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="4f1b3-106">封裝範本，以在 nuget.org 或從本機 *nupkg* 檔案發佈。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-106">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="4f1b3-107">從 nuget.org (本機 *nupkg* 檔案) 或本機檔案系統安裝範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-107">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="4f1b3-108">解除安裝範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-108">Uninstall the template.</span></span>

<span data-ttu-id="4f1b3-109">如果您偏好使用完整範例來進行教學課程，請下載[範例專案範本](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="4f1b3-110">範例範本是專為 NuGet 發佈所設定。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-110">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="4f1b3-111">如果您希望使用下載的範例和檔案系統發佈，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-111">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="4f1b3-112">將範例的 *content* 資料夾內容上移一層到 *GarciaSoftware.ConsoleTemplate.CSharp* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-112">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="4f1b3-113">刪除空白的 *content* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-113">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="4f1b3-114">刪除 *nuspec* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-114">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4f1b3-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="4f1b3-115">Prerequisites</span></span>

- <span data-ttu-id="4f1b3-116">安裝 [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-116">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="4f1b3-117">閱讀參考主題 [dotnet new 的自訂範本](../tools/custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-117">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="4f1b3-118">從專案建立範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-118">Create a template from a project</span></span>

<span data-ttu-id="4f1b3-119">使用您已確認編譯和執行的現有專案，或在硬碟的資料夾中建立新的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-119">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="4f1b3-120">本教學課程假設專案資料夾的名稱為 *GarciaSoftware.ConsoleTemplate.CSharp*，儲存在使用者設定檔的 *Documents\Templates*。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-120">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="4f1b3-121">教學課程專案範本名稱的格式為 \<公司名稱>.\<範本類型>.\<程式設計語言>  ，但是您可以依喜好隨意命名您的專案與範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-121">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="4f1b3-122">將資料夾新增至 *.template.config* 專案的根目錄。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-122">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="4f1b3-123">在 *.template.config* 資料夾中建立 *template.json* 檔案，以設定您的範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-123">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="4f1b3-124">如需 *template.json* 檔案的詳細資訊和成員定義，請參閱 [dotnet new 的自訂範本](../tools/custom-templates.md#templatejson)主題和 [JSON 結構描述存放區的 *template.json* 結構描述](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-124">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

<span data-ttu-id="4f1b3-125">已完成範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-125">The template is finished.</span></span> <span data-ttu-id="4f1b3-126">此時，您有兩個範本發佈的選項。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-126">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="4f1b3-127">若要繼續本教學課程，請在兩個路徑中選擇其中之一：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-127">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="4f1b3-128">[NuGet 發佈](#use-nuget-distribution)：從 NuGet 或從本機 *nupkg* 檔案安裝範本，並使用已安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-128">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="4f1b3-129">[檔案系統發佈](#use-file-system-distribution)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-129">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="4f1b3-130">使用 NuGet 發佈</span><span class="sxs-lookup"><span data-stu-id="4f1b3-130">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="4f1b3-131">將範本封裝至 NuGet 套件中</span><span class="sxs-lookup"><span data-stu-id="4f1b3-131">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="4f1b3-132">建立 NuGet 套件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-132">Create a folder for the NuGet package.</span></span> <span data-ttu-id="4f1b3-133">教學課程中使用 *GarciaSoftware.ConsoleTemplate.CSharp* 資料夾名稱，並在使用者設定檔的 *Documents\NuGetTemplates* 資料夾中建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-133">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="4f1b3-134">在新的範本資料夾內建立名為「內容」  的資料夾，保留專案檔。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-134">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="4f1b3-135">將專案資料夾的內容以及其 *.template.config/template.json* 檔案複製到您建立的 *content* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-135">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="4f1b3-136">在 *content* 資料夾的旁邊，新增 [*nuspec* 檔案](/nuget/create-packages/creating-a-package)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-136">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="4f1b3-137">nuspec 檔案是 XML 資訊清單檔案，描述套件的內容及驅動建立 NuGet 套件的程序。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-137">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>

   ![目錄結構顯示 NuGet 套件的配置](./media/create-custom-template/nuget-directory-layout.png)

1. <span data-ttu-id="4f1b3-139">在 *nuspec* 檔案的 **\<packageTypes>** 項目內，包含 `name` 屬性值為 `Template` 的 **\<packageType>** 項目。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-139">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="4f1b3-140">*content* 資料夾和 *nuspec* 檔案都應該位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-140">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="4f1b3-141">下表顯示將範本製作為 NuGet 套件所需之最小的 *nuspec* 檔案項目。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-141">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="4f1b3-142">元素</span><span class="sxs-lookup"><span data-stu-id="4f1b3-142">Element</span></span>            | <span data-ttu-id="4f1b3-143">類型</span><span class="sxs-lookup"><span data-stu-id="4f1b3-143">Type</span></span>   | <span data-ttu-id="4f1b3-144">說明</span><span class="sxs-lookup"><span data-stu-id="4f1b3-144">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="4f1b3-145">**\<作者>**</span><span class="sxs-lookup"><span data-stu-id="4f1b3-145">**\<authors>**</span></span>     | <span data-ttu-id="4f1b3-146">字串</span><span class="sxs-lookup"><span data-stu-id="4f1b3-146">string</span></span> | <span data-ttu-id="4f1b3-147">以逗號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些作者會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-147">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="4f1b3-148">**\<描述>**</span><span class="sxs-lookup"><span data-stu-id="4f1b3-148">**\<description>**</span></span> | <span data-ttu-id="4f1b3-149">字串</span><span class="sxs-lookup"><span data-stu-id="4f1b3-149">string</span></span> | <span data-ttu-id="4f1b3-150">UI 顯示中的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-150">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="4f1b3-151">**\<識別碼>**</span><span class="sxs-lookup"><span data-stu-id="4f1b3-151">**\<id>**</span></span>          | <span data-ttu-id="4f1b3-152">字串</span><span class="sxs-lookup"><span data-stu-id="4f1b3-152">string</span></span> | <span data-ttu-id="4f1b3-153">不區分大小寫的套件識別碼，在整個 nuget.org 或套件所在的任何組件庫都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-153">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="4f1b3-154">識別碼可能不包含對 URL 而言無效的空格或字元，而且通常會遵循 .NET 命名空間規則。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-154">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="4f1b3-155">如需指導方針，請參閱[選擇唯一的套件識別碼並設定版本號碼](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-155">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="4f1b3-156">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="4f1b3-156">**\<packageType>**</span></span> | <span data-ttu-id="4f1b3-157">字串</span><span class="sxs-lookup"><span data-stu-id="4f1b3-157">string</span></span> | <span data-ttu-id="4f1b3-158">將此項目放在 **\<metadata>** 項目中的 **\<packageTypes>** 項目內。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-158">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="4f1b3-159">將 **\<packageType>** 項目的 `name` 屬性設定為 `Template`。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-159">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="4f1b3-160">**\<版本>**</span><span class="sxs-lookup"><span data-stu-id="4f1b3-160">**\<version>**</span></span>     | <span data-ttu-id="4f1b3-161">字串</span><span class="sxs-lookup"><span data-stu-id="4f1b3-161">string</span></span> | <span data-ttu-id="4f1b3-162">套件版本，遵循 major.minor.patch 模式。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-162">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="4f1b3-163">版本號碼可以包含預先發行版本的後置詞，如[預先發行版本](/nuget/create-packages/prerelease-packages#semantic-versioning)中所述。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-163">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="4f1b3-164">請參閱 [.nuspec 參考](/nuget/schema/nuspec)以取得完整的 *nuspec* 檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-164">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="4f1b3-165">教學課程的 *nuspec* 檔案名為 *GarciaSoftware.ConsoleTemplate.CSharp.nuspec*，且包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-165">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. <span data-ttu-id="4f1b3-166">使用 `nuget pack <PATH_TO_NUSPEC_FILE>` 命令[建立套件](/nuget/create-packages/creating-a-package#creating-the-package)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-166">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="4f1b3-167">下列命令假設，保存 NuGet 資產的資料夾位於 *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-167">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span></span> <span data-ttu-id="4f1b3-168">但無論資料夾放在系統上的任何位置，`nuget pack` 命令都接受 *nuspec* 檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-168">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="4f1b3-169">將套件發佈至 nuget.org</span><span class="sxs-lookup"><span data-stu-id="4f1b3-169">Publishing the package to nuget.org</span></span>

<span data-ttu-id="4f1b3-170">若要發佈 NuGet 套件，請遵循[建立和發佈套件](/nuget/quickstart/create-and-publish-a-package#publish-the-package)主題中的指示。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-170">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="4f1b3-171">不過，我們建議您不要將教學課程的範本發佈至 NuGet，因為它一旦發佈即永不刪除，只能取消列入。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-171">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="4f1b3-172">既然已有 *nupkg* 檔案形式的 NuGet 套件，建議您遵循下列指示直接從本機 *nupkg* 檔案安裝範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-172">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="4f1b3-173">從 NuGet 套件安裝範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-173">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="4f1b3-174">從本機 *nupkg* 檔案安裝範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-174">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="4f1b3-175">若要從您製作的 *nupkg* 檔案安裝範本，請使用 `dotnet new` 命令搭配 `-i|--install` 選項，然後提供 *nupkg* 檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-175">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="4f1b3-176">從儲存在 nuget.org 的 NuGet 套件安裝範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-176">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="4f1b3-177">如果您想要從儲存在 nuget.org 的 NuGet 套件安裝範本，請使用 `dotnet new` 命令搭配 `-i|--install` 選項，並提供 NuGet 套件的名稱：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-177">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="4f1b3-178">範例僅供示範之用。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-178">The example is for demonstration purposes only.</span></span> <span data-ttu-id="4f1b3-179">nuget.org 沒有 `GarciaSoftware.ConsoleTemplate.CSharp` NuGet 套件，我們也不建議您發佈及使用來自 NuGet 的測試範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-179">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="4f1b3-180">如果您執行命令，不會安裝任何範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-180">If you run the command, no template is installed.</span></span> <span data-ttu-id="4f1b3-181">不過，您可以直接參考本機檔案系統上的 *nupkg* 檔案，安裝尚未發佈至 nuget.org 的範本，如上一節[從本機 nupkg 檔案安裝範本](#install-the-template-from-the-local-nupkg-file)中所示。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-181">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="4f1b3-182">如果您想要如何從 nuget.org 的套件安裝範本的即時範例，您可以使用 [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) (dotnet-new 的 NUnit 3 範本)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-182">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="4f1b3-183">此範本會設定專案使用 NUnit 單元測試。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-183">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="4f1b3-184">使用下列命令來安裝：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-184">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="4f1b3-185">當您列出範本與 `dotnet new -l` 時，您會在範本清單中看到 *NUnit 3 測試專案*的簡短名稱 *nunit*。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-185">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="4f1b3-186">您已準備好在下一節中使用範本。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-186">You're ready to use the template in the next section.</span></span>

![顯示 NUnit 範本和其他範本的主控台視窗](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="4f1b3-188">從範本建立專案</span><span class="sxs-lookup"><span data-stu-id="4f1b3-188">Create a project from the template</span></span>

<span data-ttu-id="4f1b3-189">從 NuGet 安裝範本之後，從放置範本引擎輸出的目錄執行 `dotnet new <TEMPLATE>` 命令來使用範本 (除非您要使用 `-o|--output` 選項來指定特定的目錄)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-189">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="4f1b3-190">如需詳細資訊，請參閱[`dotnet new`選項](~/docs/core/tools/dotnet-new.md#options)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-190">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="4f1b3-191">直接將範本的簡短名稱提供給 `dotnet new` 命令。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-191">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="4f1b3-192">若要從 NUnit 範本建立專案，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-192">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="4f1b3-193">主控台會顯示專案已建立，且專案套件已還原。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-193">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="4f1b3-194">命令執行之後，專案即可供使用。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-194">After the command is run, the project is ready for use.</span></span>

![主控台視窗顯示 dotnet new nunit 的輸出，包括還原專案相依性](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="4f1b3-196">從儲存在 nuget.org 的 NuGet 套件解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-196">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="4f1b3-197">範例僅供示範之用。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-197">The example is for demonstration purposes only.</span></span> <span data-ttu-id="4f1b3-198">nuget.org 沒有 `GarciaSoftware.ConsoleTemplate.CSharp` NuGet 套件，也未與 .NET Core SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-198">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="4f1b3-199">如果執行命令，但未解除安裝套件/範本，且收到下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-199">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
>
> > <span data-ttu-id="4f1b3-200">找不到稱為 'GarciaSoftware.ConsoleTemplate.CSharp' 要解除安裝的項目。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="4f1b3-201">如已安裝 [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) (dotnet-new 的 NUnit 3 範本)，現在希望解除安裝，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-201">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="4f1b3-202">從本機 nupkg 檔案解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-202">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="4f1b3-203">當您想要解除安裝範本時，請勿嘗試使用 *nupkg* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-203">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="4f1b3-204">*嘗試使用 `dotnet new -u <PATH_TO_NUPKG_FILE>` 解除安裝範本失敗。*</span><span class="sxs-lookup"><span data-stu-id="4f1b3-204">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="4f1b3-205">依套件的 `id` 參考套件：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-205">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="4f1b3-206">使用檔案系統發佈</span><span class="sxs-lookup"><span data-stu-id="4f1b3-206">Use file system distribution</span></span>

<span data-ttu-id="4f1b3-207">若要發佈範本，請將專案範本資料夾放在網路上使用者能存取的位置。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-207">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="4f1b3-208">使用 `dotnet new` 命令搭配 `-i|--install` 選項，並指定範本資料夾的路徑 (包含專案的專案資料夾和 *.template.config* 資料夾)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-208">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="4f1b3-209">教學課程假設專案範本是儲存在使用者設定檔的 *Documents/Templates* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-209">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="4f1b3-210">從該位置安裝範本，以下列命令取代 \<使用者> 和使用者的設定檔名稱：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-210">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="4f1b3-211">從範本建立專案</span><span class="sxs-lookup"><span data-stu-id="4f1b3-211">Create a project from the template</span></span>

<span data-ttu-id="4f1b3-212">從檔案系統安裝範本之後，從放置範本引擎輸出的目錄執行 `dotnet new <TEMPLATE>` 命令來使用範本 (除非您要使用 `-o|--output` 選項來指定特定的目錄)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-212">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="4f1b3-213">如需詳細資訊，請參閱[`dotnet new`選項](~/docs/core/tools/dotnet-new.md#options)。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-213">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="4f1b3-214">直接將範本的簡短名稱提供給 `dotnet new` 命令。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-214">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="4f1b3-215">從在 *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp* 建立的新專案資料夾，建立來自 `garciaconsole` 範本的專案：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-215">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="4f1b3-216">解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-216">Uninstall the template</span></span>

<span data-ttu-id="4f1b3-217">如果在 *C:\Users\\\<USER>\Document\Templates\GarciaSoftware.ConsoleTemplate.CSharp* 的本機檔案系統上建立範本，請使用 `-u|--uninstall` 參數和範本資料夾路徑將其解除安裝：</span><span class="sxs-lookup"><span data-stu-id="4f1b3-217">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="4f1b3-218">若要將範本從您的本機檔案系統解除安裝，您需要使路徑成為完整路徑。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-218">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="4f1b3-219">例如，*C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-219">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4f1b3-220">此外，請勿在範本路徑中包含最終結尾目錄斜線。</span><span class="sxs-lookup"><span data-stu-id="4f1b3-220">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f1b3-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f1b3-221">See also</span></span>

- <span data-ttu-id="4f1b3-222">[dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="4f1b3-222">[dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)</span></span>
- <span data-ttu-id="4f1b3-223">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="4f1b3-223">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="4f1b3-224">如何建立您自己的 dotnet new 範本</span><span class="sxs-lookup"><span data-stu-id="4f1b3-224">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="4f1b3-225">JSON 結構描述保存區的 *template.json* 結構描述</span><span class="sxs-lookup"><span data-stu-id="4f1b3-225">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
