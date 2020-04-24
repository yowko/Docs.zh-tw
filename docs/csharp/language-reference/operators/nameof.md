---
title: 'nameof 運算式-c # 參考'
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: d71acf0cf7d5cdcfa5310455af2120fa1f82d567
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135915"
---
# <a name="nameof-expression-c-reference"></a>nameof 運算式（c # 參考）

`nameof`運算式會產生變數、類型或成員的名稱做為字串常數：

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。

在[逐字識別碼](../tokens/verbatim.md)的情況下， `@`字元不是名稱的一部分，如下列範例所示：

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

`nameof`運算式會在編譯時期評估，而且在執行時間不會有任何作用。

您可以使用`nameof`運算式，讓引數檢查程式碼更容易維護：

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

`nameof`運算式適用于 c # 6 和更新版本。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C # 運算子](index.md)
