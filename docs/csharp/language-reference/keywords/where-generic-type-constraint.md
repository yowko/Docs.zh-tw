---
title: where (泛型類型條件約束) - C# 參考
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: bccc22f5362b22540dadf08e6b21a07cbc578327
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433853"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (泛型類型條件約束) (C# 參考)

泛型定義中的 `where` 子句指定型別上的條件約束，以用來作為泛型型別、方法、委派或本機函式中型別參數的引數。 條件約束可以指定介面、基底類別或需要作為參考、值或非受控型別的泛型型別。 它們會宣告型別引數必須擁有的功能。

例如，您可以宣告泛型類別 `MyGenericClass`，讓型別參數 `T` 實作 <xref:System.IComparable%601> 介面：

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> 如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](where-clause.md)。

`where` 子句也可以包含基底類別條件約束。 基底類別條件約束指出要用作該泛型型別之型別引數的型別具有作為基底類別的指定類別 (或是該基底類別)，以用作該泛型型別的型別引數。 如果使用基底類別條件約束，則它必須出現在該型別參數的任何其他條件約束之前。 某些型別不允許作為基底類別條件約束：<xref:System.Object>、<xref:System.Array> 和 <xref:System.ValueType>。 在 C# 7.3 之前，也不允許 <xref:System.Enum>、<xref:System.Delegate> 和 <xref:System.MulticastDelegate> 作為基底類別條件約束。 下列範例會顯示現在可以指定為基底類別的型別：

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` 子句可以指定型別是 `class` 或 `struct`。 `struct` 條件約束不需要指定 `System.ValueType` 的基底類別條件約束。 `System.ValueType` 型別不能用作基底類別條件約束。 下列範例顯示 `class` 和 `struct` 條件約束：

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` 子句也可能包含 `unmanaged` 條件約束。 `unmanaged` 條件約束會將型別參數限制為稱為[「非受控型別」](../builtin-types/unmanaged-types.md)的型別。 `unmanaged` 條件約束可讓您更輕鬆地使用 C# 撰寫低階 Interop 程式碼。 此條件約束會啟用所有非受控型別的可重複使用常式。 `unmanaged` 條件約束不能與 `class` 或 `struct` 條件約束合併使用。 `unmanaged` 條件約束會強制型別必須是 `struct`：

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` 子句也可能包含建構函式條件約束 `new()`。 該條件約束可讓您使用 `new` 運算子建立型別參數執行個體。 [new() 條件約束](new-constraint.md)可讓編譯器知道提供的任何類型引數都必須有可存取的無參數或預設建構函式。 例如：

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` 條件約束會出現在 `where` 子句中的最後。 `new()` 條件約束不能與 `struct` 或 `unmanaged` 條件約束合併使用。 所有滿足這些條件約束的型別都必須具有可存取的無參數建構函式，讓 `new()` 條件約束成為備援。

若有多個類型參數，請對每個類型參數使用一個 `where` 子句，例如：

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

您也可以將條件約束附加至泛型方法的型別參數，如下列範例所示︰

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

請注意，描述委派類型參數條件約束的語法與方法的語法相同︰

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

如需泛型委派的資訊，請參閱[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。

如需條件約束語法和用法的詳細資料，請參閱[類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。

## <a name="c-language-specification"></a>C# 語言規格

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [泛型簡介](../../../csharp/programming-guide/generics/index.md)
- [new 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)
- [型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
