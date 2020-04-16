---
title: where (泛型類型條件約束) - C# 參考
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 5a56b8058735d3ca786520a82424c79d1975bfc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463017"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (泛型類型條件約束) (C# 參考)

泛型定義中的 `where` 子句指定型別上的條件約束，以用來作為泛型型別、方法、委派或本機函式中型別參數的引數。 約束可以指定介面、基類或要求泛型類型為引用類型、值類型或非託管類型。 它們聲明類型參數必須具有的功能。

例如，您可以宣告泛型類別 `MyGenericClass`，讓型別參數 `T` 實作 <xref:System.IComparable%601> 介面：

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> 如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](where-clause.md)。

`where` 子句也可以包含基底類別條件約束。 基類約束規定,要用作該泛型類型的類型具有指定類作為基類,或者該基類。 如果使用基底類別條件約束，則它必須出現在該型別參數的任何其他條件約束之前。 某些型別不允許作為基底類別條件約束：<xref:System.Object>、<xref:System.Array> 和 <xref:System.ValueType>。 在 C# 7.3<xref:System.Delegate>之前<xref:System.MulticastDelegate><xref:System.Enum>, 和 也不允許作為基類約束。 下列範例會顯示現在可以指定為基底類別的型別：

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

在 C# 8.0 及更高版本中的可空上下文中,將強制執行基類類型的 null。 如果基類是不可 null 的`Base`(例如 ),則類型參數必須為非空。 如果基類是空的(例如`Base?`),類型參數可以是空引用類型,也可以是不可空的引用類型。 如果類型參數是空引用類型,則當基類為非空時,編譯器會發出警告。

`where` 子句可以指定型別是 `class` 或 `struct`。 `struct` 條件約束不需要指定 `System.ValueType` 的基底類別條件約束。 `System.ValueType` 型別不能用作基底類別條件約束。 下列範例顯示 `class` 和 `struct` 條件約束：

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

在 C# 8.0 及更高版本中的空`class`上下文中 ,約束要求類型為不可空引用類型。 要允許可無效引用類型,`class?`請使用約束,該約束允許空引用類型和非空引用類型。

子`where`句可能包括`notnull`約束 。 約束`notnull`將類型參數限制為非空類型。 該類型可以是[值類型](../builtin-types/value-types.md)或不可消除的引用類型。 該`notnull`規範在 C# 8.0 中開始可用於[`nullable enable`在上下文中](../../nullable-references.md#nullable-contexts)編譯的代碼。 與其他約束不同,如果類型參數違反約束`notnull`,編譯器將生成警告而不是錯誤。 警告僅在`nullable enable`上下文中生成。

> [!IMPORTANT]
> 包含約束的`notnull`泛型聲明可以在可忽略的上下文中使用,但編譯器不強制執行約束。

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

`where` 子句也可能包含 `unmanaged` 條件約束。 `unmanaged` 條件約束會將型別參數限制為稱為[「非受控型別」](../builtin-types/unmanaged-types.md)的型別。 `unmanaged` 條件約束可讓您更輕鬆地使用 C# 撰寫低階 Interop 程式碼。 此條件約束會啟用所有非受控型別的可重複使用常式。 `unmanaged` 條件約束不能與 `class` 或 `struct` 條件約束合併使用。 `unmanaged` 條件約束會強制型別必須是 `struct`：

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` 子句也可能包含建構函式條件約束 `new()`。 該條件約束可讓您使用 `new` 運算子建立型別參數執行個體。 [new() 約束](new-constraint.md)使編譯器知道提供的任何類型參數都必須具有可訪問的無參數構造函數。 例如：

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` 條件約束會出現在 `where` 子句中的最後。 `new()` 條件約束不能與 `struct` 或 `unmanaged` 條件約束合併使用。 所有滿足這些條件約束的型別都必須具有可存取的無參數建構函式，讓 `new()` 條件約束成為備援。

若有多個類型參數，請對每個類型參數使用一個 `where` 子句，例如：

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

您也可以將條件約束附加至泛型方法的型別參數，如下列範例所示︰

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

請注意，描述委派類型參數條件約束的語法與方法的語法相同︰

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

如需泛型委派的資訊，請參閱[泛型委派](../../programming-guide/generics/generic-delegates.md)。

如需條件約束語法和用法的詳細資料，請參閱[類型參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)。

## <a name="c-language-specification"></a>C# 語言規格

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 編程指南](../../programming-guide/index.md)
- [泛型簡介](../../programming-guide/generics/index.md)
- [新的約束](./new-constraint.md)
- [型別參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)
