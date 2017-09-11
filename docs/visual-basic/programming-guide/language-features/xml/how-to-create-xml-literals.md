---
title: "如何︰ 建立 XML 常值 (Visual Basic) |Microsoft 文件"
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
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 17
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
ms.openlocfilehash: 3a7b5dc692317067290b48222ba056d765a449f3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="e8ece-102">如何：建立 XML 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8ece-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="e8ece-103">您可以直接在程式碼中建立 XML 文件、 片段或項目，使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="e8ece-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="e8ece-104">本主題中的範例將示範如何建立 XML 項目具有三個子項目，以及如何建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e8ece-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="e8ece-105">您也可以使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Api 來建立[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="e8ece-105">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="e8ece-106">如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="e8ece-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="e8ece-107">若要建立的 XML 項目</span><span class="sxs-lookup"><span data-stu-id="e8ece-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="e8ece-108">使用 XML 常值語法，與實際的 XML 語法相同，建立內嵌的 XML。</span><span class="sxs-lookup"><span data-stu-id="e8ece-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     <span data-ttu-id="e8ece-109">[!code-vb[VbXMLSamples #&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8ece-109">[!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="e8ece-110">執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8ece-110">Run the code.</span></span> <span data-ttu-id="e8ece-111">此程式碼的輸出如下︰</span><span class="sxs-lookup"><span data-stu-id="e8ece-111">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="e8ece-112">若要建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="e8ece-112">To create an XML document</span></span>  
  
-   <span data-ttu-id="e8ece-113">建立內嵌的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e8ece-113">Create the XML document inline.</span></span> <span data-ttu-id="e8ece-114">下列程式碼會建立 XML 文件具有常值的語法，XML 宣告、 處理指示、 註解和包含另一個項目。</span><span class="sxs-lookup"><span data-stu-id="e8ece-114">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     <span data-ttu-id="e8ece-115">[!code-vb[VbXMLSamples #&30;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8ece-115">[!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="e8ece-116">執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8ece-116">Run the code.</span></span> <span data-ttu-id="e8ece-117">此程式碼的輸出如下︰</span><span class="sxs-lookup"><span data-stu-id="e8ece-117">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="e8ece-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8ece-118">See Also</span></span>  
 <span data-ttu-id="e8ece-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="e8ece-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="e8ece-120"> [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="e8ece-120"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="e8ece-121"> [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="e8ece-121"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="e8ece-122"> [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span><span class="sxs-lookup"><span data-stu-id="e8ece-122"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span></span>
