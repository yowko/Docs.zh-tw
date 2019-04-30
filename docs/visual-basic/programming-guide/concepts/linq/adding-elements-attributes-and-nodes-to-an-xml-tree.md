---
title: 將項目、 屬性和節點加入至 XML 樹狀結構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 35d3bdb27342dd7a871778ad4749db4d6849bd60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021852"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>將項目、 屬性和節點加入至 XML 樹狀結構 (Visual Basic)
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

- [修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
