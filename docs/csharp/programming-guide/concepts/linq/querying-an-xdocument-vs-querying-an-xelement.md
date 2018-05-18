---
title: 查詢 XDocument 與查詢 XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 61d8c70b9cbaeeb487059e4acfc88dc165c45d65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>查詢 XDocument 與查詢 XElement (C#)
當您透過 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 載入文件時，您將會注意到您必須撰寫的查詢與透過 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 載入時撰寫的查詢稍有不同。  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument.Load 和 XElement.Load 之比較  
 當您透過 <xref:System.Xml.Linq.XElement>，將 XML 文件載入到 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 時，XML 樹狀結構根目錄的 <xref:System.Xml.Linq.XElement> 會包含已載入之文件的根項目。 不過，當您透過 <xref:System.Xml.Linq.XDocument>，將相同的 XML 文件載入到 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 時，樹狀目錄的根目錄為 <xref:System.Xml.Linq.XDocument> 節點，而已載入之文件的根項目為允許 <xref:System.Xml.Linq.XElement> 之子系 <xref:System.Xml.Linq.XDocument> 節點的項目。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 座標軸會相對於根節點進行運算。  
  
 這個第一個範例會使用 <xref:System.Xml.Linq.XElement.Load%2A> 載入 XML 樹狀結構。 接著，它會針對樹狀結構根目錄的子項目進行查詢。  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 這個範例預期會產生下列輸出：  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 下列範例與上述範例幾乎相同，不同處在於會將 XML 樹狀結構載入到 <xref:System.Xml.Linq.XDocument> 而非 <xref:System.Xml.Linq.XElement>。  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 這個範例會產生下列輸出：  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 請注意，相同的查詢會傳回一個 `Root` 節點，而非三個子節點。  
  
 其中一個處理方法為，在存取座標軸方法之前，先使用 <xref:System.Xml.Linq.XDocument.Root%2A> 屬性，如下所示：  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 這個查詢現在會以查詢樹狀結構根目錄 <xref:System.Xml.Linq.XElement> 的相同方式執行。 這個範例會產生下列輸出：  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>請參閱  
 [基本查詢 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
