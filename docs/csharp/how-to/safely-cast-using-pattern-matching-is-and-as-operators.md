---
title: 如何使用模式符合和作為運算子安全地強制轉換
description: 了解如何使用模式比對技術，將變數安全地轉換為不同類型。 您可以使用模式比對、is 和 as 運算子，安全地進行轉換類型。
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 9f5690e6840098f94360dba89f09fb23b258b782
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739053"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>如何使用模式符合和作為運算子安全地強制轉換

因為物件都是多型的，所以可能會針對基底類別類型的變數來保存衍生[類型](../programming-guide/types/index.md)。 若要存取衍生類型的執行個體成員，就需要將值[轉換](../programming-guide/types/casting-and-type-conversions.md)回衍生類型。 不過，轉換帶有擲回 <xref:System.InvalidCastException> 的風險。 C# 提供[模式比對](../pattern-matching.md)陳述式，只有在成功時才會有條件地執行轉換。 C# 也提供 [is](../language-reference/operators/type-testing-and-cast.md#is-operator) 和 [as](../language-reference/operators/type-testing-and-cast.md#as-operator) 運算子，藉此測試值是否為特定類型。

下面的範例展示如何使用模式相`is`片語語:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

上述範例示範模式比對語法的一些功能。 語句`if (a is Mammal m)`將測試與初始化分配相結合。 只有在測試成功時，才會進行指派。 變數 `m` 僅會在已指派的內嵌 `if` 陳述式範圍內。 您隨後無法使用相同的方法存取 `m`。 前面的範例還展示如何使用[`as`運算子](../language-reference/operators/type-testing-and-cast.md#as-operator)將物件轉換為指定類型。

如果[空值類型](../language-reference/builtin-types/nullable-value-types.md)具有值,也可以使用相同的語法進行測試,如以下範例所示:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

上述範例示範模式比對轉換的其他功能，以便與轉換一起使用。 您可以特別檢查 `null` 值，藉此測試 Null 模式的變數。 當執行階段變數的值是 `null`，則 `is` 陳述式的類型檢查一律會傳回 `false`。 模式比對 `is` 陳述式不允許可為 Null 的值型別 (例如 `int?` 或 `Nullable<int>`)，但您可以測試其他值的型別。 上`is`例中的模式不限於空值類型。 您還可以使用這些模式來測試引用類型的變數是否具有值或該`null`值。

前面的示例還顯示了如何在`switch`語句中使用類型模式,其中變數可能是許多不同類型的類型之一。

如果要測試變數是否為給定類型,但不將其分配給新變數,則可以使用`is`和`as`運算元進行引用類型和空值類型。 下列程式碼示範在模式比對推出之前，如何使用屬於 C# 語言的 `is` 和 `as` 陳述式測試變數是否屬於特定類型：

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

透過將此程式碼與模式比對程式碼進行比較，明顯可見，模式比對語法藉著在單一陳述式中結合測試和指派來提供更強大的功能。 請盡可能使用模式比對語法。

您可以通過查看[GitHub 儲存庫](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/safelycast)中的代碼來嘗試這些範例。 或者，您可以將範例下載[為 ZIP 檔案](../../../samples/snippets/csharp/how-to/safelycast.zip)。
