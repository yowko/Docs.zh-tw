---
title: XPath 和 LINQ to XML 的比較
ms.date: 07/20/2015
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: 64860ab538105e7e3826b29f83b8e713ca525e21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326429"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath 和 LINQ to XML 的比較
XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供一些類似的功能。 兩者都可用於查詢 XML 樹狀結構，將此類結果當做項目的集合、屬性的集合、節點的集合，以及項目或屬性的值傳回。 不過，也有一些差異。  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>XPath 與 LINQ to XML 之間的差異  
 XPath 不允許評估新的型別。 它只能從樹狀結構傳回節點的集合，而 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可以執行查詢並評估新圖案中的物件圖形或 XML 樹狀結構。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢包含的功能更多，而且比 XPath 運算式的功能更強大。  
  
 XPath 運算式存在於字串內的隔離中。 C# 編譯器在編譯時期無法協助剖析 XPath 運算式。 相較之下，C# 編譯器不會剖析與編譯 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢。 該編譯器可以擷取許多查詢錯誤。  
  
 XPath 結果不是強型別 (Strongly Typed)。 在許多情況下，評估 XPath 運算式的結果不是物件，而且開發人員可以決定適當的型別，並在必要時轉換結果。 相較之下，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的評估為強型別。  
  
## <a name="result-ordering"></a>結果順序  
 XPath 1.0 建議事項說明評估 XPath 運算式之結果的集合沒有排序。  
  
 不過，逐一查看由 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath 軸方法傳回的集合時，會以文件順序傳回集合中的節點。 即使在存取 XPath 軸 (其中的述詞會根據反向的文件順序表示，例如，`preceding` 和 `preceding-sibling`) 時，也是如此。  
  
 相較之下，大部分的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 軸會以文件順序傳回集合，但其中兩個 (<xref:System.Xml.Linq.XNode.Ancestors%2A> 和 <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>) 會以反向的文件順序傳回集合。 下表列舉座標軸，並指出每個座標軸的集合順序：  
  
|LINQ to XML 軸|排序|  
|----------------------|--------------|  
|XContainer.DescendantNodes|文件順序|  
|XContainer.Descendants|文件順序|  
|XContainer.Elements|文件順序|  
|XContainer.Nodes|文件順序|  
|XContainer.NodesAfterSelf|文件順序|  
|XContainer.NodesBeforeSelf|文件順序|  
|XElement.AncestorsAndSelf|反向的文件順序|  
|XElement.Attributes|文件順序|  
|XElement.DescendantNodesAndSelf|文件順序|  
|XElement.DescendantsAndSelf|文件順序|  
|XNode.Ancestors|反向的文件順序|  
|XNode.ElementsAfterSelf|文件順序|  
|XNode.ElementsBeforeSelf|文件順序|  
|XNode.NodesAfterSelf|文件順序|  
|XNode.NodesBeforeSelf|文件順序|  
  
## <a name="positional-predicates"></a>位置性述詞  
 在 XPath 運算式內，許多座標軸的位置性述詞都是以文件順序表示，但是反向座標軸則以反向的文件順序表示，這些反向座標軸包括 `preceding`、`preceding-sibling`、`ancestor` 和 `ancestor-or-self`。 例如，XPath 運算式 `preceding-sibling::*[1]` 會傳回正前面的同層級。 即使最後的結果集會以文件順序呈現，也是如此。  
  
 相較之下，LINQ to XML 中的所有位置性述詞都一律會以座標軸的順序表示。 例如，`anElement.ElementsBeforeSelf().ToList()[0]` 會傳回所查詢項目之父代的第一個子項目，而非正前面的同層級。 另一個範例：`anElement.Ancestors().ToList()[0]` 會傳回父項目。  
  
 請注意，上述的方法會具體化整個集合。 這不是撰寫該查詢的最有效方式。 此範例以該方式撰寫，以示範位置性述詞的行為。 撰寫相同查詢更適當的方式為使用 <xref:System.Linq.Enumerable.First%2A> 方法，如下所示：`anElement.ElementsBeforeSelf().First()`。  
  
 如果您要在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中尋找正前面的項目，您可以撰寫下列運算式：  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>效能差異  
 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中使用 XPath 功能的 XPath 查詢以及 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢將不會執行。  
  
## <a name="comparison-of-composition"></a>撰寫比較  
 撰寫 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢與撰寫 XPath 運算式類似，但是在語法上非常不同。  
  
 例如，如果您在變數中有一個名稱為 `customers` 的項目，而且您想要在名稱為 `CompanyName` 的所有子項目下，尋找名稱為 `Customer` 的後代子項目，您可以撰寫 XPath 運算式，如下所示：  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName");  
```  
  
 對等的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢是：  
  
```csharp  
customers.Element("Customer").Elements("CompanyName");  
```  
  
 每個 XPath 座標軸都有類似的項目。  
  
|XPath 座標軸|LINQ to XML 軸|  
|----------------|----------------------|  
|child (預設軸)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Parent (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|attribute 軸 (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|ancestor 軸|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|ancestor-or-self 軸|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|descendant 軸 (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|following-sibling|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|preceding-sibling|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|following|沒有直接的對等。|  
|preceding|沒有直接的對等。|  
  
## <a name="see-also"></a>請參閱  
 [XPath 使用者適用的 LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
