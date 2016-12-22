---
title: "unchecked (C# 參考) | Microsoft Docs"
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
  - "unchecked_CSharpKeyword"
  - "unchecked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "unchecked 關鍵字 [C#]"
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# unchecked (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`unchecked` 關鍵字是用來隱藏整數類資料型別 \(Integral Type\) 之算術運算和轉換的溢位檢查。  
  
 在不檢查 \(Unchecked\) 的內容中，如果運算式產生在目的型別範圍之外的值，不會以旗標標示溢位。  例如，因為下列範例中的計算會以 `unchecked` 區塊或運算式執行，所以，會忽略該結果對於整數而言太大的結果，同時，`int1` 會指派為值 \-2,147,483,639。  
  
 [!CODE [csrefKeywordsChecked#5](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsChecked#5)]  
  
 如果移除環境 `unchecked`，則會發生編譯錯誤。  在編譯期間，因為運算式的所有條件都是固定的，所以可以偵測溢位。  
  
 根據預設，在編譯期間與執行階段，不會檢查包含非常數條件的運算式。  如需啟用檢查 \(Checked\) 環境的詳細資訊，請參閱 [checked](../../../csharp/language-reference/keywords/checked.md)。  
  
 因為檢查溢位耗費時間，所以在沒有溢位危險的情況中使用不檢查的程式碼，可以提升效能。  不過，如果仍有溢位的可能性，則必須使用檢查環境。  
  
## 範例  
 這個範例顯示如何使用 `unchecked` 關鍵字。  
  
 [!CODE [csrefKeywordsChecked#2](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsChecked#2)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [checked](../../../csharp/language-reference/keywords/checked.md)