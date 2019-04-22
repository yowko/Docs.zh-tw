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
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814936"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="a9547-102">建議可用於文件註解的 XML 標記 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9547-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="a9547-103">Visual Basic 編譯器可以處理 XML 檔案的程式碼中的文件註解。</span><span class="sxs-lookup"><span data-stu-id="a9547-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="a9547-104">您可以使用其他工具來處理文件的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="a9547-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="a9547-105">XML 註解不能使用的程式碼建構，例如類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="a9547-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="a9547-106">部分型別，只有一個部分的型別可以有 XML 註解，雖然沒有註解成員沒有限制。</span><span class="sxs-lookup"><span data-stu-id="a9547-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9547-107">文件註解不能套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="a9547-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="a9547-108">原因會是一個命名空間可以跨數個組件，而且並非所有的組件需要載入一次。</span><span class="sxs-lookup"><span data-stu-id="a9547-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="a9547-109">編譯器會處理任何標記，來有效的 XML。</span><span class="sxs-lookup"><span data-stu-id="a9547-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="a9547-110">下列標記提供使用者文件中的常用的功能。</span><span class="sxs-lookup"><span data-stu-id="a9547-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="a9547-111">\<c></span><span class="sxs-lookup"><span data-stu-id="a9547-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="a9547-112">\<code></span><span class="sxs-lookup"><span data-stu-id="a9547-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="a9547-113">\<example></span><span class="sxs-lookup"><span data-stu-id="a9547-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="a9547-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a9547-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="a9547-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a9547-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="a9547-116">\<list></span><span class="sxs-lookup"><span data-stu-id="a9547-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="a9547-117">\<para></span><span class="sxs-lookup"><span data-stu-id="a9547-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="a9547-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a9547-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="a9547-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="a9547-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="a9547-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a9547-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="a9547-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="a9547-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="a9547-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="a9547-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="a9547-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a9547-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="a9547-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a9547-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="a9547-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="a9547-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="a9547-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a9547-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="a9547-127">\<value></span><span class="sxs-lookup"><span data-stu-id="a9547-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="a9547-128">(<sup>1</sup>編譯器會驗證語法。)</span><span class="sxs-lookup"><span data-stu-id="a9547-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9547-129">如果您想要括弧出現在文件註解文字中，使用`&lt;`和`&gt;`。</span><span class="sxs-lookup"><span data-stu-id="a9547-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="a9547-130">例如，字串`"&lt;text in angle brackets&gt;"`會顯示為`<text in angle brackets>`。</span><span class="sxs-lookup"><span data-stu-id="a9547-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9547-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9547-131">See also</span></span>

- [<span data-ttu-id="a9547-132">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="a9547-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="a9547-133">/doc</span><span class="sxs-lookup"><span data-stu-id="a9547-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="a9547-134">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="a9547-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
