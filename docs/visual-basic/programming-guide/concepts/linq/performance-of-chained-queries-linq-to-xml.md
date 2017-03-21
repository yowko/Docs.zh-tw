---
title: "鏈結的查詢 (LINQ to XML) 的效能 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dd5b63f255107c5864108cfbb87bef6e53a971a0
ms.lasthandoff: 03/13/2017


---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>鏈結的查詢 (LINQ to XML) 的效能 (Visual Basic)
LINQ (和 LINQ to XML) 其中一個最重要的優點在於，鏈結查詢的執行效能就如同單一較大且更複雜的查詢。  
  
 鏈結查詢是指使用其他查詢當做其來源的查詢。 例如，在下列簡單程式碼中，`query2` 具有 `query1` 當做其來源：  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
  
```  
  
 這個範例會產生下列輸出：  
  
```  
4  
```  
  
 這個鏈結查詢會與逐一查看連結串列 (Linked List) 提供相同的效能設定檔。  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>軸基本上具有相同的效能與逐一查看連結串列。</xref:System.Xml.Linq.XContainer.Elements%2A> <xref:System.Xml.Linq.XContainer.Elements%2A>會實作成延後執行迭代器。</xref:System.Xml.Linq.XContainer.Elements%2A> 這表示，除了逐一查看連結串列以外，它會執行一些工作，例如配置 Iterator 物件和追蹤執行狀態。 這項工作可分成兩個分類：在設定 Iterator 時完成的工作，以及在每次反覆運算期間完成的工作。 設定工作是小型且固定的工作量，而在每次反覆運算期間完成的工作則與來源集合中的項目數成正比。  
  
-   在`query1`、`Where`子句會讓查詢呼叫<xref:System.Linq.Enumerable.Where%2A>方法。</xref:System.Linq.Enumerable.Where%2A> 這個方法也會實作成 Iterator。 設定工作包含具現化將參考 Lambda 運算式的委派 (Delegate)，以及進行 Iterator 的一般設定。 進行每次反覆運算時，系統會呼叫此委派來執行述詞 (Predicate)。 設定工作以及在每次反覆運算期間完成的工作與逐一查看軸時完成的工作很相似。  
  
-   在`query1`，select 子句會讓查詢呼叫<xref:System.Linq.Enumerable.Select%2A>方法。</xref:System.Linq.Enumerable.Select%2A> 這個方法具有相同的效能設定檔，做為<xref:System.Linq.Enumerable.Where%2A>方法。</xref:System.Linq.Enumerable.Where%2A>  
  
-   在 `query2` 中，`Where` 子句和 `Select` 子句都具有相同的效能設定檔，如同 `query1`。  
  
 因此，逐一查看 `query2` 的作業會直接與第一個查詢之來源中的項目數成正比 (亦即，線性時間)。  
  
## <a name="see-also"></a>另請參閱  
 [效能 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
