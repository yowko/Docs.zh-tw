---
title: 總覽-LINQ to XML
description: LINQ to XML 提供記憶體中的 XML 程式設計介面，它是以 .NET 功能為基礎，並且相當於更新的 DOM API。
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552237"
---
# <a name="linq-to-xml-overview"></a><span data-ttu-id="553a0-103">LINQ to XML 總覽</span><span class="sxs-lookup"><span data-stu-id="553a0-103">LINQ to XML overview</span></span>

<span data-ttu-id="553a0-104">LINQ to XML 提供運用 .NET Language-Integrated Query (LINQ) Framework 的記憶體中 XML 程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="553a0-104">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="553a0-105">LINQ to XML 會使用 .NET 功能，而且相當於更新的、重新設計的文件物件模型 (DOM) XML 程式發展介面。</span><span class="sxs-lookup"><span data-stu-id="553a0-105">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="553a0-106">XML 已被廣泛採用為格式化許多內容之資料的方式。</span><span class="sxs-lookup"><span data-stu-id="553a0-106">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="553a0-107">例如，您可以在 Web、組態檔、Microsoft Office Word 檔案與資料庫中發現 XML。</span><span class="sxs-lookup"><span data-stu-id="553a0-107">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

<span data-ttu-id="553a0-108">LINQ to XML 是使用 XML 進行程式設計的最新、重新設計的方法。</span><span class="sxs-lookup"><span data-stu-id="553a0-108">LINQ to XML is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="553a0-109">它會提供檔物件模型 (DOM) 的記憶體中檔修改功能，並支援 LINQ 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="553a0-109">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="553a0-110">雖然這些查詢運算式在語法上與 XPath 不同，但是它們會提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="553a0-110">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="553a0-111">LINQ to XML 開發人員</span><span class="sxs-lookup"><span data-stu-id="553a0-111">LINQ to XML developers</span></span>

<span data-ttu-id="553a0-112">LINQ to XML 以各種開發人員為目標。</span><span class="sxs-lookup"><span data-stu-id="553a0-112">LINQ to XML targets a variety of developers.</span></span> <span data-ttu-id="553a0-113">針對只想要完成一些工作的一般開發人員，LINQ to XML 提供類似 SQL 的查詢體驗，讓 XML 更容易。</span><span class="sxs-lookup"><span data-stu-id="553a0-113">For an average developer who just wants to get something done, LINQ to XML makes XML easier by providing a query experience that's similar to SQL.</span></span> <span data-ttu-id="553a0-114">只要稍微研究，程式設計人員就可以學會如何以自己選擇的程式語言來撰寫簡潔而且功能強大的查詢。</span><span class="sxs-lookup"><span data-stu-id="553a0-114">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="553a0-115">專業開發人員可以使用 LINQ to XML 大幅提高生產力。</span><span class="sxs-lookup"><span data-stu-id="553a0-115">Professional developers can use LINQ to XML to greatly increase their productivity.</span></span> <span data-ttu-id="553a0-116">藉由 LINQ to XML，他們可以撰寫較少的程式碼，更具表達性、更精簡且更強大。</span><span class="sxs-lookup"><span data-stu-id="553a0-116">With LINQ to XML, they can write less code that's more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="553a0-117">他們可以同時使用多個資料網域的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="553a0-117">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="linq-to-xml-is-an-xml-programming-interface"></a><span data-ttu-id="553a0-118">LINQ to XML 是 XML 程式設計介面</span><span class="sxs-lookup"><span data-stu-id="553a0-118">LINQ to XML is an XML programming interface</span></span>

<span data-ttu-id="553a0-119">LINQ to XML 是已啟用 LINQ 的記憶體內部 XML 程式設計介面，可讓您在 .NET 程式設計語言中使用 XML。</span><span class="sxs-lookup"><span data-stu-id="553a0-119">LINQ to XML is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

<span data-ttu-id="553a0-120">LINQ to XML 與檔物件模型 (DOM) 一樣，它會將 XML 檔帶入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="553a0-120">LINQ to XML is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="553a0-121">您可以查詢與修改文件，並在修改後儲存到檔案，或將其序列化並透過網際網路傳送。</span><span class="sxs-lookup"><span data-stu-id="553a0-121">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="553a0-122">但是，LINQ to XML 與 DOM 不同：</span><span class="sxs-lookup"><span data-stu-id="553a0-122">However, LINQ to XML differs from DOM:</span></span>

- <span data-ttu-id="553a0-123">它提供了較輕量且更容易使用的新物件模型。</span><span class="sxs-lookup"><span data-stu-id="553a0-123">It provides a new object model that's lighter weight and easier to work with.</span></span>
- <span data-ttu-id="553a0-124">它會利用 c # 和 Visual Basic 中的語言功能。</span><span class="sxs-lookup"><span data-stu-id="553a0-124">It takes advantage of language features in C# and Visual Basic.</span></span>

