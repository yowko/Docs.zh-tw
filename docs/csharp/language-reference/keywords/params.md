---
title: 參數陣列的參數關鍵字 - C# 引用
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738827"
---
# <a name="params-c-reference"></a>params (C# 參考)

使用 `params` 關鍵字，您可以指定[方法參數](method-parameters.md)，其採用可變數目的引數。 參數類型必須是單維陣組。

在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。

如果`params`參數聲明的類型不是單維陣列,則會發生編譯器錯誤[CS0225。](../../misc/cs0225.md)

使用`params`參數呼叫方法時,可以傳遞:

- 陣列元素類型的參數的逗號分隔清單。
- 指定類型的參數陣列。
- 無引數。 如果不傳送任何引數，`params` 清單的長度為零。

## <a name="example"></a>範例

下例示範將引數傳送至 `params` 參數的各種方式。

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 編程指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [方法參數](method-parameters.md)
