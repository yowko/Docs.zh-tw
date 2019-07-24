---
title: 針對 dotnet new 建立項目範本 - .NET Core CLI
description: 了解如何針對 dotnet new 命令建立項目範本。 項目範本可能會包含數個檔案。
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: c50aaf413f08c2e4cbe3f8ce8c057e5841067c92
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870607"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="14eb1-104">教學課程：建立項目範本</span><span class="sxs-lookup"><span data-stu-id="14eb1-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="14eb1-105">透過 .NET Core，您可以建立及部署能產生專案、檔案，甚至是資源的範本。</span><span class="sxs-lookup"><span data-stu-id="14eb1-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="14eb1-106">此教學課程是指導您如何建立、安裝及解除安裝能搭配 `dotnet new` 命令使用之範的本系列文章第一部分。</span><span class="sxs-lookup"><span data-stu-id="14eb1-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="14eb1-107">在這部分的系列文章中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="14eb1-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="14eb1-108">針對項目範本建立類別</span><span class="sxs-lookup"><span data-stu-id="14eb1-108">Create a class for an item template</span></span>
> * <span data-ttu-id="14eb1-109">建立範本設定資料夾和檔案</span><span class="sxs-lookup"><span data-stu-id="14eb1-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="14eb1-110">從檔案路徑安裝範本</span><span class="sxs-lookup"><span data-stu-id="14eb1-110">Install a template from a file path</span></span>
> * <span data-ttu-id="14eb1-111">測試項目範本</span><span class="sxs-lookup"><span data-stu-id="14eb1-111">Test an item template</span></span>
> * <span data-ttu-id="14eb1-112">將項目範本解除安裝</span><span class="sxs-lookup"><span data-stu-id="14eb1-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14eb1-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="14eb1-113">Prerequisites</span></span>

