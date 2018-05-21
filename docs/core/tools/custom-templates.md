---
title: dotnet new 的自訂範本
description: 了解任何 .NET 專案或檔案類型的自訂範本。
author: guardrex
ms.author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: fe888d0bfeeb51d77b73ec481b93fec9b40aa6ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="be6e1-103">dotnet new 的自訂範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="be6e1-104">[.NET Core SDK](https://www.microsoft.com/net/download/core) 隨附許多預先安裝的範本，搭配 [`dotnet new` 命令](dotnet-new.md)一起使用。</span><span class="sxs-lookup"><span data-stu-id="be6e1-104">The [.NET Core SDK](https://www.microsoft.com/net/download/core) comes with many templates pre-installed to use with the [`dotnet new` command](dotnet-new.md).</span></span> <span data-ttu-id="be6e1-105">從 .NET Core 2.0 開始，您可以建立任何專案類型的自訂範本，例如應用程式、服務、工具或類別庫。</span><span class="sxs-lookup"><span data-stu-id="be6e1-105">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="be6e1-106">您甚至可以建立會輸出一或多個獨立檔案的範本，例如組態檔。</span><span class="sxs-lookup"><span data-stu-id="be6e1-106">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="be6e1-107">您可以直接參考 NuGet *nupkg* 檔案，或指定包含範本的檔案系統目錄，從任何 NuGet 摘要的 NuGet 套件安裝自訂的範本。</span><span class="sxs-lookup"><span data-stu-id="be6e1-107">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="be6e1-108">範本引擎提供的功能，可讓您取代值、包含與排除檔案和檔案區域，以及在使用範本時執行自訂的處理作業。</span><span class="sxs-lookup"><span data-stu-id="be6e1-108">The template engine offers features that allow you to replace values, include and exclude files and regions of files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="be6e1-109">範本引擎是開放原始碼，而線上程式碼存放庫位於 GitHub 的 [dotnet/templating](https://github.com/dotnet/templating/)。</span><span class="sxs-lookup"><span data-stu-id="be6e1-109">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="be6e1-110">如需範本範例，請瀏覽 [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="be6e1-110">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="be6e1-111">GitHub 的 [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (dotnet new 的可用範本) 中，有包括協力廠商範本在內的更多範本。</span><span class="sxs-lookup"><span data-stu-id="be6e1-111">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="be6e1-112">如需建立與使用自訂範本的詳細資訊，請參閱[如何建立您自己的 dotnet new 範本](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)以及 [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)。</span><span class="sxs-lookup"><span data-stu-id="be6e1-112">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="be6e1-113">若要遵循逐步解說並建立範本，請參閱[建立 dotnet new 的自訂範本](~/docs/core/tutorials/create-custom-template.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="be6e1-113">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

## <a name="configuration"></a><span data-ttu-id="be6e1-114">組態</span><span class="sxs-lookup"><span data-stu-id="be6e1-114">Configuration</span></span>

<span data-ttu-id="be6e1-115">範本是由下列元件組成：</span><span class="sxs-lookup"><span data-stu-id="be6e1-115">A template is composed of the following components:</span></span>

- <span data-ttu-id="be6e1-116">來源檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="be6e1-116">Source files and folders</span></span>
- <span data-ttu-id="be6e1-117">組態檔 (*template.json*)</span><span class="sxs-lookup"><span data-stu-id="be6e1-117">A configuration file (*template.json*)</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="be6e1-118">來源檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="be6e1-118">Source files and folders</span></span>

<span data-ttu-id="be6e1-119">來源檔案和資料夾包含執行 `dotnet new <TEMPLATE>` 命令時，您希望範本引擎使用的任何檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="be6e1-119">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is executed.</span></span> <span data-ttu-id="be6e1-120">範本引擎的設計是將「可執行專案」用為原始程式碼以產生專案。</span><span class="sxs-lookup"><span data-stu-id="be6e1-120">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="be6e1-121">這有幾項優點：</span><span class="sxs-lookup"><span data-stu-id="be6e1-121">This has several benefits:</span></span>

- <span data-ttu-id="be6e1-122">範本引擎不需要您將特殊權杖插入專案的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="be6e1-122">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="be6e1-123">程式碼檔案不是特殊的檔案，也不使用範本引擎以任何方式修改。</span><span class="sxs-lookup"><span data-stu-id="be6e1-123">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="be6e1-124">因此，通常在處理專案時使用的工具也用來處理範本內容。</span><span class="sxs-lookup"><span data-stu-id="be6e1-124">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="be6e1-125">您會建置、執行和偵錯範本專案，就如同您對任何其他專案一樣。</span><span class="sxs-lookup"><span data-stu-id="be6e1-125">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="be6e1-126">您可以從現有的專案快速建立範本，只要將 *template.json* 組態檔新增至專案即可。</span><span class="sxs-lookup"><span data-stu-id="be6e1-126">You can quickly create a template from an existing project just by adding a *template.json* configuration file to the project.</span></span>

<span data-ttu-id="be6e1-127">儲存在範本中的檔案和資料夾不限於正式的 .NET 專案類型，例如 .NET Core 或 .NET Framework 解決方案。</span><span class="sxs-lookup"><span data-stu-id="be6e1-127">Files and folders stored in the template aren't limited to formal .NET project types, such as .NET Core or .NET Framework solutions.</span></span> <span data-ttu-id="be6e1-128">當使用範本時，來源檔案和資料夾可由任何您想要建立的內容組成，即使範本引擎只產生一個輸出檔，例如組態檔或方案檔。</span><span class="sxs-lookup"><span data-stu-id="be6e1-128">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file for its output, such as a configuration file or a solution file.</span></span> <span data-ttu-id="be6e1-129">例如，您可以建立包含 *web.config* 來源檔案的範本，並為已使用範本的專案建立修改過的 *web.config* 檔案。</span><span class="sxs-lookup"><span data-stu-id="be6e1-129">For example, you can create a template that contains a *web.config* source file and creates a modified *web.config* file for projects where the template is used.</span></span> <span data-ttu-id="be6e1-130">根據您在 *template.json* 組態檔提供的邏輯和設定，以及使用者提供的值 (當成選項傳遞給 `dotnet new <TEMPLATE>` 命令)，修改來源檔案。</span><span class="sxs-lookup"><span data-stu-id="be6e1-130">The modifications to source files are based on logic and settings you've provided in the *template.json* configuration file along with values provided by the user passed as options to the `dotnet new <TEMPLATE>` command.</span></span>

### <a name="templatejson"></a><span data-ttu-id="be6e1-131">template.json</span><span class="sxs-lookup"><span data-stu-id="be6e1-131">template.json</span></span>

<span data-ttu-id="be6e1-132">*template.json* 檔案放在範本根目錄的 *.template.config* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="be6e1-132">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="be6e1-133">檔案向範本引擎提供組態資訊。</span><span class="sxs-lookup"><span data-stu-id="be6e1-133">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="be6e1-134">最小的組態需要下表顯示的成員，這即足以建立具有功能的範本。</span><span class="sxs-lookup"><span data-stu-id="be6e1-134">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="be6e1-135">成員</span><span class="sxs-lookup"><span data-stu-id="be6e1-135">Member</span></span>            | <span data-ttu-id="be6e1-136">類型</span><span class="sxs-lookup"><span data-stu-id="be6e1-136">Type</span></span>          | <span data-ttu-id="be6e1-137">描述</span><span class="sxs-lookup"><span data-stu-id="be6e1-137">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="be6e1-138">URI</span><span class="sxs-lookup"><span data-stu-id="be6e1-138">URI</span></span>           | <span data-ttu-id="be6e1-139">*template.json* 檔案的 JSON 結構描述。</span><span class="sxs-lookup"><span data-stu-id="be6e1-139">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="be6e1-140">支援 JSON 結構描述的編輯器，會在指定結構描述時，啟用 JSON 編輯功能。</span><span class="sxs-lookup"><span data-stu-id="be6e1-140">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="be6e1-141">例如，[Visual Studio Code](https://code.visualstudio.com/) 需要此成員才能啟用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="be6e1-141">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="be6e1-142">使用 `http://json.schemastore.org/template` 的值。</span><span class="sxs-lookup"><span data-stu-id="be6e1-142">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="be6e1-143">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-143">string</span></span>        | <span data-ttu-id="be6e1-144">範本的作者。</span><span class="sxs-lookup"><span data-stu-id="be6e1-144">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="be6e1-145">array(string)</span><span class="sxs-lookup"><span data-stu-id="be6e1-145">array(string)</span></span> | <span data-ttu-id="be6e1-146">搜尋範本時，使用者可能用來尋找範本的零或多個範本特性。</span><span class="sxs-lookup"><span data-stu-id="be6e1-146">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="be6e1-147">當它出現在使用 <code>dotnet new -l&#124;--list</code> 命令產生的範本清單中時，分類也會出現在「標記」資料行中。</span><span class="sxs-lookup"><span data-stu-id="be6e1-147">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the <code>dotnet new -l&#124;--list</code> command.</span></span> |
| `identity`        | <span data-ttu-id="be6e1-148">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-148">string</span></span>        | <span data-ttu-id="be6e1-149">此範本的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="be6e1-149">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="be6e1-150">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-150">string</span></span>        | <span data-ttu-id="be6e1-151">使用者應該會看到的範本名稱。</span><span class="sxs-lookup"><span data-stu-id="be6e1-151">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="be6e1-152">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-152">string</span></span>        | <span data-ttu-id="be6e1-153">預設的速記，用於選取適用於環境的範本，在此環境中，範本名稱由使用者指定，不是透過 GUI 選取。</span><span class="sxs-lookup"><span data-stu-id="be6e1-153">A default shorthand for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="be6e1-154">例如，從命令提示字元以 CLI 命令使用範本時，簡短名稱很有用。</span><span class="sxs-lookup"><span data-stu-id="be6e1-154">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

#### <a name="example"></a><span data-ttu-id="be6e1-155">範例：</span><span class="sxs-lookup"><span data-stu-id="be6e1-155">Example:</span></span>

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

<span data-ttu-id="be6e1-156">*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="be6e1-156">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span>

## <a name="net-default-templates"></a><span data-ttu-id="be6e1-157">.NET 預設範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-157">.NET default templates</span></span>

<span data-ttu-id="be6e1-158">當您安裝 [.NET Core SDK](https://www.microsoft.com/net/download/core) 時，您會收到十多個用於建立專案和檔案的內建範本，包括主控台應用程式、類別庫、單元測試專案，ASP.NET Core 應用程式 (包括 [Angular](https://angular.io/) 和 [React](https://facebook.github.io/react/) 專案) 和組態檔。</span><span class="sxs-lookup"><span data-stu-id="be6e1-158">When you install the [.NET Core SDK](https://www.microsoft.com/net/download/core), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="be6e1-159">若要列出內建範本，請執行 `dotnet new` 命令搭配 `-l|--list` 選項：</span><span class="sxs-lookup"><span data-stu-id="be6e1-159">To list the built-in templates, execute the `dotnet new` command with the `-l|--list` option:</span></span>

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="be6e1-160">將範本封裝在 NuGet 套件中 (nupkg 檔案)</span><span class="sxs-lookup"><span data-stu-id="be6e1-160">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="be6e1-161">目前，Windows 上的自訂範本使用 [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) 封裝 (不是 [dotnet pack](dotnet-pack.md))。</span><span class="sxs-lookup"><span data-stu-id="be6e1-161">Currently, a custom template is packed on Windows with [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (not [dotnet pack](dotnet-pack.md)).</span></span> <span data-ttu-id="be6e1-162">跨平台的封裝請考慮使用 [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000)。</span><span class="sxs-lookup"><span data-stu-id="be6e1-162">For cross-platform packaging, consider using [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).</span></span>

<span data-ttu-id="be6e1-163">將專案資料夾的內容及其 *.template.config/template.json* 檔案放入名為 *content* 的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="be6e1-163">The contents of the project folder, together with its *.template.config/template.json* file, are placed into a folder named *content*.</span></span> <span data-ttu-id="be6e1-164">在 *content* 資料夾旁邊，新增 [*nuspec* 檔案](/nuget/create-packages/creating-a-package)，它是 XML 資訊清單檔案，描述套件的內容及驅動建立 NuGet 套件的程序。</span><span class="sxs-lookup"><span data-stu-id="be6e1-164">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package), which is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span> <span data-ttu-id="be6e1-165">在 *nuspec* 檔案的 **\<packageTypes>** 項目內，包含 `name` 屬性值為 `Template` 的 **\<packageType>** 項目。</span><span class="sxs-lookup"><span data-stu-id="be6e1-165">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="be6e1-166">*content* 資料夾和 *nuspec* 檔案都應該位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="be6e1-166">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="be6e1-167">下表顯示將範本製作為 NuGet 套件所需之最小的 *nuspec* 檔案項目。</span><span class="sxs-lookup"><span data-stu-id="be6e1-167">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

| <span data-ttu-id="be6e1-168">元素</span><span class="sxs-lookup"><span data-stu-id="be6e1-168">Element</span></span>            | <span data-ttu-id="be6e1-169">類型</span><span class="sxs-lookup"><span data-stu-id="be6e1-169">Type</span></span>   | <span data-ttu-id="be6e1-170">描述</span><span class="sxs-lookup"><span data-stu-id="be6e1-170">Description</span></span> |
| ------------------ | ------ | ----------- |
| <span data-ttu-id="be6e1-171">**\<作者>**</span><span class="sxs-lookup"><span data-stu-id="be6e1-171">**\<authors>**</span></span>     | <span data-ttu-id="be6e1-172">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-172">string</span></span> | <span data-ttu-id="be6e1-173">以逗號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些作者會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。</span><span class="sxs-lookup"><span data-stu-id="be6e1-173">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
| <span data-ttu-id="be6e1-174">**\<描述>**</span><span class="sxs-lookup"><span data-stu-id="be6e1-174">**\<description>**</span></span> | <span data-ttu-id="be6e1-175">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-175">string</span></span> | <span data-ttu-id="be6e1-176">UI 顯示中的套件詳細描述。</span><span class="sxs-lookup"><span data-stu-id="be6e1-176">A long description of the package for UI display.</span></span> |
| <span data-ttu-id="be6e1-177">**\<識別碼>**</span><span class="sxs-lookup"><span data-stu-id="be6e1-177">**\<id>**</span></span>          | <span data-ttu-id="be6e1-178">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-178">string</span></span> | <span data-ttu-id="be6e1-179">不區分大小寫的套件識別碼，在整個 nuget.org 或套件所在的任何組件庫都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="be6e1-179">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="be6e1-180">識別碼可能不包含對 URL 而言無效的空格或字元，而且通常會遵循 .NET 命名空間規則。</span><span class="sxs-lookup"><span data-stu-id="be6e1-180">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="be6e1-181">如需指導方針，請參閱[選擇唯一的套件識別碼並設定版本號碼](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)。</span><span class="sxs-lookup"><span data-stu-id="be6e1-181">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
| <span data-ttu-id="be6e1-182">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="be6e1-182">**\<packageType>**</span></span> | <span data-ttu-id="be6e1-183">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-183">string</span></span> | <span data-ttu-id="be6e1-184">將此項目放在 **\<metadata>** 項目中的 **\<packageTypes>** 項目內。</span><span class="sxs-lookup"><span data-stu-id="be6e1-184">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="be6e1-185">將 **\<packageType>** 項目的 `name` 屬性設定為 `Template`。</span><span class="sxs-lookup"><span data-stu-id="be6e1-185">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
| <span data-ttu-id="be6e1-186">**\<版本>**</span><span class="sxs-lookup"><span data-stu-id="be6e1-186">**\<version>**</span></span>     | <span data-ttu-id="be6e1-187">字串</span><span class="sxs-lookup"><span data-stu-id="be6e1-187">string</span></span> | <span data-ttu-id="be6e1-188">套件版本，遵循 major.minor.patch 模式。</span><span class="sxs-lookup"><span data-stu-id="be6e1-188">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="be6e1-189">版本號碼可以包含預先發行版本的後置詞，如[預先發行版本](/nuget/create-packages/prerelease-packages#semantic-versioning)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="be6e1-189">Version numbers may include a pre-release suffix as described in the [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning) topic.</span></span> |

<span data-ttu-id="be6e1-190">請參閱 [.nuspec 參考](/nuget/schema/nuspec)以取得完整的 *nuspec* 檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="be6e1-190">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span> <span data-ttu-id="be6e1-191">範本的範例 *nuspec* 檔案會出現在[建立 dotnet new 的自訂範本](~/docs/core/tutorials/create-custom-template.md)教學課程中。</span><span class="sxs-lookup"><span data-stu-id="be6e1-191">An example *nuspec* file for a template appears in the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

<span data-ttu-id="be6e1-192">使用 `nuget pack <PATH_TO_NUSPEC_FILE>` 命令[建立套件](/nuget/create-packages/creating-a-package#creating-the-package)。</span><span class="sxs-lookup"><span data-stu-id="be6e1-192">[Create a package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span>

## <a name="installing-a-template"></a><span data-ttu-id="be6e1-193">安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-193">Installing a template</span></span>

<span data-ttu-id="be6e1-194">直接參考 *nupkg* 檔案，或指定包含組態範本的檔案系統目錄，從任何 NuGet 摘要的 NuGet 套件安裝自訂的範本。</span><span class="sxs-lookup"><span data-stu-id="be6e1-194">Install a custom template from a NuGet package on any NuGet feed by referencing a *nupkg* file directly or by specifying a file system directory that contains a templating configuration.</span></span> <span data-ttu-id="be6e1-195">使用 `-i|--install` 選項與 [dotnet new](dotnet-new.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="be6e1-195">Use the `-i|--install` option with the [dotnet new](dotnet-new.md) command.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="be6e1-196">從儲存在 nuget.org 的 NuGet 套件安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-196">To install a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="be6e1-197">從本機 nupkg 檔案安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-197">To install a template from a local nupkg file</span></span>

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="be6e1-198">從檔案系統目錄安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-198">To install a template from a file system directory</span></span>

<span data-ttu-id="be6e1-199">`FILE_SYSTEM_DIRECTORY` 是包含專案和 *.template.config* 資料夾的專案資料夾：</span><span class="sxs-lookup"><span data-stu-id="be6e1-199">The `FILE_SYSTEM_DIRECTORY` is the project folder containing the project and the *.template.config* folder:</span></span>

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a><span data-ttu-id="be6e1-200">解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-200">Uninstalling a template</span></span>

<span data-ttu-id="be6e1-201">參考 NuGet 套件的 `id` 或指定包含組態範本的檔案系統目錄，解除安裝自訂的範本。</span><span class="sxs-lookup"><span data-stu-id="be6e1-201">Uninstall a custom template by referencing a NuGet package by its `id` or by specifying a file system directory that contains a templating configuration.</span></span> <span data-ttu-id="be6e1-202">使用 `-u|--uninstall` 安裝選項與 [dotnet new](dotnet-new.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="be6e1-202">Use the `-u|--uninstall` install option with the [dotnet new](dotnet-new.md) command.</span></span>

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="be6e1-203">從儲存在 nuget.org 的 NuGet 套件解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-203">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="be6e1-204">從本機 nupkg 檔案解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-204">To uninstall a template from a local nupkg file</span></span>

<span data-ttu-id="be6e1-205">當您想要解除安裝範本時，請勿嘗試使用 *nupkg* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="be6e1-205">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="be6e1-206">*嘗試使用 `dotnet new -u <PATH_TO_NUPKG_FILE>` 解除安裝範本失敗。*</span><span class="sxs-lookup"><span data-stu-id="be6e1-206">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="be6e1-207">依套件的 `id` 參考套件：</span><span class="sxs-lookup"><span data-stu-id="be6e1-207">Reference the package by its `id`:</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a><span data-ttu-id="be6e1-208">從檔案系統目錄解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-208">To uninstall a template from a file system directory</span></span>

<span data-ttu-id="be6e1-209">`FILE_SYSTEM_DIRECTORY` 是包含專案和 *.template.config* 資料夾的專案資料夾：</span><span class="sxs-lookup"><span data-stu-id="be6e1-209">The `FILE_SYSTEM_DIRECTORY` is the project folder containing the project and the *.template.config* folder:</span></span>

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="be6e1-210">使用自訂範本建立專案</span><span class="sxs-lookup"><span data-stu-id="be6e1-210">Create a project using a custom template</span></span>

<span data-ttu-id="be6e1-211">在安裝範本之後，如同處理任何其他預先安裝的範本一樣，執行 `dotnet new <TEMPLATE>` 命令使用範本。</span><span class="sxs-lookup"><span data-stu-id="be6e1-211">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="be6e1-212">您也可以指定 `dotnet new` 命令的[選項](dotnet-new.md#options)，包括您在範本設定中設定的範本特定選項。</span><span class="sxs-lookup"><span data-stu-id="be6e1-212">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template specific options you configured in the template settings.</span></span> <span data-ttu-id="be6e1-213">直接將範本的簡短名稱提供給命令：</span><span class="sxs-lookup"><span data-stu-id="be6e1-213">Supply the template's short name directly to the command:</span></span>

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="be6e1-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be6e1-214">See also</span></span>

[<span data-ttu-id="be6e1-215">建立 dotnet new 的自訂範本 (教學課程)</span><span class="sxs-lookup"><span data-stu-id="be6e1-215">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/create-custom-template.md)  
<span data-ttu-id="be6e1-216">[dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="be6e1-216">[dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)</span></span>  
<span data-ttu-id="be6e1-217">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)</span><span class="sxs-lookup"><span data-stu-id="be6e1-217">[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)</span></span>  
[<span data-ttu-id="be6e1-218">如何建立您自己的 dotnet new 範本</span><span class="sxs-lookup"><span data-stu-id="be6e1-218">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[<span data-ttu-id="be6e1-219">JSON 結構描述保存區的 *template.json* 結構描述</span><span class="sxs-lookup"><span data-stu-id="be6e1-219">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)  
