---
title: "LINQ to XML 程式設計概觀 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2dfa9b6f-5890-461d-b81c-316853c7f320
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6f5634392336d2cb74b4df44fba55f8d2ef8b0c3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-programming-overview-c"></a><span data-ttu-id="2bcae-102">LINQ to XML 程式設計概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-102">LINQ to XML Programming Overview (C#)</span></span>
<span data-ttu-id="2bcae-103">這些主題提供有關 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 類別的高階概觀資訊，以及關於其中三個最重要類別的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2bcae-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bcae-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2bcae-104">In This Section</span></span>  
  
|<span data-ttu-id="2bcae-105">主題</span><span class="sxs-lookup"><span data-stu-id="2bcae-105">Topic</span></span>|<span data-ttu-id="2bcae-106">說明</span><span class="sxs-lookup"><span data-stu-id="2bcae-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2bcae-107">函數式與程序性程式設計的比較 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-107">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="2bcae-108">提供兩個撰寫 LINQ to XML 應用程式之準則方法的高階檢視。</span><span class="sxs-lookup"><span data-stu-id="2bcae-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="2bcae-109">LINQ to XML 類別概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-109">LINQ to XML Classes Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="2bcae-110">提供 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 類別的概觀。</span><span class="sxs-lookup"><span data-stu-id="2bcae-110">Provides an overview of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes.</span></span>|  
|[<span data-ttu-id="2bcae-111">XElement 類別概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-111">XElement Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="2bcae-112">介紹 <xref:System.Xml.Linq.XElement> 類別，其代表 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2bcae-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="2bcae-113"><xref:System.Xml.Linq.XElement> 是 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 類別階層中的其中一個基礎類別。</span><span class="sxs-lookup"><span data-stu-id="2bcae-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="2bcae-114">XAttribute 類別概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-114">XAttribute Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="2bcae-115">介紹 <xref:System.Xml.Linq.XAttribute> 類別，其代表 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="2bcae-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="2bcae-116">XDocument 類別概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-116">XDocument Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="2bcae-117">介紹 <xref:System.Xml.Linq.XDocument> 類別，其代表 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="2bcae-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="2bcae-118">如何：建置 LINQ to XML 範例 (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-118">How to: Build LINQ to XML Examples (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="2bcae-119">包含建置 LINQ to XML 範例所需的 `Using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="2bcae-119">Contains the `Using` directives that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bcae-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bcae-120">See Also</span></span>  
 [<span data-ttu-id="2bcae-121">程式設計手冊 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcae-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
