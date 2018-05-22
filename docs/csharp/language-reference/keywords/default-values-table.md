---
title: 預設值表 (C# 參考)
description: 了解預設建構函式所傳回之實值型別的預設值。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="default-values-table-c-reference"></a>預設值表 (C# 參考)

下表顯示預設建構函式所傳回之實值型別的預設值。 預設建構函式是透過 `new` 運算子來叫用，如下所示：

```csharp
int myInt = new int();
```

上面的陳述式與下面的陳述式效果相同：

```csharp
int myInt = 0;
```

請記住，C# 中不允許使用未初始化的變數。

|值類型|預設值|
|----------------|-------------------|
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0.0D|
|[enum](enum.md)|這個值是由運算式 (E)0 所產生，其中 E 是列舉識別項。|
|[float](float.md)|0.0F|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="see-also"></a>另請參閱
 [C# 參考](../index.md)  
 [C# 程式設計指南](../../programming-guide/index.md)  
 [實值型別表](value-types-table.md)  
 [實值型別](value-types.md)  
 [內建型別表](built-in-types-table.md)  
 [型別的參考表](reference-tables-for-types.md)