<span data-ttu-id="553a0-125">LINQ to XML 最重要的優點是它與與語言整合的查詢 (LINQ) 的整合。</span><span class="sxs-lookup"><span data-stu-id="553a0-125">The most important advantage of LINQ to XML is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="553a0-126">這種整合可讓您在記憶體中 XML 文件上撰寫查詢以擷取項目和屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="553a0-126">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="553a0-127">LINQ to XML 的查詢功能可在功能 (中進行比較，不過不像 XPath 和 XQuery 的語法) 。</span><span class="sxs-lookup"><span data-stu-id="553a0-127">The query capability of LINQ to XML is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="553a0-128">C # 與 Visual Basic 的 LINQ 整合提供更強的型別、編譯時間檢查，以及改善的偵錯工具支援。</span><span class="sxs-lookup"><span data-stu-id="553a0-128">The integration of LINQ in C# and Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="553a0-129">LINQ to XML 的另一個優點是能夠使用查詢結果做為和物件的參數， <xref:System.Xml.Linq.XElement> 並 <xref:System.Xml.Linq.XAttribute> 可讓您建立 XML 樹狀結構的強大方法。</span><span class="sxs-lookup"><span data-stu-id="553a0-129">Another advantage of LINQ to XML is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="553a0-130">此方法稱為「功能建構」\*\*，可讓開發人員輕鬆將 XML 樹狀結構從某種圖形轉換為另一種圖形。</span><span class="sxs-lookup"><span data-stu-id="553a0-130">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="553a0-131">例如，您可能會有一般的 XML 採購順序，如 [範例 xml 檔：典型採購訂單](sample-xml-file-typical-purchase-order.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="553a0-131">For example, you might have a typical XML purchase order as described in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span> <span data-ttu-id="553a0-132">您可以使用 LINQ to XML 來執行下列查詢，以取得訂單中每個專案專案的元件編號屬性值：</span><span class="sxs-lookup"><span data-stu-id="553a0-132">By using LINQ to XML, you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

<span data-ttu-id="553a0-133">在 c # 中，這可以用方法語法形式重寫：</span><span class="sxs-lookup"><span data-stu-id="553a0-133">In C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="553a0-134">另一個範例是，您可能會想要一份值大於 $100 之項目的清單 (以零件編號排序)。</span><span class="sxs-lookup"><span data-stu-id="553a0-134">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="553a0-135">若要取得此資訊，您可以執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="553a0-135">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

<span data-ttu-id="553a0-136">同樣地，在 c # 中，這可以用方法語法形式重寫：</span><span class="sxs-lookup"><span data-stu-id="553a0-136">Again, in C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="553a0-137">除了這些 LINQ 功能，LINQ to XML 還提供改良的 XML 程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="553a0-137">In addition to these LINQ capabilities, LINQ to XML provides an improved XML programming interface.</span></span> <span data-ttu-id="553a0-138">使用 LINQ to XML，您可以：</span><span class="sxs-lookup"><span data-stu-id="553a0-138">Using LINQ to XML, you can:</span></span>

- <span data-ttu-id="553a0-139">[從檔案](load-xml-file.md)或[資料流程](stream-xml-fragments-xmlreader.md)載入 XML。</span><span class="sxs-lookup"><span data-stu-id="553a0-139">Load XML from [files](load-xml-file.md) or [streams](stream-xml-fragments-xmlreader.md).</span></span>
- <span data-ttu-id="553a0-140">將 XML 序列化為檔案或資料流。</span><span class="sxs-lookup"><span data-stu-id="553a0-140">Serialize XML to files or streams.</span></span>
- <span data-ttu-id="553a0-141">使用功能結構從頭開始建立 XML。</span><span class="sxs-lookup"><span data-stu-id="553a0-141">Create XML from scratch by using functional construction.</span></span>
- <span data-ttu-id="553a0-142">使用類似 XPath 的座標軸查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="553a0-142">Query XML using XPath-like axes.</span></span>
- <span data-ttu-id="553a0-143">使用 <xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A> 和 <xref:System.Xml.Linq.XElement.SetValue%2A> 之類的方法管理記憶體中 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="553a0-143">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>
- <span data-ttu-id="553a0-144">使用 XSD 驗證 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="553a0-144">Validate XML trees using XSD.</span></span>
- <span data-ttu-id="553a0-145">使用這些功能的組合，將 XML 樹狀結構從一個組織結構轉換為另一個組織結構。</span><span class="sxs-lookup"><span data-stu-id="553a0-145">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="create-xml-trees"></a><span data-ttu-id="553a0-146">建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="553a0-146">Create XML trees</span></span>

<span data-ttu-id="553a0-147">使用 LINQ to XML 進行程式設計最重要的優點之一，就是可以輕鬆地建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="553a0-147">One of the most significant advantages of programming with LINQ to XML is that it's easy to create XML trees.</span></span> <span data-ttu-id="553a0-148">例如，若要建立小型 XML 樹狀結構，您可以使用下列方式來撰寫程式碼：</span><span class="sxs-lookup"><span data-stu-id="553a0-148">For example, to create a small XML tree, you can write code as follows:</span></span>

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

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

> [!NOTE]
> <span data-ttu-id="553a0-149">範例的 Visual Basic 版本會使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="553a0-149">The Visual Basic version of the example uses XML literals.</span></span> <span data-ttu-id="553a0-150">您也可以 <xref:System.Xml.Linq.XElement> 在 Visual Basic 中使用，如同 c # 版本。</span><span class="sxs-lookup"><span data-stu-id="553a0-150">You can also use <xref:System.Xml.Linq.XElement> in Visual Basic, as in the C# version.</span></span>

<span data-ttu-id="553a0-151">如需詳細資訊，請參閱 [XML 樹狀](functional-construction.md)結構。</span><span class="sxs-lookup"><span data-stu-id="553a0-151">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="553a0-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="553a0-152">See also</span></span>

- [<span data-ttu-id="553a0-153">參考</span><span class="sxs-lookup"><span data-stu-id="553a0-153">Reference</span></span>](reference.md)
- [<span data-ttu-id="553a0-154">LINQ to XML 比較DOM</span><span class="sxs-lookup"><span data-stu-id="553a0-154">LINQ to XML vs. DOM</span></span>](linq-xml-vs-dom.md)
- [<span data-ttu-id="553a0-155">LINQ to XML 與其他 XML 技術的比較</span><span class="sxs-lookup"><span data-stu-id="553a0-155">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
