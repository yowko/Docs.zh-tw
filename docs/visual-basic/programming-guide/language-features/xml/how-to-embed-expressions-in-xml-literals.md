---
title: "如何︰ 將運算式內嵌在 XML 常值 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
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
ms.openlocfilehash: e4f086b06575cb8300bd65d450cda6b9893bb692
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="0a9b5-102">如何：將運算式內嵌在 XML 常值中 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9b5-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="0a9b5-103">您可以結合 XML 常值的內嵌的運算式，來建立 XML 文件、 片段中或包含在執行階段建立的內容項目。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="0a9b5-104">下列範例示範如何使用內嵌的運算式來填入項目內容、 屬性和項目名稱，在執行階段。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="0a9b5-105">內嵌運算式的語法是`<%=` `exp` `%>`，這是相同的語法，[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] uses.</span></span> <span data-ttu-id="0a9b5-106">如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="0a9b5-107">您也可以使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Api 來建立[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-107">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="0a9b5-108">如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="0a9b5-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0a9b5-109">程序</span><span class="sxs-lookup"><span data-stu-id="0a9b5-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="0a9b5-110">若要為項目內容中插入文字</span><span class="sxs-lookup"><span data-stu-id="0a9b5-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="0a9b5-111">下列範例示範如何插入文字中包含的`contactName`變數之間的開頭和結尾的名稱項目。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     <span data-ttu-id="0a9b5-112">[!code-vb[VbXMLSamples #&39;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0a9b5-112">[!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="0a9b5-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0a9b5-113">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="0a9b5-114">若要插入文字做為屬性值</span><span class="sxs-lookup"><span data-stu-id="0a9b5-114">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="0a9b5-115">下列範例示範如何插入文字中包含的`phoneType`變數的值為`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-115">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     <span data-ttu-id="0a9b5-116">[!code-vb[VbXMLSamples #&40;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0a9b5-116">[!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="0a9b5-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0a9b5-117">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="0a9b5-118">若要插入的項目名稱的文字</span><span class="sxs-lookup"><span data-stu-id="0a9b5-118">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="0a9b5-119">下列範例示範如何插入文字中包含的`elementName`變數做為項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-119">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="0a9b5-120">當使用這項技術建立的項目，您必須先關閉它們與\</ > 標記。</span><span class="sxs-lookup"><span data-stu-id="0a9b5-120">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     <span data-ttu-id="0a9b5-121">[!code-vb[VbXMLSamples #&41;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0a9b5-121">[!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="0a9b5-122">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0a9b5-122">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0a9b5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a9b5-123">See Also</span></span>  
 <span data-ttu-id="0a9b5-124">[如何︰ 建立 XML 常值](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span><span class="sxs-lookup"><span data-stu-id="0a9b5-124">[How to: Create XML Literals](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span></span>  
<span data-ttu-id="0a9b5-125"> [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="0a9b5-125"> [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="0a9b5-126"> [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="0a9b5-126"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="0a9b5-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="0a9b5-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
