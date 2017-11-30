---
title: "在 Visual Basic 中管理 XML"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 061617524659ac2f8793e2030f26a2d6b2724a64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="e14b1-102">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="e14b1-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="e14b1-103">您可以使用*XML 常值*從外部來源，例如字串、 檔案或資料流載入 XML。</span><span class="sxs-lookup"><span data-stu-id="e14b1-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="e14b1-104">然後您可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]操作 XML，並使用[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]來查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="e14b1-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e14b1-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e14b1-105">In This Section</span></span>  
 [<span data-ttu-id="e14b1-106">如何：從檔案、字串或資料流載入 XML</span><span class="sxs-lookup"><span data-stu-id="e14b1-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="e14b1-107">示範如何載入到 XML<xref:System.Xml.Linq.XDocument>或<xref:System.Xml.Linq.XElement>從文字檔、 字串或資料流的物件。</span><span class="sxs-lookup"><span data-stu-id="e14b1-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="e14b1-108">如何：使用 LINQ 轉換 XML</span><span class="sxs-lookup"><span data-stu-id="e14b1-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="e14b1-109">示範如何將轉換的內容<xref:System.Xml.Linq.XDocument>成為新的 XML 文件物件。</span><span class="sxs-lookup"><span data-stu-id="e14b1-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="e14b1-110">如何：修改 XML 常值</span><span class="sxs-lookup"><span data-stu-id="e14b1-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="e14b1-111">示範如何修改項目、 屬性和 XML 常值中的值。</span><span class="sxs-lookup"><span data-stu-id="e14b1-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e14b1-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="e14b1-112">Related Sections</span></span>  
 [<span data-ttu-id="e14b1-113">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="e14b1-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="e14b1-114">提供各節，說明各種 XML 存取內容的連結。</span><span class="sxs-lookup"><span data-stu-id="e14b1-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="e14b1-115">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="e14b1-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="e14b1-116">提供簡介使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="e14b1-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e14b1-117">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="e14b1-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="e14b1-118">提供 Visual Basic 中使用 XML 常值的簡介。</span><span class="sxs-lookup"><span data-stu-id="e14b1-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e14b1-119">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="e14b1-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="e14b1-120">示範如何存取組件的 XML 元素或在 Visual Basic 中的文件。</span><span class="sxs-lookup"><span data-stu-id="e14b1-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e14b1-121">XML</span><span class="sxs-lookup"><span data-stu-id="e14b1-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="e14b1-122">提供描述如何使用連結[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="e14b1-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e14b1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e14b1-123">See Also</span></span>  
 [<span data-ttu-id="e14b1-124">XML</span><span class="sxs-lookup"><span data-stu-id="e14b1-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="e14b1-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="e14b1-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="e14b1-126">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="e14b1-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
