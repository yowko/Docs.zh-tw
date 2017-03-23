---
title: "checked (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "checked_CSharpKeyword"
  - "checked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "checked 關鍵字 [C#]"
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# checked (C# 參考)
`checked` 關鍵字是用來明確啟用整數類資料型別 \(Integral Type\) 算術運算和轉換的溢位檢查。  
  
 根據預設，當運算式只包含常數值時，如果該運算式所產生的值位於目的型別範圍之外，就會造成編譯器錯誤。  如果運算式包含一個或多個非常數值，編譯器就不會偵測到溢位。  在下列範例中，評估指派給 `i2` 的運算式並不會造成編譯器錯誤。  
  
 [!code-cs[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 根據預設，在執行階段不會檢查這些非常數運算式是否有溢位，而且也不會引發溢位例外狀況。  前述範例會顯示 \-2,147,483,639 做為兩個正整數的加總。  
  
 您可以藉由編譯器選項、環境組態或使用 `checked` 關鍵字，啟用溢位檢查。  下列範例將示範如何使用 `checked` 運算式或 `checked` 區塊，偵測前述加總作業在執行階段產生的溢位。  這兩個範例都會引發溢位例外狀況。  
  
 [!code-cs[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字可以用來防止溢位檢查。  
  
## 範例  
 這個範例顯示如何使用 `checked` 在執行階段啟用溢位檢查。  
  
 [!code-cs[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)