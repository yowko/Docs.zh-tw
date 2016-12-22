---
title: "傳遞參數 (C# 程式設計手冊) | Microsoft Docs"
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
  - "引數 [C#]"
  - "C# 語言, 方法參數"
  - "方法 [C#], 傳遞參數"
  - "參數 [C#], 傳遞"
  - "傳遞參數 [C#]"
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 傳遞參數 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在 C\# 中，引數可以藉由傳值 \(By Value\) 或傳址 \(By Reference\) 方式來傳遞至參數。  以傳址方式傳遞，可讓函式成員、方法、屬性、索引子、運算子及建構函式變更參數的值，並在呼叫環境中保存該變更。  若要以傳址方式傳遞參數，請使用 `ref` 或 `out` 關鍵字。  為了簡化，所以本主題的範例中只使用 `ref` 關鍵字。  如需 `ref` 與 `out` 之間差異的詳細資訊，請參閱 [ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out.md) 和[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。  
  
 下列範例會說明值和參考參數之間的差異。  
  
 [!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [傳遞實值類型參數](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [傳遞參考類型參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)