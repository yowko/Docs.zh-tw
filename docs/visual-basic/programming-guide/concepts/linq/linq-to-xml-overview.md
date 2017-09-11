---
title: "LINQ to XML 概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
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
ms.openlocfilehash: 4732aaa64119ba98ab11205e8c93dd8d3eb62d4b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="1faf6-102">LINQ to XML 概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1faf6-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="1faf6-103">XML 已被廣泛採用為格式化許多內容之資料的方式。</span><span class="sxs-lookup"><span data-stu-id="1faf6-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="1faf6-104">例如，您可以在 Web、組態檔、Microsoft Office Word 檔案與資料庫中發現 XML。</span><span class="sxs-lookup"><span data-stu-id="1faf6-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="1faf6-105"> 是經過重新設計，用以進行 XML 程式設計的最新方法。</span><span class="sxs-lookup"><span data-stu-id="1faf6-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="1faf6-106">它提供文件物件模型 (DOM) 的記憶體中文件修改能力，而且支援 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="1faf6-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expressions.</span></span> <span data-ttu-id="1faf6-107">雖然這些查詢運算式在語法上與 XPath 不同，但是它們會提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="1faf6-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="1faf6-108">LINQ to XML 開發人員</span><span class="sxs-lookup"><span data-stu-id="1faf6-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="1faf6-109"> 的目標為各種開發人員。</span><span class="sxs-lookup"><span data-stu-id="1faf6-109"> targets a variety of developers.</span></span> <span data-ttu-id="1faf6-110">對於只想要完成某些事情的一般開發人員而言，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 會提供類似 SQL 的查詢經驗，讓 XML 更容易。</span><span class="sxs-lookup"><span data-stu-id="1faf6-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="1faf6-111">只要稍微研究，程式設計人員就可以學會如何以自己選擇的程式語言來撰寫簡潔而且功能強大的查詢。</span><span class="sxs-lookup"><span data-stu-id="1faf6-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="1faf6-112">專業開發人員可以使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 大量增加其產能。</span><span class="sxs-lookup"><span data-stu-id="1faf6-112">Professional developers can use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="1faf6-113">他們可以利用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 撰寫更明確、更精簡而且功能更強大的較少程式碼。</span><span class="sxs-lookup"><span data-stu-id="1faf6-113">With [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="1faf6-114">他們可以同時使用多個資料網域的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="1faf6-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="1faf6-115">何謂 LINQ to XML？</span><span class="sxs-lookup"><span data-stu-id="1faf6-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="1faf6-116"> 是一個以 LINQ 為基礎、記憶體中的 XML 程式發展介面，可讓您從 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 程式設計語言內使用 XML。</span><span class="sxs-lookup"><span data-stu-id="1faf6-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="1faf6-117">是類似文件物件模型 (DOM)，因為它會將 XML 文件帶到記憶體。</span><span class="sxs-lookup"><span data-stu-id="1faf6-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="1faf6-118">您可以查詢與修改文件，並在修改後儲存到檔案，或將其序列化並透過網際網路傳送。</span><span class="sxs-lookup"><span data-stu-id="1faf6-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="1faf6-119">不過，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]與 DOM 不同︰ 它提供新的物件模型較為輕量且更容易使用，而且會在 Visual Basic 語言功能的優點。</span><span class="sxs-lookup"><span data-stu-id="1faf6-119">However, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="1faf6-120">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 最重要的優點為其與 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] 的整合能力。</span><span class="sxs-lookup"><span data-stu-id="1faf6-120">The most important advantage of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is its integration with [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].</span></span> <span data-ttu-id="1faf6-121">這種整合可讓您在記憶體中 XML 文件上撰寫查詢以擷取項目和屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="1faf6-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="1faf6-122">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的查詢功能相當於 (雖然語法上不同) XPath 和 Xquery 的功能。</span><span class="sxs-lookup"><span data-stu-id="1faf6-122">The query capability of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="1faf6-123">整合[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]在 Visual Basic 中提供更強、 編譯時期檢查功能，以及改善偵錯工具支援。</span><span class="sxs-lookup"><span data-stu-id="1faf6-123">The integration of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="1faf6-124">另一項優點[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]是做為參數，將查詢結果的能力<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XAttribute>物件建構函式可讓建立 XML 樹狀結構的強大方法。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="1faf6-124">Another advantage of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="1faf6-125">這個方法，稱為*功能結構*，可讓開發人員輕易地將轉換 XML 樹狀結構從一個組織到另一個。</span><span class="sxs-lookup"><span data-stu-id="1faf6-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="1faf6-126">例如，您可能有典型的 XML 採購訂單中所述[範例 XML 檔︰ 典型採購訂單 (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348)。</span><span class="sxs-lookup"><span data-stu-id="1faf6-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span></span> <span data-ttu-id="1faf6-127">您可以使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 執行下列查詢，以便在採購訂單中取得每個項目的零件編號屬行值：</span><span class="sxs-lookup"><span data-stu-id="1faf6-127">By using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="1faf6-128">另一個範例是，您可能會想要一份值大於 $100 之項目的清單 (以零件編號排序)。</span><span class="sxs-lookup"><span data-stu-id="1faf6-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="1faf6-129">若要取得此資訊，您可以執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="1faf6-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="1faf6-130">除了這些[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]功能，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]提供改善的 XML 程式發展介面。</span><span class="sxs-lookup"><span data-stu-id="1faf6-130">In addition to these [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] capabilities, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="1faf6-131">利用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，您可以：</span><span class="sxs-lookup"><span data-stu-id="1faf6-131">Using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can:</span></span>  
  
