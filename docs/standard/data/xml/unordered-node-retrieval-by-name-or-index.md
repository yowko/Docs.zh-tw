---
title: "根據名稱或索引擷取的未排序節點"
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
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8bea8f373dced08fd7a2a828255a593533df9d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="9e257-102">根據名稱或索引擷取的未排序節點</span><span class="sxs-lookup"><span data-stu-id="9e257-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="9e257-103">**XmlNamedNodeMap** namednodemap 的 World Wide Web Consortium (W3C) 規格所述，而且需要參考節點能夠處理未排序的節點集，根據名稱或索引。</span><span class="sxs-lookup"><span data-stu-id="9e257-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="9e257-104">您可以存取的唯一方式**XmlNamedNodeMap**時**XmlNamedNodeMap**透過方法或屬性會傳回。</span><span class="sxs-lookup"><span data-stu-id="9e257-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="9e257-105">有三種方法或屬性會傳回**XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="9e257-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="9e257-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="9e257-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="9e257-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="9e257-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="9e257-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="9e257-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="9e257-109">例如， **XmlDocumentType.Entities**屬性取得的集合**XmlEntity**文件類型宣告中宣告的節點。</span><span class="sxs-lookup"><span data-stu-id="9e257-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="9e257-110">這個集合會當成**XmlNamedNodeMap**，您可以逐一查看集合的使用和**計數**屬性並且顯示實體資訊。</span><span class="sxs-lookup"><span data-stu-id="9e257-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="9e257-111">如需逐一查看**XmlNamedNodeMap**，請參閱<xref:System.Xml.XmlDocumentType.Entities%2A>。</span><span class="sxs-lookup"><span data-stu-id="9e257-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="9e257-112">**XmlAttributeCollection**衍生自**XmlNamedNodeMap**和只有屬性可以修改，標記法和實體處於唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="9e257-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="9e257-113">使用**XmlNamedNodeMap**屬性，您可以取得節點的那些屬性，根據其 XML 名稱。</span><span class="sxs-lookup"><span data-stu-id="9e257-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="9e257-114">這提供簡單的方法來管理項目節點上的屬性集合。</span><span class="sxs-lookup"><span data-stu-id="9e257-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="9e257-115">這可以對照直接與**XmlNodeList**，它也會實作**IEnumerable**介面，但使用索引存取子，而不是字串。</span><span class="sxs-lookup"><span data-stu-id="9e257-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="9e257-116">**RemoveNamedItem**和**SetNamedItem**方法只能用於**XmlAttributeCollection**。</span><span class="sxs-lookup"><span data-stu-id="9e257-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="9e257-117">新增或移除從屬性集合，是否使用**AttributeCollection**或**XmlNamedNodeMap**實作中，修改項目的屬性集合。</span><span class="sxs-lookup"><span data-stu-id="9e257-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="9e257-118">下列程式碼範例將說明如何移動屬性及建立新屬性。</span><span class="sxs-lookup"><span data-stu-id="9e257-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="9e257-119">若要查看其他程式碼範例顯示移除從屬性**AttributeCollection**，請參閱[XmlNamedNodeMap.RemoveNamedItem 方法](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem)。</span><span class="sxs-lookup"><span data-stu-id="9e257-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="9e257-120">如需有關的方法和屬性的詳細資訊，請參閱[XmlNamedNodeMap 成員](AllMembers.T:System.Xml.XmlNamedNodeMap)。</span><span class="sxs-lookup"><span data-stu-id="9e257-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e257-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e257-121">See Also</span></span>  
 [<span data-ttu-id="9e257-122">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="9e257-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
