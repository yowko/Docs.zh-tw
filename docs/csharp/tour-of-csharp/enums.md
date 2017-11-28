---
title: "C# 列舉 - C# 語言教學課程"
description: "了解 C# 中的列舉、離散的具名常數。"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 77d315dd87d9cab32605de415674d146eb9115fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="enums"></a><span data-ttu-id="009bd-104">列舉</span><span class="sxs-lookup"><span data-stu-id="009bd-104">Enums</span></span>

<span data-ttu-id="009bd-105">「列舉型別」是含一組具名常數的相異實值型別。</span><span class="sxs-lookup"><span data-stu-id="009bd-105">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="009bd-106">當您需要定義可擁有一組離散值的型別時，便可定義列舉。</span><span class="sxs-lookup"><span data-stu-id="009bd-106">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="009bd-107">它們使用其中一個整數值型別作為其基礎儲存體。</span><span class="sxs-lookup"><span data-stu-id="009bd-107">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="009bd-108">它們會為離散值提供語意意義。</span><span class="sxs-lookup"><span data-stu-id="009bd-108">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="009bd-109">下列範例會宣告並使用名為 `Color` 的 `enum` 型別搭配三個常數值 `Red`、`Green` 及 `Blue`。</span><span class="sxs-lookup"><span data-stu-id="009bd-109">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="009bd-110">每個 `enum` 型別都有對應的整數型別，稱為 `enum` 型別的「基礎型別」。</span><span class="sxs-lookup"><span data-stu-id="009bd-110">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="009bd-111">未明確宣告基礎型別的 `enum` 型別會擁有 `int` 基礎型別。</span><span class="sxs-lookup"><span data-stu-id="009bd-111">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="009bd-112">`enum` 型別的儲存格式和可能的值範圍取決於其基礎型別。</span><span class="sxs-lookup"><span data-stu-id="009bd-112">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="009bd-113">`enum` 型別可接受的一組值並不受其 `enum` 成員限制。</span><span class="sxs-lookup"><span data-stu-id="009bd-113">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="009bd-114">特別是，`enum` 之基礎型別的任何值都可轉換成 `enum` 型別，並且是該 `enum` 型別的相異有效值。</span><span class="sxs-lookup"><span data-stu-id="009bd-114">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="009bd-115">下列範例會宣告一個基礎型別為 `sbyte`、名為 `Alignment` 的 `enum` 型別。</span><span class="sxs-lookup"><span data-stu-id="009bd-115">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="009bd-116">如上一個範例所示，`enum` 成員宣告可以包含會指定成員值的常數運算式。</span><span class="sxs-lookup"><span data-stu-id="009bd-116">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="009bd-117">每個 `enum` 成員的常數值都必須在 `enum` 的基礎型別範圍內。</span><span class="sxs-lookup"><span data-stu-id="009bd-117">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="009bd-118">當 `enum` 成員宣告並未明確指定值時，賦予成員的值會是零 (如果它是 `enum` 型別中的第一個成員) 或是本文上前面 `enum` 成員的值加 1。</span><span class="sxs-lookup"><span data-stu-id="009bd-118">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="009bd-119">您可以使用型別轉換將 `Enum` 值轉換成整數值。</span><span class="sxs-lookup"><span data-stu-id="009bd-119">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="009bd-120">例如: </span><span class="sxs-lookup"><span data-stu-id="009bd-120">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="009bd-121">任何 `enum` 型別的預設值都是轉換成 `enum` 型別的整數值零。</span><span class="sxs-lookup"><span data-stu-id="009bd-121">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="009bd-122">在變數自動初始化成預設值的情況中，這是賦予 `enum` 型別之變數的值。</span><span class="sxs-lookup"><span data-stu-id="009bd-122">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="009bd-123">為了讓 `enum` 型別的預設值可供輕鬆取得，常值 `0` 會隱含地轉換成任何 `enum` 型別。</span><span class="sxs-lookup"><span data-stu-id="009bd-123">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="009bd-124">因此，允許以下的情況。</span><span class="sxs-lookup"><span data-stu-id="009bd-124">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
<span data-ttu-id="009bd-125">[上一頁](interfaces.md)
[下一頁](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="009bd-125">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
