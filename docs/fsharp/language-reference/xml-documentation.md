---
title: XML 文件
description: '瞭解 F # 中的支援，以從批註產生檔。'
ms.date: 09/15/2020
ms.openlocfilehash: 8720d66204333eb21dc998655467f9a5745a33f3
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982475"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="95d3e-103">使用 XML 批註記錄您的程式碼</span><span class="sxs-lookup"><span data-stu-id="95d3e-103">Document your code with XML comments</span></span>

<span data-ttu-id="95d3e-104">您可以從三斜線產生檔 (//) F # 中的程式碼批註。</span><span class="sxs-lookup"><span data-stu-id="95d3e-104">You can produce documentation from triple-slash (///) code comments in F#.</span></span> <span data-ttu-id="95d3e-105">XML 批註可以在程式碼檔中的宣告之前 (. fs) 或簽章 (. fsi) 檔。</span><span class="sxs-lookup"><span data-stu-id="95d3e-105">XML comments can precede declarations in code files (.fs) or signature (.fsi) files.</span></span>

<span data-ttu-id="95d3e-106">XML 文件註解是一種特殊類型的註解，新增於任何使用者定義型別或成員的定義上方。</span><span class="sxs-lookup"><span data-stu-id="95d3e-106">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="95d3e-107">XML 文件註解具特殊性，因為編譯器可以處理它們以在編譯時期產生 XML 文件檔案。</span><span class="sxs-lookup"><span data-stu-id="95d3e-107">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="95d3e-108">編譯器產生的 XML 檔案可以與您的 .NET 元件一起散發，讓 Ide 可以使用工具提示來顯示類型或成員的快速資訊。</span><span class="sxs-lookup"><span data-stu-id="95d3e-108">The compiler-generated XML file can be distributed alongside your .NET assembly so that IDEs can use tooltips to show quick information about types or members.</span></span> <span data-ttu-id="95d3e-109">此外，XML 檔案可以透過 [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) 之類的工具來執行，以產生 API 參考網站。</span><span class="sxs-lookup"><span data-stu-id="95d3e-109">Additionally, the XML file can be run through tools like [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) to generate API reference websites.</span></span>

<span data-ttu-id="95d3e-110">XML 檔批註（如同所有其他批註）將會被編譯器忽略，除非已啟用以下所述的選項，以便在編譯時間檢查批註的有效性和完整性。</span><span class="sxs-lookup"><span data-stu-id="95d3e-110">XML documentation comments, like all other comments, are ignored by the compiler, unless the options described below are enabled to check the validity and completeness of comments at compile-time.</span></span>

<span data-ttu-id="95d3e-111">您可以執行下列其中一項動作，以在編譯時期產生 XML 檔案︰</span><span class="sxs-lookup"><span data-stu-id="95d3e-111">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="95d3e-112">您可以在 `GenerateDocumentationFile` 專案檔的 `<PropertyGroup>` 區段中加入 `.fsproj` 專案，這會在專案目錄中產生 XML 檔案，該檔案的根檔案名與元件相同。</span><span class="sxs-lookup"><span data-stu-id="95d3e-112">You can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your `.fsproj` project file, which generates an XML file in the project directory with the same root filename as the assembly.</span></span> <span data-ttu-id="95d3e-113">例如：</span><span class="sxs-lookup"><span data-stu-id="95d3e-113">For example:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

- <span data-ttu-id="95d3e-114">如果您正在使用 Visual Studio 開發應用程式，請以滑鼠右鍵按一下專案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="95d3e-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="95d3e-115">在屬性對話方塊中，選取 [建置] 索引標籤，然後檢查 [XML 文件檔案]。</span><span class="sxs-lookup"><span data-stu-id="95d3e-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="95d3e-116">您也可以變更編譯器寫入檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="95d3e-116">You can also change the location to which the compiler writes the file.</span></span>

<span data-ttu-id="95d3e-117">有兩種方式可以撰寫 XML 檔批註： with 和不含 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="95d3e-117">There are two ways to write XML documentation comments: with and without XML tags.</span></span> <span data-ttu-id="95d3e-118">兩者都使用三斜線批註。</span><span class="sxs-lookup"><span data-stu-id="95d3e-118">Both use triple-slash comments.</span></span>

## <a name="comments-without-xml-tags"></a><span data-ttu-id="95d3e-119">沒有 XML 標記的批註</span><span class="sxs-lookup"><span data-stu-id="95d3e-119">Comments without XML tags</span></span>

<span data-ttu-id="95d3e-120">如果 `///` 批註的開頭不是，則 `<` 會將整個註解文字視為程式碼結構的摘要檔（緊接在後面）。</span><span class="sxs-lookup"><span data-stu-id="95d3e-120">If a `///` comment does not start with a `<` then the entire comment text is taken as the summary documentation for the code construct that immediately follows.</span></span> <span data-ttu-id="95d3e-121">當您只想撰寫每個結構的簡短摘要時，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="95d3e-121">Use this method when you want to write only a brief summary for each construct.</span></span>

<span data-ttu-id="95d3e-122">批註會在檔準備期間編碼為 XML，因此 `<` `>` 不需要將字元（如和）編碼 `&` 。</span><span class="sxs-lookup"><span data-stu-id="95d3e-122">The comment is encoded to XML during documentation preparation, so characters such as `<`, `>` and `&` need not be escaped.</span></span> <span data-ttu-id="95d3e-123">如果您未明確指定摘要標記，則不應指定 **其他標記，** 例如 **param** 或傳回標記。</span><span class="sxs-lookup"><span data-stu-id="95d3e-123">If you don't specify a summary tag explicitly, you should not specify other tags, such as **param** or **returns** tags.</span></span>

<span data-ttu-id="95d3e-124">下列範例顯示不含 XML 標記的替代方法。</span><span class="sxs-lookup"><span data-stu-id="95d3e-124">The following example shows the alternative method, without XML tags.</span></span> <span data-ttu-id="95d3e-125">在此範例中，批註中的整個文字都會被視為摘要。</span><span class="sxs-lookup"><span data-stu-id="95d3e-125">In this example, the entire text in the comment is considered a summary.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="comments-with-xml-tags"></a><span data-ttu-id="95d3e-126">具有 XML 標記的批註</span><span class="sxs-lookup"><span data-stu-id="95d3e-126">Comments with XML tags</span></span>

<span data-ttu-id="95d3e-127">如果批註主體的開頭是 `<` (一般 `<summary>`) 則會使用 xml 標記將它視為 xml 格式的批註主體。</span><span class="sxs-lookup"><span data-stu-id="95d3e-127">If a comment body begins with `<` (normally `<summary>`) then it is treated as an XML formatted comment body using XML tags.</span></span> <span data-ttu-id="95d3e-128">第二個可讓您指定簡短摘要的個別附注、其他備註、每個參數的檔、類型參數和所擲回的例外狀況，以及傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="95d3e-128">This second enables you to specify separate notes for a short summary, additional remarks, documentation for each parameter and type parameter and exceptions thrown, and a description of the return value.</span></span>

<span data-ttu-id="95d3e-129">以下是簽章檔案中的一般 XML 檔批註：</span><span class="sxs-lookup"><span data-stu-id="95d3e-129">The following is a typical XML documentation comment in a signature file:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="recommended-tags"></a><span data-ttu-id="95d3e-130">建議的標記</span><span class="sxs-lookup"><span data-stu-id="95d3e-130">Recommended Tags</span></span>

<span data-ttu-id="95d3e-131">如果您使用 XML 標記，下表描述 F # XML 程式碼批註中所識別的外部標記。</span><span class="sxs-lookup"><span data-stu-id="95d3e-131">If you are using XML tags, the following table describes the outer tags recognized in F# XML code comments.</span></span>

| <span data-ttu-id="95d3e-132">標記語法</span><span class="sxs-lookup"><span data-stu-id="95d3e-132">Tag syntax</span></span>                                  | <span data-ttu-id="95d3e-133">Description</span><span class="sxs-lookup"><span data-stu-id="95d3e-133">Description</span></span> |
|---------------------------------------------|-----------|
| <span data-ttu-id="95d3e-134">`<summary>`**_文本_**`</summary>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-134">`<summary>`**_text_**`</summary>`</span></span>           | <span data-ttu-id="95d3e-135">指定 *文字* 是程式元素的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="95d3e-135">Specifies that *text* is a brief description of the program element.</span></span> <span data-ttu-id="95d3e-136">描述通常是一或兩個句子。</span><span class="sxs-lookup"><span data-stu-id="95d3e-136">The description is usually one or two sentences.</span></span>|
| <span data-ttu-id="95d3e-137">`<remarks>`**_文本_**`</remarks>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-137">`<remarks>`**_text_**`</remarks>`</span></span>           | <span data-ttu-id="95d3e-138">指定 *文字* 包含程式元素的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="95d3e-138">Specifies that *text* contains supplementary information about the program element.</span></span>|
| <span data-ttu-id="95d3e-139">`<param name="`**_名稱_** `">`**_描述_**`</param>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-139">`<param name="`**_name_**`">`**_description_**`</param>`</span></span> | <span data-ttu-id="95d3e-140">指定函數或方法參數的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="95d3e-140">Specifies the name and description for a function or method parameter.</span></span>|
| <span data-ttu-id="95d3e-141">`<typeparam name="`**_名稱_** `">`**_描述_**`</typeparam>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-141">`<typeparam name="`**_name_**`">`**_description_**`</typeparam>`</span></span> | <span data-ttu-id="95d3e-142">指定型別參數的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="95d3e-142">Specifies the name and description for a type parameter.</span></span>|
| <span data-ttu-id="95d3e-143">`<returns>`**_文本_**`</returns>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-143">`<returns>`**_text_**`</returns>`</span></span>           | <span data-ttu-id="95d3e-144">指定 *文字* 描述函數或方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="95d3e-144">Specifies that *text* describes the return value of a function or method.</span></span>|
| <span data-ttu-id="95d3e-145">`<exception cref="`**_類型_** `">`**_描述_**`</exception>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-145">`<exception cref="`**_type_**`">`**_description_**`</exception>`</span></span> |<span data-ttu-id="95d3e-146">指定可以產生的例外狀況類型，以及擲回它的情況。</span><span class="sxs-lookup"><span data-stu-id="95d3e-146">Specifies the type of exception that can be generated and the circumstances under which it is thrown.</span></span>|
| <span data-ttu-id="95d3e-147">`<seealso cref="`**_參考_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-147">`<seealso cref="`**_reference_**`"/>`</span></span>      | <span data-ttu-id="95d3e-148">指定另一種類型之檔的 [另一個] 連結。</span><span class="sxs-lookup"><span data-stu-id="95d3e-148">Specifies a See Also link to the documentation for another type.</span></span> <span data-ttu-id="95d3e-149">*參考* 是 XML 檔檔案中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="95d3e-149">The *reference* is the name as it appears in the XML documentation file.</span></span> <span data-ttu-id="95d3e-150">另請參閱檔頁面底部的連結。</span><span class="sxs-lookup"><span data-stu-id="95d3e-150">See Also links usually appear at the bottom of a documentation page.</span></span>|

<span data-ttu-id="95d3e-151">下表描述在 [描述] 區段內使用的標記：</span><span class="sxs-lookup"><span data-stu-id="95d3e-151">The following table describes the tags for use inside description sections:</span></span>

| <span data-ttu-id="95d3e-152">標記語法</span><span class="sxs-lookup"><span data-stu-id="95d3e-152">Tag syntax</span></span>                                | <span data-ttu-id="95d3e-153">Description</span><span class="sxs-lookup"><span data-stu-id="95d3e-153">Description</span></span> |
|-------------------------------------------|-------------|
| <span data-ttu-id="95d3e-154">`<para>`**_文本_**`</para>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-154">`<para>`**_text_**`</para>`</span></span>               | <span data-ttu-id="95d3e-155">指定文欄位落。</span><span class="sxs-lookup"><span data-stu-id="95d3e-155">Specifies a paragraph of text.</span></span> <span data-ttu-id="95d3e-156">這是用來分隔 **備註** 標記內的文字。</span><span class="sxs-lookup"><span data-stu-id="95d3e-156">This is used to separate text inside the **remarks** tag.</span></span>|
| <span data-ttu-id="95d3e-157">`<code>`**_文本_**`</code>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-157">`<code>`**_text_**`</code>`</span></span>               | <span data-ttu-id="95d3e-158">指定 *文字* 是多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="95d3e-158">Specifies that *text* is multiple lines of code.</span></span> <span data-ttu-id="95d3e-159">檔產生器可以使用這個標記，以適用于程式碼的字型來顯示文字。</span><span class="sxs-lookup"><span data-stu-id="95d3e-159">This tag can be used by documentation generators to display text in a font that is appropriate for code.</span></span>|
| <span data-ttu-id="95d3e-160">`<paramref name="`**_名字_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-160">`<paramref name="`**_name_**`"/>`</span></span>         | <span data-ttu-id="95d3e-161">指定相同檔批註中的參數參考。</span><span class="sxs-lookup"><span data-stu-id="95d3e-161">Specifies a reference to a parameter in the same documentation comment.</span></span>|
| <span data-ttu-id="95d3e-162">`<typeparamref name="`**_名字_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-162">`<typeparamref name="`**_name_**`"/>`</span></span>     | <span data-ttu-id="95d3e-163">在相同的檔批註中指定類型參數的參考。</span><span class="sxs-lookup"><span data-stu-id="95d3e-163">Specifies a reference to a type parameter in the same documentation comment.</span></span>|
| <span data-ttu-id="95d3e-164">`<c>`**_文本_**`</c>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-164">`<c>`**_text_**`</c>`</span></span>                     | <span data-ttu-id="95d3e-165">指定 *文字* 為內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="95d3e-165">Specifies that *text* is inline code.</span></span> <span data-ttu-id="95d3e-166">檔產生器可以使用這個標記，以適用于程式碼的字型來顯示文字。</span><span class="sxs-lookup"><span data-stu-id="95d3e-166">This tag can be used by documentation generators to display text in a font that is appropriate for code.</span></span>|
| <span data-ttu-id="95d3e-167">`<see cref="`**_參考_** `">`**_文字_**`</see>`</span><span class="sxs-lookup"><span data-stu-id="95d3e-167">`<see cref="`**_reference_**`">`**_text_**`</see>`</span></span> | <span data-ttu-id="95d3e-168">指定另一個程式元素的內嵌連結。</span><span class="sxs-lookup"><span data-stu-id="95d3e-168">Specifies an inline link to another program element.</span></span> <span data-ttu-id="95d3e-169">*參考* 是 XML 檔檔案中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="95d3e-169">The *reference* is the name as it appears in the XML documentation file.</span></span> <span data-ttu-id="95d3e-170">*文字* 是連結中所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="95d3e-170">The *text* is the text shown in the link.</span></span>|

### <a name="user-defined-tags"></a><span data-ttu-id="95d3e-171">使用者定義標記</span><span class="sxs-lookup"><span data-stu-id="95d3e-171">User-defined tags</span></span>

<span data-ttu-id="95d3e-172">先前的標記代表 F # 編譯器和一般 F # 編輯器工具所能辨識的標記。</span><span class="sxs-lookup"><span data-stu-id="95d3e-172">The previous tags represent those that are recognized by the F# compiler and typical F# editor tooling.</span></span> <span data-ttu-id="95d3e-173">不過，使用者可以定義自己的標記。</span><span class="sxs-lookup"><span data-stu-id="95d3e-173">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="95d3e-174">Fsdocs 之類的工具可為您提供額外標記的支援 [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md) 。</span><span class="sxs-lookup"><span data-stu-id="95d3e-174">Tools like fsdocs bring support for extra tags like [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md).</span></span>
<span data-ttu-id="95d3e-175">自訂或內部文件產生工具也可以與標準標記搭配使用，而且可以支援從 HTML 到 PDF 的多個輸出格式。</span><span class="sxs-lookup"><span data-stu-id="95d3e-175">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="compile-time-checking"></a><span data-ttu-id="95d3e-176">編譯時間檢查</span><span class="sxs-lookup"><span data-stu-id="95d3e-176">Compile-time checking</span></span>

<span data-ttu-id="95d3e-177">當 `--warnon:3390` 啟用時，編譯器會驗證 XML 的語法和和標記中參考的參數 `<param>` `<paramref>` 。</span><span class="sxs-lookup"><span data-stu-id="95d3e-177">When `--warnon:3390` is enabled, the compiler verifies the syntax of the XML and the parameters referred to in `<param>` and `<paramref>` tags.</span></span>

## <a name="documenting-f-constructs"></a><span data-ttu-id="95d3e-178">記載 F # 結構</span><span class="sxs-lookup"><span data-stu-id="95d3e-178">Documenting F# Constructs</span></span>

<span data-ttu-id="95d3e-179">F # 結構（例如模組、成員、聯集案例和記錄欄位）會在 `///` 其宣告之前立即以批註記載。</span><span class="sxs-lookup"><span data-stu-id="95d3e-179">F# constructs such as modules, members, union cases and record fields are documented by a `///` comment immediately prior to their declaration.</span></span>
<span data-ttu-id="95d3e-180">如有需要，會在 `///` 引數清單之前提供批註，以記載類別的隱含函式。</span><span class="sxs-lookup"><span data-stu-id="95d3e-180">If needed, implicit constructors of classes are documented by giving a `///` comment prior to the argument list.</span></span> <span data-ttu-id="95d3e-181">例如：</span><span class="sxs-lookup"><span data-stu-id="95d3e-181">For example:</span></span>

```fsharp
/// This is the type
type SomeType
      /// This is the implicit constructor
      (a: int, b: int) =

    /// This is the member
    member _.Sum() = a + b
```

## <a name="limitations"></a><span data-ttu-id="95d3e-182">限制</span><span class="sxs-lookup"><span data-stu-id="95d3e-182">Limitations</span></span>

<span data-ttu-id="95d3e-183">C # 中不支援 XML 檔的某些功能（c # 和其他 .NET 語言）。</span><span class="sxs-lookup"><span data-stu-id="95d3e-183">Some features of XML documentation in C# and other .NET languages are not supported in C#.</span></span>

- <span data-ttu-id="95d3e-184">例如，在 F # 中，交互參考必須使用對應符號的完整 XML 簽章 `cref="T:System.Console"` 。</span><span class="sxs-lookup"><span data-stu-id="95d3e-184">In F#, cross-references must use the full XML signature of the corresponding symbol, for example `cref="T:System.Console"`.</span></span>
  <span data-ttu-id="95d3e-185">簡單的 c # 樣式交互參考（例如） `cref="Console"` 不會針對完整的 XML 簽章進行詳細檢查，而且 F # 編譯器不會檢查這些元素。</span><span class="sxs-lookup"><span data-stu-id="95d3e-185">Simple C#-style cross-references such as `cref="Console"` are not elaborated to full XML signatures and these elements are not checked by the F# compiler.</span></span> <span data-ttu-id="95d3e-186">某些檔工具可能會允許後續處理使用這些交叉參考，但是應該使用完整簽章。</span><span class="sxs-lookup"><span data-stu-id="95d3e-186">Some documentation tooling may allow the use of these cross-references by subsequent processing, but the full signatures should be used.</span></span>
  
- <span data-ttu-id="95d3e-187">`<include>` `<inheritdoc>` F # 編譯器不支援這些標記。</span><span class="sxs-lookup"><span data-stu-id="95d3e-187">The tags `<include>`, `<inheritdoc>` are not supported by the F# compiler.</span></span> <span data-ttu-id="95d3e-188">如果使用它們，則不會提供任何錯誤，但會直接複製到產生的檔檔，而不會影響所產生的檔。</span><span class="sxs-lookup"><span data-stu-id="95d3e-188">No error is given if they are used, but they are simply copied to the generated documentation file without otherwise affecting the documentation generated.</span></span>

- <span data-ttu-id="95d3e-189">F # 編譯器不會檢查交互參考，即使使用時也一樣 `-warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="95d3e-189">Cross-references are not checked by the F# compiler, even when `-warnon:3390` is used.</span></span>

- <span data-ttu-id="95d3e-190">`<typeparam>` `<typeparamref>` F # 編譯器不會檢查標記中使用的名稱，即使使用時也不會檢查 `--warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="95d3e-190">The names used in the tags `<typeparam>` and `<typeparamref>` are not checked by the F# compiler, even when `--warnon:3390` is used.</span></span>

- <span data-ttu-id="95d3e-191">如果遺漏檔，則不會提供任何警告，即使使用時也不會出現 `--warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="95d3e-191">No warnings are given if documentation is missing, even when `--warnon:3390` is used.</span></span>

## <a name="recommendations"></a><span data-ttu-id="95d3e-192">建議</span><span class="sxs-lookup"><span data-stu-id="95d3e-192">Recommendations</span></span>

<span data-ttu-id="95d3e-193">有許多原因，建議您記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="95d3e-193">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="95d3e-194">以下是一些最佳作法、一般使用案例，以及在 F # 程式碼中使用 XML 檔標記時應該知道的事項。</span><span class="sxs-lookup"><span data-stu-id="95d3e-194">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your F# code.</span></span>

- <span data-ttu-id="95d3e-195">`--warnon:3390`在您的程式碼中啟用選項，以協助確保您的 xml 檔是有效的 xml。</span><span class="sxs-lookup"><span data-stu-id="95d3e-195">Enable the option `--warnon:3390` in your code to help ensure your XML documentation is valid XML.</span></span>

- <span data-ttu-id="95d3e-196">請考慮新增簽章檔案，以便將大型 XML 檔批註與您的實作分開。</span><span class="sxs-lookup"><span data-stu-id="95d3e-196">Consider adding signature files to separate long XML documentation comments from your implementation.</span></span>

- <span data-ttu-id="95d3e-197">為保持一致性，應該記錄所有公開可見的類型和其成員。</span><span class="sxs-lookup"><span data-stu-id="95d3e-197">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="95d3e-198">如果您必須執行它，則請執行。</span><span class="sxs-lookup"><span data-stu-id="95d3e-198">If you must do it, do it all.</span></span>

- <span data-ttu-id="95d3e-199">最小的模組、類型和其成員應具有純文字 `///` 批註或 `<summary>` 標記。</span><span class="sxs-lookup"><span data-stu-id="95d3e-199">At a bare minimum, modules, types and their members should have a plain `///` comment or `<summary>` tag.</span></span> <span data-ttu-id="95d3e-200">這會顯示在 F # 編輯工具的自動完成工具提示視窗中。</span><span class="sxs-lookup"><span data-stu-id="95d3e-200">This will show in an autocompletion tooltip window in F# editing tools.</span></span>

- <span data-ttu-id="95d3e-201">應該使用結尾為句號的完整句子來撰寫文件文字。</span><span class="sxs-lookup"><span data-stu-id="95d3e-201">Documentation text should be written using complete sentences ending with full stops.</span></span>

## <a name="see-also"></a><span data-ttu-id="95d3e-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95d3e-202">See also</span></span>

- <span data-ttu-id="95d3e-203">C [# XML 檔批註 &#40;c&#35; 程式設計指南&#41;](../../csharp/programming-guide/xmldoc/index.md)。</span><span class="sxs-lookup"><span data-stu-id="95d3e-203">[C# XML Documentation Comments &#40;C&#35; Programming Guide&#41;](../../csharp/programming-guide/xmldoc/index.md).</span></span>
- [<span data-ttu-id="95d3e-204">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="95d3e-204">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="95d3e-205">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="95d3e-205">Compiler Options</span></span>](compiler-options.md)
