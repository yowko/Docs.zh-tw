---
title: 列舉類型- C#參考
description: 瞭解代表C#選擇或選擇組合的列舉類型
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 72bc867bf0a789279da9a01f97c85d96b78684ed
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75444344"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="d5429-103">列舉類型（C#參考）</span><span class="sxs-lookup"><span data-stu-id="d5429-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="d5429-104">列舉型別（或列舉型別）是由基礎[整數數值](integral-numeric-types.md)類型的一組命名常數所定義的實值型別。</span><span class="sxs-lookup"><span data-stu-id="d5429-104">An enumeration type (or enum type) is a value type defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="d5429-105">若要定義列舉類型，請使用 `enum` 關鍵字，並指定*列舉成員*的名稱：</span><span class="sxs-lookup"><span data-stu-id="d5429-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="d5429-106">根據預設，列舉成員的相關聯常數值是 `int`的類型;開頭為零，並依照定義文字順序增加一個。</span><span class="sxs-lookup"><span data-stu-id="d5429-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="d5429-107">您可以明確地指定任何其他[整數數值](integral-numeric-types.md)類型做為列舉類型的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="d5429-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="d5429-108">您也可以明確指定相關聯的常數值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d5429-108">You also can explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="d5429-109">您無法在列舉類型的定義內定義方法。</span><span class="sxs-lookup"><span data-stu-id="d5429-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="d5429-110">若要將功能加入至列舉類型，請建立[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d5429-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="d5429-111">列舉型別的預設值 `E` 是運算式 `(E)0`所產生的值，即使零沒有對應的列舉成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="d5429-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="d5429-112">您可以使用列舉類型，從一組互斥值或選擇組合來表示選擇。</span><span class="sxs-lookup"><span data-stu-id="d5429-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="d5429-113">若要代表選擇的組合，請將列舉類型定義為位旗標。</span><span class="sxs-lookup"><span data-stu-id="d5429-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="d5429-114">作為位元旗標的列舉類型</span><span class="sxs-lookup"><span data-stu-id="d5429-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="d5429-115">如果您想要列舉類型來代表選擇的組合，請針對這些選擇定義列舉成員，讓個別的選擇是位欄位。</span><span class="sxs-lookup"><span data-stu-id="d5429-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="d5429-116">也就是說，這些列舉成員的相關聯值應該是兩個的乘冪。</span><span class="sxs-lookup"><span data-stu-id="d5429-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="d5429-117">然後，您可以使用[位邏輯運算子 `|` 或 `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) ，分別結合選擇或交集的選擇組合。</span><span class="sxs-lookup"><span data-stu-id="d5429-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="d5429-118">若要指出列舉類型會宣告位欄位，請將[Flags](xref:System.FlagsAttribute)屬性套用至其中。</span><span class="sxs-lookup"><span data-stu-id="d5429-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="d5429-119">如下列範例所示，您也可以在列舉類型的定義中包含一些一般組合。</span><span class="sxs-lookup"><span data-stu-id="d5429-119">As the following example shows, you also can include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

<span data-ttu-id="d5429-120">如需詳細資訊和範例，請參閱 <xref:System.Enum?displayProperty=nameWithType> API 參考頁面的 <xref:System.FlagsAttribute?displayProperty=nameWithType> API 參考頁面和[非獨佔成員和 Flags 屬性](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute)一節。</span><span class="sxs-lookup"><span data-stu-id="d5429-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="d5429-121">System.string 類型和 enum 條件約束</span><span class="sxs-lookup"><span data-stu-id="d5429-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="d5429-122"><xref:System.Enum?displayProperty=nameWithType> 類型是所有列舉類型的抽象基類。</span><span class="sxs-lookup"><span data-stu-id="d5429-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="d5429-123">它提供了數種方法來取得列舉型別和其值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d5429-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="d5429-124">如需詳細資訊和範例，請參閱 <xref:System.Enum?displayProperty=nameWithType> API 參考頁面。</span><span class="sxs-lookup"><span data-stu-id="d5429-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="d5429-125">從C# 7.3 開始，您可以在基類條件約束（也稱為[列舉條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)）中使用 `System.Enum`，以指定類型參數是列舉類型。</span><span class="sxs-lookup"><span data-stu-id="d5429-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="d5429-126">轉換</span><span class="sxs-lookup"><span data-stu-id="d5429-126">Conversions</span></span>

<span data-ttu-id="d5429-127">針對任何列舉型別，列舉型別與其基礎整數型別之間存在明確轉換。</span><span class="sxs-lookup"><span data-stu-id="d5429-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="d5429-128">如果您將列舉值[轉換](../operators/type-testing-and-cast.md#cast-operator-)為其基礎類型，則結果會是列舉成員的相關整數值。</span><span class="sxs-lookup"><span data-stu-id="d5429-128">If you [cast](../operators/type-testing-and-cast.md#cast-operator-) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

<span data-ttu-id="d5429-129">使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 方法來判斷列舉類型是否包含具有特定相關聯值的列舉成員。</span><span class="sxs-lookup"><span data-stu-id="d5429-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="d5429-130">針對任何列舉類型，會分別存在與 <xref:System.Enum?displayProperty=nameWithType> 類型之間的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="d5429-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d5429-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d5429-131">C# language specification</span></span>

<span data-ttu-id="d5429-132">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="d5429-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d5429-133">列舉</span><span class="sxs-lookup"><span data-stu-id="d5429-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="d5429-134">列舉值和作業</span><span class="sxs-lookup"><span data-stu-id="d5429-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="d5429-135">列舉邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="d5429-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="d5429-136">列舉比較運算子</span><span class="sxs-lookup"><span data-stu-id="d5429-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="d5429-137">明確列舉轉換</span><span class="sxs-lookup"><span data-stu-id="d5429-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="d5429-138">隱含列舉轉換</span><span class="sxs-lookup"><span data-stu-id="d5429-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="d5429-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5429-139">See also</span></span>

- [<span data-ttu-id="d5429-140">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d5429-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d5429-141">列舉類型格式字串</span><span class="sxs-lookup"><span data-stu-id="d5429-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="d5429-142">列舉命名慣例</span><span class="sxs-lookup"><span data-stu-id="d5429-142">Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="d5429-143">switch 陳述式</span><span class="sxs-lookup"><span data-stu-id="d5429-143">switch statement</span></span>](../keywords/switch.md)
