---
title: "單位類型 (F#)"
description: "了解 F # 'unit' 型別通常如何使用保留值需要的語言語法所需或預期任何值時的位置。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: eabbb6d7-80f3-4fa5-80b4-0f48982466a7
ms.openlocfilehash: 60ac08c0e3f8380a8f9dec7a083ede93c68bb0e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="unit-type"></a><span data-ttu-id="79b77-104">單位類型</span><span class="sxs-lookup"><span data-stu-id="79b77-104">Unit Type</span></span>

<span data-ttu-id="79b77-105">`unit`類型是類型，指出特定的值; 不存在`unit`類型具有只有單一值，當沒有其他值存在，或是否需要做為預留位置。</span><span class="sxs-lookup"><span data-stu-id="79b77-105">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="79b77-106">語法</span><span class="sxs-lookup"><span data-stu-id="79b77-106">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="79b77-107">備註</span><span class="sxs-lookup"><span data-stu-id="79b77-107">Remarks</span></span>
<span data-ttu-id="79b77-108">每個 F # 運算式必須評估為值。</span><span class="sxs-lookup"><span data-stu-id="79b77-108">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="79b77-109">不會產生值感興趣，類型的值，這個值的運算式`unit`用。</span><span class="sxs-lookup"><span data-stu-id="79b77-109">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="79b77-110">`unit`類型類似於`void`C# 和 c + + 等語言中的類型。</span><span class="sxs-lookup"><span data-stu-id="79b77-110">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="79b77-111">`unit`類型具有單一值，而且該值會指出語彙基元所`()`。</span><span class="sxs-lookup"><span data-stu-id="79b77-111">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="79b77-112">值`unit`類型通常用在 F # 的程式設計語言語法，所需有一個值，但所需或預期任何值時，保留位置。</span><span class="sxs-lookup"><span data-stu-id="79b77-112">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="79b77-113">可能的傳回值的範例。`printf`函式。</span><span class="sxs-lookup"><span data-stu-id="79b77-113">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="79b77-114">因為重要的動作`printf`作業發生在函數中，函式沒有傳回實際的值。</span><span class="sxs-lookup"><span data-stu-id="79b77-114">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="79b77-115">因此，傳回的值屬於型別`unit`。</span><span class="sxs-lookup"><span data-stu-id="79b77-115">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="79b77-116">有些建構預期`unit`值。</span><span class="sxs-lookup"><span data-stu-id="79b77-116">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="79b77-117">例如，`do`繫結或最上層模組的任何程式碼必須評估為`unit`值。</span><span class="sxs-lookup"><span data-stu-id="79b77-117">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="79b77-118">編譯器會回報警告時`do`繫結或在模組的最上層的程式碼會產生結果以外`unit`未使用，如下列範例所示的值。</span><span class="sxs-lookup"><span data-stu-id="79b77-118">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="79b77-119">這項警告是功能性程式設計; 的特性它不會出現在其他.NET 程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="79b77-119">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="79b77-120">在純粹功能的程式中，在其中函式沒有任何副作用，最終的傳回值會是函式呼叫的唯一結果。</span><span class="sxs-lookup"><span data-stu-id="79b77-120">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="79b77-121">因此，當結果會被忽略，就可能發生程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="79b77-121">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="79b77-122">雖然 F # 不是純功能性程式設計語言，它是最好的作法是遵循盡可能的功能性程式設計方式。</span><span class="sxs-lookup"><span data-stu-id="79b77-122">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="79b77-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79b77-123">See Also</span></span>
[<span data-ttu-id="79b77-124">基本</span><span class="sxs-lookup"><span data-stu-id="79b77-124">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="79b77-125">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="79b77-125">F# Language Reference</span></span>](index.md)
