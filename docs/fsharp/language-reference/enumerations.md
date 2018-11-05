---
title: 列舉 (F#)
description: 了解如何使用 F# 列舉型別取代常值，讓程式碼，更容易讀取與維護。
ms.date: 05/16/2016
ms.openlocfilehash: 47fb353c2698f8b1474834ebbd1b0eff2c7f76e7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "46003161"
---
# <a name="enumerations"></a><span data-ttu-id="a571c-103">列舉</span><span class="sxs-lookup"><span data-stu-id="a571c-103">Enumerations</span></span>

<span data-ttu-id="a571c-104">*列舉型別*也稱為*列舉*、 是整數類資料類型，將標籤指派給值的子集。</span><span class="sxs-lookup"><span data-stu-id="a571c-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="a571c-105">列舉可用來取代常值，讓程式碼更容易閱讀及維護。</span><span class="sxs-lookup"><span data-stu-id="a571c-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="a571c-106">語法</span><span class="sxs-lookup"><span data-stu-id="a571c-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="a571c-107">備註</span><span class="sxs-lookup"><span data-stu-id="a571c-107">Remarks</span></span>

<span data-ttu-id="a571c-108">列舉型別看起來很像已區分的聯集具有簡單的值，不同之處在於可指定的值。</span><span class="sxs-lookup"><span data-stu-id="a571c-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="a571c-109">值通常是 0 或 1，開始的整數或整數，表示位元位置。</span><span class="sxs-lookup"><span data-stu-id="a571c-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="a571c-110">如果列舉型別用來表示的位元位置，您也應該使用[旗標](xref:System.FlagsAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="a571c-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="a571c-111">因此，比方說，您可以使用常值加上尾碼，例如，列舉的基礎型別從常值使用時，決定`1u`， `2u`，依此類推，不帶正負號的整數 (`uint32`) 型別。</span><span class="sxs-lookup"><span data-stu-id="a571c-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="a571c-112">當您參考具名的值時，您必須使用列舉型別本身的名稱與限定詞，亦即`enum-name.value1`，而非只`value1`。</span><span class="sxs-lookup"><span data-stu-id="a571c-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="a571c-113">此行為不同於的差別聯集。</span><span class="sxs-lookup"><span data-stu-id="a571c-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="a571c-114">這是因為列舉型別一定[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)屬性。</span><span class="sxs-lookup"><span data-stu-id="a571c-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="a571c-115">下列程式碼示範宣告和使用列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a571c-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="a571c-116">您可以輕鬆地轉換列舉的基礎型別使用適當的運算子，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a571c-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="a571c-117">列舉型別可以有下列的基礎類型的其中一個： `sbyte`， `byte`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint16`， `uint64`，以及`char`。</span><span class="sxs-lookup"><span data-stu-id="a571c-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="a571c-118">列舉型別以.NET framework 型別繼承自`System.Enum`，接著繼承自`System.ValueType`。</span><span class="sxs-lookup"><span data-stu-id="a571c-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="a571c-119">因此，它們是位於堆疊或內嵌在所包含的物件的實值型別，並且基礎型別的任何值是列舉的有效值。</span><span class="sxs-lookup"><span data-stu-id="a571c-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="a571c-120">這是重大時模式比對列舉值，因為您必須提供一種模式，會攔截未命名的數值。</span><span class="sxs-lookup"><span data-stu-id="a571c-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="a571c-121">`enum` F# 文件庫中的函式可用來產生列舉值，即使值以外的值預先定義，其中一項名為值。</span><span class="sxs-lookup"><span data-stu-id="a571c-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="a571c-122">您使用`enum`函式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a571c-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="a571c-123">預設值`enum`函式適用於類型`int32`。</span><span class="sxs-lookup"><span data-stu-id="a571c-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="a571c-124">因此，它不能有其他的基礎類型的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="a571c-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="a571c-125">相反地，使用下列項目。</span><span class="sxs-lookup"><span data-stu-id="a571c-125">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="a571c-126">此外，情況下，如列舉永遠會發出為`public`。</span><span class="sxs-lookup"><span data-stu-id="a571c-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="a571c-127">這是讓它們符合 C# 和.NET 平台的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="a571c-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="a571c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a571c-128">See also</span></span>

- [<span data-ttu-id="a571c-129">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a571c-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a571c-130">轉型和轉換</span><span class="sxs-lookup"><span data-stu-id="a571c-130">Casting and Conversions</span></span>](casting-and-conversions.md)
