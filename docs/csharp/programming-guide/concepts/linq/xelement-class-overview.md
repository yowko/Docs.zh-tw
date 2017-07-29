---
title: "XElement 類別概觀 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 20c6c7aed7d00b26d08f3733147616313ad851f3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="xelement-class-overview-c"></a>XElement 類別概觀 (C#)
<xref:System.Xml.Linq.XElement> 類別是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的其中一個基本類別。 它代表 XML 項目。 您可以使用這個類別來建立項目；變更項目的內容；加入、變更或刪除子項目；將屬性加入到項目中；或以文字格式序列化項目的內容。 您也可以與 <xref:System.Xml?displayProperty=fullName> 中的其他類別相互溝通，例如，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>。  
  
## <a name="xelement-functionality"></a>XElement 功能  
 本主題描述 <xref:System.Xml.Linq.XElement> 類別提供的功能。  
  
### <a name="constructing-xml-trees"></a>建構 XML 樹狀結構  
 您可以用各種方式建構 XML 樹狀結構，包括：  
  
-   您可以在程式碼中建構 XML 樹狀結構。 如需詳細資訊，請參閱[建立 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)。  
  
-   您可以剖析來自各種來源的 XML，包括 <xref:System.IO.TextReader>、文字檔或網路位址 (URL)。 如需詳細資訊，請參閱[剖析 XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)。  
  
-   您可以使用 <xref:System.Xml.XmlReader> 來填入樹狀結構。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XNode.ReadFrom%2A>。  
  
-   如果您擁有的模組可以將內容寫入到 <xref:System.Xml.XmlWriter>，您可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法來建立寫入器、將寫入器傳遞到模組，然後使用寫入到 <xref:System.Xml.XmlWriter> 的內容填入 XML 樹狀結構。  
  
 不過，建立 XML 樹狀結構最常見的方式為下：  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 建立 XML 樹狀結構的另一個非常常見的技術包含使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的結果填入 XML 樹狀結構，如下列範例所示：  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
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
 您可以將 XML 樹狀結構序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。  
  
 如需詳細資訊，請參閱[序列化 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)。  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>透過座標軸方法擷取 XML 資料  
 您可以使用座標軸方法來擷取屬性、子項目、子系項目以及祖系項目。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢會在座標軸方法上操作，而且會提供數種具彈性而且功能強大的方式，導覽並處理 XML 樹狀結構。  
  
 如需詳細資訊，請參閱 [LINQ to XML 座標軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)。  
  
### <a name="querying-xml-trees"></a>查詢 XML 樹狀  
 您可以撰寫從 XML 樹狀結構擷取資料的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢。  
  
 如需詳細資訊，請參閱[查詢 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)。  
  
### <a name="modifying-xml-trees"></a>修改 XML 樹狀  
 您可以用各種方式修改項目，包括變更其內容或屬性。 您也可以從其父代移除項目。  
  
 如需詳細資訊，請參閱[修改 XML 樹狀結構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 程式設計概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

