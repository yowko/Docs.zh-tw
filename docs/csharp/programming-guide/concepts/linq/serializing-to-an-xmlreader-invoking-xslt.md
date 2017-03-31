---
title: "序列化至 XmlReader (叫用 XSLT) (C#) | Microsoft Docs"
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
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 96fed09349264710dc8f0591a0022939e9a4181a
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>序列化至 XmlReader (叫用 XSLT) (C#)
當您使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的 <xref:System.Xml?displayProperty=fullName> 互通性功能，即可使用 <xref:System.Xml.Linq.XNode.CreateReader%2A> 來建立 <xref:System.Xml.XmlReader>。 從這個 <xref:System.Xml.XmlReader> 讀取的模組會讀取 XML 樹狀結構中的節點，並據此進行處理。  
  
## <a name="invoking-an-xslt-transformation"></a>叫用 XSLT 轉換  
 此方法的其中一個可能的使用時機為叫用 XSLT 轉換時。 您可以建立 XML 樹狀結構、從 XML 樹狀結構建立 <xref:System.Xml.XmlReader>、建立新的文件，然後建立 <xref:System.Xml.XmlWriter> 來寫入新文件。 您接著可以叫用 XSLT 轉換，並傳入 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter>。 轉換成功完成後，系統會使用轉換的結果填入新的 XML 樹狀結構。  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>另請參閱  
 [序列化 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
