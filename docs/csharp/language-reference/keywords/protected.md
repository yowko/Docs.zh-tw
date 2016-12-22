---
title: "protected (C# 參考) | Microsoft Docs"
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
  - "protected"
  - "protected_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "protected 關鍵字 [C#]"
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# protected (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`protected` 關鍵字是成員存取修飾詞。  protected 成員可在其類別內由衍生類別執行個體存取。  如需 `protected` 和其他存取修飾詞的比較，請參閱[存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。  
  
## 範例  
 只有當存取是透過衍生類別型別進行時，才可以存取衍生類別中基底類別 \(Base Class\) 的 protected 成員。  例如，請考量下列程式碼區段：  
  
 [!code-cs[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 陳述式 `a.x = 10` 會產生錯誤，因為它位於靜態方法 Main，而不是類別 B 的執行個體。  
  
 結構成員不可以是 protected 成員是因為無法繼承結構。  
  
## 範例  
 在此範例中，類別 `DerivedPoint` 衍生自 `Point`。  因此，您可以直接從該衍生類別存取基底類別的 protected 成員。  
  
 [!code-cs[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 如果您將 `x` 和 `y` 的存取層級更改為 [private](../../../csharp/language-reference/keywords/private.md)，編譯器會發出錯誤訊息：  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)