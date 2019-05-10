---
title: HOW TO：將運算式內嵌在 XML 常值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: ca80ac666e8676e4e58a9741b00125c0126570fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598385"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="481ef-102">HOW TO：將運算式內嵌在 XML 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="481ef-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="481ef-103">您可以使用內嵌的運算式，來建立 XML 文件、 片段中或包含在執行階段建立的內容項目結合 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="481ef-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="481ef-104">下列範例示範如何使用內嵌的運算式在執行階段填入項目內容、 屬性和項目名稱。</span><span class="sxs-lookup"><span data-stu-id="481ef-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="481ef-105">內嵌運算式的語法`<%=` `exp` `%>`，這是相同的語法，[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="481ef-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="481ef-106">如需詳細資訊，請參閱 < [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="481ef-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="481ef-107">您也可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Api 來建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="481ef-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="481ef-108">如需詳細資訊，請參閱 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="481ef-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="481ef-109">程序</span><span class="sxs-lookup"><span data-stu-id="481ef-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="481ef-110">若要為項目內容中插入文字</span><span class="sxs-lookup"><span data-stu-id="481ef-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="481ef-111">下列範例示範如何插入文字中包含`contactName`變數之間的開頭和結尾的名稱項目。</span><span class="sxs-lookup"><span data-stu-id="481ef-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="481ef-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="481ef-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="481ef-113">若要做為屬性值插入文字</span><span class="sxs-lookup"><span data-stu-id="481ef-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="481ef-114">下列範例示範如何插入文字中包含`phoneType`變數的值設定為`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="481ef-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="481ef-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="481ef-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="481ef-116">若要插入項目名稱的文字</span><span class="sxs-lookup"><span data-stu-id="481ef-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="481ef-117">下列範例示範如何插入文字中包含`elementName`變數做為項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="481ef-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="481ef-118">在建立項目時使用這項技術，您必須先關閉它們與\</ > 標記。</span><span class="sxs-lookup"><span data-stu-id="481ef-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="481ef-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="481ef-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="481ef-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="481ef-120">See also</span></span>

- [<span data-ttu-id="481ef-121">如何：建立 XML 常值</span><span class="sxs-lookup"><span data-stu-id="481ef-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="481ef-122">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="481ef-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="481ef-123">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="481ef-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="481ef-124">XML</span><span class="sxs-lookup"><span data-stu-id="481ef-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
