---
title: "XML (Visual Basic) 中內嵌運算式 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
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
ms.openlocfilehash: d24a49f2fa6fd66fe6e4c7724bd4298d65fb7a59
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="30ece-102">XML 中內嵌的運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30ece-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="30ece-103">內嵌的運算式可讓您建立 XML 常值包含在執行階段評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="30ece-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="30ece-104">內嵌運算式的語法是`<%=` `expression` `%>`，這會是相同的語法中使用[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="30ece-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].</span></span>  
  
 <span data-ttu-id="30ece-105">例如，您可以建立的 XML 項目常值，結合使用常值文字內容有內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="30ece-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 <span data-ttu-id="30ece-106">[!code-vb[VbXMLSamples #&27;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="30ece-106">[!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span></span>  
  
 <span data-ttu-id="30ece-107">如果`isbnNumber`包含整數 12345 和`modifiedDate`包含的日期 3/5/2006，此程式碼執行時，值`book`是︰</span><span class="sxs-lookup"><span data-stu-id="30ece-107">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="30ece-108">內嵌的運算式的位置和驗證</span><span class="sxs-lookup"><span data-stu-id="30ece-108">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="30ece-109">內嵌的運算式只可以出現在 XML 常值運算式內的特定位置。</span><span class="sxs-lookup"><span data-stu-id="30ece-109">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="30ece-110">可以傳回型別運算式的運算式位置控制項，以及如何`Nothing`處理。</span><span class="sxs-lookup"><span data-stu-id="30ece-110">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="30ece-111">下表描述允許的位置和內嵌運算式的型別。</span><span class="sxs-lookup"><span data-stu-id="30ece-111">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="30ece-112">常值中的位置</span><span class="sxs-lookup"><span data-stu-id="30ece-112">Location in literal</span></span>|<span data-ttu-id="30ece-113">運算式的型別</span><span class="sxs-lookup"><span data-stu-id="30ece-113">Type of expression</span></span>|<span data-ttu-id="30ece-114">處理`Nothing`</span><span class="sxs-lookup"><span data-stu-id="30ece-114">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="30ece-115">XML 項目名稱</span><span class="sxs-lookup"><span data-stu-id="30ece-115">XML element name</span></span>|<span data-ttu-id="30ece-116"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="30ece-116"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="30ece-117">錯誤</span><span class="sxs-lookup"><span data-stu-id="30ece-117">Error</span></span>|  
|<span data-ttu-id="30ece-118">XML 項目內容</span><span class="sxs-lookup"><span data-stu-id="30ece-118">XML element content</span></span>|<span data-ttu-id="30ece-119">`Object`或陣列`Object`</span><span class="sxs-lookup"><span data-stu-id="30ece-119">`Object` or array of `Object`</span></span>|<span data-ttu-id="30ece-120">略過</span><span class="sxs-lookup"><span data-stu-id="30ece-120">Ignored</span></span>|  
|<span data-ttu-id="30ece-121">XML 項目屬性名稱</span><span class="sxs-lookup"><span data-stu-id="30ece-121">XML element attribute name</span></span>|<span data-ttu-id="30ece-122"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="30ece-122"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="30ece-123">錯誤，除非也是屬性值`Nothing`</span><span class="sxs-lookup"><span data-stu-id="30ece-123">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="30ece-124">XML 項目屬性值</span><span class="sxs-lookup"><span data-stu-id="30ece-124">XML element attribute value</span></span>|`Object`|<span data-ttu-id="30ece-125">略過屬性宣告</span><span class="sxs-lookup"><span data-stu-id="30ece-125">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="30ece-126">XML 項目屬性</span><span class="sxs-lookup"><span data-stu-id="30ece-126">XML element attribute</span></span>|<span data-ttu-id="30ece-127"><xref:System.Xml.Linq.XAttribute>或集合<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="30ece-127"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="30ece-128">略過</span><span class="sxs-lookup"><span data-stu-id="30ece-128">Ignored</span></span>|  
|<span data-ttu-id="30ece-129">XML 文件根項目</span><span class="sxs-lookup"><span data-stu-id="30ece-129">XML document root element</span></span>|<span data-ttu-id="30ece-130"><xref:System.Xml.Linq.XElement>一個<xref:System.Xml.Linq.XElement>物件和任意數目的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件</xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XElement>的集合，或</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="30ece-130"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="30ece-131">略過</span><span class="sxs-lookup"><span data-stu-id="30ece-131">Ignored</span></span>|  
  
