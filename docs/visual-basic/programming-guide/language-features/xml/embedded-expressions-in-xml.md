---
title: XML 中內嵌的運算式
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332346"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="f70e7-102">XML 中內嵌的運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f70e7-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="f70e7-103">內嵌運算式可讓您建立 XML 常值，其中包含在執行時間評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="f70e7-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="f70e7-104">內嵌運算式的語法是 `<%=` `expression` `%>`，這與 ASP.NET 中所使用的語法相同。</span><span class="sxs-lookup"><span data-stu-id="f70e7-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="f70e7-105">例如，您可以建立 XML 元素常值，並結合內嵌運算式與常值文字內容。</span><span class="sxs-lookup"><span data-stu-id="f70e7-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="f70e7-106">如果 `isbnNumber` 包含整數12345，而 `modifiedDate` 包含日期3/5/2006，則當此程式碼執行時，`book` 的值為：</span><span class="sxs-lookup"><span data-stu-id="f70e7-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="f70e7-107">內嵌運算式位置和驗證</span><span class="sxs-lookup"><span data-stu-id="f70e7-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="f70e7-108">內嵌運算式只能出現在 XML 常值運算式內的特定位置。</span><span class="sxs-lookup"><span data-stu-id="f70e7-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="f70e7-109">運算式位置會控制運算式可以傳回的類型，以及處理 `Nothing` 的方式。</span><span class="sxs-lookup"><span data-stu-id="f70e7-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="f70e7-110">下表描述內嵌運算式的允許位置和類型。</span><span class="sxs-lookup"><span data-stu-id="f70e7-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="f70e7-111">常值中的位置</span><span class="sxs-lookup"><span data-stu-id="f70e7-111">Location in literal</span></span>|<span data-ttu-id="f70e7-112">運算式的類型</span><span class="sxs-lookup"><span data-stu-id="f70e7-112">Type of expression</span></span>|<span data-ttu-id="f70e7-113">`Nothing` 的處理</span><span class="sxs-lookup"><span data-stu-id="f70e7-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="f70e7-114">XML 元素名稱</span><span class="sxs-lookup"><span data-stu-id="f70e7-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="f70e7-115">錯誤</span><span class="sxs-lookup"><span data-stu-id="f70e7-115">Error</span></span>|  
|<span data-ttu-id="f70e7-116">XML 元素內容</span><span class="sxs-lookup"><span data-stu-id="f70e7-116">XML element content</span></span>|<span data-ttu-id="f70e7-117">`Object` 的 `Object` 或陣列</span><span class="sxs-lookup"><span data-stu-id="f70e7-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="f70e7-118">略過</span><span class="sxs-lookup"><span data-stu-id="f70e7-118">Ignored</span></span>|  
|<span data-ttu-id="f70e7-119">XML 元素屬性名稱</span><span class="sxs-lookup"><span data-stu-id="f70e7-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="f70e7-120">錯誤，除非屬性值也 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="f70e7-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="f70e7-121">XML 元素屬性值</span><span class="sxs-lookup"><span data-stu-id="f70e7-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="f70e7-122">已忽略屬性宣告</span><span class="sxs-lookup"><span data-stu-id="f70e7-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="f70e7-123">XML 元素屬性</span><span class="sxs-lookup"><span data-stu-id="f70e7-123">XML element attribute</span></span>|<span data-ttu-id="f70e7-124"><xref:System.Xml.Linq.XAttribute> 或 <xref:System.Xml.Linq.XAttribute> 的集合</span><span class="sxs-lookup"><span data-stu-id="f70e7-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="f70e7-125">略過</span><span class="sxs-lookup"><span data-stu-id="f70e7-125">Ignored</span></span>|  
|<span data-ttu-id="f70e7-126">XML 檔根項目</span><span class="sxs-lookup"><span data-stu-id="f70e7-126">XML document root element</span></span>|<span data-ttu-id="f70e7-127"><xref:System.Xml.Linq.XElement> 或一個 <xref:System.Xml.Linq.XElement> 物件的集合，以及任意數目的 <xref:System.Xml.Linq.XProcessingInstruction> 和 <xref:System.Xml.Linq.XComment> 物件</span><span class="sxs-lookup"><span data-stu-id="f70e7-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="f70e7-128">略過</span><span class="sxs-lookup"><span data-stu-id="f70e7-128">Ignored</span></span>|  
  
