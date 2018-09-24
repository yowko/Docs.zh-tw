---
title: 從 XML 樹狀結構移除項目、屬性和節點 (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 9ce63ce6a4ef75dedc788efca11e8dd2bdb471eb
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46584112"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>從 XML 樹狀結構移除項目、屬性和節點 (C#)
您可以修改 XML 樹狀以移除項目、屬性以及其他類型的節點。  
  
 從 XML 文件移除單一項目或單一屬性很直接。 不過，移除項目或屬性的集合時，您應該先將集合具體化到清單中，然後從清單中刪除項目或屬性。 最好的方法是，使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法替您執行。  
  
 這麼做的主要原因是因為您從 XML 樹狀結構中擷取的大部分集合都是使用延後執行產生的。 如果您沒有先將這些集合具體化到清單中，或沒有使用擴充方法，則可能發生特定類別的 Bug。 如需詳細資訊，請參閱[混合的宣告式程式碼/命令式程式碼 Bug (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)。  
  
 下列方法會從 XML 樹狀移除節點和屬性。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|從其父代移除 <xref:System.Xml.Linq.XAttribute>。|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|從 <xref:System.Xml.Linq.XContainer> 移除子節點。|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|從 <xref:System.Xml.Linq.XElement> 移除內容和屬性。|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|移除 <xref:System.Xml.Linq.XElement> 的屬性。|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|如果您針對值傳遞 `null`，則會移除屬性。|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|如果您針對值傳遞 `null`，則會移除子項目。|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|從其父代移除 <xref:System.Xml.Linq.XNode>。|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|從其父項目移除來源集合中的每個屬性或項目。|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 這個範例會示範三種移除項目的方法。 首先，它會移除單一項目。 接著，它會反覆運算項目的集合，使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 運算子具體化它們，然後移除集合。 最後，它會擷取項目的集合，並使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法加以移除。  
  
 如需 <xref:System.Linq.Enumerable.ToList%2A> 運算子的詳細資訊，請參閱[轉換資料類型 (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)。  
  
### <a name="code"></a>程式碼  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
    <Child1>  
        <GrandChild1/>  
        <GrandChild2/>  
        <GrandChild3/>  
    </Child1>  
    <Child2>  
        <GrandChild4/>  
        <GrandChild5/>  
        <GrandChild6/>  
    </Child2>  
    <Child3>  
        <GrandChild7/>  
        <GrandChild8/>  
        <GrandChild9/>  
    </Child3>  
</Root>");  
root.Element("Child1").Element("GrandChild1").Remove();  
root.Element("Child2").Elements().ToList().Remove();  
root.Element("Child3").Elements().Remove();  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>註解  
 此程式碼會產生下列輸出：  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 請注意，第一個後代子項目已從 `Child1` 移除。 所有後代子項目都已經從 `Child2` 和 `Child3` 移除。  
  
## <a name="see-also"></a>請參閱

- [修改 XML 樹狀結構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
