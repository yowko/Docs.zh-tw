---
title: 建立適用於 dotnet new 的專案範本
description: 了解如何針對 dotnet new 命令建立專案範本。
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503529"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="b8b5c-103">教學課程：建立專案範本</span><span class="sxs-lookup"><span data-stu-id="b8b5c-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="b8b5c-104">透過 .NET Core，您可以建立及部署能產生專案、檔案，甚至是資源的範本。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="b8b5c-105">此教學課程是指導您如何建立、安裝及解除安裝能搭配 `dotnet new` 命令使用之範的本系列文章第二部分。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="b8b5c-106">在這部分的系列文章中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="b8b5c-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="b8b5c-107">建立專案範本的資源</span><span class="sxs-lookup"><span data-stu-id="b8b5c-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="b8b5c-108">建立範本設定資料夾和檔案</span><span class="sxs-lookup"><span data-stu-id="b8b5c-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="b8b5c-109">從檔案路徑安裝範本</span><span class="sxs-lookup"><span data-stu-id="b8b5c-109">Install a template from a file path</span></span>
> * <span data-ttu-id="b8b5c-110">測試項目範本</span><span class="sxs-lookup"><span data-stu-id="b8b5c-110">Test an item template</span></span>
> * <span data-ttu-id="b8b5c-111">將項目範本解除安裝</span><span class="sxs-lookup"><span data-stu-id="b8b5c-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b8b5c-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b8b5c-112">Prerequisites</span></span>

