---
title: LINQ to XML 概觀 (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 2394151d855d75b418616d9fa1a6f69b08cdef86
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585758"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="238ed-102">LINQ to XML 概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="238ed-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="238ed-103">XML 已被廣泛採用為格式化許多內容之資料的方式。</span><span class="sxs-lookup"><span data-stu-id="238ed-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="238ed-104">例如，您可以在 Web、組態檔、Microsoft Office Word 檔案與資料庫中發現 XML。</span><span class="sxs-lookup"><span data-stu-id="238ed-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="238ed-105">是經過重新設計，用以進行 XML 程式設計的最新方法。</span><span class="sxs-lookup"><span data-stu-id="238ed-105">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="238ed-106">它提供文件物件模型 (DOM) 的記憶體中文件修改能力，而且支援 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="238ed-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="238ed-107">雖然這些查詢運算式在語法上與 XPath 不同，但是它們會提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="238ed-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="238ed-108">LINQ to XML 開發人員</span><span class="sxs-lookup"><span data-stu-id="238ed-108">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="238ed-109">的目標為各種開發人員。</span><span class="sxs-lookup"><span data-stu-id="238ed-109">targets a variety of developers.</span></span> <span data-ttu-id="238ed-110">對於只想要完成某些事情的一般開發人員而言，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會提供類似 SQL 的查詢經驗，讓 XML 更容易。</span><span class="sxs-lookup"><span data-stu-id="238ed-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="238ed-111">只要稍微研究，程式設計人員就可以學會如何以自己選擇的程式語言來撰寫簡潔而且功能強大的查詢。</span><span class="sxs-lookup"><span data-stu-id="238ed-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="238ed-112">專業開發人員可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 大量增加其產能。</span><span class="sxs-lookup"><span data-stu-id="238ed-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="238ed-113">他們可以利用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 撰寫更明確、更精簡而且功能更強大的較少程式碼。</span><span class="sxs-lookup"><span data-stu-id="238ed-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="238ed-114">他們可以同時使用多個資料網域的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="238ed-114">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="238ed-115">何謂 LINQ to XML？</span><span class="sxs-lookup"><span data-stu-id="238ed-115">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="238ed-116">是一個啟用 LINQ 的記憶體內部 XML 程式設計介面，可讓您從 .NET Framework 程式設計語言內使用 XML。</span><span class="sxs-lookup"><span data-stu-id="238ed-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="238ed-117">如同文件物件模型 (DOM)，它會將 XML 文件帶到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="238ed-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="238ed-118">您可以查詢與修改文件，並在修改後儲存到檔案，或將其序列化並透過網際網路傳送。</span><span class="sxs-lookup"><span data-stu-id="238ed-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="238ed-119">不過，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 與 DOM 不同：它所提供的新物件模型較為輕量且較容易使用，且會利用 C# 中的語言功能。</span><span class="sxs-lookup"><span data-stu-id="238ed-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="238ed-120">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 最重要的優點為其與 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 的整合能力。</span><span class="sxs-lookup"><span data-stu-id="238ed-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="238ed-121">這種整合可讓您在記憶體中 XML 文件上撰寫查詢以擷取項目和屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="238ed-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="238ed-122">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的查詢功能相當於 (雖然語法上不同) XPath 和 Xquery 的功能。</span><span class="sxs-lookup"><span data-stu-id="238ed-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="238ed-123">整合 C# 中的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 時，可提供更強的型別、編譯時間檢查功能，以及改善的偵錯工具支援。</span><span class="sxs-lookup"><span data-stu-id="238ed-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="238ed-124">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的另一項優點是將查詢結果當做 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 物件建構函式參數的功能，可提供建立 XML 樹狀結構的強大方法。</span><span class="sxs-lookup"><span data-stu-id="238ed-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="238ed-125">此方法稱為「功能建構」，可讓開發人員輕鬆將 XML 樹狀結構從某種圖形轉換為另一種圖形。</span><span class="sxs-lookup"><span data-stu-id="238ed-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="238ed-126">例如，您可能有一個典型的 XML 訂購單，如以下連結所述：[XML 範例檔：典型訂購單 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="238ed-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="238ed-127">您可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 執行下列查詢，以便在採購訂單中取得每個項目的零件編號屬行值：</span><span class="sxs-lookup"><span data-stu-id="238ed-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="238ed-128">這可以用方法語法的形式改寫：</span><span class="sxs-lookup"><span data-stu-id="238ed-128">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="238ed-129">另一個範例是，您可能會想要一份值大於 $100 之項目的清單 (以零件編號排序)。</span><span class="sxs-lookup"><span data-stu-id="238ed-129">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="238ed-130">若要取得此資訊，您可以執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="238ed-130">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="238ed-131">同樣地，這可以用方法語法的形式改寫：</span><span class="sxs-lookup"><span data-stu-id="238ed-131">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="238ed-132">除了這些 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 功能以外，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 還提供了改善的 XML 程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="238ed-132">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="238ed-133">利用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，您可以：</span><span class="sxs-lookup"><span data-stu-id="238ed-133">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="238ed-134">從[檔案](how-to-load-xml-from-a-file.md)或[資料流](how-to-stream-xml-fragments-from-an-xmlreader.md)載入 XML。</span><span class="sxs-lookup"><span data-stu-id="238ed-134">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="238ed-135">將 XML 序列化為檔案或資料流。</span><span class="sxs-lookup"><span data-stu-id="238ed-135">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="238ed-136">使用功能結構從頭開始建立 XML。</span><span class="sxs-lookup"><span data-stu-id="238ed-136">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="238ed-137">使用類似 XPath 的座標軸查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="238ed-137">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="238ed-138">使用 <xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A> 和 <xref:System.Xml.Linq.XElement.SetValue%2A> 之類的方法管理記憶體中 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="238ed-138">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="238ed-139">使用 XSD 驗證 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="238ed-139">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="238ed-140">使用這些功能的組合，將 XML 樹狀結構從一個組織結構轉換為另一個組織結構。</span><span class="sxs-lookup"><span data-stu-id="238ed-140">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="238ed-141">建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="238ed-141">Creating XML Trees</span></span>

<span data-ttu-id="238ed-142">使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 進行程式設計其中一項最重要的優點是，建立 XML 樹狀結構很容易。</span><span class="sxs-lookup"><span data-stu-id="238ed-142">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="238ed-143">例如，若要建立小型 XML 樹狀結構，您可以使用下列方式來撰寫程式碼：</span><span class="sxs-lookup"><span data-stu-id="238ed-143">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
        new XElement("Address",
            new XElement("Street1", "123 Main St"),
            new XElement("City", "Mercer Island"),
            new XElement("State", "WA"),
            new XElement("Postal", "68042")
        )
    )
);
```

<span data-ttu-id="238ed-144">如需詳細資訊，請參閱[建立 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="238ed-144">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="238ed-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="238ed-145">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="238ed-146">使用者入門 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="238ed-146">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
