---
title: 實值型別 - C# 參考
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 77aed78e7822e06b3b1e6c48b07790d93e09559c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612721"
---
# <a name="value-types-c-reference"></a>實值型別 (C# 參考)

有兩種實值型別：

- [結構](struct.md)

- [列舉](enum.md)

## <a name="main-features-of-value-types"></a>實值型別的主要功能

實值型別的變數會包含該型別的值。 例如，`int` 型別的變數可能包含 `42`值。 這與參考型別的變數不同，參考型別的變數會包含型別執行個體 (也稱為物件) 的參考。 當您指派新值給某個實值型別的變數時，系統會複製該值。 當您指派新值給某個參考型別的變數時，系統會複製參考，而不是物件本身。

所有實值型別都是隱含地衍生自 <xref:System.ValueType?displayProperty=nameWithType>。

與參考型別不同，您無法從實值型別衍生新的類型。 不過，就像參考型別，結構可以實作介面。

實值型別預設不可為 `null`。 不過，相對應的[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)則可為 `null`。

每種實值型別都具有初始化該類型預設值的隱含預設建構函式。 如需有關實值型別預設值的資訊，請參閱[預設值表](default-values-table.md)。

## <a name="simple-types"></a>簡單型別

「簡單型別」是 C# 所提供的一組預先定義結構型別，其中包含下列型別：

- [整數型別](integral-types-table.md)：整數數字型別和 [char](char.md) 型別
- [浮點類型](floating-point-types-table.md)
- [bool](bool.md)

透過關鍵字即可識別簡單型別，但這些關鍵字只是 <xref:System> 命名空間中預先定義之結構型別的別名。 例如，[int](int.md) 是 <xref:System.Int32?displayProperty=nameWithType> 的別名。 如需完整的別名清單，請參閱[內建型別表](built-in-types-table.md)。

簡單型別與其他結構型別的差異在於它們可允許某些額外的作業：

- 簡單類型可以使用常值進行初始化。 例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。

- 您可以使用 [const](const.md) 關鍵字來宣告簡單型別的常數。 其他結構型別則不可能有常數。

- 常數運算式如果運算元全都是簡單型別常數，就會在編譯階段進行評估。

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[簡單型別](~/_csharplang/spec/types.md#simple-types)一節。

## <a name="initializing-value-types"></a>將實值型別初始化

必須先初始化 C# 中的區域變數，再使用它們。 例如，您可以宣告區域變數，而不進行初始化，如下列範例所示：

```csharp
int myInt;
```

您不能先使用它，再將它初始化。 您可以使用下列陳述式來初始化執行個體：

```csharp
myInt = new int();  // Invoke default constructor for int type.
```

這個陳述式相當於下列陳述式：

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

當然，您可以有相同陳述式中的宣告和初始化，如下列範例所示：

```csharp
int myInt = new int();
```

-或-

```csharp
int myInt = 0;
```

使用 [new](new.md) 運算子會呼叫特定類型的預設建構函式，並將預設值指派給變數。 在上述範例中，預設建構函式已將 `0` 值指派給 `myInt`。 如需有關透過呼叫預設建構函式來指派的值之詳細資訊，請參閱[預設值表](default-values-table.md)。

如果要使用使用者定義型別，請使用 [new](new.md) 來叫用預設建構函式。 例如，下列陳述式會叫用 `Point` 結構的預設建構函式：

```csharp
Point p = new Point(); // Invoke default constructor for the struct.
```

在此呼叫之後，會視為已明確指派結構，也就是說，其所有成員都已初始化為其預設值。

如需有關 `new` 運算子的詳細資訊，請參閱 [new](new.md)。

如需有關將數字型別輸出格式化的資訊，請參閱[格式化數值結果表](formatting-numeric-results-table.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [型別](types.md)
- [型別的參考表](reference-tables-for-types.md)
- [參考型別](reference-types.md)
- [可為 Null 的型別](../../programming-guide/nullable-types/index.md)