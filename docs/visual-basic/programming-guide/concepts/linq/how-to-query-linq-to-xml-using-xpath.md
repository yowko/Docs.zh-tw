---
title: 如何：使用 XPath 查詢 LINQ to XML
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: 563756c019ddd458d46f47c843e32ddc7bbaacd1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347649"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>如何：使用 XPath 查詢 LINQ to XML （Visual Basic）
本主題說明可讓您使用 XPath 查詢 XML 樹狀結構的擴充方法。 如需有關使用這些擴充方法的詳細資訊，請參閱 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。  
  
 除非您已經有非常特定的理由要使用 XPath 查詢 (例如，廣泛使用舊版程式碼)，否則，不建議搭配 LINQ to XML 使用 XPath。 XPath 查詢將不會與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢一起執行。  
  
## <a name="example"></a>範例  
 下列範例會建立小型 XML 樹狀結構，並使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 來選取一組項目。  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>另請參閱

- [先進的查詢技術（LINQ to XML）（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
