---
title: 列舉
description: 瞭解如何使用F#列舉來取代常值, 讓您的程式碼更容易閱讀和維護。
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630345"
---
# <a name="enumerations"></a><span data-ttu-id="9417a-103">列舉</span><span class="sxs-lookup"><span data-stu-id="9417a-103">Enumerations</span></span>

<span data-ttu-id="9417a-104">列舉 (也稱為列舉  ) 是整數類資料類型, 其中的標籤會指派給值的子集。</span><span class="sxs-lookup"><span data-stu-id="9417a-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="9417a-105">列舉可用來取代常值，讓程式碼更容易閱讀及維護。</span><span class="sxs-lookup"><span data-stu-id="9417a-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="9417a-106">語法</span><span class="sxs-lookup"><span data-stu-id="9417a-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="9417a-107">備註</span><span class="sxs-lookup"><span data-stu-id="9417a-107">Remarks</span></span>

<span data-ttu-id="9417a-108">列舉看起來很像具有簡單值的區分聯集, 但可以指定值。</span><span class="sxs-lookup"><span data-stu-id="9417a-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="9417a-109">這些值通常是從0或1開始的整數, 或是代表位位置的整數。</span><span class="sxs-lookup"><span data-stu-id="9417a-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="9417a-110">如果列舉的目的是要代表位位置, 您也應該使用[Flags](xref:System.FlagsAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="9417a-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="9417a-111">列舉的基礎類型取決於所使用的常值, 因此, 您可以針對不帶正負號的整數 ( `1u` `uint32`) 類型, 使用具有後置字元`2u`的常值, 例如、等等。</span><span class="sxs-lookup"><span data-stu-id="9417a-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="9417a-112">當您參考已命名的值時, 您必須使用列舉類型本身的名稱做為辨識符號, 也就是`enum-name.value1`, 而不`value1`只是。</span><span class="sxs-lookup"><span data-stu-id="9417a-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="9417a-113">此行為不同于相異聯集的行為。</span><span class="sxs-lookup"><span data-stu-id="9417a-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="9417a-114">這是因為列舉一律具有[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)屬性。</span><span class="sxs-lookup"><span data-stu-id="9417a-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="9417a-115">下列程式碼顯示列舉的宣告和使用。</span><span class="sxs-lookup"><span data-stu-id="9417a-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="9417a-116">您可以使用適當的運算子, 輕鬆地將列舉轉換成基礎類型, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9417a-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="9417a-117">列舉型別可以具有下列其中一種基礎類型`sbyte`: `byte`、 `int16` `int64`、 `uint16`、 `int32`、 `uint32`、 `uint16` `uint64`、、、和`char`。</span><span class="sxs-lookup"><span data-stu-id="9417a-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="9417a-118">列舉類型會在 .NET Framework 中表示為繼承自`System.Enum`的類型, 而後者又繼承自。 `System.ValueType`</span><span class="sxs-lookup"><span data-stu-id="9417a-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="9417a-119">因此, 它們是位於堆疊上或內嵌于包含物件中的實數值型別, 而基礎類型的任何值都是列舉的有效值。</span><span class="sxs-lookup"><span data-stu-id="9417a-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="9417a-120">這在使用列舉值進行模式比對時很重要, 因為您必須提供可攔截未命名值的模式。</span><span class="sxs-lookup"><span data-stu-id="9417a-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="9417a-121">連結`enum` F#庫中的函式可以用來產生列舉值, 甚至是其中一個預先定義的已命名值以外的值。</span><span class="sxs-lookup"><span data-stu-id="9417a-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="9417a-122">您可以使用`enum`函數, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="9417a-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="9417a-123">預設`enum`函式可與類型`int32`搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9417a-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="9417a-124">因此, 它不能與具有其他基礎類型的列舉類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9417a-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="9417a-125">相反地, 請使用下列。</span><span class="sxs-lookup"><span data-stu-id="9417a-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="9417a-126">此外, 列舉的案例一律會以的`public`形式發出。</span><span class="sxs-lookup"><span data-stu-id="9417a-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="9417a-127">這是為了讓它們與C# .net 平臺的其餘部分一致。</span><span class="sxs-lookup"><span data-stu-id="9417a-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="9417a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9417a-128">See also</span></span>

- [<span data-ttu-id="9417a-129">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="9417a-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9417a-130">轉型和轉換</span><span class="sxs-lookup"><span data-stu-id="9417a-130">Casting and Conversions</span></span>](casting-and-conversions.md)
