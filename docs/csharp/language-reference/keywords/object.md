---
title: "object (C# 參考) | Microsoft Docs"
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
  - "object_CSharpKeyword"
  - "object"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "object 關鍵字 [C#]"
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# object (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`object` 型別是 .NET Framework 中 <xref:System.Object> 的別名。  在 C\# 的統一型別系統中，所有型別 \(預先定義和使用者定義、參考型別和實值型別\) 都直接或間接繼承自 <xref:System.Object>。  您可以將任何型別的值指派給 `object` 型別的變數。  當實值型別的變數轉換成物件時，就是所謂的 "*boxed*"。  當型別物件的變數轉換為數值型別時，便稱為 "*unboxed*"。  如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)。  
  
## 範例  
 下列範例顯示 `object` 型別的變數如何接受任何資料型別的值，以及 `object` 型別的變數可如何將方法使用在 .NET Framework 的 <xref:System.Object> 上。  
  
 [!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [參考類型](../../../csharp/language-reference/keywords/reference-types.md)   
 [實值類型](../../../csharp/language-reference/keywords/value-types.md)