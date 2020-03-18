---
title: 枚舉類型 - C# 引用
description: 瞭解表示選擇或選項群組合的 C# 枚舉類型
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
ms.openlocfilehash: ab5eb1679f846bf0e25d90a4d0e0a71f0bdb0096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847701"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="f9b79-103">枚舉類型（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="f9b79-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="f9b79-104">*枚舉類型*（或*枚舉類型*）是由基礎[整體數值](integral-numeric-types.md)類型的一組命名常量定義的[數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f9b79-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="f9b79-105">要定義枚舉類型，請使用 關鍵字`enum`並指定*枚舉成員*的名稱：</span><span class="sxs-lookup"><span data-stu-id="f9b79-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="f9b79-106">預設情況下，枚舉成員的關聯常量值為`int`類型 ;它們以零開始，然後按照定義文本順序增加一個。</span><span class="sxs-lookup"><span data-stu-id="f9b79-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="f9b79-107">您可以顯式指定任何其他[積分數值](integral-numeric-types.md)類型作為枚舉類型的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="f9b79-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="f9b79-108">您還可以顯式指定關聯的常量值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="f9b79-108">You also can explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="f9b79-109">不能在枚舉類型的定義中定義方法。</span><span class="sxs-lookup"><span data-stu-id="f9b79-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="f9b79-110">要將功能添加到枚舉類型，請創建[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="f9b79-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="f9b79-111">枚舉類型的`E`預設值是運算式`(E)0`生成的值，即使零沒有相應的枚舉成員也是如此。</span><span class="sxs-lookup"><span data-stu-id="f9b79-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="f9b79-112">您可以使用枚舉類型表示一組互斥值或選項群組合的選擇。</span><span class="sxs-lookup"><span data-stu-id="f9b79-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="f9b79-113">要表示選項的組合，請將枚舉類型定義為位標誌。</span><span class="sxs-lookup"><span data-stu-id="f9b79-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="f9b79-114">作為位元旗標的列舉類型</span><span class="sxs-lookup"><span data-stu-id="f9b79-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="f9b79-115">如果希望枚舉類型表示選項的組合，請為這些選項定義枚舉成員，以便單個選項是位欄位。</span><span class="sxs-lookup"><span data-stu-id="f9b79-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="f9b79-116">也就是說，這些枚舉成員的相關值應該是兩者的權力。</span><span class="sxs-lookup"><span data-stu-id="f9b79-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="f9b79-117">然後，您可以使用[位邏輯運算子`|``&`，也可以](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators)分別組合選項或相交選項群組合。</span><span class="sxs-lookup"><span data-stu-id="f9b79-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="f9b79-118">要指示枚舉型別宣告位欄位，請對其應用[Flags](xref:System.FlagsAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="f9b79-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="f9b79-119">如以下示例所示，您還可以在枚舉類型的定義中包括一些典型的組合。</span><span class="sxs-lookup"><span data-stu-id="f9b79-119">As the following example shows, you also can include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

<span data-ttu-id="f9b79-120">有關詳細資訊和示例，請參閱<xref:System.FlagsAttribute?displayProperty=nameWithType>API 參考頁和非[獨佔成員以及](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) <xref:System.Enum?displayProperty=nameWithType> API 參考頁的標誌屬性部分。</span><span class="sxs-lookup"><span data-stu-id="f9b79-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="f9b79-121">系統.枚舉類型和枚舉約束</span><span class="sxs-lookup"><span data-stu-id="f9b79-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="f9b79-122">類型<xref:System.Enum?displayProperty=nameWithType>是所有枚舉類型的抽象基類。</span><span class="sxs-lookup"><span data-stu-id="f9b79-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="f9b79-123">它提供了許多方法來獲取有關枚舉類型及其值的資訊。</span><span class="sxs-lookup"><span data-stu-id="f9b79-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="f9b79-124">有關詳細資訊和示例，<xref:System.Enum?displayProperty=nameWithType>請參閱 API 參考頁。</span><span class="sxs-lookup"><span data-stu-id="f9b79-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="f9b79-125">從 C# 7.3 開始，`System.Enum`可以在基類約束（稱為[枚舉約束](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)）中使用來指定類型參數是枚舉類型。</span><span class="sxs-lookup"><span data-stu-id="f9b79-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="f9b79-126">轉換</span><span class="sxs-lookup"><span data-stu-id="f9b79-126">Conversions</span></span>

<span data-ttu-id="f9b79-127">對於任何枚舉類型，枚舉類型與其基礎積分類型之間存在顯式轉換。</span><span class="sxs-lookup"><span data-stu-id="f9b79-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="f9b79-128">如果將枚舉值[轉換為](../operators/type-testing-and-cast.md#cast-operator-)其基礎類型，則結果為枚舉成員的關聯積分值。</span><span class="sxs-lookup"><span data-stu-id="f9b79-128">If you [cast](../operators/type-testing-and-cast.md#cast-operator-) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

<span data-ttu-id="f9b79-129">使用<xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>方法確定枚舉類型是否包含具有特定關聯值的枚舉成員。</span><span class="sxs-lookup"><span data-stu-id="f9b79-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="f9b79-130">對於任何枚舉類型，分別存在與<xref:System.Enum?displayProperty=nameWithType>類型轉換的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="f9b79-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f9b79-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f9b79-131">C# language specification</span></span>

<span data-ttu-id="f9b79-132">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="f9b79-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f9b79-133">列舉</span><span class="sxs-lookup"><span data-stu-id="f9b79-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="f9b79-134">列舉值和作業</span><span class="sxs-lookup"><span data-stu-id="f9b79-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="f9b79-135">列舉邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="f9b79-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="f9b79-136">枚舉比較運算子</span><span class="sxs-lookup"><span data-stu-id="f9b79-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="f9b79-137">顯式枚舉轉換</span><span class="sxs-lookup"><span data-stu-id="f9b79-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="f9b79-138">隱式枚舉轉換</span><span class="sxs-lookup"><span data-stu-id="f9b79-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="f9b79-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9b79-139">See also</span></span>

- [<span data-ttu-id="f9b79-140">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f9b79-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f9b79-141">列舉類型格式字串</span><span class="sxs-lookup"><span data-stu-id="f9b79-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="f9b79-142">設計指南 - 枚舉設計</span><span class="sxs-lookup"><span data-stu-id="f9b79-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="f9b79-143">設計指南 - 枚舉命名約定</span><span class="sxs-lookup"><span data-stu-id="f9b79-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="f9b79-144">Switch 陳述式</span><span class="sxs-lookup"><span data-stu-id="f9b79-144">switch statement</span></span>](../keywords/switch.md)
