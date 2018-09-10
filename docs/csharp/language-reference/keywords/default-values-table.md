---
title: 預設值表 (C# 參考)
description: 了解 C# 實值型別的預設值是什麼。
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 184a9f42ddd3654a81aef0b7ce35e404de2d4bb9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43737979"
---
# <a name="default-values-table-c-reference"></a>預設值表 (C# 參考)

下列表格顯示[實值型別](value-types.md)的預設值。

|值類型|預設值|
|----------------|-------------------|
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0.0D|
|[enum](enum.md)|這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。|
|[float](float.md)|0.0F|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="remarks"></a>備註

您無法在 C# 中使用未初始化的變數。 您可以使用該型別的預設值初始化變數。 您也可以使用型別的預設值來指定方法中[選擇性引數](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments)的預設值。

使用[預設值運算式](../../programming-guide/statements-expressions-operators/default-value-expressions.md)以產生型別的預設值，如下列範例所示：

```csharp
int a = default(int);
```

從 C# 7.1 開始，您可以使用 [`default` 常值](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference)　來以型別的預設值初始化變數：

```csharp
int a = default;
```

您也可以使用預設建構函式或隱含預設建構函式產生實值型別的預設值，如下列範例所示。 如需建構函式的詳細資訊，請參閱[建構函式](../../programming-guide/classes-and-structs/constructors.md)一文。

```csharp
int a = new int();
```

任何[參考型別](reference-types.md)的預設值皆為 `null`。 [可為 Null 的型別](../../programming-guide/nullable-types/index.md)的預設值為 <xref:System.Nullable%601.HasValue%2A> 屬性為 `false`，且其 <xref:System.Nullable%601.Value%2A> 屬性為未定義的執行個體。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [型別的參考表](reference-tables-for-types.md)
- [實值型別](value-types.md)
- [實值型別表](value-types-table.md)
- [內建型別表](built-in-types-table.md)
