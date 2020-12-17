---
title: 建立 dotnet 新 .NET CLI 的專案範本
titleSuffix: ''
description: 了解如何針對 dotnet new 命令建立項目範本。 項目範本可能會包含數個檔案。
author: adegeo
ms.date: 12/11/2020
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: d213646a933c77bd0d9a3f1aa9b6b4948b66439b
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633659"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="58895-104">教學課程：建立專案範本</span><span class="sxs-lookup"><span data-stu-id="58895-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="58895-105">您可以使用 .NET 來建立和部署範本，以產生專案、檔案，甚至是資源。</span><span class="sxs-lookup"><span data-stu-id="58895-105">With .NET, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="58895-106">本教學課程是指導您如何建立、安裝及卸載範本以搭配命令使用之系列文章的第一篇 `dotnet new` 。</span><span class="sxs-lookup"><span data-stu-id="58895-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="58895-107">在這部分的系列文章中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="58895-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="58895-108">針對項目範本建立類別</span><span class="sxs-lookup"><span data-stu-id="58895-108">Create a class for an item template</span></span>
> * <span data-ttu-id="58895-109">建立範本設定資料夾和檔案</span><span class="sxs-lookup"><span data-stu-id="58895-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="58895-110">從檔案路徑安裝範本</span><span class="sxs-lookup"><span data-stu-id="58895-110">Install a template from a file path</span></span>
> * <span data-ttu-id="58895-111">測試項目範本</span><span class="sxs-lookup"><span data-stu-id="58895-111">Test an item template</span></span>
> * <span data-ttu-id="58895-112">將項目範本解除安裝</span><span class="sxs-lookup"><span data-stu-id="58895-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58895-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="58895-113">Prerequisites</span></span>

