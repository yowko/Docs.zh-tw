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
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="4b7c5-102">為 DOM 中的項目建立新屬性</span><span class="sxs-lookup"><span data-stu-id="4b7c5-102">Creating New Attributes for Elements in the DOM</span></span>
<span data-ttu-id="4b7c5-103">建立新的屬性是不同於建立其他節點型別，因為屬性不是節點，但是是元素節點的屬性，而且包含在**XmlAttributeCollection**項目相關聯。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="4b7c5-104">有許多方法可以建立屬性並且將它附加於項目：</span><span class="sxs-lookup"><span data-stu-id="4b7c5-104">There are multiple ways to create an attribute and attach it to an element:</span></span>  
  
-   <span data-ttu-id="4b7c5-105">取得項目節點並且使用**SetAttribute**將屬性新增至該元素的屬性集合。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>  
  
-   <span data-ttu-id="4b7c5-106">建立**XmlAttribute**節點使用**Xmlattribute**方法，取得項目 節點，然後使用**SetAttributeNode**將節點新增至該屬性集合項目。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>  
  
 <span data-ttu-id="4b7c5-107">下列範例示範如何將屬性加入項目使用**SetAttribute**方法。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-107">The following example shows how to add an attribute to an element using the **SetAttribute** method.</span></span>  
  
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
  
 <span data-ttu-id="4b7c5-108">下列範例示範新的屬性正在使用建立**Xmlattribute**方法。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="4b7c5-109">然後它會顯示加入至屬性集合的屬性**書籍**項目使用**SetAttributeNode**方法。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>  
  
 <span data-ttu-id="4b7c5-110">假設有下列的 XML：</span><span class="sxs-lookup"><span data-stu-id="4b7c5-110">Given the following XML:</span></span>  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="4b7c5-111">建立新屬性並指定其值：</span><span class="sxs-lookup"><span data-stu-id="4b7c5-111">create a new attribute and give it a value:</span></span>  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 <span data-ttu-id="4b7c5-112">將它附加於項目：</span><span class="sxs-lookup"><span data-stu-id="4b7c5-112">and attach it to the element:</span></span>  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 <span data-ttu-id="4b7c5-113">**輸出**</span><span class="sxs-lookup"><span data-stu-id="4b7c5-113">**Output**</span></span>  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="4b7c5-114">完整的程式碼範例，請參閱<xref:System.Xml.XmlDocument.CreateAttribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>  
  
 <span data-ttu-id="4b7c5-115">您也可以建立**XmlAttribute**節點並且使用**InsertBefore**或**InsertAfter**方法將它置於集合中的適當位置。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="4b7c5-116">具有相同名稱的屬性是否已存在於屬性集合，現有**XmlAttribute**節點會從集合與新移除**XmlAttribute**節點會插入。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="4b7c5-117">這會執行的相同方式**SetAttribute**方法。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="4b7c5-118">這些方法會採用，做為參數，以現有節點作為參考點來執行**InsertBefore**和**InsertAfter**。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="4b7c5-119">如果您未提供要插入新節點的預設值的參考節點**InsertAfter**方法是在集合的開頭插入新節點。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="4b7c5-120">預設位置**InsertBefore**，不提供任何參考節點，如果位於集合的結尾。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>  
  
 <span data-ttu-id="4b7c5-121">如果您建立**XmlNamedNodeMap**屬性，您可以新增的屬性名稱使用<xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span></span> <span data-ttu-id="4b7c5-122">如需詳細資訊，請參閱[Namednodemap 和 Nodelist 中的節點集合](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span></span>  
  
## <a name="default-attributes"></a><span data-ttu-id="4b7c5-123">預設屬性</span><span class="sxs-lookup"><span data-stu-id="4b7c5-123">Default Attributes</span></span>  
 <span data-ttu-id="4b7c5-124">如果您建立了宣告要有預設屬性的項目，那麼具有預設值的新預設屬性會由 XML 文件物件模型 (DOM) 建立並且附加於項目。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="4b7c5-125">預設屬性的子節點也會在此時建立。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-125">The child nodes of the default attribute are also created at this time.</span></span>  
  
## <a name="attribute-child-nodes"></a><span data-ttu-id="4b7c5-126">屬性子節點</span><span class="sxs-lookup"><span data-stu-id="4b7c5-126">Attribute Child Nodes</span></span>  
 <span data-ttu-id="4b7c5-127">屬性節點的值會成為它的子節點。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="4b7c5-128">沒有有效的子節點只有兩種類型： **XmlText**節點，和**XmlEntityReference**節點。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-128">There are only two types of valid child nodes: **XmlText** nodes, and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="4b7c5-129">這些是子節點，因為該方法，如**FirstChild**和**LastChild**處理它們做為子節點。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="4b7c5-130">這種擁有子節點的屬性的區別在嘗試移除屬性或屬性子節點時很重要。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="4b7c5-131">如需詳細資訊，請參閱[移除 DOM 中項目節點的屬性](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="4b7c5-131">For more information, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b7c5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b7c5-132">See Also</span></span>  
 [<span data-ttu-id="4b7c5-133">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="4b7c5-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