- <span data-ttu-id="f70e7-129">XML 元素名稱中內嵌運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="f70e7-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="f70e7-130">XML 元素內容中的內嵌運算式範例：</span><span class="sxs-lookup"><span data-stu-id="f70e7-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="f70e7-131">XML 元素屬性名稱中的內嵌運算式範例：</span><span class="sxs-lookup"><span data-stu-id="f70e7-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="f70e7-132">XML 元素屬性值中的內嵌運算式範例：</span><span class="sxs-lookup"><span data-stu-id="f70e7-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="f70e7-133">XML 元素屬性中的內嵌運算式範例：</span><span class="sxs-lookup"><span data-stu-id="f70e7-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="f70e7-134">XML 檔根項目中的內嵌運算式範例：</span><span class="sxs-lookup"><span data-stu-id="f70e7-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="f70e7-135">如果您啟用 `Option Strict`，編譯器會檢查每個內嵌運算式的類型是否加寬成所需的類型。</span><span class="sxs-lookup"><span data-stu-id="f70e7-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="f70e7-136">唯一的例外是針對 XML 檔的根項目，這會在程式碼執行時進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f70e7-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="f70e7-137">如果您編譯時沒有 `Option Strict`，您可以內嵌類型 `Object` 的運算式，並在執行時間驗證其類型。</span><span class="sxs-lookup"><span data-stu-id="f70e7-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="f70e7-138">在內容為選擇性的位置中，會忽略包含 `Nothing` 的內嵌運算式。</span><span class="sxs-lookup"><span data-stu-id="f70e7-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="f70e7-139">這表示您不需要在使用 XML 常值之前，檢查元素內容、屬性值和陣列元素是否 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f70e7-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="f70e7-140">無法 `Nothing`必要的值，例如元素和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f70e7-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="f70e7-141">如需在特定類型的常值中使用內嵌運算式的詳細資訊，請參閱[Xml 檔常](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)值、 [xml 元素常](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)值。</span><span class="sxs-lookup"><span data-stu-id="f70e7-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="f70e7-142">範圍規則</span><span class="sxs-lookup"><span data-stu-id="f70e7-142">Scoping Rules</span></span>  
 <span data-ttu-id="f70e7-143">編譯器會將每個 XML 常值轉換成適當常數值型別的函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f70e7-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="f70e7-144">XML 常值中的常值內容和內嵌運算式會當做引數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="f70e7-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="f70e7-145">這表示可用於 XML 常值的所有 Visual Basic 程式設計專案也可用於其內嵌運算式。</span><span class="sxs-lookup"><span data-stu-id="f70e7-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="f70e7-146">在 XML 常值內，您可以存取以 `Imports` 語句宣告的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f70e7-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="f70e7-147">您可以使用 `xmlns` 屬性，在元素中宣告新的 XML 命名空間前置詞，或遮蔽現有的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f70e7-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="f70e7-148">新的命名空間可用於該元素的子節點，但不能用於內嵌運算式中的 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="f70e7-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f70e7-149">當您使用 `xmlns` namespace 屬性來宣告 XML 命名空間前置詞時，屬性值必須是常數位串。</span><span class="sxs-lookup"><span data-stu-id="f70e7-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="f70e7-150">在這方面，使用 `xmlns` 屬性就像使用 `Imports` 語句來宣告 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="f70e7-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="f70e7-151">您不能使用內嵌運算式來指定 XML 命名空間值。</span><span class="sxs-lookup"><span data-stu-id="f70e7-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70e7-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="f70e7-152">See also</span></span>

- [<span data-ttu-id="f70e7-153">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="f70e7-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f70e7-154">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="f70e7-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="f70e7-155">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="f70e7-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="f70e7-156">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="f70e7-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f70e7-157">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="f70e7-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="f70e7-158">XML 常值概觀</span><span class="sxs-lookup"><span data-stu-id="f70e7-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
