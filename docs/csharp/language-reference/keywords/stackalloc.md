---
title: "stackalloc (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b9c5328bfa1b0fc9a7751763c7d728096886905
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# 參考)
unsafe 程式碼內容中使用 `stackalloc` 關鍵字來配置堆疊上的記憶體區塊。  
  
```csharp  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>備註  
 關鍵字只適用於區域變數初始設定式。 下列程式碼會導致編譯器錯誤。  
  
```csharp  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 因為涉及指標類型，所以 `stackalloc` 需要 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容。 如需詳細資訊，請參閱 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。  
  
 `stackalloc` 就像 C 執行階段程式庫中的 [_alloca](/cpp/c-runtime-library/reference/alloca)。  
  
 下列範例會計算並顯示 Fibonacci 序列中的前 20 個數字。 每個數字都是前兩個數字的總和。 在程式碼中，大小足以包含 20 個類型 `int` 的項目的記憶體區塊會配置於堆疊上，而不是堆積。 區塊的位址會儲存在指標 `fib` 中。 這個記憶體不會進行記憶體回收，因此不需要固定 (使用 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md))。 記憶體區塊的存留期只限於定義它的方法的存留期。 傳回方法之前，無法釋放記憶體。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>安全性  
 不安全程式碼比安全替代項目不安全。 不過，使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。 如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
