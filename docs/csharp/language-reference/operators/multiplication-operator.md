---
title: '* 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977340"
---
# <a name="-operator-c-reference"></a>* 運算子 (C# 參考)

`*` 運算子支援兩種形式：一元指標間接運算子或二元乘法運算子。

## <a name="pointer-indirection-operator"></a>指標間接運算子

使用一元 `*` 運算子來取得指標類型的運算元所指向的變數。 如需詳細資訊，請參閱[如何：取得指標變數值](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md)。

指標間接運算子 `*` 需要 [unsafe](../keywords/unsafe.md) 內容。

## <a name="multiplication-operator"></a>乘法運算子

針對數值類型，`*` 運算子會計算其運算元的乘積：

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義類型可以[多載](../keywords/operator.md)二元 `*` 運算子。 多載二元 `*` 運算子時，[乘法指派運算子](multiplication-assignment-operator.md) `*=` 也會隱含地多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[指標間接](~/_csharplang/spec/unsafe-code.md#pointer-indirection)與[乘法運算子](~/_csharplang/spec/expressions.md#multiplication-operator)小節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)