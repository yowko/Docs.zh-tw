---
title: "複製與附加 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c86a75b1c9b4dc25e29d8323d23f89232b8de80
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="d3630-102">複製與附加 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3630-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="d3630-103">當加入<xref:System.Xml.Linq.XNode>(包括<xref:System.Xml.Linq.XElement>) 或<xref:System.Xml.Linq.XAttribute>物件至新的樹狀目錄中，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="d3630-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="d3630-104">如果新內容已經成為父代，而且屬於其他 XML 樹狀結構的一部分，則會複製新內容。</span><span class="sxs-lookup"><span data-stu-id="d3630-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="d3630-105">然後，新複製的內容會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d3630-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3630-106">範例</span><span class="sxs-lookup"><span data-stu-id="d3630-106">Example</span></span>  
 <span data-ttu-id="d3630-107">下列程式碼示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。</span><span class="sxs-lookup"><span data-stu-id="d3630-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="d3630-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d3630-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3630-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3630-109">See Also</span></span>  
 [<span data-ttu-id="d3630-110">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3630-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
