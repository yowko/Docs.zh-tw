---
title: 建立 .NET 應用程式的資源檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7ff34285220fd1e3c17503a8387104e91ec08b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313654"
---
# <a name="create-resource-files-for-net-apps"></a><span data-ttu-id="905aa-102">建立 .NET 應用程式的資源檔</span><span class="sxs-lookup"><span data-stu-id="905aa-102">Create resource files for .NET apps</span></span>

<span data-ttu-id="905aa-103">您可以在資源檔中包括資源 (例如字串、影像或物件資料)，以讓應用程式輕鬆地使用它們。</span><span class="sxs-lookup"><span data-stu-id="905aa-103">You can include resources, such as strings, images, or object data, in resources files to make them easily available to your application.</span></span> <span data-ttu-id="905aa-104">.NET Framework 提供五種方式來建立資源檔：</span><span class="sxs-lookup"><span data-stu-id="905aa-104">The .NET Framework offers five ways to create resources files:</span></span>

- <span data-ttu-id="905aa-105">建立包含字串資源的文字檔。</span><span class="sxs-lookup"><span data-stu-id="905aa-105">Create a text file that contains string resources.</span></span> <span data-ttu-id="905aa-106">您必須使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將文字檔轉換成二進位資源 (.resources) 檔案。</span><span class="sxs-lookup"><span data-stu-id="905aa-106">You can use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to convert the text file into a binary resource (.resources) file.</span></span> <span data-ttu-id="905aa-107">您接著可以使用語言編譯器將二進位資源檔內嵌在應用程式可執行檔或應用程式程式庫中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-107">You can then embed the binary resource file  in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="905aa-108">如需詳細資訊，請參閱[文字檔中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles)一節。</span><span class="sxs-lookup"><span data-stu-id="905aa-108">For more information, see the [Resources in Text Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) section.</span></span>

- <span data-ttu-id="905aa-109">建立包含字串、影像或物件資料的 XML 資源 (.resx) 檔案。</span><span class="sxs-lookup"><span data-stu-id="905aa-109">Create an XML resource (.resx) file that contains string, image, or object data.</span></span> <span data-ttu-id="905aa-110">您必須使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將 .resx 檔案轉換成二進位資源檔 (.resources)。</span><span class="sxs-lookup"><span data-stu-id="905aa-110">You can use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to convert the .resx file into a binary resource (.resources) file.</span></span> <span data-ttu-id="905aa-111">您接著可以使用語言編譯器將二進位資源檔內嵌在應用程式可執行檔或應用程式程式庫中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-111">You can then embed the binary resource file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="905aa-112">如需詳細資訊，請參閱 [.resx 檔案中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles)一節。</span><span class="sxs-lookup"><span data-stu-id="905aa-112">For more information, see the [Resources in .resx Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles) section.</span></span>

- <span data-ttu-id="905aa-113">使用 <xref:System.Resources> 命名空間中的類型，以程式設計方式建立 XML 資源檔 (.resx)。</span><span class="sxs-lookup"><span data-stu-id="905aa-113">Create an XML resource (.resx) file programmatically by using types in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="905aa-114">您可以建立 .resx 檔案、列舉其資源，並依名稱擷取特定資源。</span><span class="sxs-lookup"><span data-stu-id="905aa-114">You can create a .resx file, enumerate its resources, and retrieve specific resources by name.</span></span> <span data-ttu-id="905aa-115">如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)主題。</span><span class="sxs-lookup"><span data-stu-id="905aa-115">For more information, see the topic [Working with .resx Files Programmatically](../../../docs/framework/resources/working-with-resx-files-programmatically.md).</span></span>

