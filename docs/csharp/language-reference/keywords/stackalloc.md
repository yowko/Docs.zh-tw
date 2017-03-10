---
title: "stackalloc (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "stackalloc_CSharpKeyword"
  - "stackalloc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "stackalloc 關鍵字 [C#]"
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# stackalloc (C# 參考)
`stackalloc` 關鍵字會在 Unsafe 程式碼內容中用來配置堆疊上的記憶體區塊。  
  
```  
int* block = stackalloc int[100];  
```  
  
## 備註  
 關鍵字僅在區域變數初始設定式中有效。  下列程式碼會產生編譯器錯誤。  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 因為牽涉到指標型別 \(Pointer Type\)，`stackalloc` 需要 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容。  如需詳細資訊，請參閱 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。  
  
 `stackalloc` 的功用與 C 執行階段程式庫中的 [\_alloca](/visual-cpp/c-runtime-library/reference/alloca) 相似。  
  
 下列範例會計算並顯示 Fibonacci 序列中的前 20 個數字。  每個數字都是前兩個數字的總和。  在程式碼中，足以容納 20 個 `int` 型別之項目的記憶體區塊會配置在堆疊上，而不是堆積中。  該區塊的位址會儲存於指標 `fib` 中。  這個記憶體不會進行記憶體回收，因此不須使用 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 將記憶體固定住。  記憶體區塊的存留期 \(Lifetime\) 受限於定義該區塊之方法的存留期。  方法傳回之前，您無法釋放記憶體。  
  
## 範例  
 [!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#15)]  
  
## 安全性  
 Unsafe 程式碼的安全性不如 Safe 程式碼。  然而，使用 `stackalloc` 會自動啟用 Common Language Runtime \(CLR\) 的緩衝區滿溢偵測功能。  如果偵測到緩衝區滿溢，就會儘速中斷處理序，將執行惡意程式碼的機會降到最低。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)