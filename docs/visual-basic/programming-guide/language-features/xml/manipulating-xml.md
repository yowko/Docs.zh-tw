---
title: "在 Visual Basic 中管理 XML |Microsoft 文件"
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
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
caps.latest.revision: 5
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
ms.openlocfilehash: 62b955d78eb507aab4c786e84f3044ba54a38ebc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="e6811-102">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="e6811-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="e6811-103">您可以使用*XML 常值*從外部來源，例如字串、 檔案或資料流載入 XML。</span><span class="sxs-lookup"><span data-stu-id="e6811-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="e6811-104">然後您可以使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]操作 XML，並使用[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]來查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="e6811-104">You can then use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6811-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e6811-105">In This Section</span></span>  
 [<span data-ttu-id="e6811-106">如何：從檔案、字串或資料流載入 XML</span><span class="sxs-lookup"><span data-stu-id="e6811-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="e6811-107">示範如何在 xml 載入<xref:System.Xml.Linq.XDocument>或<xref:System.Xml.Linq.XElement>從文字檔案、 字串或資料流的物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="e6811-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="e6811-108">如何：使用 LINQ 轉換 XML</span><span class="sxs-lookup"><span data-stu-id="e6811-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="e6811-109">示範如何將轉換的內容<xref:System.Xml.Linq.XDocument>物件插入新的 XML 文件。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="e6811-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="e6811-110">如何：修改 XML 常值</span><span class="sxs-lookup"><span data-stu-id="e6811-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="e6811-111">示範如何修改項目、 屬性和 XML 常值中的值。</span><span class="sxs-lookup"><span data-stu-id="e6811-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e6811-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="e6811-112">Related Sections</span></span>  
 [<span data-ttu-id="e6811-113">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="e6811-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="e6811-114">提供說明各種 XML 存取屬性的章節連結。</span><span class="sxs-lookup"><span data-stu-id="e6811-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="e6811-115">LINQ to XML 在 Visual Basic 中的概觀</span><span class="sxs-lookup"><span data-stu-id="e6811-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="e6811-116">介紹使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="e6811-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e6811-117">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="e6811-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="e6811-118">介紹 Visual Basic 中使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="e6811-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e6811-119">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="e6811-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="e6811-120">示範如何存取 XML 項目或在 Visual Basic 中的文件的部分。</span><span class="sxs-lookup"><span data-stu-id="e6811-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e6811-121">XML</span><span class="sxs-lookup"><span data-stu-id="e6811-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="e6811-122">提供描述如何使用連結[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="e6811-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6811-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6811-123">See Also</span></span>  
 <span data-ttu-id="e6811-124">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6811-124">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="e6811-125"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6811-125"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="e6811-126"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="e6811-126"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
