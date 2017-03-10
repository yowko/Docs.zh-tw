---
title: "long (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "long_CSharpKeyword"
  - "long"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "long 關鍵字 [C#]"
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# long (C# 參考)
`long` 關鍵字表示一種儲存數值的整數型別，其儲存數值的大小與範圍如下表所示。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`long`|\-9,223,372,036,854,775,808 至 9,223,372,036,854,775,807|帶正負號的 64 位元整數|<xref:System.Int64?displayProperty=fullName>|  
  
## 常值  
 您可以採用以下範例中同時宣告和初始化 `long` 變數的做法：  
  
```  
  
long long1 = 4294967296;  
```  
  
 當整數常值沒有後置字元時，它的型別會是下列可表示其值的第一個型別：[int](../../../csharp/language-reference/keywords/int.md)、[unit](../../../csharp/language-reference/keywords/uint.md)、`long` 和 [ulong](../../../csharp/language-reference/keywords/ulong.md)。  在上述範例中是 `long` 型別，因為它超過 [unit](../../../csharp/language-reference/keywords/uint.md) 的範圍 \(如需整數類資料型別之儲存體大小的詳細資訊，請參閱[整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)\)。  
  
 您也可以將後置字元 L 與 `long` 型別一起使用，例如：  
  
```  
  
long long2 = 4294967296L;  
```  
  
 使用後置字元 L 時，常值整數的型別會依據其大小決定是 `long` 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)。  在這個情況下，因為它小於 [ulong](../../../csharp/language-reference/keywords/ulong.md) 的範圍，所以會是 `long`。  
  
 後置字元的常見用於呼叫多載方法。  以下列使用 `long` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法為例：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 使用後置字元 L 可確保呼叫正確的型別，例如：  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 您也可以在同一個運算式裡使用 `long` 型別和其他數字整數型別，在這種情況下會將運算式評估為 `long` \(或者，在關係運算式或布林運算式裡則是 [bool](../../../csharp/language-reference/keywords/bool.md)\)。  例如，下列運算式評估為 `long`：  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  您也可以使用小寫字母 "l" 為後置字元。  然而，這會產生編譯器警告，因為字母 "l" 很容易與數字 "1" 混淆。 請使用 "L" 以避免困擾。  
  
 如需混合浮點型別和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
## 轉換  
 系統已預先定義好從 `long` 至 [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的隱含轉換。  否則，需要使用型別轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯錯誤：  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 也有預先定義從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 至 `long` 的隱含轉換。  
  
 請注意，沒有從浮點型別到 `long` 的隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯器錯誤：  
  
```  
  
        long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.Int64>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)