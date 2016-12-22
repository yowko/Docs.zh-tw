---
title: "++ 運算子 (C# 參考) | Microsoft Docs"
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
  - "++_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "++ 運算子 [C#]"
  - "遞增運算子 (++) [C#]"
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ++ 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

遞增運算子 \(`++`\) 的運算元遞增量為 1。 遞增運算子可以出現在其運算元的前後：`++variable` 和 `variable++`。  
  
## 備註  
 第一種形式是前置詞遞增作業。 作業的結果是運算元已遞增之後的值。  
  
 第二種形式是後置遞增作業。 作業的結果是運算元遞增之前的值。  
  
 數字和列舉型別有預先定義的遞增運算子。 使用者定義類型可以多載 `++` 運算子。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## 範例  
 [!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)