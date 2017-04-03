---
title: "隱含數值轉換表 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e4a0eca529b7c66cca527cfef3078a2c5bd24555
ms.lasthandoff: 03/13/2017

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
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [轉換和型別轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
