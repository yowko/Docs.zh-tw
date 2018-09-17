---
title: XML 文件註解 (C# 程式設計手冊)
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
ms.openlocfilehash: ab4f8fae748455f96ca5ea0255658cc76dd14f97
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45677652"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="cb513-102">XML 文件註解 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cb513-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="cb513-103">在 Visual C# 中，您可以加入程式碼的文件，加入的方法是在原始程式碼中，於註解所參考程式碼區塊之前的特殊註解欄位 (以三個斜線表示) 中加入 XML 項目，例如：</span><span class="sxs-lookup"><span data-stu-id="cb513-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="cb513-104">當您使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 選項編譯時，編譯器將會搜尋原始程式碼中的所有 XML 標記，然後建立 XML 文件檔。</span><span class="sxs-lookup"><span data-stu-id="cb513-104">When you compile with the [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="cb513-105">若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具。</span><span class="sxs-lookup"><span data-stu-id="cb513-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="cb513-106">若要參考 XML 項目，例如，您的函式處理要在 XML 文件註解中描述的特定 XML 項目，您可以使用標準引號機制 (`<` 和 `>`)。</span><span class="sxs-lookup"><span data-stu-id="cb513-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="cb513-107">若要參照程式碼參考 (`cref`) 項目中的泛型識別碼，您可以使用逸出字元 (例如 `cref="List&lt;T&gt;"`) 或大括號 (`cref="List{T}"`)。</span><span class="sxs-lookup"><span data-stu-id="cb513-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="cb513-108">視為特殊案例的情形是，編譯器將大括號剖析為角括號，如此在參考泛型識別項時，文件註解撰寫起來就變得不那麼複雜。</span><span class="sxs-lookup"><span data-stu-id="cb513-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb513-109">XML 文件註解並不是中繼資料，這些註解不會包含在編譯的組件內，因此不能透過反映存取。</span><span class="sxs-lookup"><span data-stu-id="cb513-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb513-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="cb513-110">In This Section</span></span>  
  
-   [<span data-ttu-id="cb513-111">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="cb513-111">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="cb513-112">處理 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="cb513-112">Processing the XML File</span></span>](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="cb513-113">文件標籤的分隔符號</span><span class="sxs-lookup"><span data-stu-id="cb513-113">Delimiters for Documentation Tags</span></span>](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [<span data-ttu-id="cb513-114">如何：使用 XML 文件功能</span><span class="sxs-lookup"><span data-stu-id="cb513-114">How to: Use the XML Documentation Features</span></span>](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="cb513-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="cb513-115">Related Sections</span></span>  
 <span data-ttu-id="cb513-116">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb513-116">For more information, see:</span></span>  
  
-   [<span data-ttu-id="cb513-117">/doc (處理文件註解)</span><span class="sxs-lookup"><span data-stu-id="cb513-117">/doc (Process Documentation Comments)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="cb513-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="cb513-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb513-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb513-119">See Also</span></span>

- [<span data-ttu-id="cb513-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cb513-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
