---
title: "傳遞參考類型的參數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "方法參數 [C#], 參考類型"
  - "參數 [C#], 參考"
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 傳遞參考類型的參數 (C# 程式設計手冊)
[參考型別](../../../csharp/language-reference/keywords/reference-types.md)的參數並不會直接包含它的資料；它包含資料的參考。  以傳值方式傳遞參考型別參數時，它有可能會變更到參考指到的資料，例如類別成員的值。  然而，您無法變更參考本身的值；您不能使用相同的參考來對一個新類別配置記憶體和使它保存在區塊外。  若要完成上面所述，請使用 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 關鍵字傳遞參數。  為了簡化，下列範例使用 `ref`。  
  
## 以傳遞值的方式傳遞參考型別  
 下列範例說明以傳值方式將參考型別參數 `arr` 傳遞到 `Change` 方法。  因為參數是 `arr` 的參考，它有可能變更到陣列元素的值。  然而，嘗試將參數指派到不同的記憶體位置，只會在方法內產生作用，並不會影響到原本的變數 `arr`。  
  
 [!code-cs[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 在之前的範例中，參考具型別陣列 `arr` 被傳遞到方法中沒有使用 `ref` 參數。  在這個例子，傳遞到方法的是指向 `arr` 參考的複本。  輸出顯示，此種方法有可能變更陣列元素的內容，在此情況下為從 `1` 到 `888`。  然而，在 `Change` 方法內使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子配置新的記憶體部分，即可使變數 `pArray` 參考產生新的陣列。  因此，之後的任何變更並不會影響到在 `Main` 中所產生的原始陣列 `arr`。  事實上，本範例中建立了兩個陣列：一個在 `Main` 裡面，另一個在 `Change` 方法內。  
  
## 以傳遞參考的方式傳遞參考型別  
 下列範例等同於先前範例中，除了， `ref`關鍵字加入至方法標頭和呼叫。  在方法上進行任何變更會影響呼叫程式中的原始變數。  
  
 [!code-cs[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 發生在方法內的所有變更會影響 `Main` 裡面的原始陣列。  事實上，原始陣列是用 `new` 運算子重新配置的。  因此，呼叫 `Change` 方法後，任一個 `arr` 的參考都會指到 `Change` 方法內所建立五個元素的陣列。  
  
## 交換兩個字串  
 以傳址方式傳遞參考型別參數的良好範例便是交換字串。  在本範例中，字串 `str1` 和 `str2` 是在 `Main` 內初始化，並以 `ref` 關鍵字修改它來做為傳遞到 `SwapStrings` 方法的參數。  兩個字串同時在方法內和 `Main` 內交換。  
  
 [!code-cs[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 在本範例中，參數需要以傳址方式傳遞參數以影響呼叫程式內的變數。  如果您將 `ref` 關鍵字從方法標頭和方法呼叫中移除，則在呼叫程式中不會發生任何變更。  
  
 如需字串的詳細資訊，請參閱[字串](../../../csharp/language-reference/keywords/string.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [傳遞參數](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [參考類型](../../../csharp/language-reference/keywords/reference-types.md)