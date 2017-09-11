---
title: "建議的文件註解 (Visual Basic) 的 XML 標記 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e4a6c3128a69e8d666d44882ef3eac9f9a31a51a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="9fc21-102">建議可用於文件註解的 XML 標記 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fc21-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="9fc21-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器可以處理 XML 檔案的程式碼中的文件註解。</span><span class="sxs-lookup"><span data-stu-id="9fc21-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="9fc21-104">您可以使用其他工具來處理文件的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="9fc21-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="9fc21-105">XML 註解不能使用程式碼建構，例如型別和型別成員。</span><span class="sxs-lookup"><span data-stu-id="9fc21-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="9fc21-106">部分型別，如類型只有一個部分可以有 XML 註解，雖然其成員的註解不受限制。</span><span class="sxs-lookup"><span data-stu-id="9fc21-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fc21-107">文件註解不能套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="9fc21-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="9fc21-108">原因是，一個命名空間可以跨越多個組件，且並非所有的組件必須載入一次。</span><span class="sxs-lookup"><span data-stu-id="9fc21-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="9fc21-109">編譯器會處理任何有效的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="9fc21-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="9fc21-110">下列標記會提供使用者文件中的常用的功能。</span><span class="sxs-lookup"><span data-stu-id="9fc21-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="9fc21-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="9fc21-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="9fc21-112">\<程式碼 ></span><span class="sxs-lookup"><span data-stu-id="9fc21-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="9fc21-113">\<範例 ></span><span class="sxs-lookup"><span data-stu-id="9fc21-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="9fc21-114">[\<例外狀況 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9fc21-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="9fc21-115">[\<包含 >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9fc21-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="9fc21-116">\<list></span><span class="sxs-lookup"><span data-stu-id="9fc21-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="9fc21-117">\<並行 ></span><span class="sxs-lookup"><span data-stu-id="9fc21-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="9fc21-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9fc21-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="9fc21-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="9fc21-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="9fc21-120">[\<權限 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9fc21-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="9fc21-121">\<註解 ></span><span class="sxs-lookup"><span data-stu-id="9fc21-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="9fc21-122">\<傳回 ></span><span class="sxs-lookup"><span data-stu-id="9fc21-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="9fc21-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9fc21-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="9fc21-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9fc21-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="9fc21-125">\<摘要 ></span><span class="sxs-lookup"><span data-stu-id="9fc21-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="9fc21-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9fc21-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="9fc21-127">\<值 ></span><span class="sxs-lookup"><span data-stu-id="9fc21-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="9fc21-128">(<sup>1</sup>編譯器會驗證語法。)</span><span class="sxs-lookup"><span data-stu-id="9fc21-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fc21-129">如果您想要出現在文件註解文字的角括號時，使用`<`和`>`。</span><span class="sxs-lookup"><span data-stu-id="9fc21-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="9fc21-130">例如，字串`"<text in angle brackets>"`會顯示為`<text in angle``brackets>`。</span><span class="sxs-lookup"><span data-stu-id="9fc21-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc21-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fc21-131">See Also</span></span>  
 <span data-ttu-id="9fc21-132">[記錄與 XML 程式碼](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="9fc21-132">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="9fc21-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span><span class="sxs-lookup"><span data-stu-id="9fc21-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span></span>  
<span data-ttu-id="9fc21-134"> [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="9fc21-134"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span></span>
