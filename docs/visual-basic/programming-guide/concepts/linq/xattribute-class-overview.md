---
title: "XAttribute 類別概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
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
ms.openlocfilehash: 1ce5f4be6006908b35057854f89432471fd9f06b
ms.lasthandoff: 03/13/2017

---
# <a name="xattribute-class-overview-visual-basic"></a>XAttribute 類別概觀 (Visual Basic)
屬性是與項目相關聯的成對名稱/值。 <xref:System.Xml.Linq.XAttribute>類別代表 XML 屬性。</xref:System.Xml.Linq.XAttribute>  
  
## <a name="overview"></a>概觀  
 在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中使用屬性的方式類似於使用項目。 其建構函式類似。 您用來擷取其集合的方法也類似。 A[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]屬性集合的查詢運算式看起來非常類似於[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢運算式的項目集合。  
  
 系統會保留將屬性加入到項目的順序。 也就是說，當您逐一查看屬性時，您會看到加入這些屬性的相同順序。  
  
## <a name="the-xattribute-constructor"></a>XAttribute 建構函式  
 下列建構函式的<xref:System.Xml.Linq.XAttribute>類別是您最常使用的那個︰</xref:System.Xml.Linq.XAttribute>  
  
|建構函式|描述|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|建立<xref:System.Xml.Linq.XAttribute>物件。</xref:System.Xml.Linq.XAttribute> `name` 引數會指定屬性的名稱；`content` 會指定屬性的內容。|  
  
### <a name="creating-an-element-with-an-attribute"></a>建立具有屬性的項目  
 下列程式碼會顯示包含在 Visual Basic 中使用 XML 常值的屬性的項目︰  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>屬性的功能結構  
 您可以建構<xref:System.Xml.Linq.XAttribute>物件內嵌結構的<xref:System.Xml.Linq.XElement>物件，如下所示︰</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>屬性不是節點  
 屬性和項目有一些差異。 <xref:System.Xml.Linq.XAttribute>物件不是 XML 樹狀結構中的節點。</xref:System.Xml.Linq.XAttribute> 它們是與 XML 項目相關聯的成對名稱/值。 相較於文件物件模型 (DOM)，這在反映 XML 的結構時，更為接近。 雖然<xref:System.Xml.Linq.XAttribute>物件不是實際使用的 XML 樹狀目錄中的節點<xref:System.Xml.Linq.XAttribute>物件的方式非常類似於使用<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XAttribute>  
  
 這個區別只有對於撰寫可在節點層級使用 XML 樹狀結構之程式碼的開發人員特別重要。 這個區別與許多開發人員都無關。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 程式設計概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
