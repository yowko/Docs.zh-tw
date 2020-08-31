---
description: 'nameof 運算式-c # 參考'
title: 'nameof 運算式-c # 參考'
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04109cde2a1f9146bf9bb44f301272808797ded0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118308"
---
# <a name="nameof-expression-c-reference"></a>nameof 運算式 (c # 參考) 

`nameof`運算式會產生變數、類型或成員的名稱做為字串常數：

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。

在 [逐字識別碼](../tokens/verbatim.md)的情況下， `@` 字元不是名稱的一部分，如下列範例所示：

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

`nameof`運算式會在編譯時期進行評估，而且在執行時間不會有任何作用。

您可以使用 `nameof` 運算式讓引數檢查程式碼更容易維護：

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

`nameof`運算式可在 c # 6 和更新版本中使用。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
