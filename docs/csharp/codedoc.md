---
title: 使用 XML 註解記錄您的程式碼
description: 了解如何使用 XML 文件註解記錄您的程式碼，並在編譯時期產生 XML 文件檔案。
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1284f179c7debb323ea3bbd302df1f02bf8b31b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="b35d6-103">使用 XML 註解記錄您的程式碼</span><span class="sxs-lookup"><span data-stu-id="b35d6-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="b35d6-104">XML 文件註解是一種特殊類型的註解，新增於任何使用者定義型別或成員的定義上方。</span><span class="sxs-lookup"><span data-stu-id="b35d6-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span> <span data-ttu-id="b35d6-105">XML 文件註解具特殊性，因為編譯器可以處理它們以在編譯時期產生 XML 文件檔案。</span><span class="sxs-lookup"><span data-stu-id="b35d6-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="b35d6-106">編譯器所產生的 XML 檔案可以隨著 .NET 組件一起散發，因此 Visual Studio 和其他 IDE 可以使用 IntelliSense 來顯示類型或成員的快速資訊。</span><span class="sxs-lookup"><span data-stu-id="b35d6-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="b35d6-107">此外，可以透過 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具執行 XML 檔案來產生 API 參考網站。</span><span class="sxs-lookup"><span data-stu-id="b35d6-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="b35d6-108">編譯器會忽略 XML 文件註解 (例如所有其他註解)。</span><span class="sxs-lookup"><span data-stu-id="b35d6-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="b35d6-109">您可以執行下列其中一項動作，以在編譯時期產生 XML 檔案︰</span><span class="sxs-lookup"><span data-stu-id="b35d6-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="b35d6-110">如果您正在從命令列使用 .NET Core 開發應用程式，則可以將 [DocumentationFile 項目](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties)新增至 .csproj 專案檔的 `<PropertyGroup>` 區段。</span><span class="sxs-lookup"><span data-stu-id="b35d6-110">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="b35d6-111">下列範例會在根檔案名稱與組件相同的專案目錄中產生 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="b35d6-111">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="b35d6-112">您也可以指定 XML 檔案的確切絕對或相對路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="b35d6-112">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="b35d6-113">下列範例會在與應用程式的偵錯版本相同的目錄中產生 XML 檔案︰</span><span class="sxs-lookup"><span data-stu-id="b35d6-113">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="b35d6-114">如果您正在使用 Visual Studio 開發應用程式，請以滑鼠右鍵按一下專案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b35d6-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="b35d6-115">在屬性對話方塊中，選取 [建置] 索引標籤，然後檢查 [XML 文件檔案]。</span><span class="sxs-lookup"><span data-stu-id="b35d6-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="b35d6-116">您也可以變更編譯器寫入檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="b35d6-116">You can also change the location to which the compiler writes the file.</span></span> 

