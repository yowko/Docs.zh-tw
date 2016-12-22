---
title: "傳遞實值類型的參數 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "方法參數 [C#], 實值類型"
  - "參數 [C#], value"
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 傳遞實值類型的參數 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[實值型別](../../../csharp/language-reference/keywords/value-types.md)變數直接包含其資料，這點相對於[參考型別](../../../csharp/language-reference/keywords/reference-types.md)變數包含其資料的參考。  傳值方式傳遞實值型別變數的方法，以表示該變數的複本傳遞給方法。  給參數的方法內發生的任何變更會對不會影響到原本的資料儲存在引數的變數。  如果您想要變更參數的值被呼叫的方法，您必須傳送它所參考，使用 [ref](../../../csharp/language-reference/keywords/ref.md) 或[出](../../../csharp/language-reference/keywords/out.md)關鍵字。  為了簡化，下列範例使用 `ref`。  
  
## 以傳值方式傳遞實值型別  
 下列範例說明以傳值方式傳遞實值型別。  變數 `n` 是以傳值方式傳遞到方法 `SquareIt`。  在方法中對參數的任何變更並不會影響到變數原本的值。  
  
 [!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 將變數`n`實值型別。  它包含它的資料，值`5`。  在叫用 \(Invoke\) `SquareIt` 時，`n` 的內容便會複製到方法括號內的 `x` 參數。  在`Main`，然而，值`n`之後相同電話`SquareIt`發生之前的方法。  發生在方法內的變更只會影響區域變數`x`。  
  
## 以傳遞參考的方式傳遞實值型別  
 下列範例等同於先前的範例中，不同之處在於引數傳遞為`ref`參數。  基礎的引數，值`n`，何時變更`x`方法中發生變更。  
  
 [!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 在本範例中，並非傳遞 `n` 的值；而是傳遞 `n` 的參考。  參數 `x` 不是 [int](../../../csharp/language-reference/keywords/int.md)，而是 `int` 的參考。在此情況下為 `n` 的參考。  因此，當`x`求取平方時的方法，什麼實際上就是`x`指的是， `n`。  
  
## 交換實值型別  
 變更引數的值的常見例子為 swap 方法，其中您將兩個變數傳遞至方法，而此方法交換它們的內容。  您必須引數 swap 方法以傳址方式傳遞。  否則，您切換至方法中，參數的本機複本，並不會變更在呼叫的方法。  下列範例將交換的整數值。  
  
 [!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 當您呼叫`SwapByRef`方法中使用`ref`在呼叫時，如下列範例所示的關鍵字。  
  
 [!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [傳遞參數](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [傳遞參考類型參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)