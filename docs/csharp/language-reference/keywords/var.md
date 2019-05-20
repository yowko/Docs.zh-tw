---
title: var - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: a523e575f14c88ea385bf115f0b07f54190499a5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633207"
---
# <a name="var-c-reference"></a>var (C# 參考)

從 Visual C# 3.0 開始，在方法範圍內宣告的變數可以使用隱含的「類型」`var`。 隱含型別區域變數如同您自己宣告的類型一樣是強型別，但是編譯器會判斷類型。 下列兩個 `i` 宣告的功能相同：

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

如需詳細資訊，請參閱[隱含型別區域變數](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [LINQ 查詢作業中的類型關聯性](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。

## <a name="example"></a>範例

下例示範兩個查詢運算式。 在第一個運算式中允許使用 `var`，但並非必要，因為查詢結果的類型可以明確陳述為 `IEnumerable<string>`。 不過，在第二個運算式中，`var` 允許結果是匿名型別的集合，而且只有編譯器本身才能存取該型別的名稱。 使用 `var` 就不需要建立結果的新類別。 請注意，在範例 #2 中，`foreach` 反覆運算變數 `item` 必須也是隱含型別。

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [隱含型別區域變數](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
