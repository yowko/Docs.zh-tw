---
title: "匿名方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "匿名方法 [C#]"
  - "委派 [C#], 匿名方法"
  - "方法 [C#], 匿名"
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# 匿名方法 (C# 程式設計手冊)
在 C\# 2.0 以前的版本中，宣告[委派](../../../csharp/language-reference/keywords/delegate.md) \(Delegate\) 的唯一方式是使用[具名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)。  C\# 2.0 引進了匿名方法 \(Anonymous Method\)，在 C\# 3.0 \(含\) 以後版本，則以 Lambda 運算式取代匿名方法來做為撰寫內嵌 \(Inline\) 程式碼的慣用方式。  不過，本主題中關於匿名方法的資訊也同時適用於 Lambda 運算式。  在某個特定情況下，匿名方法會提供 Lambda 運算式未提供的功能。  匿名方法可以讓您省略參數清單，  而這表示匿名方法可以轉換為具有各種簽章的委派。  Lambda 運算式並未提供這項功能。  如需 Lambda 運算式的專屬詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 基本上，建立匿名方法是將程式碼區塊當做委派參數傳遞的一種方式。  以下為兩個範例：  
  
 [!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 在使用匿名方法時，因為不需要建立個別的方法，所以您可以減少在具現化委派時所需要另外撰寫的程式碼。  
  
 例如，當需要建立似乎不太有必要的方法時，就可以指定程式碼區塊來替代委派。  啟動新執行緒時就是個好例子。  這個類別會建立執行緒，並會包含執行緒所執行的程式碼，而不需要為委派建立額外方法。  
  
 [!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## 備註  
 匿名方法之參數的範圍就是 *anonymous\-method\-block*。  
  
 如果目標位於匿名方法區塊外部，則在區塊內部便不能放入跳躍陳述式 \(Jump Statement\)，例如 [goto](../../../csharp/language-reference/keywords/goto.md)、[break](../../../csharp/language-reference/keywords/break.md) 或 [continue](../../../csharp/language-reference/keywords/continue.md)。  如果目標位於匿名方法區塊內部，則在區塊外部也不能出現跳躍陳述式，例如 `goto`、`break` 或 `continue`。  
  
 若區域變數和參數的範圍包含匿名方法宣告，這些變數和參數便稱為匿名方法的 *outer* 變數。  例如，在下面一段程式碼中，`n` 即為外部變數：  
  
 [!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 外部變數的參考`n`即為*擷取*委派建立時。  與區域變數不同的是擷取變數的存留期會延伸直到參考匿名方法的委派可進行記憶體回收為止。  
  
 匿名方法不能存取外部範圍的 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數。  
  
 在 *anonymous\-method\-block* 內部不能存取任何 Unsafe 程式碼。  
  
 [is](../../../csharp/language-reference/keywords/is.md) 運算子的左邊不允許使用匿名方法。  
  
## 範例  
 下列範例會示範具現化委派的兩種方式：  
  
-   將一個匿名方法與該委派建立關聯  
  
-   將一個具名的方法 \(`DoWork`\) 與該委派建立關聯  
  
 該委派被叫用 \(Invoke\) 時都會顯示訊息。  
  
 [!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [使用具名和匿名方法委派的比較](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)