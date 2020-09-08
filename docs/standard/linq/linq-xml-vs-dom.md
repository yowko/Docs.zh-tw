---
title: LINQ to XML 比較DOM
description: LINQ to XML 與 DOM 之間有一些主要差異。 LINQ to XML 支援功能結構和 XML 常值，以更好的顯示其所建立之 XML 樹狀結構的結構。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552229"
---
# <a name="linq-to-xml-vs-dom"></a>LINQ to XML 比較DOM

本文描述 LINQ to XML 和目前主流 XML 程式設計 API （W3C 檔物件模型 (DOM) 之間的一些主要差異。

## <a name="new-ways-to-construct-xml-trees"></a>建立 XML 樹狀結構的新方式

在 W3C DOM 中，您可以從下往上建置 XML 樹狀；也就是說，您可以建立文件、建立項目，然後將項目加入到文件中。

例如，下列範例會使用一般的方式，利用 Microsoft 的 DOM 執行來建立 XML 樹狀結構 <xref:System.Xml.XmlDocument> 。

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
XmlElement phone1 = doc.CreateElement("Phone");
phone1.SetAttribute("Type", "Home");
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");
phone2.SetAttribute("Type", "Work");
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";
XmlElement city = doc.CreateElement("City");
city.InnerText = "Mercer Island";
XmlElement state = doc.CreateElement("State");
state.InnerText = "WA";
XmlElement postal = doc.CreateElement("Postal");
postal.InnerText = "68042";
XmlElement address = doc.CreateElement("Address");
address.AppendChild(street1);
address.AppendChild(city);
address.AppendChild(state);
address.AppendChild(postal);
XmlElement contact = doc.CreateElement("Contact");
contact.AppendChild(name);
contact.AppendChild(phone1);
contact.AppendChild(phone2);
contact.AppendChild(address);
XmlElement contacts = doc.CreateElement("Contacts");
contacts.AppendChild(contact);
doc.AppendChild(contacts);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
Dim phone1 As XmlElement = doc.CreateElement("Phone")
phone1.SetAttribute("Type", "Home")
phone1.InnerText = "206-555-0144"
Dim phone2 As XmlElement = doc.CreateElement("Phone")
phone2.SetAttribute("Type", "Work")
phone2.InnerText = "425-555-0145"
Dim street1 As XmlElement = doc.CreateElement("Street1")
street1.InnerText = "123 Main St"
Dim city As XmlElement = doc.CreateElement("City")
city.InnerText = "Mercer Island"
Dim state As XmlElement = doc.CreateElement("State")
state.InnerText = "WA"
Dim postal As XmlElement = doc.CreateElement("Postal")
postal.InnerText = "68042"
Dim address As XmlElement = doc.CreateElement("Address")
address.AppendChild(street1)
address.AppendChild(city)
address.AppendChild(state)
address.AppendChild(postal)
Dim contact As XmlElement = doc.CreateElement("Contact")
contact.AppendChild(name)
contact.AppendChild(phone1)
contact.AppendChild(phone2)
contact.AppendChild(address)
Dim contacts As XmlElement = doc.CreateElement("Contacts")
contacts.AppendChild(contact)
doc.AppendChild(contacts)
Console.WriteLine(doc.OuterXml)
```

這種編碼樣式會隱藏 XML 樹狀結構的結構。 LINQ to XML 也支援另一種方法，也就是 *功能結構*，更適合用來顯示結構。 這種方法可以使用和函式來完成 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> 。 在 Visual Basic 中，也可以使用 XML 常值來完成。 此範例示範如何使用功能結構來建立相同的 XML 樹狀結構：

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

請注意，將要建構 XML 樹狀結構的程式碼縮排可顯示基礎 XML 的結構。 Visual Basic 版本會使用 XML 常值。

如需詳細資訊，請參閱 [XML 樹狀](functional-construction.md)結構。

## <a name="work-directly-with-xml-elements"></a>直接使用 XML 元素

當您使用 XML 進行程式設計時，您的主要焦點通常是 XML 項目，也可能是屬性。 在 LINQ to XML 中，您可以直接使用 XML 元素和屬性。 例如，您可以：

- 完全不使用文件物件來建立 XML 項目。 當您必須使用 XML 樹狀結構的片段時，這可以簡化程式設計的方式。
- 從 XML 檔案直接載入 `T:System.Xml.Linq.XElement` 物件。
- 將 `T:System.Xml.Linq.XElement` 物件序列化為檔案或資料流。

將這個 XML 項目或屬性與 W3C DOM 相比較，後者中的 XML 文件會當做 XML 樹狀結構的邏輯容器使用。 在 DOM 中，XML 節點 (包括項目和屬性) 必須在 XML 文件的內容中建立。 以下是在 DOM 中建立 name 元素的程式碼片段：

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

如果您要跨多個文件使用同一個項目，您必須匯入跨這些文件的節點。 LINQ to XML 可避免這層複雜度。

使用 LINQ to XML 時，您僅能在想要於文件根層級上加入註解或處理指示時，才能使用 <xref:System.Xml.Linq.XDocument> 類別。

## <a name="simplified-handling-of-names-and-namespaces"></a>簡化名稱和命名空間的處理

名稱、命名空間和命名空間前置詞的處理通常是 XML 程式設計的複雜部分。 LINQ to XML 藉由消除處理命名空間前置詞的需求，來簡化名稱和命名空間。 您也可以控制命名空間前置詞。 但是，如果您決定不明確控制命名空間前置詞，LINQ to XML 會在序列化期間指派命名空間前置詞（如果需要的話），否則會使用預設的命名空間進行序列化（如果不是的話）。 如果使用預設的命名空間，在產生的文件中將不會有任何命名空間前置詞。 如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

DOM 的另一個問題是，它不會讓您變更節點的名稱。 而是必須建立新的節點，並將所有子節點複製到該節點中，因此會失去原始的節點識別。 LINQ to XML 可讓您在節點上設定屬性，以避免這個問題 <xref:System.Xml.Linq.XName> 。

## <a name="static-method-support-for-loading-xml"></a>載入 XML 的靜態方法支援

LINQ to XML 可讓您使用靜態方法（而非實例方法）載入 XML。 這會簡化載入和剖析的程序。 如需詳細資訊，請參閱 [如何從檔案載入 XML](load-xml-file.md)。

## <a name="removal-of-support-for-dtd-constructs"></a>移除 DTD 結構的支援

LINQ to XML 藉由移除實體和實體參考的支援，進一步簡化 XML 程式設計。 實體的管理很複雜，而且不常使用。 移除這些支援會增進效能並簡化程式設計介面。 填入 LINQ to XML 的樹狀結構時，就會展開所有 DTD 實體。

## <a name="support-for-fragments"></a>支援片段

LINQ to XML 不會提供類別的對等專案 `XmlDocumentFragment` 。 不過，在許多情況下，此 `XmlDocumentFragment` 概念可以由類型為 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode> 或的查詢結果來處理 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> 。

## <a name="support-for-xpathnavigator"></a>支援 XPathNavigator

LINQ to XML <xref:System.Xml.XPath.XPathNavigator> 透過命名空間中的擴充方法提供支援 <xref:System.Xml.XPath?displayProperty=nameWithType> 。 如需詳細資訊，請參閱<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。

## <a name="support-for-white-space-and-indentation"></a>空白字元和縮排的支援

LINQ to XML 會比 DOM 更簡單地處理空白字元。

常見的案例是讀取縮排的 XML、建立記憶體中的 XML 樹狀結構，而不含任何空白字元文位元組點 (也就是不保留空白字元) 、對 XML 進行某些作業，然後以縮排儲存 XML。 當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。 這是 LINQ to XML 的預設行為。

其他常見案例為讀取與修改已經過刻意縮排的 XML。 您可能不想用任何方式變更這個縮排。 在 LINQ to XML 中，您可以執行下列動作：

- 載入或剖析 XML 時保留空白字元。
- 當您序列化 XML 時停用格式。

LINQ to XML 會將空白字元儲存為 <xref:System.Xml.Linq.XText> 節點，而不是使用特製化的 <xref:System.Xml.XmlNodeType.Whitespace> 節點類型，如同 DOM 一樣。

## <a name="support-for-annotations"></a>支援注釋

LINQ to XML 元素支援一組可擴充的注釋。 這在追蹤項目的其他資訊 (例如，結構描述資訊)、項目是否繫結至 UI 的相關資訊，或任何種類的應用程式專屬資訊時，相當實用。 如需詳細資訊，請參閱 [LINQ to XML 附注](linq-xml-annotations.md)。

## <a name="support-for-schema-information"></a>架構資訊的支援

LINQ to XML 透過命名空間中的擴充方法，提供 XSD 驗證的支援 <xref:System.Xml.Schema?displayProperty=nameWithType> 。 您可以驗證 XML 樹狀是以 XSD 編譯。 您可以利用 Post-Schema-Validation Infoset (PSVI) 填入 XML 樹狀。 如需詳細資訊，請參閱 [如何使用 XSD 和進行驗證](validate-xsd.md) <xref:System.Xml.Schema.Extensions> 。

## <a name="see-also"></a>另請參閱

- [LINQ to XML 總覽](linq-xml-overview.md)
