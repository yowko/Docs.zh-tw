---
title: 如何：建立 XML 常值
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e3af5185d2c2106e6a696a6569ef59897d0f1fe1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332995"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="b3435-102">如何：建立 XML 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3435-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="b3435-103">您可以使用 XML 常值，直接在程式碼中建立 XML 檔、片段或元素。</span><span class="sxs-lookup"><span data-stu-id="b3435-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="b3435-104">本主題中的範例將示範如何建立具有三個子項目的 XML 專案，以及如何建立 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="b3435-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="b3435-105">您也可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Api 來建立 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="b3435-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="b3435-106">如需詳細資訊，請參閱 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="b3435-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="b3435-107">若要建立 XML 元素</span><span class="sxs-lookup"><span data-stu-id="b3435-107">To create an XML element</span></span>  
  
- <span data-ttu-id="b3435-108">使用 XML 常值語法建立 XML 內嵌，這與實際的 XML 語法相同。</span><span class="sxs-lookup"><span data-stu-id="b3435-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="b3435-109">執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="b3435-109">Run the code.</span></span> <span data-ttu-id="b3435-110">此程式碼的輸出為：</span><span class="sxs-lookup"><span data-stu-id="b3435-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="b3435-111">若要建立 XML 檔</span><span class="sxs-lookup"><span data-stu-id="b3435-111">To create an XML document</span></span>  
  
- <span data-ttu-id="b3435-112">建立內嵌的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="b3435-112">Create the XML document inline.</span></span> <span data-ttu-id="b3435-113">下列程式碼會建立 XML 檔，其中具有常值語法、XML 宣告、處理指示、批註，以及包含另一個元素的專案。</span><span class="sxs-lookup"><span data-stu-id="b3435-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="b3435-114">執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="b3435-114">Run the code.</span></span> <span data-ttu-id="b3435-115">此程式碼的輸出為：</span><span class="sxs-lookup"><span data-stu-id="b3435-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="b3435-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3435-116">See also</span></span>

- [<span data-ttu-id="b3435-117">XML</span><span class="sxs-lookup"><span data-stu-id="b3435-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="b3435-118">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="b3435-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="b3435-119">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="b3435-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="b3435-120">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="b3435-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
