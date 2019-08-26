---
title: struct - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 95c36cd039436dcddd3e2e2a3e1fae98ee885677
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924671"
---
# <a name="struct-c-reference"></a>struct (C# 參考)

`struct` 類型是實值類型，通常可用來封裝一小組相關變數，例如矩形的座標，或詳細目錄中某個項目的特性。 下列範例示範簡單結構宣告：

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>備註

結構還包含[建構函式](../../programming-guide/classes-and-structs/constructors.md)、[常數](../../programming-guide/classes-and-structs/constants.md)、[欄位](../../programming-guide/classes-and-structs/fields.md)、[方法](../../programming-guide/classes-and-structs/methods.md)、[屬性](../../programming-guide/classes-and-structs/properties.md)、[索引子](../../programming-guide/indexers/index.md)、[運算子](../operators/index.md)、[事件](../../programming-guide/events/index.md)和[巢狀型別](../../programming-guide/classes-and-structs/nested-types.md)，不過如果需要數個這類成員，您應該考慮以類別來取代類型。

如需範例，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。

結構可以實作介面，但無法繼承自其他結構。 因此，結構成員無法宣告為 `protected`。

如需詳細資訊，請參閱[結構](../../programming-guide/classes-and-structs/structs.md)。

## <a name="examples"></a>範例

如需範例和詳細資訊，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需範例，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [預設值表](default-values-table.md)
- [內建型別表](built-in-types-table.md)
- [型別](types.md)
- [實值型別](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [類別和結構](../../programming-guide/classes-and-structs/index.md)
