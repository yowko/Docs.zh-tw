---
title: HOW TO：修改 XML 常值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 7a01fdc9d0541b5d277c2f283e25e9a1cef3b862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636335"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>HOW TO：修改 XML 常值 (Visual Basic)
Visual Basic 提供便利的方式來修改 XML 常值。 您可以新增或刪除項目和屬性，您也可以使用新的 XML 項目取代現有的項目。 本主題提供如何修改現有的 XML 常值的數個範例。  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>若要修改 XML 常值的值  
  
1.  若要修改 XML 常值的值，取得 XML 常值和設定的參考`Value`屬性設為所需的值。  
  
     下列程式碼範例會更新所有的值\<價格 > 在 XML 文件中的項目。  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     下列示範範例來源 XML，並修改此程式碼範例中的 XML。  
  
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
    >  `Value`屬性參考集合中的第一個 XML 項目。 如果在集合中具有相同名稱的多個項目，則設定`Value`屬性會影響僅在集合中的第一個元素。  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>若要將屬性加入 XML 常值  
  
1.  若要加入 XML 常值中的屬性，請先取得 XML 常值的參考。 然後，您就可以藉由新增新的 XML 屬性軸屬性加入屬性。 您也可以加入新<xref:System.Xml.Linq.XAttribute>要使用常值 XML 物件<xref:System.Xml.Linq.XContainer.Add%2A>方法。 下列範例會示範這兩個選項。  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     下列示範範例來源 XML，並修改此程式碼範例中的 XML。  
  
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
  
     如需有關 XML 屬性軸屬性的詳細資訊，請參閱[XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)。  
  
### <a name="to-add-an-element-to-an-xml-literal"></a>XML 常值中新增項目  
  
1.  若要加入 XML 常值中的項目，請先取得 XML 常值的參考。 然後您可以加入新<xref:System.Xml.Linq.XElement>物件做為最後一個子元素所使用之項目的<xref:System.Xml.Linq.XContainer.Add%2A>方法。 您可以加入新<xref:System.Xml.Linq.XElement>物件所使用的第一個子元素<xref:System.Xml.Linq.XContainer.AddFirst%2A>方法。  
  
     若要在特定位置相對於其他子元素中新增新的項目，請先取得相鄰的子元素的參考。 然後您可以加入新<xref:System.Xml.Linq.XElement>之前使用相鄰的子元素物件<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>方法。 您也可以加入新<xref:System.Xml.Linq.XElement>之後使用相鄰的子元素物件<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>方法。  
  
     下列範例顯示的每一個技巧的範例。  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     下列示範範例來源 XML，並修改此程式碼範例中的 XML。  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>若要移除 XML 常值中的項目或屬性  
  
1.  若要移除 XML 常值的元素或屬性，取得參考的項目或屬性和呼叫`Remove`方法，如下列範例所示。  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     下列示範範例來源 XML，並修改此程式碼範例中的 XML。  
  
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
      </Book></Catalog>  
    ```  
  
     若要移除 XML 常值的所有項目或屬性，取得 XML 常值的參考，並呼叫<xref:System.Xml.Linq.XElement.RemoveAll%2A>方法。  
  
### <a name="to-modify-an-xml-literal"></a>若要修改 XML 常值  
  
1.  若要變更的 XML 項目名稱，請先取得項目的參考。 然後您可以建立新<xref:System.Xml.Linq.XElement>有新的名稱，並傳遞新的物件<xref:System.Xml.Linq.XElement>物件<xref:System.Xml.Linq.XNode.ReplaceWith%2A>方法的現有<xref:System.Xml.Linq.XElement>物件。  
  
     如果您要取代的項目必須保留的子元素，來設定新值<xref:System.Xml.Linq.XElement>物件至<xref:System.Xml.Linq.XContainer.Nodes%2A>現有項目的屬性。 這會將新的項目值的現有項目內部的 xml。 否則，您可以設定為新的項目值`Value`現有項目的屬性。  
  
     下列程式碼範例會取代所有\<描述 > 項目\<抽象 > 項目。 內容\<描述 > 項目會保留在新\<抽象 > 所使用的項目<xref:System.Xml.Linq.XContainer.Nodes%2A>屬性\<描述 ><xref:System.Xml.Linq.XElement>物件。  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     下列示範範例來源 XML，並修改此程式碼範例中的 XML。  
  
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
- [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [如何：從檔案、 字串或 Stream 載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
