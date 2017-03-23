---
title: "如何：了解傳遞結構和傳遞類別參考給方法之間的差異 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "方法 [C#], 傳遞類別與結構的比較"
  - "傳遞參數 [C#], 結構與類別的比較"
  - "結構 [C#], 做為方法參數傳遞"
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# 如何：了解傳遞結構和傳遞類別參考給方法之間的差異 (C# 程式設計手冊)
下列範例示範如何傳遞[結構](../../../csharp/language-reference/keywords/struct.md) 方法中，不同於傳遞 [類別](../../../csharp/language-reference/keywords/class.md)方法的執行個體。  在範例中，這兩個引數 \(結構和類別執行個體\) 所傳值方式傳遞，並將這兩種方法的引數的其中一個欄位值的變更。  不過，這兩種方法的結果並不相同因為當您傳遞結構在於傳遞差別在於傳遞時，類別的執行個體。  
  
 因為結構是 [實值型別](../../../csharp/language-reference/keywords/value-types.md)，當您 [傳遞傳值方式的結構](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)方法，方法會接收並結構引數數的複本上作業。   方法呼叫的方法中有不允許存取原始的結構，因此不能變更它的任何方式。  只有複本時，可以變更方法。  
  
 類別執行個體是[參考型別](../../../csharp/language-reference/keywords/reference-types.md)，不是實值型別。  當[是參考型別以傳值方式傳遞](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)方法，方法會收到一份類別執行個體的參考。  亦即，方法會收到一份不該執行個體本身的複本執行個體的位址。  呼叫的方法中的類別執行個體有地址、參數中被呼叫的方法有一份該地址，而這兩種位址參考相同的物件。  參數會包含的地址的複本，因為被呼叫的方法就無法變更呼叫的方法中的類別執行個體的位址。  不過，被呼叫的方法可以使用位址來存取類別成員，原來的位址，並複製參考。  如果被呼叫的方法會變更類別成員，呼叫的方法中的原始類別執行個體也會變更。  
  
 下列範例的輸出會說明這項差異。  值為`willIChange`方法的呼叫會變更它的類別執行個體的欄位`ClassTaker`因為方法參數中使用的位址，以找出類別的執行個體指定的欄位。    `willIChange`方法的呼叫不會變更欄位的結構，呼叫的方法中`StructTaker`因為引數的值是一份結構本身，不是其地址的複本。    `StructTaker`變更複本中，而複本會遺失何時呼叫`StructTaker`完畢。  
  
## 範例  
 [!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [傳遞參數](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)