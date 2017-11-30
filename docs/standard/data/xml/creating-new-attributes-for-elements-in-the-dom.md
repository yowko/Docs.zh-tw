---
title: "為 DOM 中的項目建立新屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>為 DOM 中的項目建立新屬性
建立新的屬性是不同於建立其他節點型別，因為屬性不是節點，但是是元素節點的屬性，而且包含在**XmlAttributeCollection**項目相關聯。 有許多方法可以建立屬性並且將它附加於項目：  
  
-   取得項目節點並且使用**SetAttribute**將屬性新增至該元素的屬性集合。  
  
-   建立**XmlAttribute**節點使用**Xmlattribute**方法，取得項目 節點，然後使用**SetAttributeNode**將節點新增至該屬性集合項目。  
  
 下列範例示範如何將屬性加入項目使用**SetAttribute**方法。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    XmlDocument doc = new XmlDocument();  
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 下列範例示範新的屬性正在使用建立**Xmlattribute**方法。 然後它會顯示加入至屬性集合的屬性**書籍**項目使用**SetAttributeNode**方法。  
  
 假設有下列的 XML：  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 建立新屬性並指定其值：  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 將它附加於項目：  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **輸出**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 完整的程式碼範例，請參閱<xref:System.Xml.XmlDocument.CreateAttribute%2A>。  
  
 您也可以建立**XmlAttribute**節點並且使用**InsertBefore**或**InsertAfter**方法將它置於集合中的適當位置。 具有相同名稱的屬性是否已存在於屬性集合，現有**XmlAttribute**節點會從集合與新移除**XmlAttribute**節點會插入。 這會執行的相同方式**SetAttribute**方法。 這些方法會採用，做為參數，以現有節點作為參考點來執行**InsertBefore**和**InsertAfter**。 如果您未提供要插入新節點的預設值的參考節點**InsertAfter**方法是在集合的開頭插入新節點。 預設位置**InsertBefore**，不提供任何參考節點，如果位於集合的結尾。  
  
 如果您建立**XmlNamedNodeMap**屬性，您可以新增的屬性名稱使用<xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>。 如需詳細資訊，請參閱[Namednodemap 和 Nodelist 中的節點集合](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)。  
  
## <a name="default-attributes"></a>預設屬性  
 如果您建立了宣告要有預設屬性的項目，那麼具有預設值的新預設屬性會由 XML 文件物件模型 (DOM) 建立並且附加於項目。 預設屬性的子節點也會在此時建立。  
  
## <a name="attribute-child-nodes"></a>屬性子節點  
 屬性節點的值會成為它的子節點。 沒有有效的子節點只有兩種類型： **XmlText**節點，和**XmlEntityReference**節點。 這些是子節點，因為該方法，如**FirstChild**和**LastChild**處理它們做為子節點。 這種擁有子節點的屬性的區別在嘗試移除屬性或屬性子節點時很重要。 如需詳細資訊，請參閱[移除 DOM 中項目節點的屬性](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
