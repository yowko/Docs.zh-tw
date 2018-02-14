---
title: "使用 XPath 巡覽選取節點"
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
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 836702a3200a21c6a9830bdcd1f74a78129b5a6c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="54772-102">使用 XPath 巡覽選取節點</span><span class="sxs-lookup"><span data-stu-id="54772-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="54772-103">XML 文件物件模型 (DOM) 包含可讓您在 DOM 中使用 XML 路徑語言 (XPath) 巡覽查詢資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="54772-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="54772-104">您可以使用 XPath 尋找單一特定節點，或是尋找符合某些準則的所有節點。</span><span class="sxs-lookup"><span data-stu-id="54772-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="54772-105">XPath 選取方法</span><span class="sxs-lookup"><span data-stu-id="54772-105">XPath Select Methods</span></span>  
 <span data-ttu-id="54772-106">DOM 類別提供了兩種使用 XPath 選取的方法：<xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法與 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="54772-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="54772-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法會傳回符合選取準則的第一個節點。</span><span class="sxs-lookup"><span data-stu-id="54772-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="54772-108"><xref:System.Xml.XmlNode.SelectNodes%2A> 方法則會傳回包含相符節點的 <xref:System.Xml.XmlNodeList> 方法。</span><span class="sxs-lookup"><span data-stu-id="54772-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="54772-109">下列範例使用 <xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法選取第一個 `book` 節點，其中作者的姓氏符合指定的準則。</span><span class="sxs-lookup"><span data-stu-id="54772-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="54772-110">bookstore.xml 檔案 (提供於本主題結尾) 會做為輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="54772-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="54772-111">下一個範例使用 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法來選取所有的書籍節點，其中價格大於指定的數量。</span><span class="sxs-lookup"><span data-stu-id="54772-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="54772-112">在選取清單中的每本書籍價格都會以程式設計的方式減少百分之十。</span><span class="sxs-lookup"><span data-stu-id="54772-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="54772-113">最後，會將更新的檔案寫入主控台中。</span><span class="sxs-lookup"><span data-stu-id="54772-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="54772-114">bookstore.xml 檔案 (提供於本主題結尾) 會做為輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="54772-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="54772-115">上述範例會從文件項目開始 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="54772-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="54772-116">設定 XPath 查詢的起點時，便會設定做為 XPath 查詢起點的內容節點。</span><span class="sxs-lookup"><span data-stu-id="54772-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="54772-117">如果您不想從文件項目開始，而要從文件項目的第一個項目子系開始，則可以撰寫下列所示的 Select 陳述式程式碼。</span><span class="sxs-lookup"><span data-stu-id="54772-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="54772-118">讓所有 <xref:System.Xml.XmlNodeList> 物件與基礎文件同步處理。</span><span class="sxs-lookup"><span data-stu-id="54772-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="54772-119">因此，如果您重複節點清單並修改節點的值，則也會從節點的來源文件中更新該節點。</span><span class="sxs-lookup"><span data-stu-id="54772-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="54772-120">請注意，在前述範例中，當在選取的 <xref:System.Xml.XmlNodeList> 中修改節點時，也會修改基礎文件。</span><span class="sxs-lookup"><span data-stu-id="54772-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54772-121">修改基礎文件後，建議您重新執行 select。</span><span class="sxs-lookup"><span data-stu-id="54772-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="54772-122">如果修改節點後，導致該節點被加入至節點清單 (先前未加入)，或導致該節點從節點清單中移除，則不能保證此節點清單目前是正確的。</span><span class="sxs-lookup"><span data-stu-id="54772-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="54772-123">XPath 運算式中的命名空間</span><span class="sxs-lookup"><span data-stu-id="54772-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="54772-124">XPath 運算式可包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="54772-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="54772-125">命名空間解析可透過 <xref:System.Xml.XmlNamespaceManager> 予以支援。</span><span class="sxs-lookup"><span data-stu-id="54772-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="54772-126">如果 XPath 運算式包含前置詞，則必須將前置詞及命名空間 URI 配對加入至 <xref:System.Xml.XmlNamespaceManager>，並將 <xref:System.Xml.XmlNamespaceManager> 傳遞給 <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> 或 <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="54772-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="54772-127">請注意上方的程式碼範例使用 <xref:System.Xml.XmlNamespaceManager> 來解析 bookstore.xml 文件的命名空間。</span><span class="sxs-lookup"><span data-stu-id="54772-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54772-128">如果 XPath 運算式不包含前置詞，則會假設命名空間統一資源識別元 (URI) 為空白的命名空間。</span><span class="sxs-lookup"><span data-stu-id="54772-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="54772-129">如果 XML 包含預設命名空間，則仍必須將前置詞及命名空間 URI 加入至 <xref:System.Xml.XmlNamespaceManager>，否則就不會選取任何節點。</span><span class="sxs-lookup"><span data-stu-id="54772-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="54772-130">輸入檔案</span><span class="sxs-lookup"><span data-stu-id="54772-130">Input File</span></span>  
 <span data-ttu-id="54772-131">下列是在本主題的範例中做為輸入檔案的 bookstore.xml 檔案：</span><span class="sxs-lookup"><span data-stu-id="54772-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54772-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="54772-132">See Also</span></span>  
 [<span data-ttu-id="54772-133">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="54772-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
