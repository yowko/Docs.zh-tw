---
title: '列舉型別-c # 參考'
description: '瞭解代表選擇或組合選項的 c # 列舉類型'
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
ms.openlocfilehash: 930efdbdc6a20ea301331c1ce6fc664da43bfc5f
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471846"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="dd5bd-103">列舉類型 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="dd5bd-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="dd5bd-104">*列舉型*別 (或*列舉型*別) 是一組由基礎[整數數值](integral-numeric-types.md)型別之指定常數所定義的實[值型](value-types.md)別。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="dd5bd-105">若要定義列舉型別，請使用 `enum` 關鍵字並指定 *列舉成員*的名稱：</span><span class="sxs-lookup"><span data-stu-id="dd5bd-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="dd5bd-106">根據預設，列舉成員的相關常數值為類型 `int` ; 它們是從零開始，並依照定義文字順序遞增一。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="dd5bd-107">您可以明確地指定任何其他 [整數數值](integral-numeric-types.md) 類型作為列舉型別的基礎型別。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="dd5bd-108">您也可以明確地指定相關聯的常數值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="dd5bd-108">You can also explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="dd5bd-109">您無法在列舉類型的定義內定義方法。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="dd5bd-110">若要將功能加入至列舉型別，請建立 [擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="dd5bd-111">列舉類型的預設值 `E` 是運算式所產生的值 `(E)0` ，即使零沒有對應的列舉成員。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="dd5bd-112">您可以使用列舉類型來代表一組互斥值或選擇組合的選項。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="dd5bd-113">若要表示選項的組合，請將列舉類型定義為位旗標。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="dd5bd-114">作為位元旗標的列舉類型</span><span class="sxs-lookup"><span data-stu-id="dd5bd-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="dd5bd-115">如果您想要列舉型別代表選項的組合，請定義這些選擇的列舉成員，讓個別的選擇是位欄位。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="dd5bd-116">也就是說，這些列舉成員的關聯值應該是兩個的乘冪。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="dd5bd-117">然後，您可以使用[位邏輯運算子， `|` 或 `&` ](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators)分別合併選項或交集組合的選項。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="dd5bd-118">若要指出列舉型別會宣告位欄位，請將 [Flags](xref:System.FlagsAttribute) 屬性套用至其中。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="dd5bd-119">如下列範例所示，您也可以在列舉類型的定義中包含一些典型的組合。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-119">As the following example shows, you can also include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/shared/EnumType.cs#Flags)]

<span data-ttu-id="dd5bd-120">如需詳細資訊和範例，請參閱 [api 參考] 頁面的 [ <xref:System.FlagsAttribute?displayProperty=nameWithType> api 參考] 頁面和 [ [非獨佔成員] 和 [旗標屬性](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) ] 區段 <xref:System.Enum?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="dd5bd-121">System.string 型別和列舉條件約束</span><span class="sxs-lookup"><span data-stu-id="dd5bd-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="dd5bd-122">此 <xref:System.Enum?displayProperty=nameWithType> 類型是所有列舉類型的抽象基類。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="dd5bd-123">它會提供數種方法來取得列舉型別和其值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="dd5bd-124">如需詳細資訊和範例，請參閱 <xref:System.Enum?displayProperty=nameWithType> API 參考頁面。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="dd5bd-125">從 c # 7.3 開始，您可以 `System.Enum` 在稱為 [列舉條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints) 的基類條件約束 (中使用，) 指定型別參數為列舉型別。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="dd5bd-126">轉換</span><span class="sxs-lookup"><span data-stu-id="dd5bd-126">Conversions</span></span>

<span data-ttu-id="dd5bd-127">對於任何列舉型別，列舉型別與其基礎整數型別之間存在明確的轉換。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="dd5bd-128">如果您將列舉值 [轉換](../operators/type-testing-and-cast.md#cast-expression) 為其基礎類型，結果會是列舉成員的相關整數值。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-128">If you [cast](../operators/type-testing-and-cast.md#cast-expression) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/shared/EnumType.cs#Conversions)]

<span data-ttu-id="dd5bd-129">您 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 可以使用方法來判斷列舉型別是否包含具有特定關聯值的列舉成員。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="dd5bd-130">針對任何列舉型別，會分別存在對類型的 [裝箱和取消](../../programming-guide/types/boxing-and-unboxing.md) 加入轉換 <xref:System.Enum?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="dd5bd-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dd5bd-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="dd5bd-131">C# language specification</span></span>

<span data-ttu-id="dd5bd-132">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="dd5bd-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dd5bd-133">列舉</span><span class="sxs-lookup"><span data-stu-id="dd5bd-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="dd5bd-134">列舉值和作業</span><span class="sxs-lookup"><span data-stu-id="dd5bd-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="dd5bd-135">列舉邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="dd5bd-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="dd5bd-136">列舉比較運算子</span><span class="sxs-lookup"><span data-stu-id="dd5bd-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="dd5bd-137">明確列舉轉換</span><span class="sxs-lookup"><span data-stu-id="dd5bd-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="dd5bd-138">隱含列舉轉換</span><span class="sxs-lookup"><span data-stu-id="dd5bd-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="dd5bd-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5bd-139">See also</span></span>

- [<span data-ttu-id="dd5bd-140">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="dd5bd-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dd5bd-141">列舉格式字串</span><span class="sxs-lookup"><span data-stu-id="dd5bd-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="dd5bd-142">設計指導方針-列舉設計</span><span class="sxs-lookup"><span data-stu-id="dd5bd-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="dd5bd-143">設計指導方針-列舉命名慣例</span><span class="sxs-lookup"><span data-stu-id="dd5bd-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="dd5bd-144">switch 陳述式</span><span class="sxs-lookup"><span data-stu-id="dd5bd-144">switch statement</span></span>](../keywords/switch.md)
