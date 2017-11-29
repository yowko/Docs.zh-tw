---
title: "列舉 (F#)"
description: "了解如何使用 F # 列舉型別取代常值，讓程式碼更容易讀取與維護。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9272bf5a-9a9f-4314-9e34-a3248e5244f5
ms.openlocfilehash: de0273900b707c99e6fb1bcc84e5c2b9ef2bc725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="enumerations"></a><span data-ttu-id="a88aa-104">列舉</span><span class="sxs-lookup"><span data-stu-id="a88aa-104">Enumerations</span></span>

<span data-ttu-id="a88aa-105">*列舉型別*，亦稱為*列舉*、 是整數類資料類型，其中的標籤指派給值的子集。</span><span class="sxs-lookup"><span data-stu-id="a88aa-105">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="a88aa-106">列舉可用來取代常值，讓程式碼更容易閱讀及維護。</span><span class="sxs-lookup"><span data-stu-id="a88aa-106">You can use them in place of literals to make code more readable and maintainable.</span></span>


## <a name="syntax"></a><span data-ttu-id="a88aa-107">語法</span><span class="sxs-lookup"><span data-stu-id="a88aa-107">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="a88aa-108">備註</span><span class="sxs-lookup"><span data-stu-id="a88aa-108">Remarks</span></span>
<span data-ttu-id="a88aa-109">列舉型別看起來很像差別聯集，其中包含簡單的值，不同之處在於您可以指定值。</span><span class="sxs-lookup"><span data-stu-id="a88aa-109">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="a88aa-110">值通常是從 0 或 1，開始的整數或整數，表示位元位置。</span><span class="sxs-lookup"><span data-stu-id="a88aa-110">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="a88aa-111">如果列舉型別用來表示的位元位置，您也應該使用[旗標](xref:System.FlagsAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="a88aa-111">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="a88aa-112">列舉的基礎類型由常值使用，以便比方說，您可以使用常值加上尾碼，例如`1u`， `2u`，依此類推，針對不帶正負號的整數 (`uint32`) 型別。</span><span class="sxs-lookup"><span data-stu-id="a88aa-112">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="a88aa-113">當您參考具名的值時，您必須使用列舉型別本身的名稱與限定詞，也就是`enum-name.value1`，而非只`value1`。</span><span class="sxs-lookup"><span data-stu-id="a88aa-113">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="a88aa-114">此行為不同於差別聯集。</span><span class="sxs-lookup"><span data-stu-id="a88aa-114">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="a88aa-115">這是因為列舉型別一定[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)屬性。</span><span class="sxs-lookup"><span data-stu-id="a88aa-115">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="a88aa-116">下列程式碼顯示的宣告和使用列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a88aa-116">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="a88aa-117">您可以輕鬆轉換列舉的基礎型別使用適當的運算子，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a88aa-117">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="a88aa-118">列舉型別可以有下列的基礎類型的其中一個： `sbyte`， `byte`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint16`， `uint64`，和`char`。</span><span class="sxs-lookup"><span data-stu-id="a88aa-118">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="a88aa-119">列舉型別以.NET framework 型別繼承自`System.Enum`，依序繼承自`System.ValueType`。</span><span class="sxs-lookup"><span data-stu-id="a88aa-119">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="a88aa-120">因此，它們是實值型別上堆疊或內嵌在所包含的物件，基礎類型的任何值都是有效的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a88aa-120">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="a88aa-121">這相當重要時模式比對列舉值，因為您必須提供的模式，攔截未命名的值。</span><span class="sxs-lookup"><span data-stu-id="a88aa-121">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="a88aa-122">`enum` F # 程式庫中的函式可用來產生列舉值，即使值以外的預先定義的其中一個已命名的值。</span><span class="sxs-lookup"><span data-stu-id="a88aa-122">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="a88aa-123">您使用`enum`函式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a88aa-123">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="a88aa-124">預設值`enum`函式適用於類型`int32`。</span><span class="sxs-lookup"><span data-stu-id="a88aa-124">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="a88aa-125">因此，它不能與其他基本類型的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a88aa-125">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="a88aa-126">相反地，使用下列項目。</span><span class="sxs-lookup"><span data-stu-id="a88aa-126">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a><span data-ttu-id="a88aa-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a88aa-127">See Also</span></span>
[<span data-ttu-id="a88aa-128">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a88aa-128">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a88aa-129">轉型和轉換</span><span class="sxs-lookup"><span data-stu-id="a88aa-129">Casting and Conversions</span></span>](casting-and-conversions.md)