-   <span data-ttu-id="1faf6-132">從檔案或資料流載入 XML。</span><span class="sxs-lookup"><span data-stu-id="1faf6-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="1faf6-133">將 XML 序列化為檔案或資料流。</span><span class="sxs-lookup"><span data-stu-id="1faf6-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="1faf6-134">使用功能結構從頭開始建立 XML。</span><span class="sxs-lookup"><span data-stu-id="1faf6-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="1faf6-135">使用類似 XPath 的座標軸查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="1faf6-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="1faf6-136">使用下列方法管理記憶體中 XML 樹狀結構<xref:System.Xml.Linq.XContainer.Add%2A>， <xref:System.Xml.Linq.XNode.Remove%2A>， <xref:System.Xml.Linq.XNode.ReplaceWith%2A>，和<xref:System.Xml.Linq.XElement.SetValue%2A>.</xref:System.Xml.Linq.XElement.SetValue%2A> </xref:System.Xml.Linq.XNode.ReplaceWith%2A> </xref:System.Xml.Linq.XNode.Remove%2A> </xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="1faf6-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="1faf6-137">使用 XSD 驗證 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="1faf6-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="1faf6-138">使用這些功能的組合，將 XML 樹狀結構從一個組織結構轉換為另一個組織結構。</span><span class="sxs-lookup"><span data-stu-id="1faf6-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="1faf6-139">建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="1faf6-139">Creating XML Trees</span></span>  
 <span data-ttu-id="1faf6-140">使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 進行程式設計其中一項最重要的優點是，建立 XML 樹狀結構很容易。</span><span class="sxs-lookup"><span data-stu-id="1faf6-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="1faf6-141">比方說，若要建立小型 XML 樹狀結構，您可以如下撰寫程式碼︰</span><span class="sxs-lookup"><span data-stu-id="1faf6-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 <span data-ttu-id="1faf6-142">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將轉譯成 XML 常值[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="1faf6-142">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler translates XML literals into [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] method calls.</span></span>  
  
 <span data-ttu-id="1faf6-143">如需詳細資訊，請參閱[建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="1faf6-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1faf6-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1faf6-144">See Also</span></span>  
 <span data-ttu-id="1faf6-145"><xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="1faf6-145"><xref:System.Xml.Linq></span></span>   
<span data-ttu-id="1faf6-146"> [使用者入門 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1faf6-146"> [Getting Started (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span></span>  
<span data-ttu-id="1faf6-147"> [LINQ to XML 在 Visual Basic 中的概觀](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1faf6-147"> [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md) </span></span>  
<span data-ttu-id="1faf6-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="1faf6-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
