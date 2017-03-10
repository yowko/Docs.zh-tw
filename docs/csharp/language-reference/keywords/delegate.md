---
title: "delegate (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "delegate_CSharpKeyword"
  - "delegate"
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "delegate 關鍵字 [C#]"
  - "函式指標 [C#]"
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# delegate (C# 參考)
委派型別的宣告與方法簽章類似。  它有傳回值和任何型別的任何參數數目：  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 `delegate` 是可用來封裝具名方法或匿名方法的參考型別。  委派大致類似 C\+\+ 的函式指標，但是，委派型別安全 \(Type\-Safe\) 又具有安全性。  如需委派的應用程式，請參閱[委派](../../../csharp/programming-guide/delegates/index.md)和[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。  
  
## 備註  
 委派是[事件](../../../csharp/programming-guide/events/index.md)的基礎。  
  
 將委派與具名方法或匿名方法建立關聯，即可具現化 \(Instantiated\) 委派。  如需詳細資訊，請參閱[具名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)和[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。  
  
 委派必須以具有相容傳回型別和輸入參數的方法或 Lambda 運算式具現化。  如需方法簽章中可允許之變異數等級的詳細資訊，請參閱[委派中的變異數](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)。  若要搭配匿名方法使用，就要同時宣告委派以及其相關聯的程式碼。  委派的這兩種具現化方法都將在此章節中討論。  
  
## 範例  
 [!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/csharp/delegate_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [參考類型](../../../csharp/language-reference/keywords/reference-types.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [使用具名和匿名方法委派的比較](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)   
 [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)