---
title: 如何：將運算式內嵌在 XML 常值中
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332933"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="4e6ba-102">如何：將運算式內嵌在 XML 常值中 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e6ba-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="4e6ba-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="4e6ba-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="4e6ba-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="4e6ba-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4e6ba-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="4e6ba-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="4e6ba-108">如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="4e6ba-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4e6ba-109">程序</span><span class="sxs-lookup"><span data-stu-id="4e6ba-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="4e6ba-110">To insert text as element content</span><span class="sxs-lookup"><span data-stu-id="4e6ba-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="4e6ba-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="4e6ba-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4e6ba-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="4e6ba-113">To insert text as an attribute value</span><span class="sxs-lookup"><span data-stu-id="4e6ba-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="4e6ba-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="4e6ba-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4e6ba-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="4e6ba-116">To insert text for an element name</span><span class="sxs-lookup"><span data-stu-id="4e6ba-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="4e6ba-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="4e6ba-118">When creating elements by using this technique, you must close them with the \</> tag.</span><span class="sxs-lookup"><span data-stu-id="4e6ba-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="4e6ba-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4e6ba-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4e6ba-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e6ba-120">See also</span></span>

- [<span data-ttu-id="4e6ba-121">如何：建立 XML 常值</span><span class="sxs-lookup"><span data-stu-id="4e6ba-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="4e6ba-122">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="4e6ba-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="4e6ba-123">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="4e6ba-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="4e6ba-124">XML</span><span class="sxs-lookup"><span data-stu-id="4e6ba-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
