---
title: "new 條件約束 (C# 參考) | Microsoft Docs"
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
  - "new 條件約束關鍵字 [C#]"
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# new 條件約束 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`new` 條件約束 \(Constraint\) 指定在泛用類別宣告中的任何型別參數，都必須具有公用的無參數建構函式。  若要使用 new 條件約束，則型別不可為抽象。  
  
## 範例  
 當您的泛用類別建立型別的新執行個體時，將 `new` 條件約束套用至型別參數，如下列範例所示：  
  
 [!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## 範例  
 將 `new()` 條件約束與其他條件約束一起使用時，一定要將其指定為最後一個：  
  
 [!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 如需詳細資訊，請參閱 [類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)