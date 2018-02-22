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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b80f48d425623c9e6cdf1431ceb4a37efe7f2465
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="7bbbd-102">根據名稱或索引擷取的未排序節點</span><span class="sxs-lookup"><span data-stu-id="7bbbd-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="7bbbd-103">根據全球資訊網協會 (W3C) 規格中的說明，**XmlNamedNodeMap** 是一種 NamedNodeMap，若要處理的是未排序節點集，則必須使用它，因為它可以根據名稱或索引而參考節點。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="7bbbd-104">存取 **XmlNamedNodeMap** 的唯一方法，是當 **XmlNamedNodeMap** 經由方法或屬性傳回時。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="7bbbd-105">有三種方法或屬性會傳回 **XmlNamedNodeMap**：</span><span class="sxs-lookup"><span data-stu-id="7bbbd-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="7bbbd-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="7bbbd-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="7bbbd-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="7bbbd-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="7bbbd-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="7bbbd-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="7bbbd-109">例如，**XmlDocumentType.Entities** 屬性會取得文件類型宣告中宣告的 **XmlEntity** 節點之集合。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="7bbbd-110">這個集合會以 **XmlNamedNodeMap** 傳回，而且您可以使用 **Count** 屬性重複集合並且顯示實體資訊。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="7bbbd-111">如需重複 **XmlNamedNodeMap** 的範例，請參閱 <xref:System.Xml.XmlDocumentType.Entities%2A>。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="7bbbd-112">**XmlAttributeCollection** 衍生自 **XmlNamedNodeMap** 而且只有其屬性可以修改，標記法和實體則是唯讀。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="7bbbd-113">您可以使用屬性的 **XmlNamedNodeMap**，根據其 XML 名稱取得這些屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="7bbbd-114">這提供簡單的方法來管理元素節點上的屬性集合。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="7bbbd-115">這與直接使用 **XmlNodeList** 相反，後者也實作 **IEnumerable** 介面，但是是使用索引存取子 (Accessor) 而不是字串。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="7bbbd-116">**RemoveNamedItem** 與 **SetNamedItem** 方法只能用於 **XmlAttributeCollection**。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="7bbbd-117">從屬性集合加入或移除，無論是使用 **AttributeCollection** 或 **XmlNamedNodeMap** 實作，都會在元素上修改屬性集合。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="7bbbd-118">下列程式碼範例將說明如何移動屬性及建立新屬性。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="7bbbd-119">若要查看會顯示從 **AttributeCollection** 移除屬性的其他程式碼範例，請參閱 [XmlNamedNodeMap.RemoveNamedItem 方法](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem)。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="7bbbd-120">如需方法和屬性的詳細資訊，請參閱 [XmlNamedNodeMap 成員](AllMembers.T:System.Xml.XmlNamedNodeMap)。</span><span class="sxs-lookup"><span data-stu-id="7bbbd-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bbbd-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="7bbbd-121">See Also</span></span>  
 [<span data-ttu-id="7bbbd-122">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="7bbbd-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
