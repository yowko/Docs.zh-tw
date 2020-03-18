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
ms.openlocfilehash: b6061492cc1a4f756196fb8a9050b68651431e38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847259"
---
# <a name="user-defined-conversion-operators-c-reference"></a>使用者定義轉換運算子 (C# 參考)

使用者定義型別可定義要互換型別的自訂隱含轉換和明確轉換。

隱含轉換不需要特殊的語法即可叫用，且可能在各種不同的情況下發生，例如在指派和方法引動過程中發生。 預定義的 C# 隱式轉換始終成功，從不引發異常。 使用者定義的隱含轉換也應該以類似方式運作。 如果自訂的轉換可能擲回例外狀況或遺失資訊，請將其定義為明確轉換。

[is](type-testing-and-cast.md#is-operator) 和 [as](type-testing-and-cast.md#as-operator) 運算子不會考慮使用者定義的轉換。 使用[轉換運算子 ()](type-testing-and-cast.md#cast-operator-) 叫用使用者定義的明確轉換。

使用 `operator` 和 `implicit` 或 `explicit` 關鍵字，分別定義隱含或明確轉換。 您用來定義轉換的型別必須是來源型別或該轉換的目標型別。 您可以將兩個使用者定義型別之間的轉換定義為兩個型別其中之一。

下面範例說明如何定義隱含和明確轉換：

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

您也可以使用 `operator` 關鍵字來多載預先定義的 C# 運算子。 如需詳細資訊，請參閱[運算子多載](operator-overloading.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [轉換運算子](~/_csharplang/spec/classes.md#conversion-operators)
- [使用者定義的轉化](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [隱式轉換](~/_csharplang/spec/conversions.md#implicit-conversions)
- [顯式轉換](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [運算子多載](operator-overloading.md)
- [型別測試和轉換運算子](type-testing-and-cast.md)
- [轉換和型別轉換](../../programming-guide/types/casting-and-type-conversions.md)
- [設計指南 - 轉換運算子](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [C# 中鏈結的使用者定義明確轉換](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
