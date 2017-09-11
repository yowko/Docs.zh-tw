---
title: "將項目、 屬性和節點加入至 XML 樹狀結構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f8ee26aef896a2f404e815823ade83e204270613
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="98400-102">將項目、 屬性和節點加入至 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98400-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="98400-103">您可以將內容 (項目、屬性、註解、處理指示、文字和 CDATA) 加入到現有的 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="98400-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="98400-104">加入內容的方法</span><span class="sxs-lookup"><span data-stu-id="98400-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="98400-105">下列方法會將子內容加入至<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>::</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="98400-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="98400-106">方法</span><span class="sxs-lookup"><span data-stu-id="98400-106">Method</span></span>|<span data-ttu-id="98400-107">描述</span><span class="sxs-lookup"><span data-stu-id="98400-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="98400-108"><xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="98400-108"><xref:System.Xml.Linq.XContainer.Add%2A></span></span>|<span data-ttu-id="98400-109">將內容加入<xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer>目的子內容的結尾</span><span class="sxs-lookup"><span data-stu-id="98400-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="98400-110"><xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A></span><span class="sxs-lookup"><span data-stu-id="98400-110"><xref:System.Xml.Linq.XContainer.AddFirst%2A></span></span>|<span data-ttu-id="98400-111">將內容加入<xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer>目的子內容的開頭</span><span class="sxs-lookup"><span data-stu-id="98400-111">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="98400-112">下列方法加入內容，做<xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode>的同層級節點</span><span class="sxs-lookup"><span data-stu-id="98400-112">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="98400-113">最常見的節點，您可以新增同層級內容是<xref:System.Xml.Linq.XElement>，雖然您可以新增其他類型的節點，例如<xref:System.Xml.Linq.XText><xref:System.Xml.Linq.XComment>.</xref:System.Xml.Linq.XComment>或</xref:System.Xml.Linq.XText>有效的同層級內容</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="98400-113">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="98400-114">方法</span><span class="sxs-lookup"><span data-stu-id="98400-114">Method</span></span>|<span data-ttu-id="98400-115">描述</span><span class="sxs-lookup"><span data-stu-id="98400-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="98400-116"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="98400-116"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span></span>|<span data-ttu-id="98400-117">將內容加入在<xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="98400-117">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="98400-118"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="98400-118"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span></span>|<span data-ttu-id="98400-119">新增<xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode>之前的內容</span><span class="sxs-lookup"><span data-stu-id="98400-119">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="98400-120">範例</span><span class="sxs-lookup"><span data-stu-id="98400-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="98400-121">描述</span><span class="sxs-lookup"><span data-stu-id="98400-121">Description</span></span>  
 <span data-ttu-id="98400-122">下列範例會建立兩個 XML 樹狀結構，然後修改其中一個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="98400-122">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="98400-123">程式碼</span><span class="sxs-lookup"><span data-stu-id="98400-123">Code</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
  
```  
  
### <a name="comments"></a><span data-ttu-id="98400-124">註解</span><span class="sxs-lookup"><span data-stu-id="98400-124">Comments</span></span>  
 <span data-ttu-id="98400-125">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="98400-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98400-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98400-126">See Also</span></span>  
 [<span data-ttu-id="98400-127">修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98400-127">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
