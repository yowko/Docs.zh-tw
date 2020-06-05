---
title: 如何：修改 XML 常值
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: a2ac2e9802d4c8ab522bb430d15cce5616430437
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374871"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>如何：修改 XML 常值 (Visual Basic)

Visual Basic 提供便利的方式來修改 XML 常值。 您可以新增或刪除專案和屬性，也可以使用新的 XML 元素來取代現有的專案。 本主題提供數個範例，說明如何修改現有的 XML 常值。

### <a name="to-modify-the-value-of-an-xml-literal"></a>修改 XML 常值

1. 若要修改 XML 常值的值，請取得 XML 常值的參考，並將 `Value` 屬性設為所需的值。

    下列程式碼範例會更新 \<Price> XML 檔中所有元素的值。

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。

    來源 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    修改過的 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > `Value`屬性會參考集合中的第一個 XML 元素。 如果集合中有一個以上的專案具有相同的名稱，則設定 `Value` 屬性只會影響集合中的第一個元素。

### <a name="to-add-an-attribute-to-an-xml-literal"></a>若要將屬性加入至 XML 常值

1. 若要將屬性加入至 XML 常值，請先取得 XML 常值的參考。 然後，您可以加入新的 XML 屬性軸屬性來新增屬性。 您也可以使用方法，將新的 <xref:System.Xml.Linq.XAttribute> 物件加入至 XML 常值 <xref:System.Xml.Linq.XContainer.Add%2A> 。 下列範例會顯示這兩個選項。

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。

    來源 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    修改過的 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    如需 XML 屬性軸屬性的詳細資訊，請參閱[Xml 屬性軸屬性](../../../language-reference/xml-axis/xml-attribute-axis-property.md)。

### <a name="to-add-an-element-to-an-xml-literal"></a>若要將元素加入至 XML 常值

1. 若要將元素加入至 XML 常值，請先取得 XML 常值的參考。 接著，您可以使用方法，將新的物件加入為專案的 <xref:System.Xml.Linq.XElement> 最後一個子專案 <xref:System.Xml.Linq.XContainer.Add%2A> 。 您可以使用方法，將新的 <xref:System.Xml.Linq.XElement> 物件加入為第一個子項目 <xref:System.Xml.Linq.XContainer.AddFirst%2A> 。

    若要在相對於其他子項目的特定位置加入新專案，請先取得相鄰子項目的參考。 接著，您可以 <xref:System.Xml.Linq.XElement> 使用方法，在連續的子項目之前加入新的物件 <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> 。 您也可以 <xref:System.Xml.Linq.XElement> 使用方法，在連續的子項目後面加入新的物件 <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> 。

    下列範例顯示每個技術的範例。

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。

    來源 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    修改過的 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>若要從 XML 常值中移除元素或屬性

1. 若要從 XML 常值中移除元素或屬性，請取得元素或屬性的參考，並呼叫 `Remove` 方法，如下列範例所示。

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。

    來源 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    修改過的 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    若要從 XML 常值中移除所有元素或屬性，請取得 XML 常值的參考，並呼叫 <xref:System.Xml.Linq.XElement.RemoveAll%2A> 方法。

### <a name="to-modify-an-xml-literal"></a>修改 XML 常值

1. 若要變更 XML 元素的名稱，請先取得元素的參考。 接著，您可以建立新 <xref:System.Xml.Linq.XElement> 的物件，其中包含新的名稱，並將新 <xref:System.Xml.Linq.XElement> 物件傳遞至 <xref:System.Xml.Linq.XNode.ReplaceWith%2A> 現有物件的方法 <xref:System.Xml.Linq.XElement> 。

    如果您要取代的元素具有必須保留的子項目，請將新物件的值設定 <xref:System.Xml.Linq.XElement> 為現有專案的 <xref:System.Xml.Linq.XContainer.Nodes%2A> 屬性。 這會將新元素的值設定為現有專案的內部 XML。 否則，您可以將新元素的值設定為 `Value` 現有元素的屬性。

    下列程式碼範例會以元素取代所有專案 \<Description> \<Abstract> 。 元素的內容 \<Description> 會 \<Abstract> 使用物件的屬性保留在新的專案中 <xref:System.Xml.Linq.XContainer.Nodes%2A> \<Description> <xref:System.Xml.Linq.XElement> 。

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。

    來源 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    修改過的 XML：

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中管理 XML](manipulating-xml.md)
- [XML](index.md)
- [如何：從檔案、字串或資料流載入 XML](how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../linq/index.md)
- [Visual Basic 中的 LINQ 簡介](../linq/introduction-to-linq.md)
