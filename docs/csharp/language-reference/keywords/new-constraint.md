---
title: new 條件約束 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: de0798319d91032143cb806d6d39338c4f51ac8f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237840"
---
# <a name="new-constraint-c-reference"></a>new 條件約束 (C# 參考)

`new` 條件約束指定泛型類別宣告中的任何型別引數都必須有公用的無參數建構函式。 若要使用新的條件約束，型別不能為抽象。

## <a name="example"></a>範例

當泛型類別建立新的型別執行個體時，將 `new` 條件約束套用至型別參數，如下例所示︰

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a>範例

當您使用 `new()` 條件約束與其他條件約束時，它必須是最後一個指定的︰

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

如需詳細資訊，請參閱[型別參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic>
- [C# 參考](../../language-reference/index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [運算子關鍵字](operator-keywords.md)
- [泛型](../../programming-guide/generics/index.md)