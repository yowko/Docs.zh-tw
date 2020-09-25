---
description: delegate 運算子 - C# 參考
title: delegate 運算子 - C# 參考
ms.date: 09/25/2020
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: db2bf673db12e4a10741a26112820726a4b8aaee
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247653"
---
# <a name="delegate-operator-c-reference"></a>delegate 運算子 (C# 參考)

`delegate` 運算子會建立可轉換成委派型別的匿名方法：

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> 從 C# 3 開始，Lambda 運算式提供更精簡且更具表達性的方式來建立匿名函式。 使用 [=> 運算子](lambda-operator.md)來建構 Lambda 運算式：
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> 如需 Lambda 運算式功能的詳細資訊 (例如，捕捉外部變數)，請參閱 [Lambda 運算式](lambda-expressions.md)。

當您使用 `delegate` 運算子時，您可以省略參數清單。 如果您這樣做，則可以將建立的匿名方法轉換成含任何參數清單的委派型別，如下列範例所示：

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

那是 Lambda 運算式不支援的唯一匿名方法功能。 在所有其他情況下，建議您以 Lambda 運算式的方式來撰寫內嵌程式碼。

從 c # 9.0 開始，您可以使用 [ [捨棄](../../discards.md) ] 來指定方法未使用之匿名方法的兩個或多個輸入參數：

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetDiscards" :::

為了回溯相容性，如果只命名單一參數 `_` ， `_` 會被視為匿名方法內該參數的名稱。

此外，從 c # 9.0 開始，您可以 `static` 在匿名方法的宣告中使用修飾詞：

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetStatic" :::

靜態匿名方法無法從封入範圍中捕獲本機變數或實例狀態。

您也可以使用 `delegate` 關鍵字來宣告[委派型別](../builtin-types/reference-types.md#the-delegate-type)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [=> 運算子](lambda-operator.md)
