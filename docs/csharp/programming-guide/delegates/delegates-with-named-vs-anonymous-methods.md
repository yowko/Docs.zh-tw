---
title: "使用具名和匿名方法委派的比較 (C# 程式設計手冊) | Microsoft Docs"
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
  - "委派 [C#], 使用具名和匿名方法的比較"
  - "方法 [C#], 委派中"
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 使用具名和匿名方法委派的比較 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[delegate](../../../csharp/language-reference/keywords/delegate.md) 可以與具名方法產生關聯。  當您使用具名方法執行個體化委派時，方法會當做參數傳遞，例如：  
  
 [!CODE [csProgGuideDelegates#1](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideDelegates#1)]  
  
 這會使用具名方法呼叫。  使用具名方法建構的委派可封裝[靜態](../../../visual-basic/language-reference/modifiers/static.md)方法或執行個體方法 \(Instance Method\)。  在舊版 C\# 中，要執行個體化委派只能使用具名方法。  不過，如果建立新方法會產生額外不必要的負荷，C\# 可讓您執行個體化委派，並立即指定呼叫委派時會處理的程式碼區塊。  區塊可以包含 Lambda 運算式或匿名方法。  如需詳細資訊，請參閱 [匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。  
  
## 備註  
 當做委派參數傳遞的方法必須擁有與委派宣告相同的簽章。  
  
 委派執行個體可封裝靜態或執行個體方法。  
  
 即使委派可使用 [out](../../../csharp/language-reference/keywords/out.md) 參數，但仍不建議您用於多點傳送事件委派，因為無從得知將呼叫哪一個委派。  
  
## 範例 1  
 下列是宣告和使用委派的簡單範例。  請注意，委派 `Del` 與關聯方法 `MultiplyNumbers` 擁有相同的簽章。  
  
 [!CODE [csProgGuideDelegates#2](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideDelegates#2)]  
  
## 範例 2  
 在下列範例裡，一個委派會同時對應到靜態和執行個體方法，並傳回兩者各自回傳的資訊。  
  
 [!CODE [csProgGuideDelegates#3](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideDelegates#3)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [委派](../../../visual-basic/reference/command-line-compiler/index.md)   
 [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [如何：組合委派 \(多點傳送委派\)](../Topic/How%20to:%20Combine%20Delegates%20\(Multicast%20Delegates\)\(C%23%20Programming%20Guide\).md)   
 [事件](../../../csharp/programming-guide/events/index.md)