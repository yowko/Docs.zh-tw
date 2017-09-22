---
title: "在執行階段動態指定述詞篩選"
description: "如何在執行階段動態指定述詞篩選。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e724428bce09e2b2fa20b9391ad131424e16413
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>在執行階段動態指定述詞篩選

在某些情況下，您要到執行階段才知道在 `where` 子句中必須套用多少述詞至來源項目。 動態指定多個述詞篩選的其中一個方式是使用 <xref:System.Linq.Enumerable.Contains%2A> 方法，如下列範例所示。 此範例以兩種方式建構。 首先，篩選程式中所提供的值來執行專案。 然後使用執行階段提供的輸入再次執行專案。  
  
## <a name="to-filter-by-using-the-contains-method"></a>使用 Contains 方法篩選  
  
1.  開啟新的主控台應用程式並命名為 `PredicateFilters`。  
  
2.  從[查詢物件集合](query-a-collection-of-objects.md)複製 `StudentClass` 類別，再將它貼入 `Program` 類別下的命名空間 `PredicateFilters`。 `StudentClass` 提供 `Student` 物件的清單。  
  
3.  以 `StudentClass` 註解 `Main` 方法。  
  
4.  使用下列程式碼取代 `Program` 類別。  
  
     [!code-cs[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  將下列行新增至 `ids` 宣告下之 `DynamicPredicates` 類別中的 `Main` 方法。  
  
     ```csharp
     QueryById(ids);
     ```

6.  執行專案。  
  
7.  主控台視窗會顯示下列輸出：  
  
     Garcia: 114  
  
     O'Donnell: 112  
  
     Omelchenko: 111  
  
8.  下一步是再次執行專案，這次使用在執行階段輸入的輸入，而不是陣列 `ids`。 在 `Main` 方法中，將 `QueryByID(ids)` 變更為 `QueryByID(args)`。  
  
9. 使用命令列引數 `122 117 120 115` 執行專案。 執行專案時，這些值會變成 `args` 的項目，`Main` 方法的參數。  
  
10. 主控台視窗會顯示下列輸出：  
  
     Adams: 120  
  
     Feng: 117  
  
     Garcia: 115  
  
     Tucker: 122  
  
## <a name="to-filter-by-using-a-switch-statement"></a>使用 switch 陳述式來篩選  
  
1.  您可以使用 `switch` 陳述式，在預先定義的替代查詢中選取。 在下例中，`studentQuery` 會根據執行階段指定的年級或年份，使用不同的 `where` 子句。  
  
2.  將下列方法複製並貼入 `DynamicPredicates` 類別中。  
  
     [!code-cs[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  在 `Main` 方法中，使用下列呼叫取代 `QueryByID` 的呼叫，將 `args` 陣列的第一個項目傳送為其引數︰`QueryByYear(args[0])`。  
  
4.  以 1 到 4 之間整數值的命令列引數執行專案。  
  
 
## <a name="see-also"></a>另請參閱  
 [LINQ 查詢運算式](index.md)   
 [where 子句](../language-reference/keywords/where-clause.md)

