---
title: "如何：參考相等 (識別) 的測試 (C# 程式設計手冊) | Microsoft Docs"
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
  - "物件識別 [C#]"
  - "參考相等 [C#]"
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：參考相等 (識別) 的測試 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您不需實作任何自訂邏輯，即可支援型別中的參考相等比較。  這個功能是透過靜態 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> 方法，提供給所有型別。  
  
 下列範例顯示如何判斷兩個變數是否具有「*參考相等*」\(Reference Equality\)，這代表兩個變數參考記憶體中的相同物件。  
  
 範例同時顯示為何 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> 一律對實值型別傳回 `false`，以及為何不應使用 <xref:System.Object.ReferenceEquals%2A> 來判斷字串相等。  
  
## 範例  
 [!code-cs[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 在 <xref:System.Object?displayProperty=fullName> 通用基底類別中實作 `Equals` 也會執行參考相等檢查，但最好不要使用這個用法，因為如果類別覆寫了方法，產生的結果可能不是您想要的。  對 `==` 和 `!=` 運算子來說，這同樣是成立的。  \=\= 和 `!=` 在參考型別上操作時，其預設行為是執行參考相等檢查。  不過，衍生類別也可以多載運算子來執行實值相等檢查。  為了降低發生錯誤的可能，當您必須判斷兩個物件是否具有參考相等時，最好一律使用 <xref:System.Object.ReferenceEquals%2A>。  
  
 相同組件中的常數字串一律由執行階段暫留。  也就是說，每個唯一的常值字串只會保留一個執行個體。  不過，執行階段不保證一定暫留執行階段建立的字串，也不保證會暫留不同組件中的兩個相等常數字串。  
  
## 請參閱  
 [相等比較](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)