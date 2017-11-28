---
title: "隱含數值轉換表 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6b1705dca357fd2a155fc1ea9c7fe0f65bad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>隱含數值轉換表 (C# 參考)
下表顯示預先定義的隱含數值轉換。 在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。  
  
|從|以|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`、`int`、`long`、`float`、`double` 或 `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`、`long`、`float`、`double` 或 `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`、`float`、`double` 或 `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`、`double` 或 `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`、`double` 或 `decimal`|  
  
## <a name="remarks"></a>備註  
  
-   從 `int`、`uint`、`long` 或 `ulong` 轉換為 `float`，以及從 `long` 或 `ulong` 轉換為 `double` 時，可能會遺失精確度，但不會遺失大小。  
  
-   `char` 類型沒有隱含轉換。  
  
-   浮點類型與 `decimal` 類型之間沒有隱含轉換。  
  
-   `int` 類型的常數運算式可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`，但前提是常數運算式的值必須在目的地類型的範圍內。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [轉換和型別轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
