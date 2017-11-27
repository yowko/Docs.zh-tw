---
title: "如何：建立 XML 常值 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce1bf763529b436158c2d74811c4938182166f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="27c3d-102">如何：建立 XML 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27c3d-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="27c3d-103">您可以直接在程式碼中建立 XML 文件、 片段或項目，使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="27c3d-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="27c3d-104">本主題中的範例將示範如何建立 XML 項目具有三個子項目，以及如何建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="27c3d-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="27c3d-105">您也可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Api 來建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="27c3d-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="27c3d-106">如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="27c3d-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="27c3d-107">若要建立的 XML 項目</span><span class="sxs-lookup"><span data-stu-id="27c3d-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="27c3d-108">建立內嵌的 XML 可以使用 XML 常值語法，與實際的 XML 語法相同。</span><span class="sxs-lookup"><span data-stu-id="27c3d-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="27c3d-109">執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="27c3d-109">Run the code.</span></span> <span data-ttu-id="27c3d-110">這個程式碼的輸出為：</span><span class="sxs-lookup"><span data-stu-id="27c3d-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="27c3d-111">若要建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="27c3d-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="27c3d-112">建立 XML 文件內嵌。</span><span class="sxs-lookup"><span data-stu-id="27c3d-112">Create the XML document inline.</span></span> <span data-ttu-id="27c3d-113">下列程式碼會建立 XML 文件具有常值的語法、 XML 宣告、 處理指示、 註解，以及此項目包含另一個項目。</span><span class="sxs-lookup"><span data-stu-id="27c3d-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="27c3d-114">執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="27c3d-114">Run the code.</span></span> <span data-ttu-id="27c3d-115">這個程式碼的輸出為：</span><span class="sxs-lookup"><span data-stu-id="27c3d-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="27c3d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27c3d-116">See Also</span></span>  
 [<span data-ttu-id="27c3d-117">XML</span><span class="sxs-lookup"><span data-stu-id="27c3d-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="27c3d-118">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="27c3d-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="27c3d-119">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="27c3d-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="27c3d-120">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="27c3d-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
