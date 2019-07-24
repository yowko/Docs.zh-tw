---
title: 建立適用於 dotnet new 的專案範本
description: 了解如何針對 dotnet new 命令建立專案範本。
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 31a6189c0126d6dff000bb84978c1527dbe4e2ae
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870617"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="0bfe9-103">教學課程：建立專案範本</span><span class="sxs-lookup"><span data-stu-id="0bfe9-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="0bfe9-104">透過 .NET Core，您可以建立及部署能產生專案、檔案，甚至是資源的範本。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="0bfe9-105">此教學課程是指導您如何建立、安裝及解除安裝能搭配 `dotnet new` 命令使用之範的本系列文章第二部分。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="0bfe9-106">在這部分的系列文章中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="0bfe9-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="0bfe9-107">建立專案範本的資源</span><span class="sxs-lookup"><span data-stu-id="0bfe9-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="0bfe9-108">建立範本設定資料夾和檔案</span><span class="sxs-lookup"><span data-stu-id="0bfe9-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="0bfe9-109">從檔案路徑安裝範本</span><span class="sxs-lookup"><span data-stu-id="0bfe9-109">Install a template from a file path</span></span>
> * <span data-ttu-id="0bfe9-110">測試項目範本</span><span class="sxs-lookup"><span data-stu-id="0bfe9-110">Test an item template</span></span>
> * <span data-ttu-id="0bfe9-111">將項目範本解除安裝</span><span class="sxs-lookup"><span data-stu-id="0bfe9-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0bfe9-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="0bfe9-112">Prerequisites</span></span>

* <span data-ttu-id="0bfe9-113">完成此教學課程系列的[第 1 部分](cli-templates-create-item-template.md)。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="0bfe9-114">開啟終端機並瀏覽至 _working\templates\\_ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-114">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="0bfe9-115">建立專案範本</span><span class="sxs-lookup"><span data-stu-id="0bfe9-115">Create a project template</span></span>

<span data-ttu-id="0bfe9-116">專案範本能產生可立即執行的專案，讓使用者能以一組已可運作的程式碼來輕鬆開始。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="0bfe9-117">.NET Core 包含幾個專案範本，例如主控台應用程式或類別庫。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="0bfe9-118">在此範例中，您將會建立新的主控台專案，其能啟用 C# 8.0 並產生 `async main` 進入點。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="0bfe9-119">在您的終端機中，瀏覽至 _working\templates\\_ 資料夾，並建立名為 _consoleasync_ 的新子資料夾。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-119">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="0bfe9-120">進入該子資料夾，然後執行 `dotnet new console` 以產生標準主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="0bfe9-121">您將會編輯由此範本所產生的檔案來建立新的範本。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="0bfe9-122">修改 Program.cs</span><span class="sxs-lookup"><span data-stu-id="0bfe9-122">Modify Program.cs</span></span>

<span data-ttu-id="0bfe9-123">開啟 _program.cs_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="0bfe9-124">該主控台專案不會使用非同步進入點，因次讓我們來加入它。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="0bfe9-125">將程式碼變更為下列程式碼，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="0bfe9-125">Change your code to the following and save the file:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="0bfe9-126">修改 consoleasync.csproj</span><span class="sxs-lookup"><span data-stu-id="0bfe9-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="0bfe9-127">讓我們將專案使用的 C# 語言版本更新為 8.0 版。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="0bfe9-128">編輯 _consoleasync.csproj_ 檔案並將 `<LangVersion>` 設定加入 `<PropertyGroup>` 節點。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="0bfe9-129">建置專案</span><span class="sxs-lookup"><span data-stu-id="0bfe9-129">Build the project</span></span>

<span data-ttu-id="0bfe9-130">在您完成專案範本之前，您應該測試它以確保其能正確編譯及執行。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="0bfe9-131">在終端機中執行 `dotnet run` 命令，您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0bfe9-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="0bfe9-132">您可以將使用 `dotnet run` 所建立的 _obj_ 和 _bin_ 資料夾刪除。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="0bfe9-133">刪除這些檔案能確保您的範本只會包含與範本相關的檔案，而不會包含因建置動作而產生的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="0bfe9-134">您已經建立範本的內容，現在您需要在範本的根資料夾建立範本設定。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="0bfe9-135">建立範本設定</span><span class="sxs-lookup"><span data-stu-id="0bfe9-135">Create the template config</span></span>

<span data-ttu-id="0bfe9-136">.NET Core 會將範本辨識為存在於範本根目錄中的特殊資料夾及設定檔。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="0bfe9-137">在此教學課程中，您的範本資料夾是位於 _working\templates\consoleasync\\_ 。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-137">In this tutorial, your template folder is located at _working\templates\consoleasync\\_.</span></span>

