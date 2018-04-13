---
title: XML 中內嵌的運算式 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1cdba0a39a932f143ac98c2514240e1696a8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="4aa94-102">XML 中內嵌的運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4aa94-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="4aa94-103">內嵌的運算式可讓您建立 XML 常值包含在執行階段所評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="4aa94-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="4aa94-104">內嵌運算式的語法是`<%=` `expression` `%>`，這會是相同的語法中所使用[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4aa94-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="4aa94-105">例如，您可以建立 XML 項目常值，結合使用常值的文字內容的內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="4aa94-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="4aa94-106">如果`isbnNumber`包含整數 12345 和`modifiedDate`包含日期 3/5/2006，這段程式碼執行時，值`book`是：</span><span class="sxs-lookup"><span data-stu-id="4aa94-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="4aa94-107">內嵌的運算式的位置和驗證</span><span class="sxs-lookup"><span data-stu-id="4aa94-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="4aa94-108">內嵌的運算式只可以出現在 XML 常值運算式內的特定位置。</span><span class="sxs-lookup"><span data-stu-id="4aa94-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="4aa94-109">可以傳回型別運算式的運算式位置控制項，以及如何`Nothing`處理。</span><span class="sxs-lookup"><span data-stu-id="4aa94-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="4aa94-110">下表描述允許的位置和內嵌運算式的型別。</span><span class="sxs-lookup"><span data-stu-id="4aa94-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="4aa94-111">常值中的位置</span><span class="sxs-lookup"><span data-stu-id="4aa94-111">Location in literal</span></span>|<span data-ttu-id="4aa94-112">運算式的型別</span><span class="sxs-lookup"><span data-stu-id="4aa94-112">Type of expression</span></span>|<span data-ttu-id="4aa94-113">處理`Nothing`</span><span class="sxs-lookup"><span data-stu-id="4aa94-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="4aa94-114">XML 項目名稱</span><span class="sxs-lookup"><span data-stu-id="4aa94-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="4aa94-115">錯誤</span><span class="sxs-lookup"><span data-stu-id="4aa94-115">Error</span></span>|  
|<span data-ttu-id="4aa94-116">XML 項目內容</span><span class="sxs-lookup"><span data-stu-id="4aa94-116">XML element content</span></span>|<span data-ttu-id="4aa94-117">`Object`或陣列`Object`</span><span class="sxs-lookup"><span data-stu-id="4aa94-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="4aa94-118">略過</span><span class="sxs-lookup"><span data-stu-id="4aa94-118">Ignored</span></span>|  
|<span data-ttu-id="4aa94-119">XML 項目屬性名稱</span><span class="sxs-lookup"><span data-stu-id="4aa94-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="4aa94-120">錯誤，除非也是屬性值`Nothing`</span><span class="sxs-lookup"><span data-stu-id="4aa94-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="4aa94-121">XML 項目屬性值</span><span class="sxs-lookup"><span data-stu-id="4aa94-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="4aa94-122">略過屬性宣告</span><span class="sxs-lookup"><span data-stu-id="4aa94-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="4aa94-123">XML 項目屬性</span><span class="sxs-lookup"><span data-stu-id="4aa94-123">XML element attribute</span></span>|<span data-ttu-id="4aa94-124"><xref:System.Xml.Linq.XAttribute>或選取的集合<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="4aa94-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="4aa94-125">略過</span><span class="sxs-lookup"><span data-stu-id="4aa94-125">Ignored</span></span>|  
|<span data-ttu-id="4aa94-126">XML 文件根項目</span><span class="sxs-lookup"><span data-stu-id="4aa94-126">XML document root element</span></span>|<span data-ttu-id="4aa94-127"><xref:System.Xml.Linq.XElement>或其中一個集合<xref:System.Xml.Linq.XElement>物件和任意數目的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件</span><span class="sxs-lookup"><span data-stu-id="4aa94-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="4aa94-128">略過</span><span class="sxs-lookup"><span data-stu-id="4aa94-128">Ignored</span></span>|  
  
-   <span data-ttu-id="4aa94-129">XML 項目名稱中內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="4aa94-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="4aa94-130">內嵌運算式的 XML 項目內容中的範例：</span><span class="sxs-lookup"><span data-stu-id="4aa94-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="4aa94-131">XML 項目屬性名稱中內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="4aa94-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="4aa94-132">XML 項目屬性值中的內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="4aa94-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="4aa94-133">內嵌運算式的 XML 項目屬性中的範例：</span><span class="sxs-lookup"><span data-stu-id="4aa94-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="4aa94-134">XML 文件根項目中內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="4aa94-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="4aa94-135">如果您啟用`Option Strict`，編譯器會檢查每個內嵌運算式的類型可擴展為必要型別。</span><span class="sxs-lookup"><span data-stu-id="4aa94-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="4aa94-136">唯一的例外狀況是當執行的程式碼會驗證 XML 文件的根項目。</span><span class="sxs-lookup"><span data-stu-id="4aa94-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="4aa94-137">如果您沒有編譯`Option Strict`，您可以將內嵌運算式的型別`Object`和執行階段就會驗證它們的型別。</span><span class="sxs-lookup"><span data-stu-id="4aa94-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="4aa94-138">內容是選擇性的其中的位置中內嵌包含的運算式`Nothing`都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="4aa94-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="4aa94-139">這表示您沒有核取該元素的內容，屬性值，而且不是陣列項目`Nothing`才能使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="4aa94-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="4aa94-140">必要值，例如項目和屬性名稱不能`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4aa94-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="4aa94-141">如需在特定類型的常值中使用內嵌的運算式的詳細資訊，請參閱[XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)， [XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="4aa94-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="4aa94-142">範圍規則</span><span class="sxs-lookup"><span data-stu-id="4aa94-142">Scoping Rules</span></span>  
 <span data-ttu-id="4aa94-143">編譯器會將每個 XML 常值轉換成適當的常值類型的建構函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="4aa94-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="4aa94-144">建構函式，會將常值內容和內嵌的運算式，在 XML 常值傳遞做為引數。</span><span class="sxs-lookup"><span data-stu-id="4aa94-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="4aa94-145">這表示所有[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式設計項目可使用 XML 常值也會提供給其內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="4aa94-145">This means that all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="4aa94-146">在 XML 常值，您可以存取以宣告的前置詞的 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4aa94-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="4aa94-147">您可以宣告新的 XML 命名空間前置詞，或現有 XML 命名空間前置詞，在使用項目會遮蔽`xmlns`屬性。</span><span class="sxs-lookup"><span data-stu-id="4aa94-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="4aa94-148">新的命名空間可至該項目的子節點，而非內嵌的運算式中的 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="4aa94-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4aa94-149">當您宣告 XML 命名空間前置詞使用`xmlns`命名空間屬性的屬性值必須是與常數字串。</span><span class="sxs-lookup"><span data-stu-id="4aa94-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="4aa94-150">在這方面，使用`xmlns`屬性，就像是`Imports`陳述式來宣告 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4aa94-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="4aa94-151">您無法使用內嵌的運算式來指定 XML 命名空間值。</span><span class="sxs-lookup"><span data-stu-id="4aa94-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa94-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4aa94-152">See Also</span></span>  
 [<span data-ttu-id="4aa94-153">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="4aa94-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="4aa94-154">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="4aa94-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="4aa94-155">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="4aa94-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="4aa94-156">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="4aa94-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="4aa94-157">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="4aa94-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="4aa94-158">XML 常值概觀</span><span class="sxs-lookup"><span data-stu-id="4aa94-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
