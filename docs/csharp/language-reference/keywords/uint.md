---
title: "uint (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "uint"
  - "uint_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "uint 關鍵字 [C#]"
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# uint (C# 參考)
`uint` 關鍵字表示一種儲存數值的整數型別，其所儲存之數值的大小與範圍如下表所示。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`uint`|0 至 4,294,967,295|不帶正負號的 32 位元整數|<xref:System.UInt32?displayProperty=fullName>|  
  
 **注意**：`uint` 型別不符合 CLS 標準。  請盡可能使用 `int`。  
  
## 常值  
 您可以像這個範例一樣宣告和初始化型別 `uint` 的變數：  
  
```  
  
uint myUint = 4294967290;  
```  
  
 當整數常值沒有後置字元時，它的型別會是下列可表示其值的第一個型別：[int](../../../csharp/language-reference/keywords/int.md)、`uint`、[long](../../../csharp/language-reference/keywords/long.md) 和 [ulong](../../../csharp/language-reference/keywords/ulong.md)。  在此範例裡，它是 `uint`：  
  
```  
  
uint uInt1 = 123;  
```  
  
 您也可以使用後置字元 u 或 U，就像這樣：  
  
```  
  
uint uInt2 = 123U;  
```  
  
 當您使用後置字元 `U` 或 `u` 時，根據常值的數字值，常值型別會被判斷為 `uint` 或 `ulong`。  例如：  
  
```  
Console.WriteLine(44U.GetType());  
Console.WriteLine(323442434344U.GetType());  
```  
  
 此程式碼會顯示 `System.UInt32`，後面接著 `System.UInt64` \(兩者分別為 `uint` 和 `ulong` 的基礎型別\)，因為第二個常值太大，因此無法由 `uint` 型別加以儲存。  
  
## 轉換  
 系統有預先定義從 `uint` 至 [long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的隱含轉換。  例如：  
  
```  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 系統已預先定義從 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 到 `uint` 的隱含轉換。  否則，您必須使用型別轉換。  例如，下列指派陳述式會在並未進行轉換的情況下產生編譯錯誤：  
  
```  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 請注意，從浮點型別到 `uint` 沒有隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯器錯誤：  
  
```  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 如需混合浮點型別和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數字轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.UInt32>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)