---
title: 列舉類型 - C# 程式設計指南
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: fea12a32d39f98ddc575e2d538e7501d2ff49768
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590541"
---
# <a name="enumeration-types-c-programming-guide"></a>列舉類型 (C# 程式設計手冊)

列舉類型 (也稱為列舉 (enumeration) 或列舉 (enum)) 提供有效率的方式，來定義一組可指派給變數的具名整數常數。 例如，假設您必須定義一個變數，其值代表星期幾。 該變數只會儲存七個有意義的值。 若要定義這些值，您可以使用以 [enum](../language-reference/keywords/enum.md) 關鍵字宣告的列舉類型。

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

根據預設，每個項目在列舉中的基礎類型是 [int](../language-reference/builtin-types/integral-numeric-types.md)。您可以使用冒號指定其他的整數數值類型，如上例所示。 如需可能類型的完整清單，請參閱 [enum (C# 參考)](../language-reference/keywords/enum.md)。

您可以透過轉換為基礎類型來驗證基礎數字值，如下例所示。

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

使用列舉而不使用數值類型的優點如下︰

- 清楚指定用戶端程式碼的哪些值對變數有效。

- 在 Visual Studio 中，IntelliSense 會列出已定義的值。

當您不為列舉程式清單中的項目指定值時，值會自動遞增 1。 在上例中，`Day.Sunday` 的值為 0，`Day.Monday` 的值為 1，依此類推。 當您建立新的 `Day` 物件時，如未明確指定其值，則它會有預設值 `Day.Sunday` (0)。 當您建立列舉時，請選取最符合邏輯的預設值，並指定其值為零。 這會造成所有的列舉都是預設值，如果它們在建立時未明確指派值。

如果 `meetingDay` 變數的類型是 `Day`，則 (不需要明確轉換) 您只能將 `Day` 所定義的其中一個值指派給它。 如果會議日期變更，您可以指派新值，從 `Day` 變成 `meetingDay`：

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> 您可以將任何任意整數值指派給 `meetingDay`。 例如，這行程式碼不會產生錯誤︰`meetingDay = (Day) 42`。 不過，您不應該這麼做，因為隱含預期列舉變數只保留列舉定義的其中一個值。 將任意值指派給列舉類型的變數會導致高風險錯誤。

您可以指派任何值給列舉類型的列舉程式清單中的項目，也可以使用計算的值︰

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>作為位元旗標的列舉類型

您可以使用列舉類型來定義位元旗標，讓列舉類型的執行個體儲存在列舉程式清單中所定義的任何值組。 (當然，某些組合在您的程式碼中可能無意義或不被允許。)

您可透過套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 屬性和適當定義值來建立位元旗標列舉，以對它們執行 `AND`、`OR`、`NOT` 和 `XOR` 位元運算。 在位元旗標列舉中包含值為零的具名常數，表示「未設定任何旗標」。 如果不表示「未設定任何旗標」，請勿指定旗標值為零。

在下例中，定義了另一個版本的 `Day` 列舉，名為 `Days`。 `Days` 具有 `Flags` 屬性，且每個值已指派下一個大於 2 的乘冪。 這可讓您建立其值為 `Days.Tuesday | Days.Thursday` 的 `Days` 變數。

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

若要對列舉設定旗標，請使用位元 `OR` 運算子，如下例所示︰

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

若要判斷是否已設定特定的旗標，請使用位元 `AND` 作業，如下例所示︰

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

如需在定義含有 <xref:System.FlagsAttribute?displayProperty=nameWithType> 屬性之列舉類型時需考量事項的詳細資訊，請參閱 <xref:System.Enum?displayProperty=nameWithType>。

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>使用 System.Enum 方法來探索和操作列舉值

所有列舉都是 <xref:System.Enum?displayProperty=nameWithType> 類型的執行個體。 您不能從 <xref:System.Enum?displayProperty=nameWithType> 衍生新的類別，但可以使用其方法來探索相關資訊以及操作列舉執行個體中的值。

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

如需詳細資訊，請參閱 <xref:System.Enum?displayProperty=nameWithType>。

您也可以使用擴充方法，為列舉建立新的方法。 如需詳細資訊，請參閱[如何：為列舉建立新方法](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Enum?displayProperty=nameWithType>
- [C# 程式設計指南](./index.md)
- [enum](../language-reference/keywords/enum.md)
