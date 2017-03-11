---
title: "How to: Modify XML Literals (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML axis [Visual Basic], Value"
  - "XML literals [Visual Basic]"
  - "XML literals [Visual Basic], modifying"
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Modify XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 為修改 XML 常值 \(Literal\) 提供了方便的方法。  您可以加入或刪除項目和屬性，也可以用新的 XML 項目取代現有項目。  本主題提供幾個修改現有 XML 常值的範例。  
  
### 若要修改 XML 常值的值  
  
1.  若要修改 XML 常值的值，請先取得 XML 常值的參考，並將 `Value` 屬性 \(Property\) 設定為所要的值。  
  
     下列程式碼範例會更新 XML 文件中所有 \<Price\> 項目的值。  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/visualbasic/VbXmlSamples2/Module2.vb#4)]  
  
     下列顯示範例來源 XML 和本程式碼範例中修改過的 XML。  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
    >  `Value` 屬性 \(Property\) 會參考集合中的第一個 XML 項目。  如果集合中有多個同名的項目，則設定 `Value` 屬性 \(Property\) 只會影響集合中的第一個項目。  
  
### 若要將屬性加入至 XML 常值  
  
1.  若要將屬性 \(Attribute\) 加入至 XML 常值，請先取得 XML 常值的參考。  接著您可以加入新的 XML 屬性 \(Attribute\) 軸屬性 \(Property\)，即可加入屬性 \(Attribute\)。  您也可以使用 <xref:System.Xml.Linq.XContainer.Add%2A> 方法將新的 <xref:System.Xml.Linq.XAttribute> 物件加入至 XML 常值。  下列範例顯示這兩種選項。  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/visualbasic/VbXmlSamples2/Module2.vb#5)]  
  
     下列顯示範例來源 XML 和本程式碼範例中修改過的 XML。  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     如需 XML 屬性 \(Attribute\) 軸屬性 \(Property\) 的詳細資訊，請參閱 [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)。  
  
### 若要將項目加入至 XML 常值  
  
1.  若要將項目加入至 XML 常值，請先取得 XML 常值的參考。  接著您可以使用 <xref:System.Xml.Linq.XContainer.Add%2A> 方法，將新 <xref:System.Xml.Linq.XElement> 物件加入成為項目的最後一個子項目。  您可以使用 <xref:System.Xml.Linq.XContainer.AddFirst%2A> 方法，將新的 <xref:System.Xml.Linq.XElement> 物件加入成為第一個子項目。  
  
     若要將新項目加入至相對於其他子項目的特定位置，請先取得相鄰子項目的參考。  接著您可以使用 <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> 方法，將新 <xref:System.Xml.Linq.XElement> 物件加入至相鄰子項目的前面。  您也可以使用 <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> 方法，將新 <xref:System.Xml.Linq.XElement> 物件加入至相鄰子項目的後面。  
  
     下列範例顯示每項技巧的範例。  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/visualbasic/VbXmlSamples2/Module2.vb#6)]  
  
     下列顯示範例來源 XML 和本程式碼範例中修改過的 XML。  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
### 若要從 XML 常值移除項目或屬性  
  
1.  若要從 XML 常值移除項目或屬性 \(Attribute\)，請先取得該項目或屬性 \(Attribute\) 的參考，然後呼叫 `Remove` 方法，如下列範例所示。  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/visualbasic/VbXmlSamples2/Module2.vb#7)]  
  
     下列顯示範例來源 XML 和本程式碼範例中修改過的 XML。  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
      </Book> </Catalog>  
    ```  
  
     若要移除 XML 常值的所有項目或屬性 \(Attribute\)，請先取得 XML 常值的參考，然後呼叫 <xref:System.Xml.Linq.XElement.RemoveAll%2A> 方法。  
  
### 若要修改 XML 常值  
  
1.  若要變更 XML 項目的名稱，請先取得該項目的參考。  接著您可以建立具有新名稱的新 <xref:System.Xml.Linq.XElement> 物件，並將新 <xref:System.Xml.Linq.XElement> 物件傳遞至現有 <xref:System.Xml.Linq.XElement> 物件的 <xref:System.Xml.Linq.XNode.ReplaceWith%2A> 方法。  
  
     如果要取代的項目具有需保留的子項目，請將新 <xref:System.Xml.Linq.XElement> 物件的值設為現有項目的 <xref:System.Xml.Linq.XContainer.Nodes%2A> 屬性 \(Property\)。  如此會將新項目的值設為現有項目的內部 XML。  否則，您可以將新項目的值設為現有項目的 `Value` 屬性 \(Property\)。  
  
     下列程式碼範例會將所有 \<Description\> 項目都取代為 \<Abstract\> 項目。  其中會使用 \<Description\> <xref:System.Xml.Linq.XElement> 物件的 <xref:System.Xml.Linq.XContainer.Nodes%2A> 屬性 \(Property\)，將 \<Description\> 項目的內容保留在新 \<Abstract\> 項目中。  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/visualbasic/VbXmlSamples2/Module2.vb#8)]  
  
     下列顯示範例來源 XML 和本程式碼範例中修改過的 XML。  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>     <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>     <Abstract>  
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
  
## 請參閱  
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)