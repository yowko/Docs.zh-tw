---
title: XDocument 類別總覽
description: LINQ to XML 的 XDocument 類別包含有效 XML 檔所需的資訊。 在許多情況下，您不需要 XDocument 物件的功能，也可以改用 System.xml.linq.xelement> 物件。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552107"
---
# <a name="xdocument-class-overview"></a>XDocument 類別總覽

<xref:System.Xml.Linq.XDocument>類別包含有效 xml 檔所需的資訊，其中包括 XML 宣告、處理指示和批註。

<xref:System.Xml.Linq.XDocument>如果您需要類別所提供的特定功能，您只需要建立物件 <xref:System.Xml.Linq.XDocument> 。 在許多情況下，您可以直接使用 <xref:System.Xml.Linq.XElement>。 直接使用 <xref:System.Xml.Linq.XElement> 是較簡單的程式設計模型。

<xref:System.Xml.Linq.XDocument> 衍生自 <xref:System.Xml.Linq.XContainer> ，因此可以包含子節點。 不過，<xref:System.Xml.Linq.XDocument> 物件可以有只有一個 <xref:System.Xml.Linq.XElement> 子節點。 這會反映 XML 標準，也就是說 XML 文件中只能有一個根項目 (Root Element)。

## <a name="components-of-xdocument"></a>XDocument 的元件

<xref:System.Xml.Linq.XDocument> 可以包含下列項目：

- 一個 <xref:System.Xml.Linq.XDeclaration> 物件。 <xref:System.Xml.Linq.XDeclaration> 可讓您指定 XML 宣告的相關部分： XML 版本、檔的編碼，以及 XML 檔是否是獨立的。
- 一個 <xref:System.Xml.Linq.XElement> 物件。 此物件是 XML 檔的根節點。
- 任何數目的 <xref:System.Xml.Linq.XProcessingInstruction> 物件。 處理指示會將資訊傳達到處理 XML 的應用程式。
- 任何數目的 <xref:System.Xml.Linq.XComment> 物件。 這些註解將是根項目的同層級。 物件不能 <xref:System.Xml.Linq.XComment> 是清單中的第一個引數，因為它對於 XML 檔的開頭不能是批註。
- 一個適用於 DTD 的 <xref:System.Xml.Linq.XDocumentType>。

當您序列化 <xref:System.Xml.Linq.XDocument> 時，即使 `XDocument.Declaration` 為 `null`，如果寫入器已將 `Writer.Settings.OmitXmlDeclaration` 設定為 `false` (預設值)，則輸出將會有 XML 宣告。

根據預設，LINQ to XML 會將版本設定為 "1.0"，並將編碼設定為 "utf-8"。

## <a name="use-xelement-without-xdocument"></a>使用 System.xml.linq.xelement> 而不 XDocument

如先前所述， <xref:System.Xml.Linq.XElement> 類別是 LINQ to XML 程式設計介面中的主要類別。 在許多情況下，您的應用程式不需要建立檔。 藉由使用 <xref:System.Xml.Linq.XElement> 類別，您可以：

- 建立 XML 樹狀結構。
- 將其他 XML 樹狀結構新增至其中。
- 修改 XML 樹狀結構。
- 將其儲存。

## <a name="use-xdocument"></a>使用 XDocument

若要建構 <xref:System.Xml.Linq.XDocument>，請使用功能結構，如同您建構 <xref:System.Xml.Linq.XElement> 物件時所執行的操作。

下列範例會建立 <xref:System.Xml.Linq.XDocument> 物件及其相關聯的包含物件。

```csharp
XDocument d = new XDocument(
    new XComment("This is a comment."),
    new XProcessingInstruction("xml-stylesheet",
        "href='mystyle.css' title='Compact' type='text/css'"),
    new XElement("Pubs",
        new XElement("Book",
            new XElement("Title", "Artifacts of Roman Civilization"),
            new XElement("Author", "Moreno, Jordao")
        ),
        new XElement("Book",
            new XElement("Title", "Midieval Tools and Implements"),
            new XElement("Author", "Gazit, Inbar")
        )
    ),
    new XComment("This is another comment.")
);
d.Declaration = new XDeclaration("1.0", "utf-8", "true");
Console.WriteLine(d);

d.Save("test.xml");
```

```vb
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>
                       <!--This is a comment.-->
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
                       <Pubs>
                           <Book>
                               <Title>Artifacts of Roman Civilization</Title>
                               <Author>Moreno, Jordao</Author>
                           </Book>
                           <Book>
                               <Title>Midieval Tools and Implements</Title>
                               <Author>Gazit, Inbar</Author>
                           </Book>
                       </Pubs>
                       <!--This is another comment.-->
doc.Save("test.xml")
```

此範例會在 test.xml 中產生下列輸出：

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--This is a comment.-->
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
<Pubs>
  <Book>
    <Title>Artifacts of Roman Civilization</Title>
    <Author>Moreno, Jordao</Author>
  </Book>
  <Book>
    <Title>Midieval Tools and Implements</Title>
    <Author>Gazit, Inbar</Author>
  </Book>
</Pubs>
<!--This is another comment.-->
```

## <a name="see-also"></a>另請參閱

- [LINQ to XML 總覽](linq-xml-overview.md)
