---
title: "複製與附加 (C#)"
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
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 672bea849949ecfbf0aef3390556950356b5caff
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="cloning-vs-attaching-c"></a><span data-ttu-id="0f50a-102">複製與附加 (C#)</span><span class="sxs-lookup"><span data-stu-id="0f50a-102">Cloning vs. Attaching (C#)</span></span>
<span data-ttu-id="0f50a-103">將 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件加入到新的樹狀結構時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0f50a-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="0f50a-104">如果新內容已經成為父代，而且屬於其他 XML 樹狀結構的一部分，則會複製新內容。</span><span class="sxs-lookup"><span data-stu-id="0f50a-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="0f50a-105">然後，新複製的內容會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0f50a-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f50a-106">範例</span><span class="sxs-lookup"><span data-stu-id="0f50a-106">Example</span></span>  
 <span data-ttu-id="0f50a-107">下列程式碼示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。</span><span class="sxs-lookup"><span data-stu-id="0f50a-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
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
  
 <span data-ttu-id="0f50a-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0f50a-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f50a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f50a-109">See Also</span></span>  
 [<span data-ttu-id="0f50a-110">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="0f50a-110">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

