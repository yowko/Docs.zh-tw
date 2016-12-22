---
title: "ulong (C# 參考) | Microsoft Docs"
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
  - "ulong_CSharpKeyword"
  - "ulong"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ulong 關鍵字 [C#]"
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ulong (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`ulong` 關鍵字表示一種儲存數值的整數型別，其儲存數值的大小與範圍如下表所示。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`ulong`|0 至 18,446,744,073,709,551,615|不帶正負號的 64 位元整數|<xref:System.UInt64?displayProperty=fullName>|  
  
## 常值  
 您可以採用以下範例中同時宣告和初始化 `ulong` 型別變數的做法：  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 當整數常值沒有後置字元時，它的型別會是下列中可表示其值的第一個型別：[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 和 `ulong`。  在上述範例裡，它是 `ulong` 型別。  
  
 您也可以使用後置字元，根據下列規則來指定常值的型別：  
  
-   如果您使用 L 或 l，根據其大小，常值整數的型別會是 [long](../../../csharp/language-reference/keywords/long.md) 或 `ulong`。  
  
    > [!NOTE]
    >  您也可以使用小寫字母 "l" 做為後置字元。  然而，這會產生編譯器警告，因為字母 "l" 很容易與數字 "1" 混淆。 請使用 "L" 以避免困擾。  
  
-   如果您使用 `U` 或 `u`，根據其大小，常值整數的型別會是 [uint](../../../csharp/language-reference/keywords/uint.md) 或 `ulong`。  
  
-   如果您使用 UL、ul、Ul、uL、LU、lu、Lu 或 lU，常值整數的型別會是 `ulong`。  
  
     例如，下列三個陳述式的輸出會是系統型別 `UInt64`，其對應於別名 `ulong`：  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
 後置字元的常見用於呼叫多載方法。  以下列使用 `ulong` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法為例：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 將後置字元與 `ulong` 參數一起使用可以保證呼叫正確的型別，例如：  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## 轉換  
 系統已預先定義好從 `ulong` 到 [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的隱含轉換。  
  
 從 `ulong` 到任何整數類資料型別沒有隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯錯誤：  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 也預先定義好從 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[uint](../../../csharp/language-reference/keywords/uint.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 至 `ulong` 的隱含轉換。  
  
 此外也沒有從浮點型別到 `ulong` 的隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯器錯誤：  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 如需混合浮點型別和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數字轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 <xref:System.UInt64>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)