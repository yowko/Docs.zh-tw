---
title: 命名空間 - C# 程式設計手冊
description: '深入瞭解 c # 程式設計中的命名空間。 查看命名空間屬性和查看其他資源的總覽。'
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 41a666fd5f368e6990e08a36700e18f648939213
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440337"
---
# <a name="namespaces-c-programming-guide"></a>命名空間 (C# 程式設計手冊)

C# 程式設計大量使用命名空間的原因有兩個。 首先，.NET 會使用命名空間來組織它的許多類別，如下所示：  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System> 是命名空間，而 <xref:System.Console> 是該命名空間中的類別。 您可以使用 `using` 關鍵字，如此就不需要完整名稱，如下列範例所示：

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

如需詳細資訊，請參閱 [using 指示詞](../../language-reference/keywords/using-directive.md)。

其次，宣告您自己的命名空間，將有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。 請使用 [namespace](../../language-reference/keywords/namespace.md) 關鍵字宣告命名空間，如下列範例所示：

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

命名空間的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。

## <a name="namespaces-overview"></a>命名空間概觀

命名空間具有下列屬性：

- 命名空間可組織大型程式碼專案。
- 命名空間會使用 `.` 運算子分隔。
- `using` 指示詞讓您不需要指定每個類別的命名空間名稱。
- `global` 命名空間是「根」命名空間：`global::System` 一律會參考 .NET <xref:System> 命名空間。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[命名空間](~/_csharplang/spec/namespaces.md)一節。

## <a name="see-also"></a>請參閱

- [C # 程式設計指南](../index.md)
- [使用命名空間](using-namespaces.md)
- [如何使用 My 命名空間](how-to-use-the-my-namespace.md)
- [識別碼名稱](../inside-a-program/identifier-names.md)
- [using 指示詞](../../language-reference/keywords/using-directive.md)
- [：：運算子](../../language-reference/operators/namespace-alias-qualifier.md)