* <span data-ttu-id="14eb1-114">[.NET Core 2.2 SDK](https://www.microsoft.com/net/core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="14eb1-114">[.NET Core 2.2 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
* <span data-ttu-id="14eb1-115">請參閱參考文章 [dotnet new 的自訂範本](../tools/custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="14eb1-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="14eb1-116">該參考文章會說明範本的基本概念及構成方式。</span><span class="sxs-lookup"><span data-stu-id="14eb1-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="14eb1-117">那些資訊有一部分會在此重述。</span><span class="sxs-lookup"><span data-stu-id="14eb1-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="14eb1-118">開啟終端機並瀏覽至 _working\templates\\_ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="14eb1-118">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="14eb1-119">建立必要的資料夾</span><span class="sxs-lookup"><span data-stu-id="14eb1-119">Create the required folders</span></span>

<span data-ttu-id="14eb1-120">本系列文章會使用「工作資料夾」來存放您的範本來源，並使用「測試資料夾」來測試您的範本。</span><span class="sxs-lookup"><span data-stu-id="14eb1-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="14eb1-121">工作資料夾和測試資料夾應該放在相同的父資料夾中。</span><span class="sxs-lookup"><span data-stu-id="14eb1-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="14eb1-122">首先，請建立父資料夾；其名稱並不重要。</span><span class="sxs-lookup"><span data-stu-id="14eb1-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="14eb1-123">然後，建立名為 _working_ 的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="14eb1-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="14eb1-124">在 _working_ 資料夾中，建立名為 _templates_ 的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="14eb1-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="14eb1-125">接下來，在父資料夾底下建立名為 _test_ 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="14eb1-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="14eb1-126">資料夾結構看起來應如下所示：</span><span class="sxs-lookup"><span data-stu-id="14eb1-126">The folder structure should look like the following:</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="14eb1-127">建立項目範本</span><span class="sxs-lookup"><span data-stu-id="14eb1-127">Create an item template</span></span>

<span data-ttu-id="14eb1-128">項目範本是特定類型的範本，其會包含一或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="14eb1-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="14eb1-129">這些範本類型很適合在您想要產生設定、程式碼或方案檔之類的項目時使用。</span><span class="sxs-lookup"><span data-stu-id="14eb1-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="14eb1-130">在此範例中，您將會建立能將擴充方法加入字串類型的類別。</span><span class="sxs-lookup"><span data-stu-id="14eb1-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="14eb1-131">在您的終端機中，瀏覽至 _working\templates\\_ 資料夾，並建立名為 _extensions_ 的新子資料夾。</span><span class="sxs-lookup"><span data-stu-id="14eb1-131">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="14eb1-132">進入該資料夾。</span><span class="sxs-lookup"><span data-stu-id="14eb1-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="14eb1-133">建立名為 _CommonExtensions.cs_ 的新檔案，並使用您慣用的文字編輯器開啟它。</span><span class="sxs-lookup"><span data-stu-id="14eb1-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="14eb1-134">此類別將會提供名為 `Reverse` 的擴充方法，其能反轉字串的內容。</span><span class="sxs-lookup"><span data-stu-id="14eb1-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="14eb1-135">貼上下列程式碼並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="14eb1-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="14eb1-136">您已經建立範本的內容，現在您需要在範本的根資料夾建立範本設定。</span><span class="sxs-lookup"><span data-stu-id="14eb1-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="14eb1-137">建立範本設定</span><span class="sxs-lookup"><span data-stu-id="14eb1-137">Create the template config</span></span>

<span data-ttu-id="14eb1-138">.NET Core 會將範本辨識為存在於範本根目錄中的特殊資料夾及設定檔。</span><span class="sxs-lookup"><span data-stu-id="14eb1-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="14eb1-139">在此教學課程中，您的範本資料夾是位於 _working\templates\extensions\\_ 。</span><span class="sxs-lookup"><span data-stu-id="14eb1-139">In this tutorial, your template folder is located at _working\templates\extensions\\_.</span></span>

<span data-ttu-id="14eb1-140">當您建立範本時，範本資料夾中的所有檔案和資料夾都會包含為範本的一部分，除了特殊設定資料夾之外。</span><span class="sxs-lookup"><span data-stu-id="14eb1-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="14eb1-141">此設定資料夾名為 _.template.config_。</span><span class="sxs-lookup"><span data-stu-id="14eb1-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="14eb1-142">首先，建立名為 _.template.config_ 的新子資料夾，然後進入它。</span><span class="sxs-lookup"><span data-stu-id="14eb1-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="14eb1-143">然後，建立名為 _template.json_ 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="14eb1-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="14eb1-144">您的資料夾結構看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="14eb1-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="14eb1-145">使用您慣用的文字編輯器開啟 _template.json_，然後貼上下列 JSON 程式碼並儲存它：</span><span class="sxs-lookup"><span data-stu-id="14eb1-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="14eb1-146">此設定檔會包含您範本的所有設定。</span><span class="sxs-lookup"><span data-stu-id="14eb1-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="14eb1-147">您可以看見基本設定 (例如 `name` 和 `shortName`)，但還有設定為 `item` 的 `tags/type` 值。</span><span class="sxs-lookup"><span data-stu-id="14eb1-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="14eb1-148">這會將您的範本分類為項目範本。</span><span class="sxs-lookup"><span data-stu-id="14eb1-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="14eb1-149">您可以建立的範本類型本身並無限制。</span><span class="sxs-lookup"><span data-stu-id="14eb1-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="14eb1-150">`item` 和 `project` 值是 .NET Core 建議的常用名稱，它們可以讓使用者輕鬆篩選其想要尋找的範本類型。</span><span class="sxs-lookup"><span data-stu-id="14eb1-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="14eb1-151">`classifications` 項目代表您執行 `dotnet new` 並取得範本清單時所會看見的 [標籤]  欄。</span><span class="sxs-lookup"><span data-stu-id="14eb1-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="14eb1-152">使用者也可以根據分類標籤搜尋。</span><span class="sxs-lookup"><span data-stu-id="14eb1-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="14eb1-153">不要將 \*.json 檔案中的 `tags` 屬性與 `classifications` 標籤清單混淆在一起。</span><span class="sxs-lookup"><span data-stu-id="14eb1-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="14eb1-154">它們是不同的東西，但不幸地具有類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="14eb1-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="14eb1-155">*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="14eb1-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="14eb1-156">如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="14eb1-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="14eb1-157">您已經具備有效的 _.template.config/template.json_ 檔案，現在您的範本已經準備好並可供安裝。</span><span class="sxs-lookup"><span data-stu-id="14eb1-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="14eb1-158">在您的終端機中，瀏覽至 _extensions_ 資料夾，並執行下列命令以安裝位於目前資料夾中的範本：</span><span class="sxs-lookup"><span data-stu-id="14eb1-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="14eb1-159">**在 Windows 上**：`dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="14eb1-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="14eb1-160">**在 Linux 或 MacOS 上**：`dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="14eb1-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="14eb1-161">此命令會輸出已安裝範本的清單，其中應該會包含您的範本。</span><span class="sxs-lookup"><span data-stu-id="14eb1-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a><span data-ttu-id="14eb1-162">測試項目範本</span><span class="sxs-lookup"><span data-stu-id="14eb1-162">Test the item template</span></span>

<span data-ttu-id="14eb1-163">您已經安裝項目範本，現在請測試它。</span><span class="sxs-lookup"><span data-stu-id="14eb1-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="14eb1-164">瀏覽至 _test/_ 資料夾並使用 `dotnet new console` 建立新的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="14eb1-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="14eb1-165">這會產生工作專案，其可讓您使用 `dotnet run` 命令輕鬆地進行測試。</span><span class="sxs-lookup"><span data-stu-id="14eb1-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

<span data-ttu-id="14eb1-166">接下來，執行 `dotnet new stringext` 以從範本產生 _CommonExtensions.cs_。</span><span class="sxs-lookup"><span data-stu-id="14eb1-166">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="14eb1-167">變更 _Program.cs_ 中的程式碼，以搭配由範本所提供的擴充方法來反轉 `"Hello World"` 字串。</span><span class="sxs-lookup"><span data-stu-id="14eb1-167">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="14eb1-168">再次執行該程式，您將會看到結果已被反轉。</span><span class="sxs-lookup"><span data-stu-id="14eb1-168">Run the program again and you'll see that the result is reversed.</span></span>

```console
C:\test> dotnet run
!dlroW olleH
```

<span data-ttu-id="14eb1-169">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="14eb1-169">Congratulations!</span></span> <span data-ttu-id="14eb1-170">您已透過 .NET Core 建立並部署項目範本。</span><span class="sxs-lookup"><span data-stu-id="14eb1-170">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="14eb1-171">為了針對此教學課程系列的下一部份做準備，您必須將您所建立的範本解除安裝。</span><span class="sxs-lookup"><span data-stu-id="14eb1-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="14eb1-172">同時，請務必刪除 _test_ 資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="14eb1-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="14eb1-173">這能讓您回到最原始的狀態，並準備好進行此教學課程的下一個主要區段。</span><span class="sxs-lookup"><span data-stu-id="14eb1-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="14eb1-174">解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="14eb1-174">Uninstall the template</span></span>

<span data-ttu-id="14eb1-175">由於您是依檔案路徑來安裝範本，您必須使用**絕對**檔案路徑來將它解除安裝。</span><span class="sxs-lookup"><span data-stu-id="14eb1-175">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="14eb1-176">您可以透過執行 `dotnet new -u` 命令來查看已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="14eb1-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="14eb1-177">您的範本應該會被列在最後。</span><span class="sxs-lookup"><span data-stu-id="14eb1-177">Your template should be listed last.</span></span> <span data-ttu-id="14eb1-178">使用列出的路徑來搭配 `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` 命令將您的範本解除安裝。</span><span class="sxs-lookup"><span data-stu-id="14eb1-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="14eb1-179">後續步驟</span><span class="sxs-lookup"><span data-stu-id="14eb1-179">Next steps</span></span>

<span data-ttu-id="14eb1-180">在此教學課程中，您已建立項目範本。</span><span class="sxs-lookup"><span data-stu-id="14eb1-180">In this tutorial, you created an item template.</span></span> <span data-ttu-id="14eb1-181">若要了解如何建立專案範本，請繼續進行此教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="14eb1-181">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="14eb1-182">建立專案範本</span><span class="sxs-lookup"><span data-stu-id="14eb1-182">Create a project template</span></span>](cli-templates-create-project-template.md)
