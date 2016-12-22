---
title: "short (C# 參考) | Microsoft Docs"
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
  - "short"
  - "short_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "short 關鍵字 [C#]"
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# short (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`short` 關鍵字表示一種儲存數值的整數資料型別，其儲存數值的大小與範圍如下表所示。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`short`|\-32,768 至 32,767|帶正負號的 16 位元整數|<xref:System.Int16?displayProperty=fullName>|  
  
## 常值  
 您可以採用以下範例中同時宣告和初始化 `short` 型別變數的做法：  
  
```  
  
short x = 32767;  
```  
  
 在上述宣告裡，整數常值 `32767` 隱含地從 [int](../../../csharp/language-reference/keywords/int.md) 轉換成 `short`。  如果 `short` 無法容納整個整數常值，便會產生編譯錯誤。  
  
 呼叫多載方法時必須使用轉換。  以下列使用 `short` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法為例：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 使用 `short` 轉換可以保證呼叫到正確的型別，例如：  
  
```  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## 轉換  
 有一項從 `short` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 您不能將儲存容量較大的非常值數字型別隱含轉換成 `short` \(如需整數類資料型別儲存大小的詳細資訊，請參閱[整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)\)。  以下列兩個 `short` 變數 `x` 和 `y` 為例：  
  
```  
  
short x = 5, y = 12;  
```  
  
 下列指派陳述式會產生編譯錯誤，因為根據預設，指派運算子右邊的算術運算式會評估為 [int](../../../csharp/language-reference/keywords/int.md)。  
  
 `short`   `z = x + y;   // Error: no conversion from int to short`  
  
 若要修正這個問題，請使用轉型：  
  
 `short`   `z = (`  `short`  `)(x + y);   // OK: explicit conversion`  
  
 當目的地變數有相同或較大的儲存容量時，下列陳述式仍可以使用：  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 沒有從浮點型別到 `short` 的隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯器錯誤：  
  
```  
  
        short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 如需混合浮點型別和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數字轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 <xref:System.Int16>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)