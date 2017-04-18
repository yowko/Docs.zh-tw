---
title: "XDocument 類別概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
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
ms.openlocfilehash: 31111b23adb019aad3ad55787c073dc02446291d
ms.lasthandoff: 03/13/2017

---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument 類別概觀 (Visual Basic)
本主題介紹的<xref:System.Xml.Linq.XDocument>類別。</xref:System.Xml.Linq.XDocument>  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument 類別的概觀  
 <xref:System.Xml.Linq.XDocument>類別包含有效的 XML 文件所需的資訊。</xref:System.Xml.Linq.XDocument> 這包括 XML 宣告、處理指示與註解。  
  
 請注意您只需要建立<xref:System.Xml.Linq.XDocument>物件，如果您需要特定的功能提供的<xref:System.Xml.Linq.XDocument>類別。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument> 在許多情況下，您可直接與<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement> 直接使用<xref:System.Xml.Linq.XElement>是較簡單的程式設計模型。</xref:System.Xml.Linq.XElement>  
  
 <xref:System.Xml.Linq.XDocument>衍生自<xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XDocument> 因此，它可以包含子節點。 不過，<xref:System.Xml.Linq.XDocument>物件可以有只有一個小孩<xref:System.Xml.Linq.XElement>節點。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> 這會反映 XML 標準，也就是說 XML 文件中只能有一個根項目 (Root Element)。  
  
## <a name="components-of-xdocument"></a>XDocument 的元件  
 <xref:System.Xml.Linq.XDocument>可以包含下列元素︰</xref:System.Xml.Linq.XDocument>  
  
-   一個<xref:System.Xml.Linq.XDeclaration>物件。</xref:System.Xml.Linq.XDeclaration> <xref:System.Xml.Linq.XDeclaration>可讓您指定 XML 宣告的關聯部分︰ XML 版本、 編碼方式的文件，以及是否是獨立的 XML 文件。</xref:System.Xml.Linq.XDeclaration>  
  
-   一個<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> 這是 XML 文件的根節點。  
  
-   任何數目的<xref:System.Xml.Linq.XProcessingInstruction>物件。</xref:System.Xml.Linq.XProcessingInstruction> 處理指示會將資訊傳達到處理 XML 的應用程式。  
  
-   任何數目的<xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment> 這些註解將是根項目的同層級。 <xref:System.Xml.Linq.XComment>物件不能在清單中，第一個引數，因為不是有效的 XML 文件註解的開頭。</xref:System.Xml.Linq.XComment>  
  
-   一個<xref:System.Xml.Linq.XDocumentType>適用於 DTD。</xref:System.Xml.Linq.XDocumentType>  
  
 當您序列化<xref:System.Xml.Linq.XDocument>，即使`XDocument.Declaration`是`null`，輸出將會有 XML 宣告，如果寫入器已`Writer.Settings.OmitXmlDeclaration`設為`false`（預設值）。</xref:System.Xml.Linq.XDocument>  
  
 根據預設，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 會將版本設定為 "1.0"，並將編碼設定為 "utf-8"。  
  
## <a name="using-xelement-without-xdocument"></a>在沒有 XDocument 的情況下使用 XElement  
 如先前所述，<xref:System.Xml.Linq.XElement>類別是中的主要類別[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]程式設計介面。</xref:System.Xml.Linq.XElement> 在許多情況下，您的應用程式將不需要您建立文件。 使用<xref:System.Xml.Linq.XElement>類別中，您可以建立 XML 樹狀結構中，加入其他 XML 樹狀結構、 修改 XML 樹狀結構中，並儲存它。</xref:System.Xml.Linq.XElement>  
  
## <a name="using-xdocument"></a>使用 XDocument  
 若要建構<xref:System.Xml.Linq.XDocument>，使用功能結構，就像建構<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
 下列程式碼會建立<xref:System.Xml.Linq.XDocument>物件及其相關聯所包含的物件。</xref:System.Xml.Linq.XDocument>  
  
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
  
 當您檢查 test.xml 檔案時，您會得到下列輸出：  
  
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
 [LINQ to XML 程式設計概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
