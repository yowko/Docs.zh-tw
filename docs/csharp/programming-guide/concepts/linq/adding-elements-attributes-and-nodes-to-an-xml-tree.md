---
title: "將項目、屬性和節點新增至 XML 樹狀結構 (C#)"
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
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6894e0685d413297c01118df16d01f7d956ee333
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="964ff-102">將項目、屬性和節點新增至 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="964ff-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="964ff-103">您可以將內容 (項目、屬性、註解、處理指示、文字和 CDATA) 加入到現有的 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="964ff-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="964ff-104">加入內容的方法</span><span class="sxs-lookup"><span data-stu-id="964ff-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="964ff-105">下列方法會將子內容加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>：</span><span class="sxs-lookup"><span data-stu-id="964ff-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="964ff-106">方法</span><span class="sxs-lookup"><span data-stu-id="964ff-106">Method</span></span>|<span data-ttu-id="964ff-107">描述</span><span class="sxs-lookup"><span data-stu-id="964ff-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="964ff-108">將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的結尾。</span><span class="sxs-lookup"><span data-stu-id="964ff-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="964ff-109">將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的開頭。</span><span class="sxs-lookup"><span data-stu-id="964ff-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="964ff-110">下列方法會加入內容，做為 <xref:System.Xml.Linq.XNode> 的同層級節點。</span><span class="sxs-lookup"><span data-stu-id="964ff-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="964ff-111">雖然您可以將有效的同層級內容加入到節點的其他型別 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XText>)，但是您加入同層級內容的最常見目標節點為 <xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="964ff-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="964ff-112">方法</span><span class="sxs-lookup"><span data-stu-id="964ff-112">Method</span></span>|<span data-ttu-id="964ff-113">描述</span><span class="sxs-lookup"><span data-stu-id="964ff-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="964ff-114">將內容加入到 <xref:System.Xml.Linq.XNode> 之後。</span><span class="sxs-lookup"><span data-stu-id="964ff-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="964ff-115">將內容加入到 <xref:System.Xml.Linq.XNode> 之前。</span><span class="sxs-lookup"><span data-stu-id="964ff-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="964ff-116">範例</span><span class="sxs-lookup"><span data-stu-id="964ff-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="964ff-117">描述</span><span class="sxs-lookup"><span data-stu-id="964ff-117">Description</span></span>  
 <span data-ttu-id="964ff-118">下列範例會建立兩個 XML 樹狀結構，然後修改其中一個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="964ff-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="964ff-119">程式碼</span><span class="sxs-lookup"><span data-stu-id="964ff-119">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="964ff-120">註解</span><span class="sxs-lookup"><span data-stu-id="964ff-120">Comments</span></span>  
 <span data-ttu-id="964ff-121">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="964ff-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="964ff-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="964ff-122">See Also</span></span>  
 [<span data-ttu-id="964ff-123">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="964ff-123">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

