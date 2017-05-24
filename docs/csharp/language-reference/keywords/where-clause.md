---
title: "where 子句 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1094f68293dd05fdfe69a39016689cbaa3fd6290
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="where-clause-c-reference"></a>where 子句 (C# 參考)
`where` 子句用於查詢運算式中，以指定將在查詢運算式中傳回資料來源中的項目。 它會將布林值條件 (*predicate*) 套用到每個來源項目 (透過範圍變數所參考)，並傳回所指定條件為 true 的項目。 單一查詢運算式可能會包含多個 `where` 子句，而單一子句可能會包含多個述詞子運算式。  
  
## <a name="example"></a>範例  
 在下列範例中，`where` 子句會篩選掉不小於五的所有數字。 如果您移除 `where` 子句，則會傳回資料來源中的所有數字。 `num < 5` 運算式是套用至每個項目的述詞。  
  
 [!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>範例  
 在單一 `where` 子句內，您可以使用 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 和 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 運算子來指定所需數目的述詞。 在下列範例中，查詢會指定兩個述詞，只選取小於五的偶數。  
  
 [!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>範例  
 `where` 子句可能包含一個或多個傳回布林值的方法。 在下列範例中，`where` 子句使用方法來判斷範圍變數的目前值是偶數還是奇數。  
  
 [!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>備註  
 `where` 子句是篩選機制。 它幾乎可以放在查詢運算式中的任何位置，但不能是第一個或最後一個子句。 `where` 子句可能出現在 [group](../../../csharp/language-reference/keywords/group-clause.md) 子句之前或之後，取決於必須在分組來源項目之前還是之後進行篩選。  
  
 如果指定的述詞不適用於資料來源中的項目，則會產生編譯時期錯誤。 這是 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 所提供的強類型檢查的其中一個優點。  
  
 在編譯時期，`where` 關鍵字會轉換為 <xref:System.Linq.Enumerable.Where%2A> 標準查詢運算子方法呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [查詢關鍵字 (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from 子句](../../../csharp/language-reference/keywords/from-clause.md)   
 [select 子句](../../../csharp/language-reference/keywords/select-clause.md)   
 [篩選資料](http://msdn.microsoft.com/library/cee88d0f-31aa-4c60-9452-cc122ed0057d)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [開始使用 C# 中的 LINQ](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
