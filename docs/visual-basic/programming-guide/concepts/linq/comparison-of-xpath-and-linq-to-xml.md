---
title: "比較 XPath 和 LINQ to XML1 |Microsoft 文件"
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
ms.assetid: c3fd07c1-6761-4e4b-8eb1-ddd780ed8d44
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e9601c51468fdf5adab8e521f8f89ee7f2e12869
ms.lasthandoff: 03/13/2017


---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath 和 LINQ to XML 的比較
XPath 和 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 提供一些類似的功能。 兩者都可用於查詢 XML 樹狀結構，將此類結果當做項目的集合、屬性的集合、節點的集合，以及項目或屬性的值傳回。 不過，也有一些差異。  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>XPath 與 LINQ to XML 之間的差異  
 XPath 不允許評估新的型別。 它只能從樹狀結構傳回節點的集合，而 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 可以執行查詢並評估新圖案中的物件圖形或 XML 樹狀結構。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢包含的功能更多，而且比 XPath 運算式的功能更強大。  
  
 XPath 運算式存在於字串內的隔離中。 Visual Basic 編譯器無法協助剖析 XPath 運算式，在編譯時期。 相較之下，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]剖析及 Visual Basic 編譯器所編譯的查詢。 該編譯器可以擷取許多查詢錯誤。  
  
 XPath 結果不是強型別 (Strongly Typed)。 在許多情況下，評估 XPath 運算式的結果不是物件，而且開發人員可以決定適當的型別，並在必要時轉換結果。 相較之下，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢的評估為強型別。  
  
## <a name="result-ordering"></a>結果順序  
 XPath 1.0 建議事項說明評估 XPath 運算式之結果的集合沒有排序。  
  
 不過，逐一查看由 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] XPath 軸方法傳回的集合時，會以文件順序傳回集合中的節點。 即使在存取 XPath 軸 (其中的述詞會根據反向的文件順序表示，例如，`preceding` 和 `preceding-sibling`) 時，也是如此。  
  
 相較之下，大部分的[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]軸會傳回集合中的文件順序，但其中，兩個<xref:System.Xml.Linq.XNode.Ancestors%2A>和<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>，以反向的文件順序傳回集合。</xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> </xref:System.Xml.Linq.XNode.Ancestors%2A> 下表列舉座標軸，並指出每個座標軸的集合順序：  
  
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
  
 請注意，上述的方法會具體化整個集合。 這不是撰寫該查詢的最有效方式。 此範例以該方式撰寫，以示範位置性述詞的行為。 若要撰寫相同查詢更適當的方式是使用<xref:System.Linq.Enumerable.First%2A>方法，如下︰ `anElement.ElementsBeforeSelf().First()`。</xref:System.Linq.Enumerable.First%2A>  
  
 如果您要在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中尋找正前面的項目，您可以撰寫下列運算式：  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>效能差異  
 使用 XPath 功能中的 XPath 查詢[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]將不會執行，如同[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]查詢。  
  
## <a name="comparison-of-composition"></a>撰寫比較  
 撰寫 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢與撰寫 XPath 運算式類似，但是在語法上非常不同。  
  
 例如，如果您在變數中有一個名稱為 `customers` 的項目，而且您想要在名稱為 `CompanyName` 的所有子項目下，尋找名稱為 `Customer` 的後代子項目，您可以撰寫 XPath 運算式，如下所示：  
  
```vb  
customers.XPathSelectElements("./Customer/CompanyName")  
```  
  
 對等的 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢是：  
  
```vb  
customers.Element("Customer").Elements("CompanyName")  
```  
  
 每個 XPath 座標軸都有類似的項目。  
  
|XPath 座標軸|LINQ to XML 軸|  
|----------------|----------------------|  
|child (預設軸)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|  
|Parent (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=fullName></xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=fullName>|  
|attribute 軸 (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|  
|ancestor 軸|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|  
|ancestor-or-self 軸|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|  
|descendant 軸 (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=fullName>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=fullName>|  
|following-sibling|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=fullName>|  
|preceding-sibling|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=fullName>|  
|following|沒有直接的對等。|  
|preceding|沒有直接的對等。|  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 的 XPath 使用者 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