-   <span data-ttu-id="30ece-132">XML 項目名稱中內嵌運算式的範例︰</span><span class="sxs-lookup"><span data-stu-id="30ece-132">Example of an embedded expression in an XML element name:</span></span>  
  
     <span data-ttu-id="30ece-133">[!code-vb[VbXMLSamples #&32;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="30ece-133">[!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span></span>  
  
-   <span data-ttu-id="30ece-134">XML 項目的內嵌運算式內容中的範例︰</span><span class="sxs-lookup"><span data-stu-id="30ece-134">Example of an embedded expression in the content of an XML element:</span></span>  
  
     <span data-ttu-id="30ece-135">[!code-vb[VbXMLSamples #&33;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="30ece-135">[!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span></span>  
  
-   <span data-ttu-id="30ece-136">XML 項目屬性名稱中內嵌運算式的範例︰</span><span class="sxs-lookup"><span data-stu-id="30ece-136">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     <span data-ttu-id="30ece-137">[!code-vb[VbXMLSamples #&34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="30ece-137">[!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span></span>  
  
-   <span data-ttu-id="30ece-138">內嵌運算式中的 XML 項目屬性值的範例︰</span><span class="sxs-lookup"><span data-stu-id="30ece-138">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     <span data-ttu-id="30ece-139">[!code-vb[VbXMLSamples #&35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="30ece-139">[!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span></span>  
  
-   <span data-ttu-id="30ece-140">內嵌運算式中的 XML 項目屬性的範例︰</span><span class="sxs-lookup"><span data-stu-id="30ece-140">Example of an embedded expression in an XML element attribute:</span></span>  
  
     <span data-ttu-id="30ece-141">[!code-vb[VbXMLSamples #&36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="30ece-141">[!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span></span>  
  
-   <span data-ttu-id="30ece-142">XML 文件根項目中內嵌運算式的範例︰</span><span class="sxs-lookup"><span data-stu-id="30ece-142">Example of an embedded expression in an XML document root element:</span></span>  
  
     <span data-ttu-id="30ece-143">[!code-vb[VbXMLSamples #&37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="30ece-143">[!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span></span>  
  
 <span data-ttu-id="30ece-144">如果您啟用`Option Strict`，編譯器會檢查每個內嵌的運算式的型別擴展的必要型別。</span><span class="sxs-lookup"><span data-stu-id="30ece-144">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="30ece-145">唯一的例外狀況是在程式碼執行時，系統驗證的 XML 文件的根項目。</span><span class="sxs-lookup"><span data-stu-id="30ece-145">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="30ece-146">如果您編譯而不需`Option Strict`，您可以將內嵌運算式的型別`Object`和執行階段就會驗證它們的型別。</span><span class="sxs-lookup"><span data-stu-id="30ece-146">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="30ece-147">選擇性的內容的位置內嵌運算式，包含`Nothing`會被忽略。</span><span class="sxs-lookup"><span data-stu-id="30ece-147">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="30ece-148">這表示您不需要檢查的項目內容，屬性值，而且陣列項目不`Nothing`使用 XML 常值之前。</span><span class="sxs-lookup"><span data-stu-id="30ece-148">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="30ece-149">必要值，例如項目和屬性名稱不能`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="30ece-149">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="30ece-150">如需特定類型的常值中使用內嵌的運算式的詳細資訊，請參閱[XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)， [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="30ece-150">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="30ece-151">範圍規則</span><span class="sxs-lookup"><span data-stu-id="30ece-151">Scoping Rules</span></span>  
 <span data-ttu-id="30ece-152">編譯器會將每個 XML 常值轉換成適當的常值類型的建構函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="30ece-152">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="30ece-153">建構函式，會將常值的內容和內嵌的運算式，在 XML 常值中傳遞做為引數。</span><span class="sxs-lookup"><span data-stu-id="30ece-153">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="30ece-154">這表示所有[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]用於 XML 常值的程式設計項目也是用於內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="30ece-154">This means that all [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="30ece-155">在 XML 常值，您可存取的 XML 命名空間前置詞宣告`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="30ece-155">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="30ece-156">您可以宣告新的 XML 命名空間前置詞，或遮蔽現有 XML 命名空間前置詞，在項目中使用`xmlns`屬性。</span><span class="sxs-lookup"><span data-stu-id="30ece-156">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="30ece-157">內嵌的運算式中的 XML 常值的子節點，該項目的但不是使用新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="30ece-157">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30ece-158">當您宣告 XML 命名空間前置詞使用`xmlns`命名空間屬性的屬性值必須是常數字串。</span><span class="sxs-lookup"><span data-stu-id="30ece-158">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="30ece-159">在這方面，使用`xmlns`屬性，就像是`Imports`陳述式來宣告 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="30ece-159">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="30ece-160">您無法使用內嵌的運算式來指定 XML 命名空間值。</span><span class="sxs-lookup"><span data-stu-id="30ece-160">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ece-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30ece-161">See Also</span></span>  
 <span data-ttu-id="30ece-162">[在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="30ece-162">[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="30ece-163"> [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="30ece-163"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="30ece-164"> [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="30ece-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="30ece-165"> [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="30ece-165"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="30ece-166"> [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="30ece-166"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="30ece-167"> [XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span><span class="sxs-lookup"><span data-stu-id="30ece-167"> [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span></span>
