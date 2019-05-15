---
title: 根據索引擷取的已排序節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e4847dd6bc05127799cb6d8424a8fdb63fbc0f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590067"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="20ce9-102">根據索引擷取的已排序節點</span><span class="sxs-lookup"><span data-stu-id="20ce9-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="20ce9-103">全球資訊網協會 (W3C) XML 文件物件模型 (DOM) 也說明了 NodeList；相對於能夠處理未排序節點集的 **XmlNamedNodeMap**，NodeList 具有處理已排序節點清單的功能。</span><span class="sxs-lookup"><span data-stu-id="20ce9-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="20ce9-104">Microsoft .NET Framework 中的 NodeList 稱為 **XmlNodeList**。</span><span class="sxs-lookup"><span data-stu-id="20ce9-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="20ce9-105">傳回 **XmlNodeList** 的方法和屬性有：</span><span class="sxs-lookup"><span data-stu-id="20ce9-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="20ce9-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="20ce9-106">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="20ce9-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="20ce9-107">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="20ce9-108">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="20ce9-108">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="20ce9-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="20ce9-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="20ce9-110">**XmlNodeList** 有一個 **Count** 屬性，可以用於將迴圈重複寫入 **XmlNodeList** 中的節點，如同下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="20ce9-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{     
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}   
```  
  
 <span data-ttu-id="20ce9-111">除了 **Count** 屬性之外，還有 **GetEnumerator** 方法可對 **XmlNodeList** 中的節點集合提供 `foreach` 樣式反覆運算。</span><span class="sxs-lookup"><span data-stu-id="20ce9-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="20ce9-112">下列程式碼範例顯示 `foreach` 陳述式的使用情形。</span><span class="sxs-lookup"><span data-stu-id="20ce9-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum          
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();    
     // Loop over the XmlNodeList using the enumerator ienum          
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 <span data-ttu-id="20ce9-113">如需 **XmlNodeList** 上可以使用之方法和屬性的詳細資訊，請參閱 <xref:System.Xml.XmlNodeList>。</span><span class="sxs-lookup"><span data-stu-id="20ce9-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ce9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20ce9-114">See also</span></span>

- [<span data-ttu-id="20ce9-115">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="20ce9-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
