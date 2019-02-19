---
title: 隱含數值轉換表 - C# 參考
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 703f60f48e1e569e0ffcab66ff7ccc91d4a49514
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093550"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>隱含數值轉換表 (C# 參考)

下表顯示 .NET 數字類型間預先定義的隱含數值轉換。
  
|從|以|  
|----------|--------|  
|[sbyte](sbyte.md)|`short`、`int`、`long`、`float`、`double` 或 `decimal`|  
|[byte](byte.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[char](char.md)|`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[short](short.md)|`int`、`long`、`float`、`double` 或 `decimal`|  
|[ushort](ushort.md)|`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。|  
|[int](int.md)|`long`、`float`、`double` 或 `decimal`|  
|[uint](uint.md)|`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[long](long.md)|`float`、 `double`或 `decimal`|  
|[ulong](ulong.md)|`float`、 `double`或 `decimal`|  
|[float](float.md)|`double`|  
  
## <a name="remarks"></a>備註  

- 任何[整數型別](integral-types-table.md)都會隱含轉換為任何[浮點類型](floating-point-types-table.md)。

- 從 `int`、`uint`、`long` 或 `ulong` 轉換為 `float`，以及從 `long` 或 `ulong` 轉換為 `double` 時，可能會遺失精確度，但不會遺失大小。  
  
- `char`、`byte` 與 `sbyte` 類型沒有隱含轉換。  

- 沒有來自 `double` 與 `decimal` 類型的隱含轉換。
  
- `decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。  
  
- 類型 `int` 常數運算式的值 (例如整數常值所代表的值) 可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`，前提是其在目的地類型的範圍內：

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

如需隱含轉換的詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[隱含轉換](~/_csharplang/spec/conversions.md#implicit-conversions)一節。
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [整數型別表](integral-types-table.md)
- [浮點數類型表](floating-point-types-table.md)
- [內建型別表](built-in-types-table.md)
- [明確數值轉換表](explicit-numeric-conversions-table.md)
- [轉換和類型轉換](../../programming-guide/types/casting-and-type-conversions.md)
