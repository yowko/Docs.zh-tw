---
title: new 條件約束 - C# 參考
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 6f6d1b663d03dc9b3adf0e7055dcffacc79d83dc
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795335"
---
# <a name="new-constraint-c-reference"></a>new 條件約束 (C# 參考)

`new` 條件約束指定泛型類別宣告中的型別引數都必須有公用無參數建構函式。 若要使用 `new` 條件約束，型別不能為抽象。

當泛型類別建立新的型別執行個體時，將 `new` 條件約束套用至型別參數，如下列範例所示：

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

當您使用 `new()` 條件約束與其他條件約束時，它必須是最後一個指定的︰

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

如需詳細資訊，請參閱[型別參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)。

您也可以使用 `new` 關鍵字來[建立型別的執行個體](../operators/new-operator.md)或作為[成員宣告修飾詞](new-modifier.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)中的[型別參數條件約束](~/_csharplang/spec/classes.md#type-parameter-constraints)一節。

## <a name="see-also"></a>請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
- [泛型](../../programming-guide/generics/index.md)
