---
title: 'nameof 運算式-c # 參考'
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 1bd8800a553eb9b3363da8a3b5f230caecddf223
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556406"
---
# <a name="nameof-expression-c-reference"></a>nameof expression (c # 參考) 

`nameof`運算式會產生變數、類型或成員的名稱做為字串常數：

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。

在[逐字識別碼](../tokens/verbatim.md)的情況下， `@` 字元不是名稱的一部分，如下列範例所示：

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

`nameof`運算式會在編譯時期評估，而且在執行時間不會有任何作用。

您可以使用 `nameof` 運算式，讓引數檢查程式碼更容易維護：

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

`nameof`運算式適用于 c # 6 和更新版本。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
