---
title: dotnet new 的自訂範本
description: 了解任何 .NET 專案或檔案類型的自訂範本。
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: d513965a60416392fb8acd15c9f89c8af0ec7876
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660582"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="bf42e-103">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="bf42e-104">[.NET Core SDK](https://www.microsoft.com/net/download/core) \(英文\) 具有許多已經安裝並可供您使用的範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-104">The [.NET Core SDK](https://www.microsoft.com/net/download/core) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="bf42e-105">[`dotnet new` 命令](dotnet-new.md)不僅是使用範本的方式，也是安裝及解除安裝範本的方式。</span><span class="sxs-lookup"><span data-stu-id="bf42e-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="bf42e-106">從 .NET Core 2.0 開始，您可以建立任何專案類型的自訂範本，例如應用程式、服務、工具或類別庫。</span><span class="sxs-lookup"><span data-stu-id="bf42e-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="bf42e-107">您甚至可以建立會輸出一或多個獨立檔案的範本，例如組態檔。</span><span class="sxs-lookup"><span data-stu-id="bf42e-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="bf42e-108">您可以直接參考 NuGet *.nupkg* 檔案，或指定包含範本的檔案系統目錄，來從任何 NuGet 摘要上的 NuGet 套件安裝自訂的範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="bf42e-109">範本引擎提供可讓您取代值、包含與排除檔案，以及在範本被使用時執行自訂處理作業的功能。</span><span class="sxs-lookup"><span data-stu-id="bf42e-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="bf42e-110">範本引擎是開放原始碼，而線上程式碼存放庫位於 GitHub 的 [dotnet/templating](https://github.com/dotnet/templating/)。</span><span class="sxs-lookup"><span data-stu-id="bf42e-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="bf42e-111">如需範本範例，請瀏覽 [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="bf42e-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="bf42e-112">GitHub 的 [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (dotnet new 的可用範本) 中，有包括協力廠商範本在內的更多範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="bf42e-113">如需建立與使用自訂範本的詳細資訊，請參閱[如何建立您自己的 dotnet new 範本](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)以及 [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)。</span><span class="sxs-lookup"><span data-stu-id="bf42e-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="bf42e-114">若要遵循逐步解說並建立範本，請參閱[建立 dotnet new 的自訂範本](../tutorials/create-custom-template.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="bf42e-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/create-custom-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="bf42e-115">.NET 預設範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-115">.NET default templates</span></span>

<span data-ttu-id="bf42e-116">當您安裝 [.NET Core SDK](https://www.microsoft.com/net/download/core) 時，您會收到十多個用於建立專案和檔案的內建範本，包括主控台應用程式、類別庫、單元測試專案，ASP.NET Core 應用程式 (包括 [Angular](https://angular.io/) 和 [React](https://facebook.github.io/react/) 專案) 和組態檔。</span><span class="sxs-lookup"><span data-stu-id="bf42e-116">When you install the [.NET Core SDK](https://www.microsoft.com/net/download/core), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="bf42e-117">若要列出內建範本，請執行搭配 `-l|--list` 選項執行 `dotnet new` 命令：</span><span class="sxs-lookup"><span data-stu-id="bf42e-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```console
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="bf42e-118">Configuration</span><span class="sxs-lookup"><span data-stu-id="bf42e-118">Configuration</span></span>

<span data-ttu-id="bf42e-119">範本是由下列部分組成：</span><span class="sxs-lookup"><span data-stu-id="bf42e-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="bf42e-120">來源檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf42e-120">Source files and folders.</span></span>
- <span data-ttu-id="bf42e-121">設定檔 (*template.json*)。</span><span class="sxs-lookup"><span data-stu-id="bf42e-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="bf42e-122">來源檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="bf42e-122">Source files and folders</span></span>

<span data-ttu-id="bf42e-123">來源檔案和資料夾包含您想要範本引擎在 `dotnet new <TEMPLATE>` 命令被執行時使用的任何檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf42e-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="bf42e-124">範本引擎的設計是將「可執行專案」  用為原始程式碼以產生專案。</span><span class="sxs-lookup"><span data-stu-id="bf42e-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="bf42e-125">這有幾項優點：</span><span class="sxs-lookup"><span data-stu-id="bf42e-125">This has several benefits:</span></span>

- <span data-ttu-id="bf42e-126">範本引擎不需要您將特殊權杖插入專案的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf42e-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="bf42e-127">程式碼檔案不是特殊的檔案，也不使用範本引擎以任何方式修改。</span><span class="sxs-lookup"><span data-stu-id="bf42e-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="bf42e-128">因此，通常在處理專案時使用的工具也用來處理範本內容。</span><span class="sxs-lookup"><span data-stu-id="bf42e-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="bf42e-129">您會建置、執行和偵錯範本專案，就如同您對任何其他專案一樣。</span><span class="sxs-lookup"><span data-stu-id="bf42e-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="bf42e-130">您可以將 *./.template.config/template.json* 設定檔新增至專案，來快速地從現有專案建立範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="bf42e-131">儲存在範本中的檔案和資料夾不限於正式的 .NET 專案類型。</span><span class="sxs-lookup"><span data-stu-id="bf42e-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="bf42e-132">來源檔案和資料夾可由您想要在範本被使用時建立的任何內容組成，即使範本引擎只會產生單一檔案作為其輸出。</span><span class="sxs-lookup"><span data-stu-id="bf42e-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="bf42e-133">由範本產生的檔案可以根據您在 *template.json* 設定檔中所提供的邏輯和設定進行修改。</span><span class="sxs-lookup"><span data-stu-id="bf42e-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="bf42e-134">使用者可以將選項傳遞至 `dotnet new <TEMPLATE>` 命令來覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="bf42e-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="bf42e-135">自訂邏輯的常見範例之一，是針對由範本所部署之程式碼檔案中的類別或變數提供名稱。</span><span class="sxs-lookup"><span data-stu-id="bf42e-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="bf42e-136">template.json</span><span class="sxs-lookup"><span data-stu-id="bf42e-136">template.json</span></span>

<span data-ttu-id="bf42e-137">*template.json* 檔案放在範本根目錄的 *.template.config* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bf42e-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="bf42e-138">檔案向範本引擎提供組態資訊。</span><span class="sxs-lookup"><span data-stu-id="bf42e-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="bf42e-139">最小的組態需要下表顯示的成員，這即足以建立具有功能的範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="bf42e-140">成員</span><span class="sxs-lookup"><span data-stu-id="bf42e-140">Member</span></span>            | <span data-ttu-id="bf42e-141">類型</span><span class="sxs-lookup"><span data-stu-id="bf42e-141">Type</span></span>          | <span data-ttu-id="bf42e-142">說明</span><span class="sxs-lookup"><span data-stu-id="bf42e-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="bf42e-143">URI</span><span class="sxs-lookup"><span data-stu-id="bf42e-143">URI</span></span>           | <span data-ttu-id="bf42e-144">*template.json* 檔案的 JSON 結構描述。</span><span class="sxs-lookup"><span data-stu-id="bf42e-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="bf42e-145">支援 JSON 結構描述的編輯器，會在指定結構描述時，啟用 JSON 編輯功能。</span><span class="sxs-lookup"><span data-stu-id="bf42e-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="bf42e-146">例如，[Visual Studio Code](https://code.visualstudio.com/) 需要此成員才能啟用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="bf42e-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="bf42e-147">使用 `http://json.schemastore.org/template` 的值。</span><span class="sxs-lookup"><span data-stu-id="bf42e-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="bf42e-148">字串</span><span class="sxs-lookup"><span data-stu-id="bf42e-148">string</span></span>        | <span data-ttu-id="bf42e-149">範本的作者。</span><span class="sxs-lookup"><span data-stu-id="bf42e-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="bf42e-150">array(string)</span><span class="sxs-lookup"><span data-stu-id="bf42e-150">array(string)</span></span> | <span data-ttu-id="bf42e-151">搜尋範本時，使用者可能用來尋找範本的零或多個範本特性。</span><span class="sxs-lookup"><span data-stu-id="bf42e-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="bf42e-152">當它出現在使用 `dotnet new -l|--list` 命令產生的範本清單中時，分類也會出現在「標記」  資料行中。</span><span class="sxs-lookup"><span data-stu-id="bf42e-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="bf42e-153">字串</span><span class="sxs-lookup"><span data-stu-id="bf42e-153">string</span></span>        | <span data-ttu-id="bf42e-154">此範本的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="bf42e-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="bf42e-155">字串</span><span class="sxs-lookup"><span data-stu-id="bf42e-155">string</span></span>        | <span data-ttu-id="bf42e-156">使用者應該會看到的範本名稱。</span><span class="sxs-lookup"><span data-stu-id="bf42e-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="bf42e-157">字串</span><span class="sxs-lookup"><span data-stu-id="bf42e-157">string</span></span>        | <span data-ttu-id="bf42e-158">適用於選取要套用至環境之範本的預設速記名稱；此環境中的範本名稱是由使用者指定，而不是透過 GUI 選取。</span><span class="sxs-lookup"><span data-stu-id="bf42e-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="bf42e-159">例如，從命令提示字元以 CLI 命令使用範本時，簡短名稱很有用。</span><span class="sxs-lookup"><span data-stu-id="bf42e-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="bf42e-160">*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="bf42e-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="bf42e-161">如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="bf42e-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="bf42e-162">範例</span><span class="sxs-lookup"><span data-stu-id="bf42e-162">Example</span></span>

<span data-ttu-id="bf42e-163">例如，這是包含下列兩個內容檔案的範本資料夾：*console.cs* 和 *readme.txt*。</span><span class="sxs-lookup"><span data-stu-id="bf42e-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="bf42e-164">請注意，有一個名為 *.template.config* 且包含 *template.json* 檔案的必要資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf42e-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="bf42e-165">*template.json* 檔案看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf42e-165">The *template.json* file looks like the following:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

<span data-ttu-id="bf42e-166">*mytemplate* 資料夾為可安裝的範本套件。</span><span class="sxs-lookup"><span data-stu-id="bf42e-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="bf42e-167">安裝套件之後，便可以搭配 `dotnet new` 命令使用 `shortName`。</span><span class="sxs-lookup"><span data-stu-id="bf42e-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="bf42e-168">例如，`dotnet new adatumconsole` 會將 `console.cs` 和 `readme.txt` 檔案輸出至目前的資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf42e-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="bf42e-169">將範本封裝在 NuGet 套件中 (nupkg 檔案)</span><span class="sxs-lookup"><span data-stu-id="bf42e-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="bf42e-170">自訂範本會搭配 [dotnet pack](dotnet-pack.md) 命令和 *.csproj* 檔案進行封裝。</span><span class="sxs-lookup"><span data-stu-id="bf42e-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="bf42e-171">或者，[NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) \(部分機器翻譯\) 可以搭配 [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) \(部分機器翻譯\) 命令和 *.nuspec* 檔案使用。</span><span class="sxs-lookup"><span data-stu-id="bf42e-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="bf42e-172">不過，NuGet 在 Windows 上需要 .NET Framework，在 Linux 和 MacOS 上則需要 [Mono](https://www.mono-project.com/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="bf42e-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="bf42e-173">*.csproj* 檔案與傳統的程式碼專案 *.csproj* 檔案具有些微的不同。</span><span class="sxs-lookup"><span data-stu-id="bf42e-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="bf42e-174">請注意下列設定：</span><span class="sxs-lookup"><span data-stu-id="bf42e-174">Note the following settings:</span></span>

01. <span data-ttu-id="bf42e-175">已加入 `<PackageType>` 設定並將其設定為 `Template`。</span><span class="sxs-lookup"><span data-stu-id="bf42e-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="bf42e-176">已加入 `<PackageVersion>` 設定並將其設定為有效的 [NuGet 版本號碼](/nuget/reference/package-versioning)。</span><span class="sxs-lookup"><span data-stu-id="bf42e-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="bf42e-177">已加入 `<PackageId>` 設定並將其設定為唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="bf42e-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="bf42e-178">此識別碼是用來將範本套件解除安裝，並由 NuGet 摘要用來註冊您的範本套件。</span><span class="sxs-lookup"><span data-stu-id="bf42e-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="bf42e-179">應該設定的一般中繼資料：`<Title>`、`<Authors>`、`<Description>`，以及 `<PackageTags>`。</span><span class="sxs-lookup"><span data-stu-id="bf42e-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="bf42e-180">必須設定 `<TargetFramework>` 設定，即使由範本程序所產生的二進位檔不會被使用。</span><span class="sxs-lookup"><span data-stu-id="bf42e-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="bf42e-181">在下列範例中，它被設定為 `netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="bf42e-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="bf42e-182">具有 *.nupkg* NuGet 套件的範本套件，會要求將所有範本都儲存在套件內的 *content* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bf42e-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="bf42e-183">還有幾個設定需要被加入至 *.csproj* 檔案，以確保可以將所產生的 *.nupkg* 安裝為範本套件：</span><span class="sxs-lookup"><span data-stu-id="bf42e-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="bf42e-184">`<IncludeContentInPack>` 設定已被設定為 `true`，以將專案設定為 **content** 的任何檔案包含在 NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="bf42e-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="bf42e-185">`<IncludeBuildOutput>` 設定已被設定為 `false`，以將編譯器所產生的所有二進位檔從 NuGet 套件排除。</span><span class="sxs-lookup"><span data-stu-id="bf42e-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="bf42e-186">`<ContentTargetFolders>` 設定已被設定為 `content`。</span><span class="sxs-lookup"><span data-stu-id="bf42e-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="bf42e-187">這能確保設定為 **content** 的檔案都會被儲存在 NuGet 套件中的 *content* 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="bf42e-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="bf42e-188">NuGet 套件中的這個資料夾會由 dotnet 範本系統進行剖析。</span><span class="sxs-lookup"><span data-stu-id="bf42e-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="bf42e-189">排除所有程式碼檔案來使範本專案不會對它們進行編譯的簡單方式，是在專案檔中於 `<ItemGroup>` 元素內使用 `<Compile Remove="**\*" />` 項目。</span><span class="sxs-lookup"><span data-stu-id="bf42e-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="bf42e-190">建構範本套件的簡單方式，是將所有範本置於個別的資料夾中，然後將每個範本資料夾置於與 *.csproj* 檔案相同目錄中的 *templates* 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="bf42e-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="bf42e-191">如此一來，您便可以使用單一專案項目來將 *templates* 中的所有檔案和資料夾包含為 **content**。</span><span class="sxs-lookup"><span data-stu-id="bf42e-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="bf42e-192">在 `<ItemGroup>` 元素內，建立 `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` 項目。</span><span class="sxs-lookup"><span data-stu-id="bf42e-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="bf42e-193">以下是遵循上述所有指導方針的範例 *.csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf42e-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="bf42e-194">它會將 *templates* 子資料夾封裝至 *content* 套件資料夾，並將所有程式碼檔案排除於編譯程序之外。</span><span class="sxs-lookup"><span data-stu-id="bf42e-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>
    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="bf42e-195">下列範例示範使用 *.csproj* 來建立範本套件的檔案和資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="bf42e-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="bf42e-196">*MyDotnetTemplates.csproj* 檔案和 *templates* 資料夾皆位於名為 *project_folder* 之目錄的根位置。</span><span class="sxs-lookup"><span data-stu-id="bf42e-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="bf42e-197">*templates* 資料夾包含兩個範本，*mytemplate1* 和 *mytemplate2*。</span><span class="sxs-lookup"><span data-stu-id="bf42e-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="bf42e-198">每個範本都具有內容檔案，以及具有 *template.json* 設定檔的 *.template.config* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf42e-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a><span data-ttu-id="bf42e-199">安裝範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-199">Installing a template</span></span>

<span data-ttu-id="bf42e-200">使用 [dotnet new -i|--install](dotnet-new.md) 命令來安裝套件。</span><span class="sxs-lookup"><span data-stu-id="bf42e-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="bf42e-201">從儲存在 nuget.org 的 NuGet 套件安裝範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="bf42e-202">使用 NuGet 套件識別碼來安裝範本套件。</span><span class="sxs-lookup"><span data-stu-id="bf42e-202">Use the NuGet package identifier to install a template package.</span></span>

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="bf42e-203">從本機 nupkg 檔案安裝範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="bf42e-204">提供 *.nupkg* NuGet 套件檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="bf42e-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="bf42e-205">從檔案系統目錄安裝範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-205">To install a template from a file system directory</span></span>

<span data-ttu-id="bf42e-206">可以從範本資料夾 (例如上述範例中的 *mytemplate1* 資料夾) 安裝範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="bf42e-207">指定 *.template.config* 資料夾的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="bf42e-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="bf42e-208">範本資料夾的路徑並不需要是絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="bf42e-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="bf42e-209">不過，若要將從某個資料夾安裝的範本解除安裝，便需要絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="bf42e-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="bf42e-210">取得已安裝範本的清單</span><span class="sxs-lookup"><span data-stu-id="bf42e-210">Get a list of installed templates</span></span>

<span data-ttu-id="bf42e-211">沒有任何其他參數的解除安裝命令，將會列出所有已安裝的範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```console
dotnet new -u
```

<span data-ttu-id="bf42e-212">該命令會傳回類似下列輸出的內容：</span><span class="sxs-lookup"><span data-stu-id="bf42e-212">That command returns something similar to the following output:</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

<span data-ttu-id="bf42e-213">`Currently installed items:` 之後的第一層項目，是用來將範本解除安裝的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bf42e-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="bf42e-214">而在上述範例中，系統會列出 `Microsoft.DotNet.Common.ItemTemplates` 和 `Microsoft.DotNet.Common.ProjectTemplates.3.0`。</span><span class="sxs-lookup"><span data-stu-id="bf42e-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="bf42e-215">如果範本是使用檔案系統路徑安裝，此識別碼將會是 *.template.config* 資料夾的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="bf42e-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="bf42e-216">解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-216">Uninstalling a template</span></span>

<span data-ttu-id="bf42e-217">使用 [dotnet new -u|--uninstall](dotnet-new.md) 命令來解除安裝套件。</span><span class="sxs-lookup"><span data-stu-id="bf42e-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="bf42e-218">如果套件是由 NuGet 摘要或直接由 *.nupkg* 檔案安裝，請提供識別碼。</span><span class="sxs-lookup"><span data-stu-id="bf42e-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="bf42e-219">如果套件是透過指定 *.template.config* 資料夾路徑的方式安裝，請使用該**絕對**路徑來將套件解除安裝。</span><span class="sxs-lookup"><span data-stu-id="bf42e-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="bf42e-220">您可以在由 `dotnet new -u` 命令所提供的輸出中查看範本的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="bf42e-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="bf42e-221">如需詳細資訊，請參閱上面的[取得已安裝範本的清單](#get-a-list-of-installed-templates)小節。</span><span class="sxs-lookup"><span data-stu-id="bf42e-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="bf42e-222">使用自訂範本建立專案</span><span class="sxs-lookup"><span data-stu-id="bf42e-222">Create a project using a custom template</span></span>

<span data-ttu-id="bf42e-223">在安裝範本之後，如同處理任何其他預先安裝的範本一樣，執行 `dotnet new <TEMPLATE>` 命令使用範本。</span><span class="sxs-lookup"><span data-stu-id="bf42e-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="bf42e-224">您也可以指定 `dotnet new` 命令的[選項](dotnet-new.md#options)，包括您在範本設定中設定的範本特定選項。</span><span class="sxs-lookup"><span data-stu-id="bf42e-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="bf42e-225">直接將範本的簡短名稱提供給命令：</span><span class="sxs-lookup"><span data-stu-id="bf42e-225">Supply the template's short name directly to the command:</span></span>

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="bf42e-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf42e-226">See also</span></span>

- [<span data-ttu-id="bf42e-227">建立 dotnet new 的自訂範本 (教學課程)</span><span class="sxs-lookup"><span data-stu-id="bf42e-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/create-custom-template.md)
- <span data-ttu-id="bf42e-228">[dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="bf42e-228">[dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)</span></span>
- <span data-ttu-id="bf42e-229">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="bf42e-229">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>
- [<span data-ttu-id="bf42e-230">如何建立您自己的 dotnet new 範本</span><span class="sxs-lookup"><span data-stu-id="bf42e-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="bf42e-231">JSON 結構描述保存區的 *template.json* 結構描述</span><span class="sxs-lookup"><span data-stu-id="bf42e-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
