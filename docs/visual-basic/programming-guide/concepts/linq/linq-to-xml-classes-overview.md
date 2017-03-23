---
title: "LINQ to XML 類別概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 12885f93bb7e56dd66d36090d41700195313e944
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>LINQ to XML 類別概觀 (Visual Basic)
本主題提供一份[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]中的類別<xref:System.Xml.Linq>命名空間，以及個別的簡短說明。</xref:System.Xml.Linq>  
  
## <a name="linq-to-xml-classes"></a>LINQ to XML 類別  
  
### <a name="xattribute-class"></a>XAttribute 類別  
 <xref:System.Xml.Linq.XAttribute>代表 XML 屬性。</xref:System.Xml.Linq.XAttribute> 如需詳細的資訊和範例，請參閱[XAttribute 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)。  
  
### <a name="xcdata-class"></a>XCData 類別  
 <xref:System.Xml.Linq.XCData>代表 CDATA 文字節點。</xref:System.Xml.Linq.XCData>  
  
### <a name="xcomment-class"></a>XComment 類別  
 <xref:System.Xml.Linq.XComment>代表 XML 註解。</xref:System.Xml.Linq.XComment>  
  
### <a name="xcontainer-class"></a>XContainer 類別  
 <xref:System.Xml.Linq.XContainer>是可以有子節點的所有節點的抽象基底類別。</xref:System.Xml.Linq.XContainer> 下列類別衍生自<xref:System.Xml.Linq.XContainer>類別︰</xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration 類別  
 <xref:System.Xml.Linq.XDeclaration>代表 XML 宣告。</xref:System.Xml.Linq.XDeclaration> XML 宣告用於宣告 XML 版本與文件的編碼。 此外，XML 宣告會指定 XML 文件是否為獨立的。 如果文件是獨立的，外部 DTD 或內部子集所參考的外部參數實體 (Entity) 就不會包含任何外部標記宣告。  
  
### <a name="xdocument-class"></a>XDocument 類別  
 <xref:System.Xml.Linq.XDocument>表示 XML 文件。</xref:System.Xml.Linq.XDocument> 如需詳細的資訊和範例，請參閱[XDocument 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)。  
  
### <a name="xdocumenttype-class"></a>XDocumentType 類別  
 <xref:System.Xml.Linq.XDocumentType>代表 XML 文件類型定義 (DTD)。</xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xelement-class"></a>XElement 類別  
 <xref:System.Xml.Linq.XElement>表示 XML 項目。</xref:System.Xml.Linq.XElement> 如需詳細的資訊和範例，請參閱[XElement 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)。  
  
### <a name="xname-class"></a>XName 類別  
 <xref:System.Xml.Linq.XName>代表項目的名稱 (<xref:System.Xml.Linq.XElement>) 和屬性 (<xref:System.Xml.Linq.XAttribute>)。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XName> 如需詳細的資訊和範例，請參閱[XDocument 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的設計是讓 XML 名稱盡可能直接。 由於其複雜性的緣故，XML 名稱通常被視為 XML 的進階主題。 在論證上，這個複雜性不是來自於開發人員一般用於程式設計的命名空間，而是來自於命名空間前置詞。 命名空間前置詞在減少輸入 XML 時所需的按鍵或在讓 XML 更容易讀取上，可能相當實用。 不過，前置詞通常是只使用完整的 XML 命名空間的捷徑，且不需要在大部分情況下。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]所有前置詞解析為其對應的 XML 命名空間，藉以簡化 XML 名稱。 前置詞可供使用，如有必要，透過<xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>方法。</xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>  
  
 如有需要，可以控制命名空間前置詞。 在某些情況下，如果您要使用其他 XML 系統 (例如，XSLT 或 XAML)，您必須控制命名空間前置詞。 例如，如果您所擁有的 XPath 運算式使用內嵌在 XSLT 樣式表中的命名空間前置詞，您就必須確認 XML 文件有利用符合 XPath 運算式中使用之命名空間前置詞的命名空間前置詞進行序列化。  
  
### <a name="xnamespace-class"></a>XNamespace 類別  
 <xref:System.Xml.Linq.XNamespace>代表系統<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>的命名空間</xref:System.Xml.Linq.XNamespace> 命名空間是<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>的元件  
  
### <a name="xnode-class"></a>XNode 類別  
 <xref:System.Xml.Linq.XNode>是抽象類別代表 XML 樹狀結構的節點。</xref:System.Xml.Linq.XNode> 下列類別衍生自<xref:System.Xml.Linq.XNode>類別︰</xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XText></xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType></xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer 類別  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>提供功能，可針對其文件順序比較節點。</xref:System.Xml.Linq.XNodeDocumentOrderComparer>  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer 類別  
 <xref:System.Xml.Linq.XNodeEqualityComparer>提供功能比較節點值相等。</xref:System.Xml.Linq.XNodeEqualityComparer>  
  
### <a name="xobject-class"></a>XObject 類別  
 <xref:System.Xml.Linq.XObject>是抽象的基底類別和<xref:System.Xml.Linq.XNode><xref:System.Xml.Linq.XAttribute>。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XObject> 它提供附註和事件的功能。  
  
### <a name="xobjectchange-class"></a>XObjectChange 類別  
 <xref:System.Xml.Linq.XObjectChange><xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>引發事件時指定的事件類型</xref:System.Xml.Linq.XObjectChange>  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs 類別  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>提供資料給<xref:System.Xml.Linq.XObject.Changing>和<xref:System.Xml.Linq.XObject.Changed>事件。</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObjectChangeEventArgs>  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction 類別  
 <xref:System.Xml.Linq.XProcessingInstruction>代表 XML 處理指示。</xref:System.Xml.Linq.XProcessingInstruction> 處理指示會將資訊傳達到處理 XML 的應用程式。  
  
### <a name="xtext-class"></a>XText 類別  
 <xref:System.Xml.Linq.XText>代表文字節點。</xref:System.Xml.Linq.XText> 在大部分的情況下，您不必使用這個類別。 這個類別主要用於混合的內容。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 程式設計概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
