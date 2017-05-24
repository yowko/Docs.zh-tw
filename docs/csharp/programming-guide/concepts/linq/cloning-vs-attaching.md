---
title: "複製與附加 (C#) | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 784c3b92ce10878b244ae5d965f5033a6ee6f9ae
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="cloning-vs-attaching-c"></a>複製與附加 (C#)
將 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件新增至新的樹狀結構時，如果新內容沒有父代，則這些物件只會附加至 XML 樹狀結構。 如果新內容已經成為父代，而且屬於其他 XML 樹狀結構的一部分，則會複製新內容。 然後，新複製的內容會附加到新的 XML 樹狀結構。  
  
## <a name="example"></a>範例  
 下列程式碼示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。  
  
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
  
 這個範例會產生下列輸出：  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