- <span data-ttu-id="905aa-116">以程式設計方式建立二進位資源檔 (.resources)。</span><span class="sxs-lookup"><span data-stu-id="905aa-116">Create a binary resource (.resources) file programmatically.</span></span> <span data-ttu-id="905aa-117">您接著可以使用語言編譯器將檔案內嵌在應用程式可執行檔或應用程式程式庫中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-117">You can then embed the file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="905aa-118">如需詳細資訊，請參閱 [.resources 檔案中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles)一節。</span><span class="sxs-lookup"><span data-stu-id="905aa-118">For more information, see the [Resources in .resources Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) section.</span></span>

- <span data-ttu-id="905aa-119">使用 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 建立資源檔，並將它包含在您的專案中。</span><span class="sxs-lookup"><span data-stu-id="905aa-119">Use [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) to create a resource file and include it in your project.</span></span> <span data-ttu-id="905aa-120">Visual Studio 提供可讓您新增、刪除和修改資源的資源編輯器。</span><span class="sxs-lookup"><span data-stu-id="905aa-120">Visual Studio provides a resource editor that lets you add, delete, and modify resources.</span></span> <span data-ttu-id="905aa-121">在編譯時間，資源檔會自動轉換成二進位 .resources 檔案，並內嵌在應用程式組件或附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-121">At compile time, the resource file is automatically converted to a binary .resources file and embedded in an application assembly or satellite assembly.</span></span> <span data-ttu-id="905aa-122">如需詳細資訊，請參閱 [Visual Studio 中的資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles)一節。</span><span class="sxs-lookup"><span data-stu-id="905aa-122">For more information, see the [Resource Files in Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span>

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a><span data-ttu-id="905aa-123">文字檔中的資源</span><span class="sxs-lookup"><span data-stu-id="905aa-123">Resources in text files</span></span>

<span data-ttu-id="905aa-124">您只能使用文字 (.txt 或 .restext) 檔案來儲存字串資源。</span><span class="sxs-lookup"><span data-stu-id="905aa-124">You can use text (.txt or .restext) files to store string resources only.</span></span> <span data-ttu-id="905aa-125">針對非字串資源，請使用 .resx 檔案或以程式設計方式建立它們。</span><span class="sxs-lookup"><span data-stu-id="905aa-125">For non-string resources, use .resx files or create them programmatically.</span></span> <span data-ttu-id="905aa-126">包含字串資源的文字檔的格式如下：</span><span class="sxs-lookup"><span data-stu-id="905aa-126">Text files that contain string resources have the following format:</span></span>

```text
# This is an optional comment.
name = value

; This is another optional comment.
name = value

; The following supports conditional compilation if X is defined.
#ifdef X
name1=value1
name2=value2
#endif

# The following supports conditional compilation if Y is undefined.
#if !Y
name1=value1
name2=value2
#endif
```

 <span data-ttu-id="905aa-127">.txt 和 .restext 檔案的資源檔格式完全相同。</span><span class="sxs-lookup"><span data-stu-id="905aa-127">The resource file format of .txt and .restext files is identical.</span></span> <span data-ttu-id="905aa-128">.restext 副檔名只提供可立即將文字檔識別為文字資源檔。</span><span class="sxs-lookup"><span data-stu-id="905aa-128">The .restext file extension merely serves to make text files immediately identifiable as text-based resource files.</span></span>

 <span data-ttu-id="905aa-129">字串資源會以「名稱/值」配對的形式出現，其中「名稱」是識別資源的字串，「值」則是當您將「名稱」傳遞至資源擷取方法 (例如 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>) 時所傳回的資源字串。</span><span class="sxs-lookup"><span data-stu-id="905aa-129">String resources appear as *name/value* pairs, where *name* is a string that identifies the resource, and *value* is the resource string that is returned when you pass *name* to a resource retrieval method such as <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="905aa-130">「名稱」和「值」必須以等號 (=) 分隔。</span><span class="sxs-lookup"><span data-stu-id="905aa-130">*name* and *value* must be separated by an equal sign (=).</span></span> <span data-ttu-id="905aa-131">例如：</span><span class="sxs-lookup"><span data-stu-id="905aa-131">For example:</span></span>

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> <span data-ttu-id="905aa-132">請勿使用資源檔儲存密碼、安全機密資訊或私用資料。</span><span class="sxs-lookup"><span data-stu-id="905aa-132">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="905aa-133">文字檔中允許空字串 (即其值為 <xref:System.String.Empty?displayProperty=nameWithType> 的資源)。</span><span class="sxs-lookup"><span data-stu-id="905aa-133">Empty strings (that is, a resource whose value is <xref:System.String.Empty?displayProperty=nameWithType>) are permitted in text files.</span></span> <span data-ttu-id="905aa-134">例如：</span><span class="sxs-lookup"><span data-stu-id="905aa-134">For example:</span></span>