- <span data-ttu-id="b35d6-117">如果您正在從命令列編譯 .NET Framework 應用程式，請在編譯時新增 [/doc 編譯器選項](language-reference/compiler-options/doc-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="b35d6-117">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="b35d6-118">XML 文件註解使用三個正斜線 (`///`) 和 XML 格式化註解主體。</span><span class="sxs-lookup"><span data-stu-id="b35d6-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="b35d6-119">例如: </span><span class="sxs-lookup"><span data-stu-id="b35d6-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="b35d6-120">逐步解說</span><span class="sxs-lookup"><span data-stu-id="b35d6-120">Walkthrough</span></span>

<span data-ttu-id="b35d6-121">讓我們逐步記錄極基本的數學庫，讓新的開發人員輕鬆了解/參與以及讓協力廠商開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="b35d6-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="b35d6-122">以下是簡單數學程式庫的程式碼︰</span><span class="sxs-lookup"><span data-stu-id="b35d6-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="b35d6-123">範例程式庫支援 `int` 和 `double` 資料型別上的四個主要算術運算 `add`、`subtract`、`multiply` 和 `divide`。</span><span class="sxs-lookup"><span data-stu-id="b35d6-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="b35d6-124">現在，您想要可以針對使用您的程式庫但無法存取原始程式碼的協力廠商開發人員，從您的程式碼建立 API 參考文件。</span><span class="sxs-lookup"><span data-stu-id="b35d6-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="b35d6-125">如前所述，XML 文件標記可以用來達成這項作業。現在已引進 C# 編譯器所支援的標準 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="b35d6-125">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="b35d6-126">&lt;summary&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-126">&lt;summary&gt;</span></span>

<span data-ttu-id="b35d6-127">`<summary>` 標記會新增類型或成員的簡短資訊。</span><span class="sxs-lookup"><span data-stu-id="b35d6-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="b35d6-128">我會將它新增至 `Math` 類別定義和第一個 `Add` 方法來示範其使用方式。</span><span class="sxs-lookup"><span data-stu-id="b35d6-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="b35d6-129">請自由套用至您程式碼的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="b35d6-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="b35d6-130">`<summary>` 標記十分重要，因為它的內容是 IntelliSense 或 API 參考文件中類型或成員資訊的主要來源，所以建議您包含它。</span><span class="sxs-lookup"><span data-stu-id="b35d6-130">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="b35d6-131">&lt;remarks&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-131">&lt;remarks&gt;</span></span>

<span data-ttu-id="b35d6-132">`<remarks>` 標記會補充 `<summary>` 標記所提供的類型或成員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b35d6-132">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="b35d6-133">在此範例中，您只會將它新增至類別。</span><span class="sxs-lookup"><span data-stu-id="b35d6-133">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a><span data-ttu-id="b35d6-134">&lt;returns&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-134">&lt;returns&gt;</span></span>

<span data-ttu-id="b35d6-135">`<returns>` 標記描述方法宣告的傳回值。</span><span class="sxs-lookup"><span data-stu-id="b35d6-135">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="b35d6-136">如前所示，下列範例說明第一個 `Add` 方法的 `<returns>` 標記。</span><span class="sxs-lookup"><span data-stu-id="b35d6-136">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="b35d6-137">您可以對其他方法執行相同作業。</span><span class="sxs-lookup"><span data-stu-id="b35d6-137">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a><span data-ttu-id="b35d6-138">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-138">&lt;value&gt;</span></span>

<span data-ttu-id="b35d6-139">`<value>` 標記類似於 `<returns>` 標記，但將它用作屬性除外。</span><span class="sxs-lookup"><span data-stu-id="b35d6-139">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="b35d6-140">假設 `Math` 程式庫的靜態屬性稱為 `PI`，以下是使用這個標記的方式：</span><span class="sxs-lookup"><span data-stu-id="b35d6-140">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a><span data-ttu-id="b35d6-141">&lt;example&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-141">&lt;example&gt;</span></span>

<span data-ttu-id="b35d6-142">您可以使用 `<example>` 標記，以在 XML 文件中包括範例。</span><span class="sxs-lookup"><span data-stu-id="b35d6-142">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="b35d6-143">這包含如何使用子 `<code>` 標記。</span><span class="sxs-lookup"><span data-stu-id="b35d6-143">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="b35d6-144">`code` 標記會保留分行符號以及較長範例的縮排。</span><span class="sxs-lookup"><span data-stu-id="b35d6-144">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="b35d6-145">&lt;para&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-145">&lt;para&gt;</span></span>

<span data-ttu-id="b35d6-146">您可以使用 `<para>` 標記來格式化其父標記內的內容。</span><span class="sxs-lookup"><span data-stu-id="b35d6-146">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="b35d6-147">`<para>` 通常用於標記內 (例如 `<remarks>` 或 `<returns>`)，以將文字分成數個段落。</span><span class="sxs-lookup"><span data-stu-id="b35d6-147">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="b35d6-148">您可以格式化類別定義的 `<remarks>` 標記內容。</span><span class="sxs-lookup"><span data-stu-id="b35d6-148">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a><span data-ttu-id="b35d6-149">&lt;C&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-149">&lt;c&gt;</span></span>

<span data-ttu-id="b35d6-150">仍然，在有關格式化的主題，您可以使用 `<c>` 標記將一部分文字標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="b35d6-150">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="b35d6-151">它就像 `<code>` 標記，只是會內嵌。</span><span class="sxs-lookup"><span data-stu-id="b35d6-151">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="b35d6-152">這適用於您想要將快速程式碼範例顯示為標記內容的一部分時。</span><span class="sxs-lookup"><span data-stu-id="b35d6-152">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="b35d6-153">請更新 `Math` 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="b35d6-153">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a><span data-ttu-id="b35d6-154">&lt;exception&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-154">&lt;exception&gt;</span></span>

<span data-ttu-id="b35d6-155">使用 `<exception>` 標記，讓您的開發人員知道方法可以擲回特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b35d6-155">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="b35d6-156">查看 `Math` 程式庫，即可看到兩個 `Add` 方法在符合特定條件時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b35d6-156">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="b35d6-157">雖然不明顯，但如果 `b` 參數為零，則也會擲回整數 `Divide` 方法。</span><span class="sxs-lookup"><span data-stu-id="b35d6-157">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="b35d6-158">現在將例外狀況文件新增至這個方法。</span><span class="sxs-lookup"><span data-stu-id="b35d6-158">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="b35d6-159">`cref` 屬性代表可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="b35d6-159">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="b35d6-160">這可以是專案或已參考組件中所定義的任何類型。</span><span class="sxs-lookup"><span data-stu-id="b35d6-160">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="b35d6-161">如果無法解析其值，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="b35d6-161">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="b35d6-162">&lt;see&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-162">&lt;see&gt;</span></span>

<span data-ttu-id="b35d6-163">`<see>` 標記可讓您建立另一個程式碼項目之文件頁面的可按式連結。</span><span class="sxs-lookup"><span data-stu-id="b35d6-163">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="b35d6-164">在下一個範例中，我們將在兩個 `Add` 方法之間建立可按式連結。</span><span class="sxs-lookup"><span data-stu-id="b35d6-164">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="b35d6-165">`cref` 為**必要**屬性，代表可從目前編譯環境取得的類型或其成員的參考。</span><span class="sxs-lookup"><span data-stu-id="b35d6-165">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span> <span data-ttu-id="b35d6-166">這可以是專案或已參考組件中所定義的任何類型。</span><span class="sxs-lookup"><span data-stu-id="b35d6-166">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="b35d6-167">&lt;seealso&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-167">&lt;seealso&gt;</span></span>

<span data-ttu-id="b35d6-168">`<seealso>` 標記的使用方式與 `<see>` 標記的使用方式相同。</span><span class="sxs-lookup"><span data-stu-id="b35d6-168">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="b35d6-169">唯一的差異在於它的內容一般會放在＜另請參閱＞一節中。</span><span class="sxs-lookup"><span data-stu-id="b35d6-169">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="b35d6-170">在這裡，我們將在整數 `Add` 方法上新增 `seealso` 標記，以參考類別中接受整數參數的其他方法：</span><span class="sxs-lookup"><span data-stu-id="b35d6-170">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="b35d6-171">`cref` 屬性代表可從目前編譯環境取得的類型或其成員的參考。</span><span class="sxs-lookup"><span data-stu-id="b35d6-171">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="b35d6-172">這可以是專案或已參考組件中所定義的任何類型。</span><span class="sxs-lookup"><span data-stu-id="b35d6-172">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="b35d6-173">&lt;param&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-173">&lt;param&gt;</span></span>

<span data-ttu-id="b35d6-174">您可以使用 `<param>` 標記來描述方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b35d6-174">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="b35d6-175">以下是雙 `Add` 方法的範例：標記所描述的屬性指定於**必要的** `name` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="b35d6-175">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a><span data-ttu-id="b35d6-176">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-176">&lt;typeparam&gt;</span></span>

<span data-ttu-id="b35d6-177">您可以就像使用 `<param>` 標記一樣地使用 `<typeparam>` 標記，但針對泛型型別或方法宣告來描述泛型參數。</span><span class="sxs-lookup"><span data-stu-id="b35d6-177">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="b35d6-178">請將快速泛型方法新增至 `Math` 類別，以檢查其中一個數量是否大於另一個數量。</span><span class="sxs-lookup"><span data-stu-id="b35d6-178">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a><span data-ttu-id="b35d6-179">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-179">&lt;paramref&gt;</span></span>

<span data-ttu-id="b35d6-180">您有時可能正在描述方法在 `<summary>` 標記中所執行的作業，而且您可能會想要參考參數。</span><span class="sxs-lookup"><span data-stu-id="b35d6-180">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="b35d6-181">則 `<paramref>` 標記最適合這麼做。</span><span class="sxs-lookup"><span data-stu-id="b35d6-181">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="b35d6-182">讓我們更新雙 `Add` 方法的摘要。</span><span class="sxs-lookup"><span data-stu-id="b35d6-182">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="b35d6-183">與 `<param>` 標記類似，參數名稱指定於**必要的** `name` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="b35d6-183">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a><span data-ttu-id="b35d6-184">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-184">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="b35d6-185">您可以就像使用 `<paramref>` 標記一樣地使用 `<typeparamref>` 標記，但針對泛型型別或方法宣告來描述泛型參數。</span><span class="sxs-lookup"><span data-stu-id="b35d6-185">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="b35d6-186">您可以使用先前建立的相同泛型方法。</span><span class="sxs-lookup"><span data-stu-id="b35d6-186">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a><span data-ttu-id="b35d6-187">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-187">&lt;list&gt;</span></span>

<span data-ttu-id="b35d6-188">您可以使用 `<list>` 標記，將文件資訊格式化為已排序清單、未排序清單或資料表。</span><span class="sxs-lookup"><span data-stu-id="b35d6-188">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="b35d6-189">建立 `Math` 程式庫所支援的未排序數學運算清單。</span><span class="sxs-lookup"><span data-stu-id="b35d6-189">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="b35d6-190">您可以分別將 `type` 屬性變更為 `number` 或 `table`，以建立排序過的清單或表格。</span><span class="sxs-lookup"><span data-stu-id="b35d6-190">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="b35d6-191">整體回顧</span><span class="sxs-lookup"><span data-stu-id="b35d6-191">Putting it all together</span></span>

<span data-ttu-id="b35d6-192">如已遵循本教學課程，並已在必要時將標記套用至程式碼，則程式碼現在看起來應該如下︰</span><span class="sxs-lookup"><span data-stu-id="b35d6-192">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="b35d6-193">從程式碼中，您可以產生使用可按式交互參照完成的詳細文件網站。</span><span class="sxs-lookup"><span data-stu-id="b35d6-193">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="b35d6-194">但您會面臨另一個問題︰您的程式碼變得難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="b35d6-194">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="b35d6-195">因為有太多資訊需要仔細檢查，這會是想要參與這個程式碼之開發人員的夢魘。</span><span class="sxs-lookup"><span data-stu-id="b35d6-195">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span> <span data-ttu-id="b35d6-196">還好有 XML 標記可協助您處理這個問題︰</span><span class="sxs-lookup"><span data-stu-id="b35d6-196">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="b35d6-197">&lt;include&gt;</span><span class="sxs-lookup"><span data-stu-id="b35d6-197">&lt;include&gt;</span></span>

<span data-ttu-id="b35d6-198">`<include>` 標記可讓您參考個別 XML 檔案中描述原始程式碼中類型和成員的註解，這與直接在原始程式碼檔中放置文件註解相反。</span><span class="sxs-lookup"><span data-stu-id="b35d6-198">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="b35d6-199">您現在要將所有 XML 標記移至名為 `docs.xml` 的個別 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="b35d6-199">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="b35d6-200">請放心以您想要的名稱來命名檔案。</span><span class="sxs-lookup"><span data-stu-id="b35d6-200">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="b35d6-201">在上述 XML 中，每個成員的文件註解都會直接顯示在執行動作之後所命名的標記內。</span><span class="sxs-lookup"><span data-stu-id="b35d6-201">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="b35d6-202">您可以選擇自己的策略。</span><span class="sxs-lookup"><span data-stu-id="b35d6-202">You can choose your own strategy.</span></span> <span data-ttu-id="b35d6-203">現在，您的 XML 註解位於在不同的檔案中，請查看如何使用 `<include>` 標記讓您的程式碼更容易閱讀：</span><span class="sxs-lookup"><span data-stu-id="b35d6-203">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="b35d6-204">目前您已經準備好了：我們的程式碼又再次為可讀，而且未遺失文件資訊。</span><span class="sxs-lookup"><span data-stu-id="b35d6-204">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span> 

<span data-ttu-id="b35d6-205">`filename` 屬性代表包含文件的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b35d6-205">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="b35d6-206">`path` 屬性代表存在於所指定 `filename` 中之 `tag name` 的 [XPath](https://msdn.microsoft.com/library/ms256115.aspx) 查詢。</span><span class="sxs-lookup"><span data-stu-id="b35d6-206">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="b35d6-207">`name` 屬性代表標記中位在註解前面的名稱規範。</span><span class="sxs-lookup"><span data-stu-id="b35d6-207">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="b35d6-208">可用來取代 `name` 的 `id` 屬性代表位在註解前面之標記的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b35d6-208">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="b35d6-209">使用者定義標記</span><span class="sxs-lookup"><span data-stu-id="b35d6-209">User Defined Tags</span></span>

<span data-ttu-id="b35d6-210">以上所述的所有標記都代表 C# 編譯器所辨識的標記。</span><span class="sxs-lookup"><span data-stu-id="b35d6-210">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="b35d6-211">不過，使用者可以定義自己的標記。</span><span class="sxs-lookup"><span data-stu-id="b35d6-211">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="b35d6-212">Sandcastle 這類工具會支援 [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm)、[`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) 甚至支援 [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm) (記錄命名空間) 這類額外標記。</span><span class="sxs-lookup"><span data-stu-id="b35d6-212">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="b35d6-213">自訂或內部文件產生工具也可以與標準標記搭配使用，而且可以支援從 HTML 到 PDF 的多個輸出格式。</span><span class="sxs-lookup"><span data-stu-id="b35d6-213">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="b35d6-214">建議</span><span class="sxs-lookup"><span data-stu-id="b35d6-214">Recommendations</span></span>

<span data-ttu-id="b35d6-215">有許多原因，建議您記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="b35d6-215">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="b35d6-216">接下來是一些最佳做法、一般使用案例，以及在 C# 程式碼中使用 XML 文件標記時應該知道的事項。</span><span class="sxs-lookup"><span data-stu-id="b35d6-216">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="b35d6-217">為保持一致性，應該記錄所有公開可見的類型和其成員。</span><span class="sxs-lookup"><span data-stu-id="b35d6-217">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="b35d6-218">如果您必須執行它，則請執行。</span><span class="sxs-lookup"><span data-stu-id="b35d6-218">If you must do it, do it all.</span></span>
* <span data-ttu-id="b35d6-219">也可以使用 XML 註解記錄私用成員。</span><span class="sxs-lookup"><span data-stu-id="b35d6-219">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="b35d6-220">不過，這樣會公開您程式庫的內部 (可能是機密) 運作。</span><span class="sxs-lookup"><span data-stu-id="b35d6-220">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="b35d6-221">類型和其成員最少應該具有 `<summary>` 標記，因為 IntelliSense 需要其內容。</span><span class="sxs-lookup"><span data-stu-id="b35d6-221">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="b35d6-222">應該使用結尾為句號的完整句子來撰寫文件文字。</span><span class="sxs-lookup"><span data-stu-id="b35d6-222">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="b35d6-223">完全支援部分類別，而且文件資訊將會串連為該類型的單一項目。</span><span class="sxs-lookup"><span data-stu-id="b35d6-223">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="b35d6-224">編譯器會驗證 `<exception>`、`<include>`、`<param>`、`<see>`、`<seealso>` 和 `<typeparam>` 標記的語法。</span><span class="sxs-lookup"><span data-stu-id="b35d6-224">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="b35d6-225">編譯器會驗證包含程式碼其他部分的檔案路徑和參考的參數。</span><span class="sxs-lookup"><span data-stu-id="b35d6-225">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="b35d6-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b35d6-226">See also</span></span>
[<span data-ttu-id="b35d6-227">XML 文件註解 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b35d6-227">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)

[<span data-ttu-id="b35d6-228">建議使用的文件註解標記 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b35d6-228">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
