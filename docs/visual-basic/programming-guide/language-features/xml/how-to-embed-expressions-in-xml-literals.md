---
title: 如何：將運算式內嵌在 XML 常值中 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 41dc6ef8d2ec2ffd6cd1cf793911f2e09f1a1e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652265"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="53ab0-102">如何：將運算式內嵌在 XML 常值中 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53ab0-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="53ab0-103">您可以使用內嵌的運算式，來建立 XML 文件、 片段或包含在執行階段建立的內容項目結合 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="53ab0-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="53ab0-104">下列範例會示範如何使用內嵌的運算式來填入項目內容、 屬性和項目名稱，在執行階段。</span><span class="sxs-lookup"><span data-stu-id="53ab0-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="53ab0-105">內嵌運算式的語法是`<%=` `exp` `%>`，這是相同的語法，[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="53ab0-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="53ab0-106">如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="53ab0-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="53ab0-107">您也可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Api 來建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="53ab0-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="53ab0-108">如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="53ab0-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="53ab0-109">程序</span><span class="sxs-lookup"><span data-stu-id="53ab0-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="53ab0-110">若要為項目內容中插入文字</span><span class="sxs-lookup"><span data-stu-id="53ab0-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="53ab0-111">下列範例示範如何插入文字中包含`contactName`變數之間的開頭和結尾名稱項目。</span><span class="sxs-lookup"><span data-stu-id="53ab0-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     <span data-ttu-id="53ab0-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="53ab0-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="53ab0-113">將文字插入做為屬性值</span><span class="sxs-lookup"><span data-stu-id="53ab0-113">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="53ab0-114">下列範例示範如何插入文字中包含`phoneType`變數的值作為`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="53ab0-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     <span data-ttu-id="53ab0-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="53ab0-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="53ab0-116">若要插入項目名稱的文字</span><span class="sxs-lookup"><span data-stu-id="53ab0-116">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="53ab0-117">下列範例示範如何插入文字中包含`elementName`變數做為項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="53ab0-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="53ab0-118">當使用這項技術建立的項目，您必須關閉它們與\</ > 標記。</span><span class="sxs-lookup"><span data-stu-id="53ab0-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     <span data-ttu-id="53ab0-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="53ab0-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="53ab0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ab0-120">See Also</span></span>  
 [<span data-ttu-id="53ab0-121">如何：建立 XML 常值</span><span class="sxs-lookup"><span data-stu-id="53ab0-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [<span data-ttu-id="53ab0-122">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="53ab0-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="53ab0-123">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="53ab0-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="53ab0-124">XML</span><span class="sxs-lookup"><span data-stu-id="53ab0-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