```
EmptyString=
```

 <span data-ttu-id="905aa-135">從 .NET Framework 4.5 及所有版本的 .NET Core 開始，文字檔案支援使用 `#ifdef` 符號... `#endif` 及 `#if !` 符號... `#endif` 建構的條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="905aa-135">Starting with .NET Framework 4.5 and in all versions of .NET Core, text files support conditional compilation with the `#ifdef`*symbol*... `#endif` and `#if !`*symbol*... `#endif` constructs.</span></span> <span data-ttu-id="905aa-136">您接著可以搭配使用 `/define` 切換參數與[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 來定義符號。</span><span class="sxs-lookup"><span data-stu-id="905aa-136">You can then use the `/define` switch with [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to define symbols.</span></span> <span data-ttu-id="905aa-137">每個資源都需要自己的 `#ifdef`*symbol*... `#endif` 或 `#if !`*symbol*... `#endif` 建構。</span><span class="sxs-lookup"><span data-stu-id="905aa-137">Each resource requires its own `#ifdef`*symbol*... `#endif` or `#if !`*symbol*... `#endif` construct.</span></span> <span data-ttu-id="905aa-138">如果您使用 `#ifdef` 陳述式而且已定義 *symbol*，則 .resources 檔案中會包括相關聯的資源；否則就不會包括該資源。</span><span class="sxs-lookup"><span data-stu-id="905aa-138">If you use an `#ifdef` statement and *symbol* is defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span> <span data-ttu-id="905aa-139">如果您使用 `#if !` 陳述式而且未定義 *symbol*，則 .resources 檔案中會包括相關聯的資源；否則就不會包括該資源。</span><span class="sxs-lookup"><span data-stu-id="905aa-139">If you use an `#if !` statement and *symbol* is not defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span>

 <span data-ttu-id="905aa-140">註解在文字檔中是選擇性的，並在行首加上分號 (;) 或井字號 (#)。</span><span class="sxs-lookup"><span data-stu-id="905aa-140">Comments are optional in text files and are preceded either by a semicolon (;) or by a pound sign (#) at the beginning of a line.</span></span> <span data-ttu-id="905aa-141">包含註解的程式行可以放在檔案中的任何地方。</span><span class="sxs-lookup"><span data-stu-id="905aa-141">Lines that contain comments can be placed anywhere in the file.</span></span> <span data-ttu-id="905aa-142">使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 建立的已編譯 .resources 檔案中未包括註解。</span><span class="sxs-lookup"><span data-stu-id="905aa-142">Comments are not included in a compiled .resources file that is created by using [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).</span></span>

 <span data-ttu-id="905aa-143">文字檔中的任何空白列都會視為空白字元，並且予以忽略。</span><span class="sxs-lookup"><span data-stu-id="905aa-143">Any blank lines in the text files are considered to be white space and are ignored.</span></span>

 <span data-ttu-id="905aa-144">下列範例定義兩個名為 `OKButton` 和 `CancelButton` 的字串資源。</span><span class="sxs-lookup"><span data-stu-id="905aa-144">The following example defines two string resources named `OKButton` and `CancelButton`.</span></span>

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 <span data-ttu-id="905aa-145">如果文字檔包含重複出現的「名稱」，則[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 會顯示警告，並忽略另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="905aa-145">If the text file contains duplicate occurrences of *name*, [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) displays a warning and ignores the second name.</span></span>

 <span data-ttu-id="905aa-146">「值」不可包含新行字元，但是您可以使用類似 C 語言逸出字元 (例如 `\n`) 代表新行，以及使用 `\t` 代表定位點。您也可以包括已逸出的反斜線字元 (例如，"\\\\")。</span><span class="sxs-lookup"><span data-stu-id="905aa-146">*value* cannot contain new line characters, but you can use C language-style escape characters such as `\n` to represent a new line and `\t` to represent a tab. You can also include a backslash character if it is escaped (for example, "\\\\").</span></span> <span data-ttu-id="905aa-147">此外，也允許空字串。</span><span class="sxs-lookup"><span data-stu-id="905aa-147">In addition, an empty string is permitted.</span></span>

 <span data-ttu-id="905aa-148">您應該在位元組由小到大或由大到小的位元組順序中使用 UTF-8 編碼或 UTF-16 編碼，以將資源儲存為文字檔格式。</span><span class="sxs-lookup"><span data-stu-id="905aa-148">You should save resources in text file format by using UTF-8 encoding or UTF-16 encoding in either little-endian or big-endian byte order.</span></span> <span data-ttu-id="905aa-149">不過，可將 .txt 檔案轉換為 .resources 檔案的[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，預設會將檔案視為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="905aa-149">However, [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), which converts a .txt file to a .resources file, treats files as UTF-8 by default.</span></span> <span data-ttu-id="905aa-150">如果您想要 Resgen.exe 辨識使用 UTF-16 所編碼的檔案，必須在檔案開頭包括 Unicode 位元組順序標記 (U+FEFF)。</span><span class="sxs-lookup"><span data-stu-id="905aa-150">If you want Resgen.exe to recognize a file that was encoded using UTF-16, you must include a Unicode byte order mark (U+FEFF) at the beginning of the file.</span></span>

 <span data-ttu-id="905aa-151">若要將文字格式的資源檔內嵌至 .NET 組件，您必須使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，將檔案轉換成二進位資源 (.resource) 檔。</span><span class="sxs-lookup"><span data-stu-id="905aa-151">To embed a resource file in text format into a .NET assembly, you must convert the file to a binary resource (.resources) file by using [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).</span></span> <span data-ttu-id="905aa-152">您接著可以使用語言編譯器將 .resources 檔案內嵌在 .NET 組件中，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-152">You can then embed the .resources file in a .NET assembly by using a language compiler or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>

 <span data-ttu-id="905aa-153">下列範例針對簡單 "Hello World" 主控台應用程式使用名為 GreetingResources.txt 且為文字格式的資源檔。</span><span class="sxs-lookup"><span data-stu-id="905aa-153">The following example uses a resource file in text format named GreetingResources.txt for a simple "Hello World" console application.</span></span> <span data-ttu-id="905aa-154">文字檔會定義 `prompt` 和 `greeting` 這兩個字串，提示使用者輸入其名稱並顯示問候語。</span><span class="sxs-lookup"><span data-stu-id="905aa-154">The text file defines two strings, `prompt` and `greeting`, that prompt the user to enter his or her name and display a greeting.</span></span>

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

<span data-ttu-id="905aa-155">使用下列命令，以將文字檔轉換成 .resources 檔案：</span><span class="sxs-lookup"><span data-stu-id="905aa-155">The text file is converted to a .resources file by using the following command:</span></span>

```console
resgen GreetingResources.txt
```

 <span data-ttu-id="905aa-156">下列範例顯示主控台應用程式的原始程式碼，而主控台應用程式使用 .resources 檔案向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="905aa-156">The following example shows the source code for a console application that uses the .resources file to display messages to the user.</span></span>

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 <span data-ttu-id="905aa-157">如果您使用 Visual Basic，而且原始程式碼檔案命名為 Greeting.vb，則下列命令會建立包含內嵌 .resources 檔案的可執行檔：</span><span class="sxs-lookup"><span data-stu-id="905aa-157">If you are using Visual Basic, and the source code file is named Greeting.vb, the following command creates an executable file that includes the embedded .resources file:</span></span>

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 <span data-ttu-id="905aa-158">如果您使用 C#，而且原始程式碼檔案命名為 Greeting.cs，則下列命令會建立包含內嵌 .resources 檔案的可執行檔：</span><span class="sxs-lookup"><span data-stu-id="905aa-158">If you are using C#, and the source code file is named Greeting.cs, the following command creates an executable file that includes the embedded .resources file:</span></span>

 ```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a><span data-ttu-id="905aa-159">.resx 檔案中的資源</span><span class="sxs-lookup"><span data-stu-id="905aa-159">Resources in .resx files</span></span>
 <span data-ttu-id="905aa-160">與只能儲存字串資源的文字檔不同，XML 資源檔 (.resx) 可以儲存字串；影像、圖示和音訊剪輯這類二進位資料，以及程式化物件。</span><span class="sxs-lookup"><span data-stu-id="905aa-160">Unlike text files, which can only store string resources, XML resource (.resx) files can store strings, binary data such as images, icons, and audio clips, and programmatic objects.</span></span> <span data-ttu-id="905aa-161">.resx 檔案包含描述資源項目格式的標準標頭，並指定用來剖析資料之 XML 的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="905aa-161">A .resx file contains a standard header, which describes the format of the resource entries and specifies the versioning information for the XML that is used to parse the data.</span></span> <span data-ttu-id="905aa-162">資源檔資料接在 XML 標頭後面。</span><span class="sxs-lookup"><span data-stu-id="905aa-162">The resource file data follows the XML header.</span></span> <span data-ttu-id="905aa-163">每個資料項目都會包含 `data` 標記中所含的名稱/值配對。</span><span class="sxs-lookup"><span data-stu-id="905aa-163">Each data item consists of a name/value pair that is contained in a `data` tag.</span></span> <span data-ttu-id="905aa-164">其 `name` 屬性定義資源名稱，而巢狀 `value` 標記包含資源值。</span><span class="sxs-lookup"><span data-stu-id="905aa-164">Its `name` attribute defines the resource name, and the nested `value` tag contains the resource value.</span></span> <span data-ttu-id="905aa-165">針對字串資料，`value` 標記會包含字串。</span><span class="sxs-lookup"><span data-stu-id="905aa-165">For string data, the `value` tag contains the string.</span></span>

 <span data-ttu-id="905aa-166">例如，下列 `data` 標記會定義名為 `prompt` 且其值為 "Enter your name:" 的字串資源。</span><span class="sxs-lookup"><span data-stu-id="905aa-166">For example, the following `data` tag defines a string resource named `prompt` whose value is "Enter your name:".</span></span>

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> <span data-ttu-id="905aa-167">請勿使用資源檔儲存密碼、安全機密資訊或私用資料。</span><span class="sxs-lookup"><span data-stu-id="905aa-167">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="905aa-168">針對資源物件，**data** 標記會包括 `type` 屬性，以指出資源資料類型。</span><span class="sxs-lookup"><span data-stu-id="905aa-168">For resource objects, the **data** tag includes a `type` attribute that indicates the data type of the resource.</span></span> <span data-ttu-id="905aa-169">針對包含二進位資料的物件，`data` 標記也會包括 `mimetype` 屬性，以指出二進位資料的 `base64` 類型。</span><span class="sxs-lookup"><span data-stu-id="905aa-169">For objects that consist of binary data, the `data` tag also includes a `mimetype` attribute, which indicates the `base64` type of the binary data.</span></span>

> [!NOTE]
> <span data-ttu-id="905aa-170">所有 .resx 檔案都會使用二進位序列化格式子產生和剖析所指定類型的二進位資料。</span><span class="sxs-lookup"><span data-stu-id="905aa-170">All .resx files use a binary serialization formatter to generate and parse the binary data for a specified type.</span></span> <span data-ttu-id="905aa-171">因此，如果物件的二進位序列化格式以不相容的方式變更，則 .resx 檔案可能會無效。</span><span class="sxs-lookup"><span data-stu-id="905aa-171">As a result, a .resx file can become invalid if the binary serialization format for an object changes in an incompatible way.</span></span>

 <span data-ttu-id="905aa-172">下列範例顯示 .resx 檔案中包括 <xref:System.Int32> 資源和點陣圖影像的一部分。</span><span class="sxs-lookup"><span data-stu-id="905aa-172">The following example shows a portion of a .resx file that includes an <xref:System.Int32> resource and a bitmap image.</span></span>

```xml
<data name="i1" type="System.Int32, mscorlib">
  <value>20</value>
</data>

<data name="flag" type="System.Drawing.Bitmap, System.Drawing,
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
    mimetype="application/x-microsoft.net.object.bytearray.base64">
  <value>
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…
  </value>
</data>
```

> [!IMPORTANT]
> <span data-ttu-id="905aa-173">因為 .resx 檔案必須包含具有預先定義格式的格式正確 XML，所以不建議手動使用 .resx 檔案，特別是 .resx 檔案包含字串以外的資源時。</span><span class="sxs-lookup"><span data-stu-id="905aa-173">Because .resx files must consist of well-formed XML in a predefined format, we do not recommend working with .resx files manually, particularly when the .resx files contain resources other than strings.</span></span> <span data-ttu-id="905aa-174">[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 改為提供一種透明的介面，來建立和操作 .resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="905aa-174">Instead, [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) provides a transparent interface for creating and manipulating .resx files.</span></span> <span data-ttu-id="905aa-175">如需詳細資訊，請參閱 [Visual Studio 中的資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles)一節。</span><span class="sxs-lookup"><span data-stu-id="905aa-175">For more information, see the [Resource Files in Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span> <span data-ttu-id="905aa-176">您也可以透過程式設計方式建立和操作 .resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="905aa-176">You can also create and manipulate .resx files programmatically.</span></span> <span data-ttu-id="905aa-177">如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="905aa-177">For more information, see [Working with .resx Files Programmatically](../../../docs/framework/resources/working-with-resx-files-programmatically.md).</span></span>

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a><span data-ttu-id="905aa-178">.resources 檔案中的資源</span><span class="sxs-lookup"><span data-stu-id="905aa-178">Resources in .resources files</span></span>

<span data-ttu-id="905aa-179">您可以使用 <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> 類別，以程式設計方式直接從程式碼建立二進位資源檔 (.resources)。</span><span class="sxs-lookup"><span data-stu-id="905aa-179">You can use the <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> class to programmatically create a binary resource (.resources) file directly from code.</span></span> <span data-ttu-id="905aa-180">您也可以使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，從文字檔或 .resx 檔案建立 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="905aa-180">You can also use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to create a .resources file from a text file or a .resx file.</span></span> <span data-ttu-id="905aa-181">除了字串資料之外，.resources 檔案還可以包含二進位資料 (位元組陣列) 和物件資料。</span><span class="sxs-lookup"><span data-stu-id="905aa-181">The .resources file can contain binary data (byte arrays) and object data in addition to string data.</span></span> <span data-ttu-id="905aa-182">以程式設計方式建立 .resources 檔案，需要下列步驟：</span><span class="sxs-lookup"><span data-stu-id="905aa-182">Programmatically creating a .resources file requires the following steps:</span></span>

1. <span data-ttu-id="905aa-183">建立具有唯一檔案名稱的 <xref:System.Resources.ResourceWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="905aa-183">Create a <xref:System.Resources.ResourceWriter> object with a unique file name.</span></span> <span data-ttu-id="905aa-184">做法是將檔案名稱或檔案資料流指定給 <xref:System.Resources.ResourceWriter> 類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="905aa-184">You can do this by specifying either a file name or a file stream to a <xref:System.Resources.ResourceWriter> class constructor.</span></span>

2. <span data-ttu-id="905aa-185">針對要新增至檔案的每個具名資源，呼叫 <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> 方法的其中一個多載。</span><span class="sxs-lookup"><span data-stu-id="905aa-185">Call one of the overloads of the <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> method for each named resource to add to the file.</span></span> <span data-ttu-id="905aa-186">資源可以是字串、物件或二進位資料集合 (位元組陣列)。</span><span class="sxs-lookup"><span data-stu-id="905aa-186">The resource can be a string, an object, or a collection of binary data (a byte array).</span></span>

3. <span data-ttu-id="905aa-187">呼叫 <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> 方法，以將資源寫入至檔案，並關閉 <xref:System.Resources.ResourceWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="905aa-187">Call the <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> method to write the resources to the file and to close the <xref:System.Resources.ResourceWriter> object.</span></span>

> [!NOTE]
> <span data-ttu-id="905aa-188">請勿使用資源檔儲存密碼、安全機密資訊或私用資料。</span><span class="sxs-lookup"><span data-stu-id="905aa-188">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="905aa-189">下列範例會以程式設計方式建立名為 CarResources.resources 的 .resources 檔案，其中儲存六個字串、一個圖示和兩個應用程式定義的物件 (兩個 `Automobile` 物件)。</span><span class="sxs-lookup"><span data-stu-id="905aa-189">The following example programmatically creates a .resources file named CarResources.resources that stores six strings, an icon, and two application-defined objects (two `Automobile` objects).</span></span> <span data-ttu-id="905aa-190">請注意，在此範例中定義和執行個體化的 `Automobile` 類別會標上 <xref:System.SerializableAttribute> 屬性，以讓二進位序列化格式子保存它。</span><span class="sxs-lookup"><span data-stu-id="905aa-190">Note that the `Automobile` class, which is defined and instantiated in the example, is tagged with the <xref:System.SerializableAttribute> attribute, which allows it to be persisted by the binary serialization formatter.</span></span>

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 <span data-ttu-id="905aa-191">當您建立 .resources 檔案之後，可以包括語言編譯器的 `/resource` 切換參數以將它內嵌在執行階段可執行檔或程式庫中，或是使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它內嵌在附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-191">After you create the .resources file, you can embed it in a run-time executable or library by including the language compiler's `/resource` switch, or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a><span data-ttu-id="905aa-192">Visual Studio 中的資源檔</span><span class="sxs-lookup"><span data-stu-id="905aa-192">Resource files in Visual Studio</span></span>

<span data-ttu-id="905aa-193">當您將資源檔新增至 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 專案時，Visual Studio 會在專案目錄中建立 .resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="905aa-193">When you add a resource file to your [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) project, Visual Studio creates a .resx file in the project directory.</span></span> <span data-ttu-id="905aa-194">Visual Studio 提供可讓您新增字串、影像和二進位物件的資源編輯器。</span><span class="sxs-lookup"><span data-stu-id="905aa-194">Visual Studio provides resource editors that enable you to add strings, images, and binary objects.</span></span> <span data-ttu-id="905aa-195">因為編輯器設計成只處理靜態資料，所以無法使用它們來儲存程式化物件；您必須以程式設計方式將物件資料寫入 .resx 檔案或 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="905aa-195">Because the editors are designed to handle static data only, they cannot be used to store programmatic objects; you must write object data to either a .resx file or to a .resources file programmatically.</span></span> <span data-ttu-id="905aa-196">如需詳細資訊，請參閱[以程式設計方式使用 .resx 檔案](../../../docs/framework/resources/working-with-resx-files-programmatically.md)和 [.resources 檔案中的資源](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles)章節。</span><span class="sxs-lookup"><span data-stu-id="905aa-196">For more information, see [Working with .resx Files Programmatically](../../../docs/framework/resources/working-with-resx-files-programmatically.md) and the [Resources in .resources Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) section.</span></span>

<span data-ttu-id="905aa-197">若您要新增當地語系化的資源，請提供它們與主要資源檔相同的根檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="905aa-197">If you're adding localized resources, give them the same root file name as the main resource file.</span></span> <span data-ttu-id="905aa-198">您也應在檔案名稱中指定它們的文化特性 (Culture)。</span><span class="sxs-lookup"><span data-stu-id="905aa-198">You should also designate their culture in the file name.</span></span> <span data-ttu-id="905aa-199">例如，如果您新增名為 Resources.resx 的資源檔，也可能會建立名為 Resources.en-US.resx 和 Resources.fr-FR.resx 的資源檔，來分別保留英文 (美國) 和法文 (法國) 文化特性的當地語系化資源。</span><span class="sxs-lookup"><span data-stu-id="905aa-199">For example, if you add a resource file named Resources.resx, you might also create resource files named Resources.en-US.resx and Resources.fr-FR.resx to hold localized resources for the English (United States) and French (France) cultures, respectively.</span></span> <span data-ttu-id="905aa-200">您也應該指定應用程式的預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="905aa-200">You should also designate your application's default culture.</span></span> <span data-ttu-id="905aa-201">如果找不到特定文化特性的當地語系化資源，則這是使用其資源的文化特性。</span><span class="sxs-lookup"><span data-stu-id="905aa-201">This is the culture whose resources are used if no localized resources for a particular culture can be found.</span></span> <span data-ttu-id="905aa-202">若要指定預設文化特性，請在 Visual Studio 的方案總管中以滑鼠右鍵按一下專案名稱、指向 [應用程式]、按一下 [組件資訊]，然後在 [中性語言] 清單中選取適當語言/文化特性。</span><span class="sxs-lookup"><span data-stu-id="905aa-202">To specify the default culture, in Solution Explorer in Visual Studio, right-click the project name, point to Application, click **Assembly Information**, and select the appropriate language/culture in the **Neutral language** list.</span></span>

<span data-ttu-id="905aa-203">在編譯時間，Visual Studio 先將專案中的 .resx 檔案轉換成二進位資源檔 (.resources)，並將它們儲存在專案 *obj* 目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="905aa-203">At compile time, Visual Studio first converts the .resx files in a project to binary resource (.resources) files and stores them in a subdirectory of the project's *obj* directory.</span></span> <span data-ttu-id="905aa-204">Visual Studio 會將未包含當地語系化資源的任何資源檔內嵌在專案所產生的主要組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-204">Visual Studio embeds any resource files that do not contain localized resources in the main assembly that is generated by the project.</span></span> <span data-ttu-id="905aa-205">如果任何資源檔包含當地語系化資源，Visual Studio 會將其內嵌在每個當地語系化文化特性的個別附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-205">If any resource files contain localized resources, Visual Studio embeds them in separate satellite assemblies for each localized culture.</span></span> <span data-ttu-id="905aa-206">它接著會將每個附屬組件儲存在名稱對應至當地語系化文化特性的目錄中。</span><span class="sxs-lookup"><span data-stu-id="905aa-206">It then stores each satellite assembly in a directory whose name corresponds to the localized culture.</span></span> <span data-ttu-id="905aa-207">例如，當地語系化的英文 (美國) 資源會儲存在 en-US 子目錄的附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="905aa-207">For example, localized English (United States) resources are stored in a satellite assembly in the en-US subdirectory.</span></span>

## <a name="see-also"></a><span data-ttu-id="905aa-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="905aa-208">See also</span></span>

- <xref:System.Resources>
- [<span data-ttu-id="905aa-209">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="905aa-209">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
- [<span data-ttu-id="905aa-210">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="905aa-210">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
