---
title: "泛型類型參數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "泛型 [C#], 類型參數"
  - "類型參數 [C#]"
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# 泛型類型參數 (C# 程式設計手冊)
在泛型型別或方法定義中，型別參數是用戶端在產生泛型型別的變數時所指定之特定型別的替代符號 \(Placeholder\)。  泛型類別 \(例如[泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md) 中列出的 `GenericList<T>`\) 無法以原本的狀態使用，因為它不是真的型別，而比較像是型別的藍圖。  若要使用 `GenericList<T>`，用戶端程式碼必須藉由在角括弧內指定型別引數，以宣告和產生建構的型別。  這個特定類別的型別引數可以是編譯器能夠辨認的任意型別。  您可以建立任意數目的建構型別執行個體，每個執行個體使用不同的型別引數，如下所示：  
  
 [!code-cs[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 在 `GenericList<T>` 的每個執行個體中，類別內的每個 `T` 項目都將在執行階段被型別引數取代。  藉由這項取代動作，就會使用單一類別定義建立三個不同的型別安全和效率物件。  如需 CLR 如何執行這項取代的詳細資訊，請參閱[執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。  
  
## 型別參數命名方針  
  
-   **最好**使用描述性名稱命名泛型型別，除非單一字母名稱可以充分自我闡明而描述性名稱無法再增添任何幫助。  
  
     [!code-cs[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **考慮**為使用單一字母型別參數之型別使用 T 做為其型別參數名稱。  
  
     [!code-cs[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **最好**使用 "T" 當做前置描述性型別參數名稱。  
  
     [!code-cs[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **考慮**將指示條件約束置於參數名稱中的型別參數。  例如，限制為 `ISession` 的參數可以稱為 `TSession`。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)   
 [C\+\+ 樣板和 C\# 泛型之間的差異](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)