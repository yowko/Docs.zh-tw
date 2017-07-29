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
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>將項目、屬性和節點新增至 XML 樹狀結構 (C#)
您可以將內容 (項目、屬性、註解、處理指示、文字和 CDATA) 加入到現有的 XML 樹狀結構中。  
  
## <a name="methods-for-adding-content"></a>加入內容的方法  
 下列方法會將子內容加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>：  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的結尾。|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的開頭。|  
  
 下列方法會加入內容，做為 <xref:System.Xml.Linq.XNode> 的同層級節點。 雖然您可以將有效的同層級內容加入到節點的其他型別 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XText>)，但是您加入同層級內容的最常見目標節點為 <xref:System.Xml.Linq.XComment>。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|將內容加入到 <xref:System.Xml.Linq.XNode> 之後。|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|將內容加入到 <xref:System.Xml.Linq.XNode> 之前。|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會建立兩個 XML 樹狀結構，然後修改其中一個樹狀結構。  
  
### <a name="code"></a>程式碼  
  
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
  
### <a name="comments"></a>註解  
 此程式碼會產生下列輸出：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [修改 XML 樹狀結構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

