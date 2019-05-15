---
title: ':: 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 324f6711cdec478e5647b05d84c281f79e95f036
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452358"
---
# <a name="-operator-c-reference"></a>:: 運算子 (C# 參考)

命名空間別名限定詞 (`::`) 用來查閱識別碼。 它一律位在兩個識別碼之間，如下例所示︰

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

`::` 運算子也可以搭配「using alias 指示詞」使用：

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>備註

命名空間別名限定詞可以是 `global`。 這會在全域命名空間中叫用查詢，不是在別名命名空間中。

## <a name="for-more-information"></a>如需詳細資訊

如需如何使用 `::` 運算子的範例，請參閱下一節︰

- [如何：使用全域命名空間別名](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [命名空間關鍵字](../keywords/namespace-keywords.md)
- [. 運算子](member-access-operators.md#member-access-operator-)
- [外部別名](../keywords/extern-alias.md)