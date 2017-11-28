---
title: "已鏈結之查詢的效能 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1014b7790f0ea465e10cf8fc03e59ca4d3f2d55c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>已鏈結之查詢的效能 (LINQ to XML) (C#)
LINQ (和 LINQ to XML) 其中一個最重要的優點在於，鏈結查詢的執行效能就如同單一較大且更複雜的查詢。  
  
 鏈結查詢是指使用其他查詢當做其來源的查詢。 例如，在下列簡單程式碼中，`query2` 具有 `query1` 當做其來源：  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 這個範例會產生下列輸出：  
  
```  
4  
```  
  
 這個鏈結查詢會與逐一查看連結串列 (Linked List) 提供相同的效能設定檔。  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> 軸基本上與逐一查看連結串列具有相同的效能。 <xref:System.Xml.Linq.XContainer.Elements%2A> 會實作成延後執行的 Iterator。 這表示，除了逐一查看連結串列以外，它會執行一些工作，例如配置 Iterator 物件和追蹤執行狀態。 這項工作可分成兩個分類：在設定 Iterator 時完成的工作，以及在每次反覆運算期間完成的工作。 設定工作是小型且固定的工作量，而在每次反覆運算期間完成的工作則與來源集合中的項目數成正比。  
  
-   在 `query1` 中，`where` 子句會讓查詢呼叫 <xref:System.Linq.Enumerable.Where%2A> 方法。 這個方法也會實作成 Iterator。 設定工作包含具現化將參考 Lambda 運算式的委派 (Delegate)，以及進行 Iterator 的一般設定。 進行每次反覆運算時，系統會呼叫此委派來執行述詞 (Predicate)。 設定工作以及在每次反覆運算期間完成的工作與逐一查看軸時完成的工作很相似。  
  
-   在 `query1` 中，select 子句會讓查詢呼叫 <xref:System.Linq.Enumerable.Select%2A> 方法。 這個方法與 <xref:System.Linq.Enumerable.Where%2A> 方法具有相同的效能設定檔。  
  
-   在 `query2` 中，`where` 子句和 `select` 子句都具有相同的效能設定檔，如同 `query1`。  
  
 因此，逐一查看 `query2` 的作業會直接與第一個查詢之來源中的項目數成正比 (亦即，線性時間)。 對應的 Visual Basic 範例會具有相同的效能設定檔。  
  
 如需迭代器的詳細資訊，請參閱 [yield](../../../../csharp/language-reference/keywords/yield.md)。  
  
 如需將查詢鏈結在一起的詳細教學課程，請參閱[教學課程：將查詢鏈結在一起](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c)。  
  
## <a name="see-also"></a>另請參閱  
 [效能 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