* <span data-ttu-id="b8b5c-113">完成此教學課程系列的[第 1 部分](cli-templates-create-item-template.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="b8b5c-114">開啟終端機，並流覽至_working\templates_資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="b8b5c-115">建立專案範本</span><span class="sxs-lookup"><span data-stu-id="b8b5c-115">Create a project template</span></span>

<span data-ttu-id="b8b5c-116">專案範本能產生可立即執行的專案，讓使用者能以一組已可運作的程式碼來輕鬆開始。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="b8b5c-117">.NET Core 包含幾個專案範本，例如主控台應用程式或類別庫。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="b8b5c-118">在此範例中，您將會建立新的主控台專案，其能啟用 C# 8.0 並產生 `async main` 進入點。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="b8b5c-119">在您的終端機中，流覽至 [ _working\templates_ ] 資料夾，然後建立名為_consoleasync_的新子資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="b8b5c-120">進入該子資料夾，然後執行 `dotnet new console` 以產生標準主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="b8b5c-121">您將會編輯由此範本所產生的檔案來建立新的範本。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="b8b5c-122">修改 Program.cs</span><span class="sxs-lookup"><span data-stu-id="b8b5c-122">Modify Program.cs</span></span>

<span data-ttu-id="b8b5c-123">開啟 _program.cs_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="b8b5c-124">該主控台專案不會使用非同步進入點，因次讓我們來加入它。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="b8b5c-125">將您的程式碼變更為下列，並儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-125">Change your code to the following and save the file.</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="b8b5c-126">修改 consoleasync.csproj</span><span class="sxs-lookup"><span data-stu-id="b8b5c-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="b8b5c-127">讓我們將專案使用的 C# 語言版本更新為 8.0 版。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="b8b5c-128">編輯 _consoleasync.csproj_ 檔案並將 `<LangVersion>` 設定加入 `<PropertyGroup>` 節點。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="b8b5c-129">建置專案</span><span class="sxs-lookup"><span data-stu-id="b8b5c-129">Build the project</span></span>

<span data-ttu-id="b8b5c-130">在您完成專案範本之前，您應該測試它以確保其能正確編譯及執行。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span>

<span data-ttu-id="b8b5c-131">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-131">In your terminal, run the following command.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="b8b5c-132">您會取得下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-132">You get the following output.</span></span>

```console
Hello World with C# 8.0!
```

<span data-ttu-id="b8b5c-133">您可以將使用 _所建立的_obj_和_bin`dotnet run` 資料夾刪除。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-133">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="b8b5c-134">刪除這些檔案能確保您的範本只會包含與範本相關的檔案，而不會包含因建置動作而產生的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-134">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="b8b5c-135">您已經建立範本的內容，現在您需要在範本的根資料夾建立範本設定。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-135">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="b8b5c-136">建立範本設定</span><span class="sxs-lookup"><span data-stu-id="b8b5c-136">Create the template config</span></span>

<span data-ttu-id="b8b5c-137">.NET Core 會將範本辨識為存在於範本根目錄中的特殊資料夾及設定檔。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-137">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="b8b5c-138">在本教學課程中，您的範本資料夾位於_working\templates\consoleasync_。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-138">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="b8b5c-139">當您建立範本時，範本資料夾中的所有檔案和資料夾都會包含為範本的一部分，除了特殊設定資料夾之外。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-139">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="b8b5c-140">此設定資料夾名為 _.template.config_。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-140">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="b8b5c-141">首先，建立名為 _.template.config_ 的新子資料夾，然後進入它。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-141">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="b8b5c-142">然後，建立名為 _template.json_ 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-142">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="b8b5c-143">您的資料夾結構看起來應該像這樣。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-143">Your folder structure should look like this.</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="b8b5c-144">使用您慣用的文字編輯器開啟_範本_，並貼上下列 json 程式碼並加以儲存。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-144">Open the _template.json_ with your favorite text editor and paste in the following json code and save it.</span></span>

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

<span data-ttu-id="b8b5c-145">此設定檔會包含您範本的所有設定。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-145">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="b8b5c-146">您可以看見基本設定 (例如 `name` 和 `shortName`)，但還有設定為 `tags/type` 的 `project` 值。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-146">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="b8b5c-147">這會將您的範本指定為專案範本。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-147">This designates your template as a project template.</span></span> <span data-ttu-id="b8b5c-148">您可以建立的範本類型本身並無限制。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-148">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="b8b5c-149">`item` 和 `project` 值是 .NET Core 建議的常用名稱，它們可以讓使用者輕鬆篩選其想要尋找的範本類型。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-149">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="b8b5c-150">`classifications` 項目代表您執行  **並取得範本清單時所會看見的 [標籤]** `dotnet new` 欄。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-150">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="b8b5c-151">使用者也可以根據分類標籤搜尋。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-151">Users can also search based on classification tags.</span></span> <span data-ttu-id="b8b5c-152">不要將 JSON 檔案中的 `tags` 屬性與 `classifications` 標籤清單混淆在一起。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-152">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="b8b5c-153">它們是不同的東西，但不幸地具有類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-153">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="b8b5c-154">*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-154">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="b8b5c-155">如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-155">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="b8b5c-156">您已經具備有效的 _.template.config/template.json_ 檔案，現在您的範本已經準備好並可供安裝。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-156">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="b8b5c-157">在您安裝範本之前，請確定您已將不想要包含在範本中的所有額外檔案資料夾和檔案刪除，例如 _bin_ 或 _obj_ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-157">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="b8b5c-158">在您的終端機中，瀏覽至 _consoleasync_ 資料夾，並執行 `dotnet new -i .\` 以安裝位於目前資料夾中的範本。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-158">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="b8b5c-159">如果您使用的是 Linux 或 macOS 作業系統，請使用正斜線： `dotnet new -i ./`。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-159">If you're using a Linux or macOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="b8b5c-160">此命令會輸出已安裝範本的清單，其中應該會包含您的範本。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-160">This command outputs the list of templates installed, which should include yours.</span></span>

```dotnetcli
dotnet new -i .\
```

<span data-ttu-id="b8b5c-161">您會取得如下所示的輸出。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-161">You get output similar to the following.</span></span>

```console
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

### <a name="test-the-project-template"></a><span data-ttu-id="b8b5c-162">測試專案範本</span><span class="sxs-lookup"><span data-stu-id="b8b5c-162">Test the project template</span></span>

<span data-ttu-id="b8b5c-163">您已經安裝項目範本，現在請測試它。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-163">Now that you have an item template installed, test it.</span></span>

1. <span data-ttu-id="b8b5c-164">流覽至_測試_資料夾</span><span class="sxs-lookup"><span data-stu-id="b8b5c-164">Navigate to the _test_ folder</span></span>

1. <span data-ttu-id="b8b5c-165">使用下列命令建立新的主控台應用程式，以產生可使用 `dotnet run` 命令輕鬆測試的工作專案。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-165">Create a new console application with the following command which generates a working project you can easily test with the `dotnet run` command.</span></span>

    ```dotnetcli
    dotnet new consoleasync
    ```

    <span data-ttu-id="b8b5c-166">您會取得下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-166">You get the following output.</span></span>

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. <span data-ttu-id="b8b5c-167">使用下列命令執行專案。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-167">Run the project using the following command.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="b8b5c-168">您會取得下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-168">You get the following output.</span></span>

    ```console
    Hello World with C# 8.0!
    ```

<span data-ttu-id="b8b5c-169">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b8b5c-169">Congratulations!</span></span> <span data-ttu-id="b8b5c-170">您已透過 .NET Core 建立並部署專案範本。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-170">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="b8b5c-171">為了針對此教學課程系列的下一部份做準備，您必須將您所建立的範本解除安裝。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="b8b5c-172">同時，請務必刪除 _test_ 資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="b8b5c-173">這能讓您回到最原始的狀態，並準備好進行此教學課程的下一個主要區段。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="b8b5c-174">解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="b8b5c-174">Uninstall the template</span></span>

<span data-ttu-id="b8b5c-175">由於您是依檔案路徑來安裝範本，您必須使用**絕對**檔案路徑來將它解除安裝。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-175">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="b8b5c-176">您可以透過執行 `dotnet new -u` 命令來查看已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="b8b5c-177">您的範本應該會被列在最後。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-177">Your template should be listed last.</span></span> <span data-ttu-id="b8b5c-178">使用列出的路徑來搭配 `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` 命令將您的範本解除安裝。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="b8b5c-179">您會取得如下所示的輸出。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-179">You get output similar to the following.</span></span>

```console
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

<span data-ttu-id="b8b5c-180">若要卸載範本，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-180">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="b8b5c-181">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b8b5c-181">Next steps</span></span>

<span data-ttu-id="b8b5c-182">在此教學課程中，您已建立專案範本。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-182">In this tutorial, you created a project template.</span></span> <span data-ttu-id="b8b5c-183">若要了解如何將項目和專案範本封裝為易於使用的單一檔案，請繼續進行此教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="b8b5c-183">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8b5c-184">建立範本套件</span><span class="sxs-lookup"><span data-stu-id="b8b5c-184">Create a template pack</span></span>](cli-templates-create-template-pack.md)
