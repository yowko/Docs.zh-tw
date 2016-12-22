---
title: "/ 運算子 (C# 參考) | Microsoft Docs"
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
  - "/_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/ 運算子 [C#]"
  - "division 運算子 [C#]"
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# / 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

除法運算子 \(`/`\) 會將第二個運算元所第一個運算元。  所有的數字型別都已預先定義了除法運算子。  
  
## 備註  
 使用者定義型別可多載 `/` 運算子 \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  `/` 運算子多載會隱含多載 [\/\= 運算子](../../../csharp/language-reference/operators/subtraction-assignment-operator.md)。  
  
 兩個整數相除時，結果永遠是整數。  比方說，結果為 7 \/ 3 是 2。  若要判斷 7 的其餘部分 \/ 3，使用於餘數運算子 \([%](../../../csharp/language-reference/operators/modulus-operator.md)\)。  若要取得商數做為有理數或分數，請將被除數或除數型別指定為 `float` 或 `double`。  如果您所放到小數點右邊的數字，如下列範例所示表示被除數或除數成小數，您可以隱含地指定型別。  
  
## 範例  
 [!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)