---
title: "LINQ to XML 程式設計概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: a7c07d0a-1fae-4610-ae51-56dd7075cc14
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 57d52b1bc46263e4e8e662be6a83bf4718813b43
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-programming-overview-visual-basic"></a><span data-ttu-id="857c3-102">LINQ to XML 程式設計概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-102">LINQ to XML Programming Overview (Visual Basic)</span></span>
<span data-ttu-id="857c3-103">這些主題提供有關 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 類別的高階概觀資訊，以及關於其中三個最重要類別的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="857c3-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="857c3-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="857c3-104">In This Section</span></span>  
  
|<span data-ttu-id="857c3-105">主題</span><span class="sxs-lookup"><span data-stu-id="857c3-105">Topic</span></span>|<span data-ttu-id="857c3-106">描述</span><span class="sxs-lookup"><span data-stu-id="857c3-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="857c3-107">函數式與程序性程式設計 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-107">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="857c3-108">提供兩個撰寫 LINQ to XML 應用程式之準則方法的高階檢視。</span><span class="sxs-lookup"><span data-stu-id="857c3-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="857c3-109">LINQ to XML 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-109">LINQ to XML Classes Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="857c3-110">提供 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 類別的概觀。</span><span class="sxs-lookup"><span data-stu-id="857c3-110">Provides an overview of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes.</span></span>|  
|[<span data-ttu-id="857c3-111">XElement 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-111">XElement Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="857c3-112">介紹<xref:System.Xml.Linq.XElement>類別，其代表 XML 項目。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="857c3-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="857c3-113"><xref:System.Xml.Linq.XElement>是主要的類別中的其中一個[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]類別階層。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="857c3-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="857c3-114">XAttribute 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-114">XAttribute Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="857c3-115">介紹<xref:System.Xml.Linq.XAttribute>類別代表 XML 屬性。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="857c3-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="857c3-116">XDocument 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-116">XDocument Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="857c3-117">介紹<xref:System.Xml.Linq.XDocument>類別代表 XML 文件。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="857c3-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="857c3-118">如何︰ 建置 LINQ to XML 範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-118">How to: Build LINQ to XML Examples (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="857c3-119">包含`Imports`建置 LINQ to XML 範例所需的陳述式。</span><span class="sxs-lookup"><span data-stu-id="857c3-119">Contains the `Imports` statements that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="857c3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="857c3-120">See Also</span></span>  
 [<span data-ttu-id="857c3-121">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857c3-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
