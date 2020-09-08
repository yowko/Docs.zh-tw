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
# <a name="linq-to-xml-overview"></a>LINQ to XML 總覽

LINQ to XML 提供運用 .NET Language-Integrated Query (LINQ) Framework 的記憶體中 XML 程式開發介面。 LINQ to XML 會使用 .NET 功能，而且相當於更新的、重新設計的文件物件模型 (DOM) XML 程式發展介面。

XML 已被廣泛採用為格式化許多內容之資料的方式。 例如，您可以在 Web、組態檔、Microsoft Office Word 檔案與資料庫中發現 XML。

LINQ to XML 是使用 XML 進行程式設計的最新、重新設計的方法。 它會提供檔物件模型 (DOM) 的記憶體中檔修改功能，並支援 LINQ 查詢運算式。 雖然這些查詢運算式在語法上與 XPath 不同，但是它們會提供類似的功能。

## <a name="linq-to-xml-developers"></a>LINQ to XML 開發人員

LINQ to XML 以各種開發人員為目標。 針對只想要完成一些工作的一般開發人員，LINQ to XML 提供類似 SQL 的查詢體驗，讓 XML 更容易。 只要稍微研究，程式設計人員就可以學會如何以自己選擇的程式語言來撰寫簡潔而且功能強大的查詢。

專業開發人員可以使用 LINQ to XML 大幅提高生產力。 藉由 LINQ to XML，他們可以撰寫較少的程式碼，更具表達性、更精簡且更強大。 他們可以同時使用多個資料網域的查詢運算式。

## <a name="linq-to-xml-is-an-xml-programming-interface"></a>LINQ to XML 是 XML 程式設計介面

LINQ to XML 是已啟用 LINQ 的記憶體內部 XML 程式設計介面，可讓您在 .NET 程式設計語言中使用 XML。

LINQ to XML 與檔物件模型 (DOM) 一樣，它會將 XML 檔帶入記憶體中。 您可以查詢與修改文件，並在修改後儲存到檔案，或將其序列化並透過網際網路傳送。 但是，LINQ to XML 與 DOM 不同：

- 它提供了較輕量且更容易使用的新物件模型。
- 它會利用 c # 和 Visual Basic 中的語言功能。

LINQ to XML 最重要的優點是它與與語言整合的查詢 (LINQ) 的整合。 這種整合可讓您在記憶體中 XML 文件上撰寫查詢以擷取項目和屬性的集合。 LINQ to XML 的查詢功能可在功能 (中進行比較，不過不像 XPath 和 XQuery 的語法) 。 C # 與 Visual Basic 的 LINQ 整合提供更強的型別、編譯時間檢查，以及改善的偵錯工具支援。

LINQ to XML 的另一個優點是能夠使用查詢結果做為和物件的參數， <xref:System.Xml.Linq.XElement> 並 <xref:System.Xml.Linq.XAttribute> 可讓您建立 XML 樹狀結構的強大方法。 此方法稱為「功能建構」**，可讓開發人員輕鬆將 XML 樹狀結構從某種圖形轉換為另一種圖形。

例如，您可能會有一般的 XML 採購順序，如 [範例 xml 檔：典型採購訂單](sample-xml-file-typical-purchase-order.md)中所述。 您可以使用 LINQ to XML 來執行下列查詢，以取得訂單中每個專案專案的元件編號屬性值：

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

在 c # 中，這可以用方法語法形式重寫：

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

另一個範例是，您可能會想要一份值大於 $100 之項目的清單 (以零件編號排序)。 若要取得此資訊，您可以執行下列查詢：

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

同樣地，在 c # 中，這可以用方法語法形式重寫：

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

除了這些 LINQ 功能，LINQ to XML 還提供改良的 XML 程式設計介面。 使用 LINQ to XML，您可以：

- [從檔案](load-xml-file.md)或[資料流程](stream-xml-fragments-xmlreader.md)載入 XML。
- 將 XML 序列化為檔案或資料流。
- 使用功能結構從頭開始建立 XML。
- 使用類似 XPath 的座標軸查詢 XML。
- 使用 <xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A> 和 <xref:System.Xml.Linq.XElement.SetValue%2A> 之類的方法管理記憶體中 XML 樹狀結構。
- 使用 XSD 驗證 XML 樹狀結構。
- 使用這些功能的組合，將 XML 樹狀結構從一個組織結構轉換為另一個組織結構。

## <a name="create-xml-trees"></a>建立 XML 樹狀結構

使用 LINQ to XML 進行程式設計最重要的優點之一，就是可以輕鬆地建立 XML 樹狀結構。 例如，若要建立小型 XML 樹狀結構，您可以使用下列方式來撰寫程式碼：

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
> 範例的 Visual Basic 版本會使用 XML 常值。 您也可以 <xref:System.Xml.Linq.XElement> 在 Visual Basic 中使用，如同 c # 版本。

如需詳細資訊，請參閱 [XML 樹狀](functional-construction.md)結構。

## <a name="see-also"></a>另請參閱

- [參考](reference.md)
- [LINQ to XML 比較DOM](linq-xml-vs-dom.md)
- [LINQ to XML 與其他 XML 技術的比較](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
