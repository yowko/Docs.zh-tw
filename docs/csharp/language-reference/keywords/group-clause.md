---
title: "group 子句 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "group"
  - "group_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "group 子句 [C#]"
  - "group 關鍵字 [C#]"
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# group 子句 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`group` 子句會傳回包含零個或多個符合群組之索引鍵值的 <xref:System.Linq.IGrouping%602> 物件序列。  例如，您可以根據每個字串中的第一個字母來群組字串序列。  在此情況下，第一個字母是索引鍵，而且具有 [char](../../../csharp/language-reference/keywords/char.md) 的型別，並儲存在每個 <xref:System.Linq.IGrouping%602> 物件的 `Key` 屬性中。  編譯器會推斷索引鍵的型別。  
  
 您可以在查詢運算式的結尾使用 `group` 子句，如下列範例所示：  
  
 [!code-cs[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 如果您想在每個群組上執行其他查詢作業，可以使用 [into](../../../csharp/language-reference/keywords/into.md) 內容關鍵字指定暫時識別項。  使用 `into` 時，您必須繼續進行查詢，最後再以 `select` 陳述式或其他 `group` 子句結束查詢，如下列摘錄所示：  
  
 [!code-cs[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 更多關於搭配和不搭配 `into` 來使用 `group` 的完整範例，都提供於本主題的＜範例＞一節。  
  
## 列舉群組查詢的結果  
 因為 `group` 查詢所產生的 <xref:System.Linq.IGrouping%602> 物件基本上是清單的清單，所以您必須使用巢狀的 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 迴圈來存取每個群組中的項目。  外部迴圈會逐一查看群組索引鍵，而內部迴圈則會逐一查看每個群組本身的每個項目。  群組可能只有索引鍵而沒有項目。  在前述程式碼範例中，執行查詢的 `foreach` 迴圈看起來就像這樣：  
  
 [!code-cs[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## 索引鍵型別  
 群組索引鍵可以是任何型別，例如字串、內建數值型別，或是使用者定義的具名型別或匿名型別。  
  
### 依字串群組  
 前述程式碼範例使用的是 `char`。  您可以輕易改為指定字串索引鍵，例如完整的姓氏。  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### 依 bool 群組  
 下列範例示範如何使用 bool 值做為索引鍵，以便將結果分成兩組。  請注意，這些值是由 `group` 子句中的子運算式所產生。  
  
 [!code-cs[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### 依數值範圍群組  
 下一個範例使用運算式來建立代表百分位數範圍的數值群組索引鍵。  請注意，此範例使用 [let](../../../csharp/language-reference/keywords/let-clause.md) 當做方便儲存方法呼叫結果的位置，因此您不需要在 `group` 子句中呼叫方法兩次。  另外，在 `group` 子句中，為了避免「除以零」的例外狀況，程式碼也會進行檢查，以確定學生的平均值不是零。  如需如何在查詢運算式中安全地使用方法的詳細資訊，請參閱 [如何：處理查詢運算式中的例外狀況](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)。  
  
 [!code-cs[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### 依複合索引鍵群組  
 當您想要依據一個以上的索引鍵來群組項目時，請使用複合索引鍵。  您可以使用匿名型別或具名型別來保存索引鍵項目，以便建立複合索引鍵。  在下列範例中，請假設類別 `Person` 已經利用名稱為 `surname` 和 `city` 的成員進行宣告。  `group` 子句將會針對每一組姓氏相同且住在同一個城市的學生，建立一個個別的群組。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 如果您必須將查詢變數傳遞到其他方法，請使用命名型別。  請使用索引鍵的自動實作屬性建立特殊類別，然後再覆寫 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 方法。  您也可以使用結構 \(Struct\)，如此您就不一定要覆寫這些方法。  如需詳細資訊，請參閱[如何：使用自動實作的屬性來實作輕量型類別](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)和[How to: Query for Duplicate Files in a Directory Tree \(LINQ\)](../Topic/How%20to:%20Query%20for%20Duplicate%20Files%20in%20a%20Directory%20Tree%20\(LINQ\).md)。  第二個主題包含程式碼範例，以示範如何搭配命名型別來使用複合索引鍵。  
  
## 範例  
 下列範例顯示在未對群組套用其他查詢邏輯的情況下，將來源資料排序的標準模式。  這種做法稱為無接續群組。  字串陣列中的元素會根據它們的第一個字母來分組。  查詢的結果是包含 `char` 型別之公用 `Key` 屬性的 <xref:System.Linq.IGrouping%602> 型別，以及包含群組中各個項目的 <xref:System.Collections.Generic.IEnumerable%601> 集合。  
  
 `group` 子句的結果是由多個序列組成的序列。  因此，若要存取每個傳回之群組內的個別項目，請依下列範例所示，在反覆查看群組索引鍵的迴圈內使用巢狀 `foreach` 迴圈。  
  
 [!code-cs[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## 範例  
 本範例示範如何在建立群組之後，搭配使用「*接續*」\(Continuation\) 和 `into`，對群組執行額外的邏輯。  如需詳細資訊，請參閱 [into](../../../csharp/language-reference/keywords/into.md)。  下列範例會查詢每個群組，並選取其索引鍵值為母音的項目。  
  
 [!code-cs[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## 備註  
 在編譯時期，`group` 子句會轉譯成 <xref:System.Linq.Enumerable.GroupBy%2A> 方法的呼叫。  
  
## 請參閱  
 <xref:System.Linq.IGrouping%602>   
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.Enumerable.ThenBy%2A>   
 <xref:System.Linq.Enumerable.ThenByDescending%2A>   
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)   
 [如何：建立巢狀群組](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [如何：分組查詢結果](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)   
 [如何：在分組作業上執行子查詢](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)