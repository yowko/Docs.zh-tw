---
title: 如何：使用 Descendants 方法尋找單一子系 (C#)
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: e08e07e0d32146a14b90b9d6463e6e58a233a923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a>如何：使用 Descendants 方法尋找單一子系 (C#)
您可以使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸方法快速撰寫程式碼以尋找唯一具名的單一項目。 當您想要利用特定名稱尋找特定子代時，這個技術特別實用。 您可以撰寫程式碼來導覽所需的項目，但使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸撰寫程式碼通常比較快也比較容易。  
  
## <a name="example"></a>範例  
 此範例使用 <xref:System.Linq.Enumerable.First%2A> 標準查詢運算子。  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 此程式碼會產生下列輸出：  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 此程式碼會產生下列輸出：  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a>請參閱  
 [基本查詢 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