<span data-ttu-id="0bfe9-138">當您建立範本時，範本資料夾中的所有檔案和資料夾都會包含為範本的一部分，除了特殊設定資料夾之外。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="0bfe9-139">此設定資料夾名為 _.template.config_。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="0bfe9-140">首先，建立名為 _.template.config_ 的新子資料夾，然後進入它。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="0bfe9-141">然後，建立名為 _template.json_ 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="0bfe9-142">您的資料夾結構看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="0bfe9-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="0bfe9-143">使用您慣用的文字編輯器開啟 _template.json_，然後貼上下列 JSON 程式碼並儲存它：</span><span class="sxs-lookup"><span data-stu-id="0bfe9-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

<span data-ttu-id="0bfe9-144">此設定檔會包含您範本的所有設定。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="0bfe9-145">您可以看見基本設定 (例如 `name` 和 `shortName`)，但還有設定為 `project` 的 `tags/type` 值。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="0bfe9-146">這會將您的範本指定為專案範本。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-146">This designates your template as a project template.</span></span> <span data-ttu-id="0bfe9-147">您可以建立的範本類型本身並無限制。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="0bfe9-148">`item` 和 `project` 值是 .NET Core 建議的常用名稱，它們可以讓使用者輕鬆篩選其想要尋找的範本類型。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="0bfe9-149">`classifications` 項目代表您執行 `dotnet new` 並取得範本清單時所會看見的 [標籤]  欄。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="0bfe9-150">使用者也可以根據分類標籤搜尋。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="0bfe9-151">不要將 JSON 檔案中的 `tags` 屬性與 `classifications` 標籤清單混淆在一起。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="0bfe9-152">它們是不同的東西，但不幸地具有類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="0bfe9-153">*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="0bfe9-154">如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="0bfe9-155">您已經具備有效的 _.template.config/template.json_ 檔案，現在您的範本已經準備好並可供安裝。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="0bfe9-156">在您安裝範本之前，請確定您已將不想要包含在範本中的所有額外檔案資料夾和檔案刪除，例如 _bin_ 或 _obj_ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="0bfe9-157">在您的終端機中，瀏覽至 _consoleasync_ 資料夾，並執行 `dotnet new -i .\` 以安裝位於目前資料夾中的範本。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="0bfe9-158">如果您是使用 Linux 或 MacOS 作業系統，請使用正斜線：`dotnet new -i ./`。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="0bfe9-159">此命令會輸出已安裝範本的清單，其中應該會包含您的範本。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-159">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\consoleasync> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a><span data-ttu-id="0bfe9-160">測試專案範本</span><span class="sxs-lookup"><span data-stu-id="0bfe9-160">Test the project template</span></span>

<span data-ttu-id="0bfe9-161">您已經安裝項目範本，現在請測試它。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="0bfe9-162">瀏覽至 _test_ 資料夾並使用 `dotnet new console` 建立新的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-162">Navigate to the _test_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="0bfe9-163">這會產生工作專案，其可讓您使用 `dotnet run` 命令輕鬆地進行測試。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="0bfe9-164">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="0bfe9-164">Congratulations!</span></span> <span data-ttu-id="0bfe9-165">您已透過 .NET Core 建立並部署專案範本。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="0bfe9-166">為了針對此教學課程系列的下一部份做準備，您必須將您所建立的範本解除安裝。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="0bfe9-167">同時，請務必刪除 _test_ 資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="0bfe9-168">這能讓您回到最原始的狀態，並準備好進行此教學課程的下一個主要區段。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="0bfe9-169">解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="0bfe9-169">Uninstall the template</span></span>

<span data-ttu-id="0bfe9-170">由於您是依檔案路徑來安裝範本，您必須使用**絕對**檔案路徑來將它解除安裝。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="0bfe9-171">您可以透過執行 `dotnet new -u` 命令來查看已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="0bfe9-172">您的範本應該會被列在最後。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-172">Your template should be listed last.</span></span> <span data-ttu-id="0bfe9-173">使用列出的路徑來搭配 `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` 命令將您的範本解除安裝。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="0bfe9-174">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0bfe9-174">Next steps</span></span>

<span data-ttu-id="0bfe9-175">在此教學課程中，您已建立專案範本。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="0bfe9-176">若要了解如何將項目和專案範本封裝為易於使用的單一檔案，請繼續進行此教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="0bfe9-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0bfe9-177">建立範本套件</span><span class="sxs-lookup"><span data-stu-id="0bfe9-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
