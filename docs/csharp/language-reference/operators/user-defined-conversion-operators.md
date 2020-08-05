---
title: 使用者定義轉換運算子 - C# 參考
description: 了解如何在 C# 中定義自訂的隱含和明確型別轉換。
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: ab3598b8158d0a789e8583403389df657ae01aed
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556276"
---
# <a name="user-defined-conversion-operators-c-reference"></a>使用者定義轉換運算子 (C# 參考)

使用者定義型別可定義要互換型別的自訂隱含轉換和明確轉換。

隱含轉換不需要特殊的語法即可叫用，且可能在各種不同的情況下發生，例如在指派和方法引動過程中發生。 預先定義的 c # 隱含轉換一律會成功，而且永遠不會擲回例外狀況。 使用者定義的隱含轉換也應該以類似方式運作。 如果自訂的轉換可能擲回例外狀況或遺失資訊，請將其定義為明確轉換。

[is](type-testing-and-cast.md#is-operator) 和 [as](type-testing-and-cast.md#as-operator) 運算子不會考慮使用者定義的轉換。 使用[cast 運算式](type-testing-and-cast.md#cast-expression)來叫用使用者定義的明確轉換。

使用 `operator` 和 `implicit` 或 `explicit` 關鍵字，分別定義隱含或明確轉換。 您用來定義轉換的型別必須是來源型別或該轉換的目標型別。 您可以將兩個使用者定義型別之間的轉換定義為兩個型別其中之一。

下面範例說明如何定義隱含和明確轉換：

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

您也可以使用 `operator` 關鍵字來多載預先定義的 C# 運算子。 如需詳細資訊，請參閱[運算子多載](operator-overloading.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [轉換運算子](~/_csharplang/spec/classes.md#conversion-operators)
- [使用者定義轉換](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [隱含的轉換](~/_csharplang/spec/conversions.md#implicit-conversions)
- [明確轉換](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [運算子多載](operator-overloading.md)
- [型別測試和轉換運算子](type-testing-and-cast.md)
- [轉換和型別轉換](../../programming-guide/types/casting-and-type-conversions.md)
- [設計方針-轉換運算子](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [C# 中鏈結的使用者定義明確轉換](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
