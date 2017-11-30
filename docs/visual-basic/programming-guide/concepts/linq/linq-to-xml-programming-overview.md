---
title: "LINQ to XML 程式設計概觀 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7c07d0a-1fae-4610-ae51-56dd7075cc14
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 84816fe2c75d59a8bc4a7cb93d1f87974eaf17b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-programming-overview-visual-basic"></a><span data-ttu-id="7063b-102">LINQ to XML 程式設計概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-102">LINQ to XML Programming Overview (Visual Basic)</span></span>
<span data-ttu-id="7063b-103">這些主題提供有關 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 類別的高階概觀資訊，以及關於其中三個最重要類別的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7063b-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7063b-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="7063b-104">In This Section</span></span>  
  
|<span data-ttu-id="7063b-105">主題</span><span class="sxs-lookup"><span data-stu-id="7063b-105">Topic</span></span>|<span data-ttu-id="7063b-106">說明</span><span class="sxs-lookup"><span data-stu-id="7063b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7063b-107">函數式與程序性程式設計 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-107">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="7063b-108">提供兩個撰寫 LINQ to XML 應用程式之準則方法的高階檢視。</span><span class="sxs-lookup"><span data-stu-id="7063b-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="7063b-109">LINQ to XML 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-109">LINQ to XML Classes Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="7063b-110">提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 類別的概觀。</span><span class="sxs-lookup"><span data-stu-id="7063b-110">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes.</span></span>|  
|[<span data-ttu-id="7063b-111">XElement 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-111">XElement Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="7063b-112">說明代表 XML 項目的 <xref:System.Xml.Linq.XElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="7063b-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="7063b-113"><xref:System.Xml.Linq.XElement> 是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 類別階層中的其中一個基礎類別。</span><span class="sxs-lookup"><span data-stu-id="7063b-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="7063b-114">XAttribute 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-114">XAttribute Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="7063b-115">說明代表 XML 屬性的 <xref:System.Xml.Linq.XAttribute> 類別。</span><span class="sxs-lookup"><span data-stu-id="7063b-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="7063b-116">XDocument 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-116">XDocument Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="7063b-117">說明代表 XML 文件的 <xref:System.Xml.Linq.XDocument> 類別。</span><span class="sxs-lookup"><span data-stu-id="7063b-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="7063b-118">如何： 建置 LINQ to XML 範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-118">How to: Build LINQ to XML Examples (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="7063b-119">包含`Imports`建置 LINQ to XML 範例所需的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7063b-119">Contains the `Imports` statements that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7063b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7063b-120">See Also</span></span>  
 [<span data-ttu-id="7063b-121">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063b-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
