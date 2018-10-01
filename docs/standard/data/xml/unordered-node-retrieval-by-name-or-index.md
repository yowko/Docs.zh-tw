---
title: 根據名稱或索引擷取的未排序節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da1c9f25052bb2354b435cd28b7ff55d4a754ed1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47216314"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>根據名稱或索引擷取的未排序節點
根據全球資訊網協會 (W3C) 規格中的說明，**XmlNamedNodeMap** 是一種 NamedNodeMap，若要處理的是未排序節點集，則必須使用它，因為它可以根據名稱或索引而參考節點。 存取 **XmlNamedNodeMap** 的唯一方法，是當 **XmlNamedNodeMap** 經由方法或屬性傳回時。 有三種方法或屬性會傳回 **XmlNamedNodeMap**：  
  
-   XmlElement.Attributes  
  
-   XmlDocumentType.Entities  
  
-   XmlDocumentType.Notations  
  
 例如，**XmlDocumentType.Entities** 屬性會取得文件類型宣告中宣告的 **XmlEntity** 節點之集合。 這個集合會以 **XmlNamedNodeMap** 傳回，而且您可以使用 **Count** 屬性重複集合並且顯示實體資訊。 如需重複 **XmlNamedNodeMap** 的範例，請參閱 <xref:System.Xml.XmlDocumentType.Entities%2A>。  
  
 **XmlAttributeCollection** 衍生自 **XmlNamedNodeMap** 而且只有其屬性可以修改，標記法和實體則是唯讀。 您可以使用屬性的 **XmlNamedNodeMap**，根據其 XML 名稱取得這些屬性的節點。 這提供簡單的方法來管理項目節點上的屬性集合。 這與直接使用 **XmlNodeList** 相反，後者也實作 **IEnumerable** 介面，但是是使用索引存取子 (Accessor) 而不是字串。 **RemoveNamedItem** 與 **SetNamedItem** 方法只能用於 **XmlAttributeCollection**。 從屬性集合加入或移除，無論是使用 **AttributeCollection** 或 **XmlNamedNodeMap** 實作，都會在元素上修改屬性集合。 下列程式碼範例將說明如何移動屬性及建立新屬性。  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 若要查看會顯示從 **AttributeCollection** 移除屬性的其他程式碼範例，請參閱 [XmlNamedNodeMap.RemoveNamedItem 方法](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem)。 如需方法和屬性的詳細資訊，請參閱 [XmlNamedNodeMap 成員](AllMembers.T:System.Xml.XmlNamedNodeMap)。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
