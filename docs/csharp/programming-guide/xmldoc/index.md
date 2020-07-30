---
title: 'XML 檔批註-c # 程式設計指南'
description: 瞭解 XML 檔批註。 您可以藉由在特殊批註欄位中包含 XML 元素，來建立程式碼的檔。
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: fbdeb53331d9fc63d24a3322ea13863d7c0a3630
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381875"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="a48f5-104">XML 檔批註（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="a48f5-104">XML documentation comments (C# programming guide)</span></span>

<span data-ttu-id="a48f5-105">在 c # 中，您可以建立程式碼的檔，方法是將原始程式碼中的 XML 專案（以三個斜線表示）直接包含在程式碼區塊中（例如，在批註所參考的程式碼區塊之前）。</span><span class="sxs-lookup"><span data-stu-id="a48f5-105">In C#, you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example.</span></span>

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

<span data-ttu-id="a48f5-106">當您使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)選項進行編譯時，編譯器會搜尋原始程式碼中的所有 xml 標記，並建立 xml 檔檔。</span><span class="sxs-lookup"><span data-stu-id="a48f5-106">When you compile with the [-doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="a48f5-107">若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [DocFX](https://dotnet.github.io/docfx/) 或 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具。</span><span class="sxs-lookup"><span data-stu-id="a48f5-107">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="a48f5-108">若要參考 XML 項目，例如，您的函式處理要在 XML 文件註解中描述的特定 XML 項目，您可以使用標準引號機制 (`<` 和 `>`)。</span><span class="sxs-lookup"><span data-stu-id="a48f5-108">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="a48f5-109">若要參照程式碼參考 (`cref`) 項目中的泛型識別碼，您可以使用逸出字元 (例如 `cref="List&lt;T&gt;"`) 或大括號 (`cref="List{T}"`)。</span><span class="sxs-lookup"><span data-stu-id="a48f5-109">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="a48f5-110">視為特殊案例的情形是，編譯器將大括號剖析為角括號，如此在參考泛型識別項時，文件註解撰寫起來就變得不那麼複雜。</span><span class="sxs-lookup"><span data-stu-id="a48f5-110">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>

> [!NOTE]
> <span data-ttu-id="a48f5-111">XML 文件註解並不是中繼資料，這些註解不會包含在編譯的組件內，因此不能透過反映存取。</span><span class="sxs-lookup"><span data-stu-id="a48f5-111">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a48f5-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="a48f5-112">In this section</span></span>

- [<span data-ttu-id="a48f5-113">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="a48f5-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

- [<span data-ttu-id="a48f5-114">處理 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="a48f5-114">Processing the XML file</span></span>](./processing-the-xml-file.md)

- [<span data-ttu-id="a48f5-115">文件標籤的分隔符號</span><span class="sxs-lookup"><span data-stu-id="a48f5-115">Delimiters for documentation tags</span></span>](./delimiters-for-documentation-tags.md)

- [<span data-ttu-id="a48f5-116">如何使用 XML 文件功能</span><span class="sxs-lookup"><span data-stu-id="a48f5-116">How to use the XML documentation features</span></span>](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a><span data-ttu-id="a48f5-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="a48f5-117">Related sections</span></span>

<span data-ttu-id="a48f5-118">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="a48f5-118">For more information, see:</span></span>

- [<span data-ttu-id="a48f5-119">-doc （處理檔批註）</span><span class="sxs-lookup"><span data-stu-id="a48f5-119">-doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a><span data-ttu-id="a48f5-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a48f5-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a48f5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a48f5-121">See also</span></span>

- [<span data-ttu-id="a48f5-122">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a48f5-122">C# Programming Guide</span></span>](../index.md)
