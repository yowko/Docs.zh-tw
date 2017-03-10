---
title: "volatile (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "volatile_CSharpKeyword"
  - "volatile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "volatile 關鍵字 [C#]"
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# volatile (C# 參考)
`volatile` 關鍵字表示同時執行的多執行緒可能修改了欄位。  宣告為 `volatile` 的欄位不遵從假設單一執行緒存取的編譯器最佳化。  這確保最新的值會一直出現在欄位中。  
  
 由多個執行緒在未以 [lock](../../../csharp/language-reference/keywords/lock-statement.md) 陳述式 \(Statement\) 將存取動作序列化的情況下所存取的欄位上，經常會使用 `volatile` 修飾詞 \(Modifier\)。  
  
 `volatile` 關鍵字可套用至以下型別的欄位：  
  
-   參考型別。  
  
-   指標型別 \(在 unsafe 內容中\)。  請注意，即使指標本身可以為 Volatile，但所指向的物件不可為 Volatile。  換句話說，您不能宣告 Volatile 的指標。  
  
-   sbyte、byte、short、ushort、int、uint、char、float 和 bool 之類的型別。  
  
-   具有下列一種基底型別的列舉型別：byte、sbyte、short、ushort、int 或 uint。  
  
-   已知為參考型別的泛用型別參數。  
  
-   <xref:System.IntPtr> 和 <xref:System.UIntPtr>。  
  
 Volatile 關鍵字只能套用至類別或結構 \(Struct\) 的欄位。  區域變數無法宣告為 `volatile`。  
  
## 範例  
 下列範例將示範如何將公用欄位變數宣告為 `volatile`。  
  
 [!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#24)]  
  
## 範例  
 下列範例會示範如何建立輔助執行緒或背景工作執行緒，以及使用它們和主要執行緒執行平行的處理過程。  如需多執行緒處理的背景資訊，請參閱 [Threading](../Topic/Managed%20Threading.md)和[執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 [!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/csharp/volatile_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)