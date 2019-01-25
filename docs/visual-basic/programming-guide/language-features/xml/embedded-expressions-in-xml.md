---
title: XML 中內嵌的運算式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: c02b6ea0895d8b22ac71d0cb3ea6950861de47df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678755"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="4c745-102">XML 中內嵌的運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c745-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="4c745-103">內嵌的運算式可讓您建立 XML 常值包含在執行階段評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c745-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="4c745-104">內嵌運算式的語法`<%=` `expression` `%>`，這會是相同的語法用於[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4c745-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="4c745-105">例如，您可以建立的 XML 項目常值，結合使用常值的文字內容的內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c745-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="4c745-106">如果`isbnNumber`包含整數 12345 並`modifiedDate`包含日期 3/5/2006，此程式碼執行時，值`book`是：</span><span class="sxs-lookup"><span data-stu-id="4c745-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="4c745-107">內嵌的運算式的位置和驗證</span><span class="sxs-lookup"><span data-stu-id="4c745-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="4c745-108">內嵌的運算式只可以出現在 XML 常值運算式內的特定位置。</span><span class="sxs-lookup"><span data-stu-id="4c745-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="4c745-109">運算式的位置控制項類型的運算式可以傳回及如何`Nothing`處理。</span><span class="sxs-lookup"><span data-stu-id="4c745-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="4c745-110">下表描述允許的位置和內嵌運算式的型別。</span><span class="sxs-lookup"><span data-stu-id="4c745-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="4c745-111">常值中的位置</span><span class="sxs-lookup"><span data-stu-id="4c745-111">Location in literal</span></span>|<span data-ttu-id="4c745-112">運算式的型別</span><span class="sxs-lookup"><span data-stu-id="4c745-112">Type of expression</span></span>|<span data-ttu-id="4c745-113">處理 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="4c745-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="4c745-114">XML 項目名稱</span><span class="sxs-lookup"><span data-stu-id="4c745-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="4c745-115">錯誤</span><span class="sxs-lookup"><span data-stu-id="4c745-115">Error</span></span>|  
|<span data-ttu-id="4c745-116">XML 項目內容</span><span class="sxs-lookup"><span data-stu-id="4c745-116">XML element content</span></span>|<span data-ttu-id="4c745-117">`Object` 或陣列 `Object`</span><span class="sxs-lookup"><span data-stu-id="4c745-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="4c745-118">略過</span><span class="sxs-lookup"><span data-stu-id="4c745-118">Ignored</span></span>|  
|<span data-ttu-id="4c745-119">XML 項目屬性名稱</span><span class="sxs-lookup"><span data-stu-id="4c745-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="4c745-120">錯誤，除非屬性值也是 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="4c745-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="4c745-121">XML 項目屬性值</span><span class="sxs-lookup"><span data-stu-id="4c745-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="4c745-122">忽略的屬性宣告</span><span class="sxs-lookup"><span data-stu-id="4c745-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="4c745-123">XML 項目屬性</span><span class="sxs-lookup"><span data-stu-id="4c745-123">XML element attribute</span></span>|<span data-ttu-id="4c745-124"><xref:System.Xml.Linq.XAttribute> 或集合 <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="4c745-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="4c745-125">略過</span><span class="sxs-lookup"><span data-stu-id="4c745-125">Ignored</span></span>|  
|<span data-ttu-id="4c745-126">XML 文件根項目</span><span class="sxs-lookup"><span data-stu-id="4c745-126">XML document root element</span></span>|<span data-ttu-id="4c745-127"><xref:System.Xml.Linq.XElement> 或其中一個集合<xref:System.Xml.Linq.XElement>物件和任意數目的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件</span><span class="sxs-lookup"><span data-stu-id="4c745-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="4c745-128">略過</span><span class="sxs-lookup"><span data-stu-id="4c745-128">Ignored</span></span>|  
  
-   <span data-ttu-id="4c745-129">XML 項目名稱中內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="4c745-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="4c745-130">XML 項目的內嵌運算式內容中的範例：</span><span class="sxs-lookup"><span data-stu-id="4c745-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="4c745-131">XML 項目屬性名稱中內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="4c745-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="4c745-132">XML 項目屬性值的內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="4c745-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="4c745-133">內嵌運算式中的 XML 項目屬性的範例：</span><span class="sxs-lookup"><span data-stu-id="4c745-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="4c745-134">內嵌運算式的 XML 文件根項目中的範例：</span><span class="sxs-lookup"><span data-stu-id="4c745-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="4c745-135">如果您啟用`Option Strict`，編譯器會檢查每個內嵌的運算式類型可擴展為要求的類型。</span><span class="sxs-lookup"><span data-stu-id="4c745-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="4c745-136">程式碼執行時驗證的 XML 文件的根項目是唯一的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c745-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="4c745-137">如果您編譯而不要`Option Strict`，您可以將內嵌類型的運算式`Object`和其類型在執行階段驗證。</span><span class="sxs-lookup"><span data-stu-id="4c745-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="4c745-138">內容是選擇性的其中的位置中內嵌包含的運算式`Nothing`都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="4c745-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="4c745-139">這表示您沒有檢查項目內容，屬性值，而且陣列項目不是`Nothing`才能使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="4c745-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="4c745-140">必要值，例如項目和屬性名稱不可以是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4c745-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="4c745-141">如需使用特定類型的常值中的內嵌的運算式的詳細資訊，請參閱[XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)， [XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="4c745-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="4c745-142">範圍規則</span><span class="sxs-lookup"><span data-stu-id="4c745-142">Scoping Rules</span></span>  
 <span data-ttu-id="4c745-143">編譯器會將每個 XML 常值轉換成適當的常值類型的建構函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="4c745-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="4c745-144">建構函式，會將 XML 常值中內嵌的運算式與常值內容傳遞做為引數。</span><span class="sxs-lookup"><span data-stu-id="4c745-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="4c745-145">這表示所有 Visual Basic 程式設計項目可使用 XML 常值都可內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c745-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="4c745-146">在 XML 常值，您可以存取以宣告的前置詞的 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4c745-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="4c745-147">您可以宣告新的 XML 命名空間前置詞，或遮蔽現有 XML 命名空間前置詞，在項目中使用`xmlns`屬性。</span><span class="sxs-lookup"><span data-stu-id="4c745-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="4c745-148">內嵌的運算式中的 XML 常值之子節點的該元素，但不是使用新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4c745-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c745-149">當您宣告 XML 命名空間前置詞使用`xmlns`命名空間屬性的屬性值必須是常數字串。</span><span class="sxs-lookup"><span data-stu-id="4c745-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="4c745-150">在這方面，使用`xmlns`屬性，就像是`Imports`陳述式來宣告 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4c745-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="4c745-151">您無法使用內嵌的運算式來指定 XML 命名空間值。</span><span class="sxs-lookup"><span data-stu-id="4c745-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c745-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c745-152">See also</span></span>
- [<span data-ttu-id="4c745-153">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="4c745-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="4c745-154">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="4c745-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="4c745-155">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="4c745-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="4c745-156">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="4c745-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="4c745-157">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="4c745-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="4c745-158">XML 常值概觀</span><span class="sxs-lookup"><span data-stu-id="4c745-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