* <span data-ttu-id="58895-114">[.Net 5.0 SDK](https://dotnet.microsoft.com/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="58895-114">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or a later version.</span></span>
* <span data-ttu-id="58895-115">請參閱參考文章 [dotnet new 的自訂範本](../tools/custom-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="58895-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="58895-116">該參考文章會說明範本的基本概念及構成方式。</span><span class="sxs-lookup"><span data-stu-id="58895-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="58895-117">那些資訊有一部分會在此重述。</span><span class="sxs-lookup"><span data-stu-id="58895-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="58895-118">開啟終端機並瀏覽至 _working\templates_ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="58895-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="58895-119">建立必要的資料夾</span><span class="sxs-lookup"><span data-stu-id="58895-119">Create the required folders</span></span>

<span data-ttu-id="58895-120">本系列文章會使用「工作資料夾」來存放您的範本來源，並使用「測試資料夾」來測試您的範本。</span><span class="sxs-lookup"><span data-stu-id="58895-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="58895-121">工作資料夾和測試資料夾應該放在相同的父資料夾中。</span><span class="sxs-lookup"><span data-stu-id="58895-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="58895-122">首先，請建立父資料夾；其名稱並不重要。</span><span class="sxs-lookup"><span data-stu-id="58895-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="58895-123">然後，建立名為 _working_ 的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="58895-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="58895-124">在 _working_ 資料夾中，建立名為 _templates_ 的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="58895-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="58895-125">接下來，在父資料夾底下建立名為 _test_ 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="58895-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="58895-126">資料夾結構看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="58895-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="58895-127">建立項目範本</span><span class="sxs-lookup"><span data-stu-id="58895-127">Create an item template</span></span>

<span data-ttu-id="58895-128">項目範本是特定類型的範本，其會包含一或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="58895-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="58895-129">這些範本類型很適合在您想要產生設定、程式碼或方案檔之類的項目時使用。</span><span class="sxs-lookup"><span data-stu-id="58895-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="58895-130">在此範例中，您將會建立能將擴充方法加入字串類型的類別。</span><span class="sxs-lookup"><span data-stu-id="58895-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="58895-131">在您的終端機中，瀏覽至 _working\templates_ 資料夾，並建立名為 _extensions_ 的新子資料夾。</span><span class="sxs-lookup"><span data-stu-id="58895-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="58895-132">進入該資料夾。</span><span class="sxs-lookup"><span data-stu-id="58895-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="58895-133">建立名為 _CommonExtensions.cs_ 的新檔案，並使用您慣用的文字編輯器開啟它。</span><span class="sxs-lookup"><span data-stu-id="58895-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="58895-134">此類別將會提供名為 `Reverse` 的擴充方法，其能反轉字串的內容。</span><span class="sxs-lookup"><span data-stu-id="58895-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="58895-135">貼上下列程式碼並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="58895-135">Paste in the following code and save the file:</span></span>

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

<span data-ttu-id="58895-136">您已經建立範本的內容，現在您需要在範本的根資料夾建立範本設定。</span><span class="sxs-lookup"><span data-stu-id="58895-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="58895-137">建立範本設定</span><span class="sxs-lookup"><span data-stu-id="58895-137">Create the template config</span></span>

<span data-ttu-id="58895-138">範本的根目錄中有特殊的資料夾和設定檔案可辨識範本。</span><span class="sxs-lookup"><span data-stu-id="58895-138">Templates are recognized by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="58895-139">在此教學課程中，您的範本資料夾是位於 _working\templates\extensions_。</span><span class="sxs-lookup"><span data-stu-id="58895-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="58895-140">當您建立範本時，範本資料夾中的所有檔案和資料夾都會包含為範本的一部分，除了特殊設定資料夾之外。</span><span class="sxs-lookup"><span data-stu-id="58895-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="58895-141">此設定資料夾名為 _.template.config_。</span><span class="sxs-lookup"><span data-stu-id="58895-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="58895-142">首先，建立名為 _.template.config_ 的新子資料夾，然後進入它。</span><span class="sxs-lookup"><span data-stu-id="58895-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="58895-143">然後，建立名為 _template.json_ 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="58895-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="58895-144">您的資料夾結構看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="58895-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="58895-145">使用您慣用的文字編輯器開啟template.js，並貼 _上_ 下列 JSON 程式碼並加以儲存。</span><span class="sxs-lookup"><span data-stu-id="58895-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

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

<span data-ttu-id="58895-146">此設定檔會包含您範本的所有設定。</span><span class="sxs-lookup"><span data-stu-id="58895-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="58895-147">您可以看見基本設定 (例如 `name` 和 `shortName`)，但還有設定為 `item` 的 `tags/type` 值。</span><span class="sxs-lookup"><span data-stu-id="58895-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="58895-148">這會將您的範本分類為項目範本。</span><span class="sxs-lookup"><span data-stu-id="58895-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="58895-149">您可以建立的範本類型本身並無限制。</span><span class="sxs-lookup"><span data-stu-id="58895-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="58895-150">`item`和 `project` 值是 .net 建議的通用名稱，讓使用者可以輕鬆地篩選其所搜尋的範本類型。</span><span class="sxs-lookup"><span data-stu-id="58895-150">The `item` and `project` values are common names that .NET recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="58895-151">`classifications` 項目代表您執行 `dotnet new` 並取得範本清單時所會看見的 [標籤] 欄。</span><span class="sxs-lookup"><span data-stu-id="58895-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="58895-152">使用者也可以根據分類標籤搜尋。</span><span class="sxs-lookup"><span data-stu-id="58895-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="58895-153">不要將 \*.json 檔案中的 `tags` 屬性與 `classifications` 標籤清單混淆在一起。</span><span class="sxs-lookup"><span data-stu-id="58895-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="58895-154">它們是不同的東西，但不幸地具有類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="58895-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="58895-155">*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。</span><span class="sxs-lookup"><span data-stu-id="58895-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="58895-156">如需 *template.json* 檔案的詳細資訊，請參閱 [dotnet 範本化 Wiki](https://github.com/dotnet/templating/wiki) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="58895-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="58895-157">您已經具備有效的 _.template.config/template.json_ 檔案，現在您的範本已經準備好並可供安裝。</span><span class="sxs-lookup"><span data-stu-id="58895-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="58895-158">在您的終端機中，瀏覽至 _extensions_ 資料夾，並執行下列命令以安裝位於目前資料夾中的範本：</span><span class="sxs-lookup"><span data-stu-id="58895-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="58895-159">**在 Windows 上**： `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="58895-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="58895-160">**在 Linux 或 MacOS 上**： `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="58895-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="58895-161">此命令會輸出已安裝範本的清單，其中應該會包含您的範本。</span><span class="sxs-lookup"><span data-stu-id="58895-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Example templates: string extensions              stringext                [C#]              Common/Code
Console Application                               console                  [C#], F#, VB      Common/Console
Class library                                     classlib                 [C#], F#, VB      Common/Library
WPF Application                                   wpf                      [C#], VB          Common/WPF
```

## <a name="test-the-item-template"></a><span data-ttu-id="58895-162">測試項目範本</span><span class="sxs-lookup"><span data-stu-id="58895-162">Test the item template</span></span>

<span data-ttu-id="58895-163">您已經安裝項目範本，現在請測試它。</span><span class="sxs-lookup"><span data-stu-id="58895-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="58895-164">瀏覽至 _test/_ 資料夾並使用 `dotnet new console` 建立新的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="58895-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="58895-165">這會產生工作專案，其可讓您使用 `dotnet run` 命令輕鬆地進行測試。</span><span class="sxs-lookup"><span data-stu-id="58895-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="58895-166">您會取得如下所示的輸出。</span><span class="sxs-lookup"><span data-stu-id="58895-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="58895-167">使用來執行專案。</span><span class="sxs-lookup"><span data-stu-id="58895-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="58895-168">您會取得下列輸出。</span><span class="sxs-lookup"><span data-stu-id="58895-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="58895-169">接下來，執行 `dotnet new stringext` 以從範本產生 _CommonExtensions.cs_。</span><span class="sxs-lookup"><span data-stu-id="58895-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="58895-170">您會取得下列輸出。</span><span class="sxs-lookup"><span data-stu-id="58895-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="58895-171">變更 _Program.cs_ 中的程式碼，以搭配由範本所提供的擴充方法來反轉 `"Hello World"` 字串。</span><span class="sxs-lookup"><span data-stu-id="58895-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="58895-172">再次執行該程式，您將會看到結果已被反轉。</span><span class="sxs-lookup"><span data-stu-id="58895-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="58895-173">您會取得下列輸出。</span><span class="sxs-lookup"><span data-stu-id="58895-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="58895-174">恭喜！</span><span class="sxs-lookup"><span data-stu-id="58895-174">Congratulations!</span></span> <span data-ttu-id="58895-175">您已使用 .NET 建立並部署專案範本。</span><span class="sxs-lookup"><span data-stu-id="58895-175">You created and deployed an item template with .NET.</span></span> <span data-ttu-id="58895-176">為了針對此教學課程系列的下一部份做準備，您必須將您所建立的範本解除安裝。</span><span class="sxs-lookup"><span data-stu-id="58895-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="58895-177">同時，請務必刪除 _test_ 資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="58895-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="58895-178">這能讓您回到最原始的狀態，並準備好進行此教學課程的下一個主要區段。</span><span class="sxs-lookup"><span data-stu-id="58895-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="58895-179">解除安裝範本</span><span class="sxs-lookup"><span data-stu-id="58895-179">Uninstall the template</span></span>

<span data-ttu-id="58895-180">由於您是依檔案路徑來安裝範本，您必須使用 **絕對** 檔案路徑來將它解除安裝。</span><span class="sxs-lookup"><span data-stu-id="58895-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="58895-181">您可以透過執行 `dotnet new -u` 命令來查看已安裝範本的清單。</span><span class="sxs-lookup"><span data-stu-id="58895-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="58895-182">您的範本應該會被列在最後。</span><span class="sxs-lookup"><span data-stu-id="58895-182">Your template should be listed last.</span></span> <span data-ttu-id="58895-183">使用 `Uninstall Command` 列出的來卸載您的範本。</span><span class="sxs-lookup"><span data-stu-id="58895-183">Use the `Uninstall Command` listed to uninstall your template.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="58895-184">您會取得如下所示的輸出。</span><span class="sxs-lookup"><span data-stu-id="58895-184">You get output similar to the following.</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ProjectTemplates.2.2
    Details:
      NuGetPackageId: Microsoft.DotNet.Common.ProjectTemplates.2.2
      Version: 1.0.2-beta4
      Author: Microsoft
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
    Uninstall Command:
      dotnet new -u Microsoft.DotNet.Common.ProjectTemplates.2.2

... cut to save space ...

C:\Test\templatetutorial\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
    Uninstall Command:
      dotnet new -u C:\working\templates\extensions
```

<span data-ttu-id="58895-185">若要卸載您所建立的範本，請執行 `Uninstall Command` 輸出中所顯示的範本。</span><span class="sxs-lookup"><span data-stu-id="58895-185">To uninstall the template that you created, run the `Uninstall Command` that is shown in the output.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="58895-186">下一步</span><span class="sxs-lookup"><span data-stu-id="58895-186">Next steps</span></span>

<span data-ttu-id="58895-187">在此教學課程中，您已建立項目範本。</span><span class="sxs-lookup"><span data-stu-id="58895-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="58895-188">若要了解如何建立專案範本，請繼續進行此教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="58895-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="58895-189">建立專案範本</span><span class="sxs-lookup"><span data-stu-id="58895-189">Create a project template</span></span>](cli-templates-create-project-template.md)
