---
title: 實值型別表 - C# 參考
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 959d4840344ba041ae1b01fd6d202f2b53936afc
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422367"
---
# <a name="value-types-table-c-reference"></a>實值型別表 (C# 參考)

下表顯示 C# 實值型別：

|值類型|分類|類型後置詞|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|[byte](byte.md)|不帶正負號、數值、[整數](integral-types-table.md)||
|[char](char.md)|不帶正負號、數值、[整數](integral-types-table.md)||
|[decimal](decimal.md)|數值、[浮點數](floating-point-types-table.md)|M 或 m|
|[double](double.md)|數值、[浮點數](floating-point-types-table.md)|D 或 d|
|[enum](enum.md)|列舉||
|[float](float.md)|數值、[浮點數](floating-point-types-table.md)|F 或 f|
|[int](int.md)|帶正負號、數值、[整數](integral-types-table.md)||
|[long](long.md)|帶正負號、數值、[整數](integral-types-table.md)|L 或 l|
|[sbyte](sbyte.md)|帶正負號、數值、[整數](integral-types-table.md)||
|[short](short.md)|帶正負號、數值、[整數](integral-types-table.md)||
|[struct](struct.md)|使用者定義結構||
|[uint](uint.md)|不帶正負號、數值、[整數](integral-types-table.md)|U 或 u|
|[ulong](ulong.md)|不帶正負號、數值、[整數](integral-types-table.md)|UL、Ul、uL、ul、LU、Lu、lU 或 lu|
|[ushort](ushort.md)|不帶正負號、數值、[整數](integral-types-table.md)||

## <a name="remarks"></a>備註

您可以使用類型後置詞來指定數值常值類型。 例如：

```csharp
decimal a = 0.1M;
```

如果[整數數值常值](~/_csharplang/spec/lexical-structure.md#integer-literals)沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：`int`、`uint`、`long`、`ulong`。

如果[實數數值常值](~/_csharplang/spec/lexical-structure.md#real-literals)沒有後置詞，其類型會是 `double`。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [預設值表](default-values-table.md)
- [實值型別](value-types.md)
- [格式化數值結果表](formatting-numeric-results-table.md)
