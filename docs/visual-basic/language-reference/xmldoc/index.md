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
ms.openlocfilehash: 3b2dec4224006d35fb9add11e170b9dcbeeafcf3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881277"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="9e104-102">建議可用於文件註解的 XML 標記 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e104-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="9e104-103">Visual Basic 編譯器可以處理 XML 檔案的程式碼中的文件註解。</span><span class="sxs-lookup"><span data-stu-id="9e104-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="9e104-104">您可以使用其他工具來處理文件的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="9e104-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="9e104-105">XML 註解不能使用的程式碼建構，例如類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="9e104-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="9e104-106">部分型別，只有一個部分的型別可以有 XML 註解，雖然沒有註解成員沒有限制。</span><span class="sxs-lookup"><span data-stu-id="9e104-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e104-107">文件註解不能套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="9e104-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="9e104-108">原因會是一個命名空間可以跨數個組件，而且並非所有的組件需要載入一次。</span><span class="sxs-lookup"><span data-stu-id="9e104-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="9e104-109">編譯器會處理任何標記，來有效的 XML。</span><span class="sxs-lookup"><span data-stu-id="9e104-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="9e104-110">下列標記提供使用者文件中的常用的功能。</span><span class="sxs-lookup"><span data-stu-id="9e104-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="9e104-111">\<c></span><span class="sxs-lookup"><span data-stu-id="9e104-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="9e104-112">\<code></span><span class="sxs-lookup"><span data-stu-id="9e104-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="9e104-113">\<example></span><span class="sxs-lookup"><span data-stu-id="9e104-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="9e104-114">[\<例外狀況 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e104-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="9e104-115">[\<包含 >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e104-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e104-116">\<list></span><span class="sxs-lookup"><span data-stu-id="9e104-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="9e104-117">\<para></span><span class="sxs-lookup"><span data-stu-id="9e104-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="9e104-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e104-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e104-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="9e104-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="9e104-120">[\<權限 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e104-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e104-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="9e104-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="9e104-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="9e104-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="9e104-123">[\<請參閱 >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e104-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="9e104-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e104-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e104-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="9e104-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="9e104-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e104-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e104-127">\<value></span><span class="sxs-lookup"><span data-stu-id="9e104-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="9e104-128">(<sup>1</sup>編譯器會驗證語法。)</span><span class="sxs-lookup"><span data-stu-id="9e104-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e104-129">如果您想要括弧出現在文件註解文字中，使用`&lt;`和`&gt;`。</span><span class="sxs-lookup"><span data-stu-id="9e104-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="9e104-130">例如，字串`"&lt;text in angle brackets&gt;"`會顯示為`<text in angle brackets>`。</span><span class="sxs-lookup"><span data-stu-id="9e104-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e104-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e104-131">See Also</span></span>  
 [<span data-ttu-id="9e104-132">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="9e104-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="9e104-133">/doc</span><span class="sxs-lookup"><span data-stu-id="9e104-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="9e104-134">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="9e104-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
