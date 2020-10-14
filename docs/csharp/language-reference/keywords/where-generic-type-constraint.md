---
description: where (泛型類型條件約束) - C# 參考
title: where (泛型類型條件約束) - C# 參考
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
- classconstraint_CSharpKeyword
- structconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 75885e21173d31ff0a4ba34fbbd3558f934ae5b7
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050314"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (泛型類型條件約束) (C# 參考)

泛型定義中的 `where` 子句指定型別上的條件約束，以用來作為泛型型別、方法、委派或本機函式中型別參數的引數。 條件約束可以指定介面、基類或要求泛型型別作為參考、值或非受控型別。 它們會宣告型別引數必須具有的功能。

例如，您可以宣告泛型類別 `MyGenericClass`，讓型別參數 `T` 實作 <xref:System.IComparable%601> 介面：

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#1)]

> [!NOTE]
> 如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](where-clause.md)。

`where` 子句也可以包含基底類別條件約束。 基類條件約束指出要當做該泛型型別的型別引數使用的型別具有指定的類別做為基類，或者是基類。 如果使用基底類別條件約束，則它必須出現在該型別參數的任何其他條件約束之前。 某些型別不允許作為基底類別條件約束：<xref:System.Object>、<xref:System.Array> 和 <xref:System.ValueType>。 在 c # 7.3 之前，、 <xref:System.Enum> <xref:System.Delegate> 和 <xref:System.MulticastDelegate> 也不允許作為基類條件約束。 下列範例會顯示現在可以指定為基底類別的型別：

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#2)]

在 c # 8.0 和更新版本中可為 null 的內容中，會強制執行基底類別型別的可 null 性。 如果基類不是可為 null 的 (例如 `Base`) ，則類型引數必須不可為 null。 如果基類可為 null (例如 `Base?`) ，則型別引數可以是可為 null 或不可為 null 的參考型別。 當基類不可為 null 時，如果類型引數是可為 null 的參考型別，則編譯器會發出警告。

`where` 子句可以指定型別是 `class` 或 `struct`。 `struct` 條件約束不需要指定 `System.ValueType` 的基底類別條件約束。 `System.ValueType` 型別不能用作基底類別條件約束。 下列範例顯示 `class` 和 `struct` 條件約束：

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#3)]

在 c # 8.0 和更新版本中可為 null 的內容中， `class` 條件約束需要型別為不可為 null 的參考型別。 若要允許可為 null 的參考型別，請使用 `class?` 條件約束，此條件約束允許可為 null 且不可為 null 的參考型別。

`where`子句可能包含 `notnull` 條件約束。 `notnull`條件約束會將類型參數限制為不可為 null 的類型。 該型別可以是實 [值型](../builtin-types/value-types.md) 別，也可以是不可為 null 的參考型別。 `notnull`從 c # 8.0 開始，可以在[ `nullable enable` 內容](../../nullable-references.md#nullable-contexts)中編譯的程式碼使用條件約束。 與其他條件約束不同的是，如果型別引數違反 `notnull` 條件約束，則編譯器會產生警告而非錯誤。 只有在內容中才會產生警告 `nullable enable` 。

> [!IMPORTANT]
> 包含條件約束的泛型宣告 `notnull` 可用於可為 null 的無警示內容中，但編譯器不會強制執行條件約束。

[!code-csharp[using the nonnull constraint](snippets/GenericWhereConstraints.cs#NotNull)]

`where` 子句也可能包含 `unmanaged` 條件約束。 `unmanaged` 條件約束會將型別參數限制為稱為[「非受控型別」](../builtin-types/unmanaged-types.md)的型別。 `unmanaged` 條件約束可讓您更輕鬆地使用 C# 撰寫低階 Interop 程式碼。 此條件約束會啟用所有非受控型別的可重複使用常式。 `unmanaged` 條件約束不能與 `class` 或 `struct` 條件約束合併使用。 `unmanaged` 條件約束會強制型別必須是 `struct`：

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#4)]

`where` 子句也可能包含建構函式條件約束 `new()`。 該條件約束可讓您使用 `new` 運算子建立型別參數執行個體。 [新的 ( # A1 條件約束](new-constraint.md)可讓編譯器知道任何提供的型別引數都必須具有可存取的無參數函式。 例如︰

[!code-csharp[using the new constraint](snippets/GenericWhereConstraints.cs#5)]

`new()` 條件約束會出現在 `where` 子句中的最後。 `new()` 條件約束不能與 `struct` 或 `unmanaged` 條件約束合併使用。 所有滿足這些條件約束的型別都必須具有可存取的無參數建構函式，讓 `new()` 條件約束成為備援。

若有多個類型參數，請對每個類型參數使用一個 `where` 子句，例如：

[!code-csharp[using multiple where constraints](snippets/GenericWhereConstraints.cs#6)]

您也可以將條件約束附加至泛型方法的型別參數，如下列範例所示︰

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#7)]

請注意，描述委派類型參數條件約束的語法與方法的語法相同︰

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#8)]

如需泛型委派的資訊，請參閱[泛型委派](../../programming-guide/generics/generic-delegates.md)。

如需條件約束語法和用法的詳細資料，請參閱[類型參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)。

## <a name="c-language-specification"></a>C# 語言規格

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [泛型簡介](../../programming-guide/generics/index.md)
- [new 條件約束](./new-constraint.md)
- [型別參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)
