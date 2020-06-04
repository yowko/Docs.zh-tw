---
title: 建議用於檔批註的 XML 標記
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400095"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="cca1c-102">建議可用於文件註解的 XML 標記 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cca1c-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="cca1c-103">Visual Basic 編譯器可以將程式碼中的檔批註處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="cca1c-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="cca1c-104">您可以使用其他工具，將 XML 檔案處理成檔。</span><span class="sxs-lookup"><span data-stu-id="cca1c-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="cca1c-105">程式碼結構（例如類型和類型成員）允許 XML 批註。</span><span class="sxs-lookup"><span data-stu-id="cca1c-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="cca1c-106">對於部分類型，只有類型的一個部分可以有 XML 批註，雖然對其成員的批註沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="cca1c-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cca1c-107">檔批註無法套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="cca1c-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="cca1c-108">原因是一個命名空間可以跨越數個元件，而不是所有的元件都必須同時載入。</span><span class="sxs-lookup"><span data-stu-id="cca1c-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="cca1c-109">編譯器會處理任何有效的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="cca1c-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="cca1c-110">下列標記提供使用者檔中常用的功能。</span><span class="sxs-lookup"><span data-stu-id="cca1c-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="cca1c-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cca1c-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="cca1c-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cca1c-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="cca1c-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cca1c-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="cca1c-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cca1c-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="cca1c-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cca1c-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="cca1c-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cca1c-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="cca1c-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cca1c-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="cca1c-118">（<sup>1</sup>編譯器會驗證語法）。</span><span class="sxs-lookup"><span data-stu-id="cca1c-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cca1c-119">如果您想要在檔批註的文字中出現角括弧，請使用 `&lt;` 和 `&gt;` 。</span><span class="sxs-lookup"><span data-stu-id="cca1c-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="cca1c-120">例如，字串 `"&lt;text in angle brackets&gt;"` 會顯示為 `<text in angle brackets>` 。</span><span class="sxs-lookup"><span data-stu-id="cca1c-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca1c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cca1c-121">See also</span></span>

- [<span data-ttu-id="cca1c-122">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="cca1c-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="cca1c-123">-doc</span><span class="sxs-lookup"><span data-stu-id="cca1c-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="cca1c-124">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="cca1c-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
