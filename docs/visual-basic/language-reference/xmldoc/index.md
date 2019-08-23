---
title: 建議可用於文件註解的 XML 標記 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913510"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="ac5b5-102">建議可用於文件註解的 XML 標記 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac5b5-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="ac5b5-103">Visual Basic 編譯器可以將程式碼中的檔批註處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="ac5b5-104">您可以使用其他工具, 將 XML 檔案處理成檔。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="ac5b5-105">程式碼結構 (例如類型和類型成員) 允許 XML 批註。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="ac5b5-106">對於部分類型, 只有類型的一個部分可以有 XML 批註, 雖然對其成員的批註沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac5b5-107">檔批註無法套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="ac5b5-108">原因是一個命名空間可以跨越數個元件, 而不是所有的元件都必須同時載入。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="ac5b5-109">編譯器會處理任何有效的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="ac5b5-110">下列標記提供使用者檔中常用的功能。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="ac5b5-111">\<c></span><span class="sxs-lookup"><span data-stu-id="ac5b5-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="ac5b5-112">\<code></span><span class="sxs-lookup"><span data-stu-id="ac5b5-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="ac5b5-113">\<example></span><span class="sxs-lookup"><span data-stu-id="ac5b5-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="ac5b5-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac5b5-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="ac5b5-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac5b5-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="ac5b5-116">\<list></span><span class="sxs-lookup"><span data-stu-id="ac5b5-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="ac5b5-117">\<para></span><span class="sxs-lookup"><span data-stu-id="ac5b5-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="ac5b5-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac5b5-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="ac5b5-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="ac5b5-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="ac5b5-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac5b5-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="ac5b5-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="ac5b5-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="ac5b5-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="ac5b5-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="ac5b5-123">請參閱 > <sup>1</sup> [ \< ](../../../visual-basic/language-reference/xmldoc/see.md)</span><span class="sxs-lookup"><span data-stu-id="ac5b5-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="ac5b5-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac5b5-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="ac5b5-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="ac5b5-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="ac5b5-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ac5b5-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="ac5b5-127">\<value></span><span class="sxs-lookup"><span data-stu-id="ac5b5-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="ac5b5-128">(<sup>1</sup>編譯器會驗證語法)。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac5b5-129">如果您想要在檔批註的文字中出現角括弧, 請使用`&lt;`和`&gt;`。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="ac5b5-130">例如, 字串`"&lt;text in angle brackets&gt;"`會顯示為`<text in angle brackets>`。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5b5-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac5b5-131">See also</span></span>

- [<span data-ttu-id="ac5b5-132">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="ac5b5-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="ac5b5-133">/doc</span><span class="sxs-lookup"><span data-stu-id="ac5b5-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="ac5b5-134">如何：建立 XML 檔</span><span class="sxs-lookup"><span data-stu-id="ac5b5-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
