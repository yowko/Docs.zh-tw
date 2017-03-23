---
title: "內建類型資料表 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "內建 C# 類型"
  - "類型 [C#], 內建的"
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# 內建類型資料表 (C# 參考)
下表顯示內建 C\# 型別的關鍵字，這些是 <xref:System> 命名空間裡預先定義型別的別名。  
  
|C\# 型別|.NET Framework 型別|  
|------------|-----------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## 備註  
 表中除了 `object` 和 `string` 以外的所有型別，都視為簡單型別。  
  
 C\# 型別關鍵字和它們的別名可互換。  例如，您可以使用下列任一個宣告來宣告整數變數：  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 若要顯示任一 C\# 型別的實際型別，請使用系統方法 `GetType()`。  例如，下列陳述式顯示了代表 `myVariable` 型別的系統別名：  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 您也可以使用 [typeof](../../../csharp/language-reference/keywords/typeof.md) 運算子。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [實值類型](../../../csharp/language-reference/keywords/value-types.md)   
 [預設值表](../../../csharp/language-reference/keywords/default-values-table.md)   
 [格式化數值結果表](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)