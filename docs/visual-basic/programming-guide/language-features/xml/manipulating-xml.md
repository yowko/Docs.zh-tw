---
title: 操作 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
ms.openlocfilehash: 2565f43c1014bf0fa9fab1618fedfd1bd6bdb7ca
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330434"
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="74683-102">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="74683-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="74683-103">您可以使用*xml 常*值，從外部來源（例如字串、檔案或資料流程）載入 xml。</span><span class="sxs-lookup"><span data-stu-id="74683-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="74683-104">然後，您可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 來操作 XML，並使用 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 來查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="74683-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74683-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="74683-105">In This Section</span></span>  
 [<span data-ttu-id="74683-106">如何：從檔案、字串或資料流載入 XML</span><span class="sxs-lookup"><span data-stu-id="74683-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="74683-107">示範如何從文字檔、字串或資料流程，將 XML 載入 <xref:System.Xml.Linq.XDocument> 或 <xref:System.Xml.Linq.XElement> 物件中。</span><span class="sxs-lookup"><span data-stu-id="74683-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="74683-108">如何：使用 LINQ 轉換 XML</span><span class="sxs-lookup"><span data-stu-id="74683-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="74683-109">示範如何將 <xref:System.Xml.Linq.XDocument> 物件的內容轉換成新的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="74683-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="74683-110">如何：修改 XML 常值</span><span class="sxs-lookup"><span data-stu-id="74683-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="74683-111">示範如何修改 XML 常值中的元素、屬性和值。</span><span class="sxs-lookup"><span data-stu-id="74683-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="74683-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="74683-112">Related Sections</span></span>  
 [<span data-ttu-id="74683-113">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="74683-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="74683-114">提供描述各種 XML 存取屬性之區段的連結。</span><span class="sxs-lookup"><span data-stu-id="74683-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="74683-115">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="74683-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="74683-116">提供在 Visual Basic 中使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的簡介。</span><span class="sxs-lookup"><span data-stu-id="74683-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="74683-117">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="74683-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="74683-118">提供在 Visual Basic 中使用 XML 常值的簡介。</span><span class="sxs-lookup"><span data-stu-id="74683-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="74683-119">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="74683-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="74683-120">示範如何在 Visual Basic 中存取 XML 元素或檔的某些部分。</span><span class="sxs-lookup"><span data-stu-id="74683-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="74683-121">XML</span><span class="sxs-lookup"><span data-stu-id="74683-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="74683-122">提供章節的連結，說明如何在 Visual Basic 中使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="74683-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74683-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="74683-123">See also</span></span>

- [<span data-ttu-id="74683-124">XML</span><span class="sxs-lookup"><span data-stu-id="74683-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="74683-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="74683-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="74683-126">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="74683-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
