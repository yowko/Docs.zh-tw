---
description: '參數陣列的 params 關鍵字-c # 參考'
title: '參數陣列的 params 關鍵字-c # 參考'
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134467"
---
# <a name="params-c-reference"></a>params (C# 參考)

使用 `params` 關鍵字，您可以指定[方法參數](method-parameters.md)，其採用可變數目的引數。 參數類型必須是一維陣列。

在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。

如果參數的宣告型別 `params` 不是一維陣列，就會發生編譯器錯誤 [CS0225](../../misc/cs0225.md) 。

當您使用參數呼叫方法時 `params` ，您可以傳入：

- 陣列元素型別的引數清單（以逗號分隔）。
- 指定之類型的引數陣列。
- 無引數。 如果不傳送任何引數，`params` 清單的長度為零。

## <a name="example"></a>範例

下例示範將引數傳送至 `params` 參數的各種方式。

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
- [方法參數](method-parameters.md)
