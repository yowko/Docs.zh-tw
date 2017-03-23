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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 81cbcb066d60851ba83bd4d783d34f8dd3bd1fac
ms.lasthandoff: 03/13/2017

---
# <a name="cloning-vs-attaching-visual-basic"></a>複製與附加 (Visual Basic)
當加入<xref:System.Xml.Linq.XNode>(包括<xref:System.Xml.Linq.XElement>) 或<xref:System.Xml.Linq.XAttribute>物件至新的樹狀目錄中，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode> 如果新內容已經成為父代，而且屬於其他 XML 樹狀結構的一部分，則會複製新內容。 然後，新複製的內容會附加到新的 XML 樹狀結構。  
  
## <a name="example"></a>範例  
 下列程式碼示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。  
  
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
  
 這個範例會產生下列輸出：  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
