---
title: new 運算子 - C# 參考
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403966"
---
# <a name="new-operator-c-reference"></a>new 運算子 (C# 參考)

`new` 運算子會建立型別的新執行個體。

您也可以使用 `new` 關鍵字作為[成員宣告修飾詞](../keywords/new-modifier.md)或[泛型型別條件約束](../keywords/new-constraint.md)。

## <a name="constructor-invocation"></a>建構函式引動過程

若要建立型別的新執行個體，您通常會使用 `new` 運算子叫用該型別的其中一個[建構函式](../../programming-guide/classes-and-structs/constructors.md)：

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

您可以搭配 `new` 運算子使用[物件或集合初始設定式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)，來在單一陳述式中具現化和初始化物件，如下列範例所示：

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>建立陣列

您也可以使用 `new` 運算子建立陣列執行個體，如下列範例所示：

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

在單一陳述式中使用陣列初始化語法建立陣列執行個體，並使用項目。 下列範例會示範執行該操作的各種方式：

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。

## <a name="instantiation-of-anonymous-types"></a>匿名型別的具現化

若要建立[匿名型別](../../programming-guide/classes-and-structs/anonymous-types.md)的執行個體，請使用 `new` 運算子及物件初始設定式語法：

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>型別執行個體的解構

您不需要終結先前建立的型別執行個體。 參考和實值型別的執行個體都會自動終結。 實值型別的執行個體會在內容包含它們時立即終結。 參考型別的執行個體則會由[記憶體回收行程](../../../standard/garbage-collection/index.md)在移除執行個體的最後一個參考後，於未指定的時間終結。

針對包含非受控資源的型別 (例如檔案控制代碼)，建議採用具決定性清理以確保其包含的資源會盡快釋出。 如需詳細資訊，請參閱 <xref:System.IDisposable?displayProperty=nameWithType> API 參考和 [using 陳述式](../keywords/using-statement.md)一文。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別不可多載 `new` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [new 運算子](~/_csharplang/spec/expressions.md#the-new-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [物件和集合初始設定式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
