---
title: '>> 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219720"
---
# <a name="-operator-c-reference"></a>>> 運算子 (C# 參考)

右移運算子 (`>>`) 會向其第一個運算元右移第二個運算元所定義的位元數。 所有整數型別都支援 `>>` 運算子。 不過，第二個運算元的類型必須是 [int](../keywords/int.md) 或對 `int` 進行[預先定義隱含數值轉換](../keywords/implicit-numeric-conversions-table.md)的類型。

右移作業會捨棄低位位元。 會根據第一個運算元的類型來設定高位空位元位置，如下所示：

- 若第一個運算元的型別為 [int](../keywords/int.md) 或 [long](../keywords/long.md)，則右移運算元會執行**算術**位移：第一個運算元之最高有效位元 (正負號位元) 的值會傳播到高為空位元位置。 也就是說，若第一個運算元不是負值且在為負值時被設定為一，則高位空位元位置會被設定為零。

- 若第一個運算元的型別為 [uint](../keywords/uint.md) 或 [ulong](../keywords/ulong.md)，則右移運算子會執行**邏輯**位移：高位空位元位置一律會被設定為零。

下列範例示範了該行為：

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a>位移計數

針對運算式 `x >> count`，實際位移計數相依於 `x` 的型別，如下所示：

- 若 `x` 的型別為 [int](../keywords/int.md) 或 [uint](../keywords/uint.md)，則位移計數是由第二個運算元的低位*五個*位元所給定。 也就是說，位移計數是從 `count & 0x1F` (或 `count & 0b_1_1111`) 所計算。

- 若 `x` 的型別為 [long](../keywords/long.md) 或 [ulong](../keywords/ulong.md)，則位移計數是由第二個運算元的低位*六個*位元所給定。 也就是說，位移計數是從 `count & 0x3F` (或 `count & 0b_11_1111`) 所計算。

下列範例示範了該行為：

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a>備註

位移作業一律不會導致溢位並產生[已選取與未選取](../keywords/checked-and-unchecked.md)內容的相同結果。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `>>` 運算子。 若使用者定義型別 `T` 會多載 `>>` 運算子，則第一個運算元的型別必須是 `T`，且第二個運算元的型別必須是 `int`。 多載 `>>` 運算子時，[右移指派運算子](right-shift-assignment-operator.md) `>>=`也會隱含地多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[位移運算子](~/_csharplang/spec/expressions.md#shift-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [<< 運算子](left-shift-operator.md)