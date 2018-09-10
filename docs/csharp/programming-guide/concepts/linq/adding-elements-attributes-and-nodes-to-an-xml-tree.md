---
title: 將項目、屬性和節點新增至 XML 樹狀結構 (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 1ebc300d74f8dbf0ec746a14f19b5cf0c7ffa51b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517055"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="e7f0f-102">將項目、屬性和節點新增至 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7f0f-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="e7f0f-103">您可以將內容 (項目、屬性、註解、處理指示、文字和 CDATA) 加入到現有的 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="e7f0f-104">加入內容的方法</span><span class="sxs-lookup"><span data-stu-id="e7f0f-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="e7f0f-105">下列方法會將子內容加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>：</span><span class="sxs-lookup"><span data-stu-id="e7f0f-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="e7f0f-106">方法</span><span class="sxs-lookup"><span data-stu-id="e7f0f-106">Method</span></span>|<span data-ttu-id="e7f0f-107">描述</span><span class="sxs-lookup"><span data-stu-id="e7f0f-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="e7f0f-108">將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的結尾。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="e7f0f-109">將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的開頭。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="e7f0f-110">下列方法會加入內容，做為 <xref:System.Xml.Linq.XNode> 的同層級節點。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="e7f0f-111">雖然您可以將有效的同層級內容加入到節點的其他型別 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XText>)，但是您加入同層級內容的最常見目標節點為 <xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="e7f0f-112">方法</span><span class="sxs-lookup"><span data-stu-id="e7f0f-112">Method</span></span>|<span data-ttu-id="e7f0f-113">描述</span><span class="sxs-lookup"><span data-stu-id="e7f0f-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="e7f0f-114">將內容加入到 <xref:System.Xml.Linq.XNode> 之後。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="e7f0f-115">將內容加入到 <xref:System.Xml.Linq.XNode> 之前。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7f0f-116">範例</span><span class="sxs-lookup"><span data-stu-id="e7f0f-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e7f0f-117">描述</span><span class="sxs-lookup"><span data-stu-id="e7f0f-117">Description</span></span>  
 <span data-ttu-id="e7f0f-118">下列範例會建立兩個 XML 樹狀結構，然後修改其中一個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e7f0f-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e7f0f-119">程式碼</span><span class="sxs-lookup"><span data-stu-id="e7f0f-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="e7f0f-120">註解</span><span class="sxs-lookup"><span data-stu-id="e7f0f-120">Comments</span></span>  
 <span data-ttu-id="e7f0f-121">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e7f0f-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7f0f-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="e7f0f-122">See Also</span></span>

- [<span data-ttu-id="e7f0f-123">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e7f0f-123">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
