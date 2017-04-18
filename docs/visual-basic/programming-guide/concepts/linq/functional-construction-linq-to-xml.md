---
title: "功能建構 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
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
ms.openlocfilehash: 9fa8cb3c97a1e23a863296c828c82b240e9ab5db
ms.lasthandoff: 03/13/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>功能建構 (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]提供強大的方式，來建立 XML 項目稱為*功能結構*。 功能結構是在單一陳述式中建立 XML 樹狀結構的能力。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 程式介面有數種主要功能可以使用功能結構：  
  
-   <xref:System.Xml.Linq.XElement>建構函式會採用各種引數的內容類型。</xref:System.Xml.Linq.XElement> 例如，您可以將另一個<xref:System.Xml.Linq.XElement>物件，其成為子項目。</xref:System.Xml.Linq.XElement> 您可以傳遞<xref:System.Xml.Linq.XAttribute>物件，就會變成項目的屬性。</xref:System.Xml.Linq.XAttribute> 或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。  
  
-   <xref:System.Xml.Linq.XElement>建構函式接受`params`型別的陣列<xref:System.Object>，因此您可以將任何數目的物件傳遞給建構函式。</xref:System.Object> </xref:System.Xml.Linq.XElement> 這可讓您建立包含複雜內容的項目。  
  
-   如果物件實作<xref:System.Collections.Generic.IEnumerable%601>會列舉中物件的集合，集合中的所有項目加入。</xref:System.Collections.Generic.IEnumerable%601> 如果集合包含<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件，會個別加入集合中的每個項目。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> 這很重要，因為它可讓您的結果傳遞[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]建構函式的查詢。  
  
 以下是一個範例：  
  
 這些功能可讓您撰寫程式碼使用 XML 常值，建立 XML 樹狀結構，也可以撰寫程式碼會使用結果[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢當您建立 XML 樹狀結構︰  
  
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
            Where CInt(el) > 2 _  
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
  
## <a name="see-also"></a>另請參閱  
 [建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
