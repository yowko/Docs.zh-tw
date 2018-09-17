---
title: 列舉類型 (C# 程式設計手冊)
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3efedd48303c79bafde3704b0fdd6fcdd465a0a7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45686124"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="85674-102">列舉類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="85674-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="85674-103">列舉類型 (也稱為列舉 (enumeration) 或列舉 (enum)) 提供有效率的方式，來定義一組可指派給變數的具名整數常數。</span><span class="sxs-lookup"><span data-stu-id="85674-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="85674-104">例如，假設您必須定義一個變數，其值代表星期幾。</span><span class="sxs-lookup"><span data-stu-id="85674-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="85674-105">該變數只會儲存七個有意義的值。</span><span class="sxs-lookup"><span data-stu-id="85674-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="85674-106">若要定義這些值，您可以使用以 [enum](../../csharp/language-reference/keywords/enum.md) 關鍵字宣告的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="85674-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="85674-107">根據預設，每個項目在列舉中的基礎類型是 [int](../../csharp/language-reference/keywords/int.md)。您可以使用冒號指定其他的整數數值類型，如上例所示。</span><span class="sxs-lookup"><span data-stu-id="85674-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="85674-108">如需可能類型的完整清單，請參閱 [enum (C# 參考)](../../csharp/language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="85674-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="85674-109">您可以透過轉換為基礎類型來驗證基礎數字值，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="85674-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

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

<span data-ttu-id="85674-110">使用列舉而不使用數值類型的優點如下︰</span><span class="sxs-lookup"><span data-stu-id="85674-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="85674-111">清楚指定用戶端程式碼的哪些值對變數有效。</span><span class="sxs-lookup"><span data-stu-id="85674-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="85674-112">在 Visual Studio 中，IntelliSense 會列出已定義的值。</span><span class="sxs-lookup"><span data-stu-id="85674-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="85674-113">當您不為列舉程式清單中的項目指定值時，值會自動遞增 1。</span><span class="sxs-lookup"><span data-stu-id="85674-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="85674-114">在上例中，`Day.Sunday` 的值為 0，`Day.Monday` 的值為 1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="85674-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="85674-115">當您建立新的 `Day` 物件時，如未明確指定其值，則它會有預設值 `Day.Sunday` (0)。</span><span class="sxs-lookup"><span data-stu-id="85674-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="85674-116">當您建立列舉時，請選取最符合邏輯的預設值，並指定其值為零。</span><span class="sxs-lookup"><span data-stu-id="85674-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="85674-117">這會造成所有的列舉都是預設值，如果它們在建立時未明確指派值。</span><span class="sxs-lookup"><span data-stu-id="85674-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="85674-118">如果 `meetingDay` 變數的類型是 `Day`，則 (不需要明確轉換) 您只能將 `Day` 所定義的其中一個值指派給它。</span><span class="sxs-lookup"><span data-stu-id="85674-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="85674-119">如果會議日期變更，您可以指派新值，從 `Day` 變成 `meetingDay`：</span><span class="sxs-lookup"><span data-stu-id="85674-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="85674-120">您可以將任何任意整數值指派給 `meetingDay`。</span><span class="sxs-lookup"><span data-stu-id="85674-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="85674-121">例如，這行程式碼不會產生錯誤︰`meetingDay = (Day) 42`。</span><span class="sxs-lookup"><span data-stu-id="85674-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="85674-122">不過，您不應該這麼做，因為隱含預期列舉變數只保留列舉定義的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="85674-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="85674-123">將任意值指派給列舉類型的變數會導致高風險錯誤。</span><span class="sxs-lookup"><span data-stu-id="85674-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="85674-124">您可以指派任何值給列舉類型的列舉程式清單中的項目，也可以使用計算的值︰</span><span class="sxs-lookup"><span data-stu-id="85674-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="85674-125">作為位元旗標的列舉類型</span><span class="sxs-lookup"><span data-stu-id="85674-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="85674-126">您可以使用列舉類型來定義位元旗標，讓列舉類型的執行個體儲存在列舉程式清單中所定義的任何值組。</span><span class="sxs-lookup"><span data-stu-id="85674-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="85674-127">(當然，某些組合在您的程式碼中可能無意義或不被允許。)</span><span class="sxs-lookup"><span data-stu-id="85674-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="85674-128">您可透過套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 屬性和適當定義值來建立位元旗標列舉，以對它們執行 `AND`、`OR`、`NOT` 和 `XOR` 位元運算。</span><span class="sxs-lookup"><span data-stu-id="85674-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="85674-129">在位元旗標列舉中包含值為零的具名常數，表示「未設定任何旗標」。</span><span class="sxs-lookup"><span data-stu-id="85674-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="85674-130">如果不表示「未設定任何旗標」，請勿指定旗標值為零。</span><span class="sxs-lookup"><span data-stu-id="85674-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="85674-131">在下例中，定義了另一個版本的 `Day` 列舉，名為 `Days`。</span><span class="sxs-lookup"><span data-stu-id="85674-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="85674-132">`Days` 具有 `Flags` 屬性，且每個值已指派下一個大於 2 的乘冪。</span><span class="sxs-lookup"><span data-stu-id="85674-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="85674-133">這可讓您建立其值為 `Days.Tuesday | Days.Thursday` 的 `Days` 變數。</span><span class="sxs-lookup"><span data-stu-id="85674-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="85674-134">若要對列舉設定旗標，請使用位元 `OR` 運算子，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="85674-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="85674-135">若要判斷是否已設定特定的旗標，請使用位元 `AND` 作業，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="85674-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="85674-136">如需在定義含有 <xref:System.FlagsAttribute?displayProperty=nameWithType> 屬性之列舉類型時需考量事項的詳細資訊，請參閱 <xref:System.Enum?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="85674-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="85674-137">使用 System.Enum 方法來探索和操作列舉值</span><span class="sxs-lookup"><span data-stu-id="85674-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="85674-138">所有列舉都是 <xref:System.Enum?displayProperty=nameWithType> 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="85674-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="85674-139">您不能從 <xref:System.Enum?displayProperty=nameWithType> 衍生新的類別，但可以使用其方法來探索相關資訊以及操作列舉執行個體中的值。</span><span class="sxs-lookup"><span data-stu-id="85674-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="85674-140">如需詳細資訊，請參閱<xref:System.Enum?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="85674-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="85674-141">您也可以使用擴充方法，為列舉建立新的方法。</span><span class="sxs-lookup"><span data-stu-id="85674-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="85674-142">如需詳細資訊，請參閱[如何：建立列舉的新方法 ](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="85674-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85674-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="85674-143">See Also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>  
- [<span data-ttu-id="85674-144">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="85674-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="85674-145">enum</span><span class="sxs-lookup"><span data-stu-id="85674-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
