---
title: "LINQ to XML 座標軸 (C#) | Microsoft Docs"
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
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
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
ms.openlocfilehash: 696a9057d5eb9d2a8c3a263c02571a0913af89f3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-axes-c"></a><span data-ttu-id="ed2df-102">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-102">LINQ to XML Axes (C#)</span></span>
<span data-ttu-id="ed2df-103">建立 XML 樹狀結構，或將 XML 文件載入到 XML 樹狀結構後，您可以進行查詢以尋找項目和屬性並擷取其值。</span><span class="sxs-lookup"><span data-stu-id="ed2df-103">After you have created an XML tree or loaded an XML document into an XML tree, you can query it to find elements and attributes and retrieve their values.</span></span>  
  
 <span data-ttu-id="ed2df-104">在撰寫任何查詢之前，您必須了解 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 座標軸。</span><span class="sxs-lookup"><span data-stu-id="ed2df-104">Before you can write any queries, you must understand the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axes.</span></span> <span data-ttu-id="ed2df-105">有兩種類型的座標軸方法：第一種是可以在單一 <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件或 <xref:System.Xml.Linq.XNode> 物件上呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="ed2df-105">There are two kinds of axis methods: First, there are the methods that you call on a single <xref:System.Xml.Linq.XElement> object, <xref:System.Xml.Linq.XDocument> object, or <xref:System.Xml.Linq.XNode> object.</span></span> <span data-ttu-id="ed2df-106">這些方法會在單一物件上運算，然後傳回 <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute> 或 <xref:System.Xml.Linq.XNode> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ed2df-106">These methods operate on a single object and return a collection of <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, or <xref:System.Xml.Linq.XNode> objects.</span></span> <span data-ttu-id="ed2df-107">第二，在集合上有可運算的擴充方法，並傳回集合。</span><span class="sxs-lookup"><span data-stu-id="ed2df-107">Second, there are extension methods that operate on collections and return collections.</span></span> <span data-ttu-id="ed2df-108">擴充方法會列舉來源集合、在集合的每個項目上呼叫適當的座標軸方法，然後串連結果。</span><span class="sxs-lookup"><span data-stu-id="ed2df-108">The extension methods enumerate the source collection, call the appropriate axis method on each item in the collection, and concatenate the results.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed2df-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="ed2df-109">In This Section</span></span>  
  
|<span data-ttu-id="ed2df-110">主題</span><span class="sxs-lookup"><span data-stu-id="ed2df-110">Topic</span></span>|<span data-ttu-id="ed2df-111">描述</span><span class="sxs-lookup"><span data-stu-id="ed2df-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ed2df-112">LINQ to XML 座標軸概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-112">LINQ to XML Axes Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|<span data-ttu-id="ed2df-113">定義座標軸並說明如何在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢的內容中使用這些座標軸。</span><span class="sxs-lookup"><span data-stu-id="ed2df-113">Defines axes, and explains how they are used in the context of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>|  
|[<span data-ttu-id="ed2df-114">如何：擷取項目集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-114">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|<span data-ttu-id="ed2df-115">介紹 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ed2df-115">Introduces the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="ed2df-116">此方法會擷取項目之子項目的集合。</span><span class="sxs-lookup"><span data-stu-id="ed2df-116">This method retrieves a collection of the child elements of an element.</span></span>|  
|[<span data-ttu-id="ed2df-117">如何：擷取項目的值 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-117">How to: Retrieve the Value of an Element (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|<span data-ttu-id="ed2df-118">示範如何取得項目的值。</span><span class="sxs-lookup"><span data-stu-id="ed2df-118">Shows how to get the values of elements.</span></span>|  
|[<span data-ttu-id="ed2df-119">如何：篩選項目名稱 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-119">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|<span data-ttu-id="ed2df-120">顯示使用座標軸時，如何在項目名稱上篩選。</span><span class="sxs-lookup"><span data-stu-id="ed2df-120">Shows how to filter on element names when using axes.</span></span>|  
|[<span data-ttu-id="ed2df-121">如何：鏈結軸方法呼叫 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-121">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|<span data-ttu-id="ed2df-122">示範如何將呼叫鏈結到座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="ed2df-122">Shows how to chain calls to axes methods.</span></span>|  
|[<span data-ttu-id="ed2df-123">如何：擷取單一子項目 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-123">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|<span data-ttu-id="ed2df-124">顯示如何擷取項目的單一子項目 (假設有子項目的標記名稱)。</span><span class="sxs-lookup"><span data-stu-id="ed2df-124">Shows how to retrieve a single child element of an element, given the tag name of the child element.</span></span>|  
|[<span data-ttu-id="ed2df-125">如何：擷取屬性集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-125">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|<span data-ttu-id="ed2df-126">介紹 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ed2df-126">Introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="ed2df-127">這個方法會擷取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="ed2df-127">This method retrieves the attributes of an element.</span></span>|  
|[<span data-ttu-id="ed2df-128">如何：擷取單一屬性 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-128">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|<span data-ttu-id="ed2df-129">顯示如何擷取項目的單一屬性 (假設有屬性名稱)。</span><span class="sxs-lookup"><span data-stu-id="ed2df-129">Shows how to retrieve a single attribute of an element, given the attribute name.</span></span>|  
|[<span data-ttu-id="ed2df-130">如何：擷取屬性的值 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-130">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|<span data-ttu-id="ed2df-131">示範如何取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ed2df-131">Shows how to get the values of attributes.</span></span>|  
|[<span data-ttu-id="ed2df-132">如何：擷取項目的表層值 (C#)</span><span class="sxs-lookup"><span data-stu-id="ed2df-132">How to: Retrieve the Shallow Value of an Element (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|<span data-ttu-id="ed2df-133">示範如何擷取項目的表層值。</span><span class="sxs-lookup"><span data-stu-id="ed2df-133">Shows how to retrieve the shallow value of an element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed2df-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed2df-134">See Also</span></span>  
 <span data-ttu-id="ed2df-135">[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="ed2df-135">[Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
<span data-ttu-id="ed2df-136"> [程式設計手冊 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="ed2df-136"> [Programming Guide (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)</span></span>
