---
title: 複製與附加 (C#)
ms.date: 07/20/2015
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
ms.openlocfilehash: 31b5498e18e63ffba357b34780c7eb388e08b37f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cloning-vs-attaching-c"></a><span data-ttu-id="aea50-102">複製與附加 (C#)</span><span class="sxs-lookup"><span data-stu-id="aea50-102">Cloning vs. Attaching (C#)</span></span>
<span data-ttu-id="aea50-103">將 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件加入到新的樹狀結構時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="aea50-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="aea50-104">如果新內容已經成為父代，而且屬於其他 XML 樹狀結構的一部分，則會複製新內容。</span><span class="sxs-lookup"><span data-stu-id="aea50-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="aea50-105">然後，新複製的內容會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="aea50-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea50-106">範例</span><span class="sxs-lookup"><span data-stu-id="aea50-106">Example</span></span>  
 <span data-ttu-id="aea50-107">下列程式碼示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。</span><span class="sxs-lookup"><span data-stu-id="aea50-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="aea50-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="aea50-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="aea50-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="aea50-109">See Also</span></span>  
 [<span data-ttu-id="aea50-110">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="aea50-110">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
