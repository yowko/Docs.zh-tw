---
title: "如何：查詢物件集合 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "物件集合查詢 [C#]"
  - "查詢 [C# 中的 LINQ], 物件集合"
  - "查詢運算式 [C# 中的 LINQ], 物件集合"
ms.assetid: 122d1e3b-1604-4add-b6b4-b84530a77b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：查詢物件集合 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個範例顯示如何針對 `Student` 物件清單執行簡單查詢。  每個 `Student` 物件都包含一些學生的基本資訊，以及一份代表學生四次考試分數的清單。  
  
 這個應用程式是本節中其他使用相同 `students` 資料來源的許多範例的架構。  
  
## 範例  
 下列查詢會傳回第一次考試分數高於 90 分的學生。  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-query-a-collection-of-objects_1.cs)]  
  
 這個查詢故意設計的如此簡單，好讓您可以自行學習。  例如，您可以在 `where` 子句中嘗試其他述詞 \(Predicate\)，或使用 `orderby` 子句來排序結果。  
  
## 編譯程式碼  
  
-   建立以 .NET Framework 3.5 版為目標的 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] 專案。  根據預設，專案有 System.Core.dll 的參考，以及 System.Linq 命名空間的 `using` 指示詞。  
  
-   將程式碼複製至您的專案中。  
  
-   按 F5 編譯和執行程式。  
  
-   按任何鍵離開主控台視窗。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)