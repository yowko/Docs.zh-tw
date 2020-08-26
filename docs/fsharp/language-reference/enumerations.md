---
title: 列舉
description: '瞭解如何使用 F # 列舉來取代常值，讓您的程式碼更容易讀取和維護。'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812103"
---
# <a name="enumerations"></a><span data-ttu-id="0c7a7-103">列舉</span><span class="sxs-lookup"><span data-stu-id="0c7a7-103">Enumerations</span></span>

<span data-ttu-id="0c7a7-104">列舉也稱為*列舉，這*是將標籤指派給值子集的整數類資料類型。 *enums*</span><span class="sxs-lookup"><span data-stu-id="0c7a7-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="0c7a7-105">列舉可用來取代常值，讓程式碼更容易閱讀及維護。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c7a7-106">語法</span><span class="sxs-lookup"><span data-stu-id="0c7a7-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="0c7a7-107">備註</span><span class="sxs-lookup"><span data-stu-id="0c7a7-107">Remarks</span></span>

<span data-ttu-id="0c7a7-108">列舉看起來很像是具有簡單值的差異聯集，不同之處在于可以指定值。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="0c7a7-109">這些值通常是從0或1開始的整數，或是代表位位置的整數。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="0c7a7-110">如果列舉的目的是要代表位位置，您也應該使用 [旗標](xref:System.FlagsAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="0c7a7-111">列舉的基礎類型取決於所使用的常值，因此，例如，您可以針對不帶正負號的 `1u` `2u` 整數 () 類型，使用具有尾碼的常值（例如、等） `uint32` 。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="0c7a7-112">當您參考命名值時，您必須使用列舉型別本身的名稱做為辨識符號，也就是，而 `enum-name.value1` 不只是 `value1` 。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="0c7a7-113">這種行為與不同聯集的行為不同。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="0c7a7-114">這是因為列舉一律具有 [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-114">This is because enumerations always have the [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) attribute.</span></span>

<span data-ttu-id="0c7a7-115">下列程式碼顯示列舉和使用列舉。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="0c7a7-116">您可以使用適當的運算子輕鬆地將列舉轉換成基礎型別，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="0c7a7-117">列舉類型可以具有下列其中一個基礎類型： `sbyte` 、 `byte` 、 `int16` 、 `uint16` 、、、、、 `int32` `uint32` `int64` `uint16` `uint64` 和 `char` 。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="0c7a7-118">列舉型別會在 .NET Framework 中表示為繼承自的型別，而繼承自的類型 `System.Enum` `System.ValueType` 。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="0c7a7-119">因此，它們是位於堆疊上或內嵌于包含物件中的實值型別，而基礎類型的任何值都是列舉的有效值。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="0c7a7-120">這在對列舉值進行模式比對時很重要，因為您必須提供可攔截未命名值的模式。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="0c7a7-121">`enum`F # 程式庫中的函式可用來產生列舉值，甚至是除了其中一個預先定義的命名值以外的值。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="0c7a7-122">您可以使用 `enum` 如下所示的函數。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="0c7a7-123">預設 `enum` 函數適用于類型 `int32` 。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="0c7a7-124">因此，它不能搭配具有其他基礎類型的列舉類型使用。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="0c7a7-125">請改用下列各項。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="0c7a7-126">此外，列舉的案例一律會發出為 `public` 。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="0c7a7-127">這是為了使其符合 c # 和 .NET 平臺的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="0c7a7-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c7a7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7a7-128">See also</span></span>

- [<span data-ttu-id="0c7a7-129">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="0c7a7-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0c7a7-130">轉型和轉換</span><span class="sxs-lookup"><span data-stu-id="0c7a7-130">Casting and Conversions</span></span>](casting-and-conversions.md)
