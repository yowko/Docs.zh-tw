---
title: "XElement 類別概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4b46f3cb5e0d59105fbc31424a0408c3421d9cac
ms.lasthandoff: 03/13/2017

---
# <a name="xelement-class-overview-visual-basic"></a>XElement 類別概觀 (Visual Basic)
<xref:System.Xml.Linq.XElement>類別是其中一個基礎類別中[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]。</xref:System.Xml.Linq.XElement> 它代表 XML 項目。 您可以使用這個類別來建立項目；變更項目的內容；加入、變更或刪除子項目；將屬性加入到項目中；或以文字格式序列化項目的內容。 您也可以與其他類別中的互通<xref:System.Xml?displayProperty=fullName>，例如<xref:System.Xml.XmlReader>， <xref:System.Xml.XmlWriter>，和<xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> </xref:System.Xml?displayProperty=fullName>  
  
## <a name="xelement-functionality"></a>XElement 功能  
 本主題描述<xref:System.Xml.Linq.XElement>類別</xref:System.Xml.Linq.XElement>所提供的功能  
  
### <a name="constructing-xml-trees"></a>建構 XML 樹狀結構  
 您可以用各種方式建構 XML 樹狀結構，包括：  
  
-   您可以在程式碼中建構 XML 樹狀結構。 如需詳細資訊，請參閱[建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)。  
  
-   您可以剖析來自各種來源，包括 XML <xref:System.IO.TextReader>，文字檔案或網址 (URL)。</xref:System.IO.TextReader> 如需詳細資訊，請參閱[剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)。  
  
-   您可以使用<xref:System.Xml.XmlReader>填入樹狀結構。</xref:System.Xml.XmlReader> 如需詳細資訊，請參閱<xref:System.Xml.Linq.XNode.ReadFrom%2A>。</xref:System.Xml.Linq.XNode.ReadFrom%2A>  
  
-   如果您有模組可以將內容寫入到<xref:System.Xml.XmlWriter>，您可以使用<xref:System.Xml.Linq.XContainer.CreateWriter%2A>方法來建立寫入器、 將寫入器傳遞到模組，然後使用寫入內容<xref:System.Xml.XmlWriter>填入 XML 樹狀結構。</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XContainer.CreateWriter%2A> </xref:System.Xml.XmlWriter>  
  
 不過，建立 XML 樹狀結構最常見的方式為下：  
  
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
  
 建立 XML 樹狀結構的另一個常見技術牽涉到使用結果[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢來填入 XML 樹狀結構，如下列範例所示︰  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>序列化 XML 樹狀結構  
 您可以序列化到 XML 樹狀結構<xref:System.IO.File>、 <xref:System.IO.TextWriter>，或<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File>  
  
 如需詳細資訊，請參閱[序列化 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)。  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>透過座標軸方法擷取 XML 資料  
 您可以使用座標軸方法來擷取屬性、子項目、子系項目以及祖系項目。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢會在座標軸方法上操作，而且會提供數種具彈性而且功能強大的方式，導覽並處理 XML 樹狀結構。  
  
 如需詳細資訊，請參閱[LINQ to XML 軸心方法 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)。  
  
### <a name="querying-xml-trees"></a>查詢 XML 樹狀  
 您可以撰寫[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]從 XML 樹狀結構中擷取資料的查詢。  
  
 如需詳細資訊，請參閱[查詢 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)。  
  
### <a name="modifying-xml-trees"></a>修改 XML 樹狀  
 您可以用各種方式修改項目，包括變更其內容或屬性。 您也可以從其父代移除項目。  
  
 如需詳細資訊，請參閱[修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 程式設計概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
