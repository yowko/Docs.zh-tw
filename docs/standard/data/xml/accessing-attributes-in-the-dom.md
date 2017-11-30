---
title: "存取 DOM 中的屬性"
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
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a433ec5f83a50aa4fe4b2017a0dac3d2a5e5710c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="ef010-102">存取 DOM 中的屬性</span><span class="sxs-lookup"><span data-stu-id="ef010-102">Accessing Attributes in the DOM</span></span>
<span data-ttu-id="ef010-103">屬性 (Attribute) 是項目的屬性 (Property)，而不是項目的子系。</span><span class="sxs-lookup"><span data-stu-id="ef010-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="ef010-104">這個差別是很重要的，因為這關係到用來巡覽 XML 文件物件模型 (DOM) 的同層級節點、父節點和子節點的方法。</span><span class="sxs-lookup"><span data-stu-id="ef010-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="ef010-105">例如， **PreviousSibling**和**NextSibling**方法不會用來巡覽的項目至屬性或屬性之間。</span><span class="sxs-lookup"><span data-stu-id="ef010-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="ef010-106">相反地，屬性是元素的屬性，而且由元素所擁有，具有**OwnerElement**屬性而非**parentNode**屬性，且具有不同的巡覽方法。</span><span class="sxs-lookup"><span data-stu-id="ef010-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="ef010-107">項目目前的節點時，請使用**HasAttribute**方法，以查看是否有任何項目相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="ef010-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="ef010-108">一旦知道項目有屬性 (Attribute)，就有多種存取屬性 (Attribute) 的方法。</span><span class="sxs-lookup"><span data-stu-id="ef010-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="ef010-109">若要從項目擷取單一屬性，您可以使用**Xmlelement**和**Getattribute**方法**XmlElement**也可以取得所有屬性插入集合中。</span><span class="sxs-lookup"><span data-stu-id="ef010-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="ef010-110">如果您需要重複集合，那麼取得集合很有用。</span><span class="sxs-lookup"><span data-stu-id="ef010-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="ef010-111">如果您想從元素的所有屬性，請使用**屬性**要擷取的所有屬性置於集合的項目屬性。</span><span class="sxs-lookup"><span data-stu-id="ef010-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>  
  
## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="ef010-112">擷取所有的屬性 (Attribute) 置於集合中</span><span class="sxs-lookup"><span data-stu-id="ef010-112">Retrieving All Attributes into a Collection</span></span>  
 <span data-ttu-id="ef010-113">如果您想要將所有項目節點的屬性將加入至集合，呼叫**XmlElement.Attributes**屬性。</span><span class="sxs-lookup"><span data-stu-id="ef010-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="ef010-114">這會取得**XmlAttributeCollection** ，其中包含項目的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="ef010-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="ef010-115">**XmlAttributeCollection**類別繼承自**XmlNamedNode**對應。</span><span class="sxs-lookup"><span data-stu-id="ef010-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="ef010-116">因此，方法和集合上可用的屬性包括具名的節點對應此外方法和屬性的特定**XmlAttributeCollection**類別，例如**ItemOf**屬性或**附加**方法。</span><span class="sxs-lookup"><span data-stu-id="ef010-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="ef010-117">屬性集合中的每個項目代表**XmlAttribute**節點。</span><span class="sxs-lookup"><span data-stu-id="ef010-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="ef010-118">若要尋找的屬性數目的項目上，取得**XmlAttributeCollection**，並使用**計數**屬性來查看多少**XmlAttribute**節點是在集合中。</span><span class="sxs-lookup"><span data-stu-id="ef010-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>  
  
 <span data-ttu-id="ef010-119">下列程式碼範例示範如何擷取屬性集合，使用**計數**方法迴圈索引並加以重複。</span><span class="sxs-lookup"><span data-stu-id="ef010-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="ef010-120">程式碼顯示如何從集合中擷取單一的屬性 (Attribute) 並顯示其值。</span><span class="sxs-lookup"><span data-stu-id="ef010-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
    End Sub  
End Class  
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
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 <span data-ttu-id="ef010-121">這個範例顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ef010-121">This example displays the following output:</span></span>  
  
 <span data-ttu-id="ef010-122">**輸出**</span><span class="sxs-lookup"><span data-stu-id="ef010-122">**Output**</span></span>  
  
 <span data-ttu-id="ef010-123">顯示集合中的所有屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="ef010-123">Display all the attributes in the collection.</span></span>  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 <span data-ttu-id="ef010-124">屬性集合中的資訊可以由名稱或索引編號擷取。</span><span class="sxs-lookup"><span data-stu-id="ef010-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="ef010-125">上述範例顯示如何依名稱擷取資料。</span><span class="sxs-lookup"><span data-stu-id="ef010-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="ef010-126">下一個範例則顯示如何依索引編號擷取資料。</span><span class="sxs-lookup"><span data-stu-id="ef010-126">The next example shows how to retrieve data by index number.</span></span>  
  
 <span data-ttu-id="ef010-127">因為**XmlAttributeCollection**是集合，而且可以逐一查看依名稱或索引，此範例會顯示選取的集合，使用以零為起始的索引，並使用下列檔案中，第一個屬性**baseuri.xml**作為輸入。</span><span class="sxs-lookup"><span data-stu-id="ef010-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>  
  
### <a name="input"></a><span data-ttu-id="ef010-128">輸入</span><span class="sxs-lookup"><span data-stu-id="ef010-128">Input</span></span>  
  
```xml  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="ef010-129">擷取個別屬性 (Attribute) 節點</span><span class="sxs-lookup"><span data-stu-id="ef010-129">Retrieving an Individual Attribute Node</span></span>  
 <span data-ttu-id="ef010-130">若要從項目中擷取單一屬性節點，便會使用 <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ef010-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="ef010-131">它會傳回型別的物件**XmlAttribute**。</span><span class="sxs-lookup"><span data-stu-id="ef010-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="ef010-132">一旦**XmlAttribute**，所有的方法和屬性中提供<xref:System.Xml.XmlAttribute?displayProperty=nameWithType>類別位於該物件，例如尋找**OwnerElement**。</span><span class="sxs-lookup"><span data-stu-id="ef010-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
    End Sub  
End Class  
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
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 <span data-ttu-id="ef010-133">如前一個範例所示，您也可以從屬性集合中擷取單一屬性節點。</span><span class="sxs-lookup"><span data-stu-id="ef010-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="ef010-134">下列程式碼範例顯示如何一行程式碼可以撰寫可擷取單一屬性依索引編號從 XML 文件的根樹狀結構，也稱為**DocumentElement**屬性。</span><span class="sxs-lookup"><span data-stu-id="ef010-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef010-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef010-135">See Also</span></span>  
 [<span data-ttu-id="ef010-136">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="ef010-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
