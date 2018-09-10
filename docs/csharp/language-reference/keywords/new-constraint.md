---
title: new 條件約束 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 9948fc65030a4636c5d23db4ef8c3a584018d2f5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087007"
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