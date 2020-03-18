---
title: nameof 運算子 - C# 參考
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846268"
---
# <a name="nameof-operator-c-reference"></a>nameof 運算子 (C# 參考)

`nameof` 運算子會以字串常值格式取得變數、型別或成員的名稱：

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。

運算子`nameof`在編譯時計算，在運行時無效。

您可以使用 `nameof` 運算子，讓檢查引數的程式碼更容易維護：

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

C# 6 與更新版本提供 `nameof` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
