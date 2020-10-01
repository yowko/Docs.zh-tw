---
description: new 運算子 - C# 參考
title: new 運算子 - C# 參考
ms.date: 10/02/2020
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3125f3d2c694dcfc5682ee482f3f76072ac3726d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609378"
---
# <a name="new-operator-c-reference"></a>new 運算子 (C# 參考)

`new` 運算子會建立型別的新執行個體。

您也可以使用 `new` 關鍵字作為[成員宣告修飾詞](../keywords/new-modifier.md)或[泛型型別條件約束](../keywords/new-constraint.md)。

## <a name="constructor-invocation"></a>建構函式引動過程

若要建立型別的新執行個體，您通常會使用 `new` 運算子叫用該型別的其中一個[建構函式](../../programming-guide/classes-and-structs/constructors.md)：

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

您可以搭配 `new` 運算子使用[物件或集合初始設定式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)，來在單一陳述式中具現化和初始化物件，如下列範例所示：

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

從 c # 9.0 開始，函式調用運算式是目標型別。 也就是說，如果已知運算式的目標型別，您可以省略型別名稱，如下列範例所示：

:::code language="csharp" source="snippets/shared/NewOperator.cs" id="SnippetTargetTyped":::

如先前的範例所示，您一律使用目標型別運算式中的括弧 `new` 。

如果運算式的目標型別 `new` 未知 (例如，當您使用 [`var`](../keywords/var.md) 關鍵字) 時，必須指定型別名稱。

## <a name="array-creation"></a>建立陣列

您也可以使用 `new` 運算子建立陣列執行個體，如下列範例所示：

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

在單一陳述式中使用陣列初始化語法建立陣列執行個體，並使用項目。 下列範例會示範執行該操作的各種方式：

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。

## <a name="instantiation-of-anonymous-types"></a>匿名型別的具現化

若要建立[匿名型別](../../programming-guide/classes-and-structs/anonymous-types.md)的執行個體，請使用 `new` 運算子及物件初始設定式語法：

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>型別執行個體的解構

您不需要終結先前建立的型別執行個體。 參考和實值型別的執行個體都會自動終結。 實值型別的執行個體會在內容包含它們時立即終結。 在移除參考型別的最後一個參考之後，垃圾收集行程會將這些實例被 [垃圾收集](../../../standard/garbage-collection/index.md) 行程終結。

針對包含非受控資源的類型實例（例如，檔案控制代碼），建議採用具決定性的清除，以確保其所包含的資源會儘快釋出。 如需詳細資訊，請參閱 <xref:System.IDisposable?displayProperty=nameWithType> API 參考和 [using 陳述式](../keywords/using-statement.md)一文。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別不可多載 `new` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [new 運算子](~/_csharplang/spec/expressions.md#the-new-operator)一節。

如需目標型別運算式的詳細資訊 `new` ，請參閱 [功能提案注意事項](~/_csharplang/proposals/csharp-9.0/target-typed-new.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [物件和集合初始化運算式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
