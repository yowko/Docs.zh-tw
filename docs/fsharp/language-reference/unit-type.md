---
title: 單位類型
description: F#瞭解「單位」類型通常用來存放語言語法在不需要任何值或需要時需要值的位置。
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424035"
---
# <a name="unit-type"></a><span data-ttu-id="e4abb-103">單位類型</span><span class="sxs-lookup"><span data-stu-id="e4abb-103">Unit Type</span></span>

<span data-ttu-id="e4abb-104">`unit` 類型是表示沒有特定值的類型。`unit` 類型只有單一值，當沒有其他值存在或需要時，它會作為預留位置。</span><span class="sxs-lookup"><span data-stu-id="e4abb-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4abb-105">語法</span><span class="sxs-lookup"><span data-stu-id="e4abb-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="e4abb-106">備註</span><span class="sxs-lookup"><span data-stu-id="e4abb-106">Remarks</span></span>

<span data-ttu-id="e4abb-107">每F#個運算式都必須評估為值。</span><span class="sxs-lookup"><span data-stu-id="e4abb-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="e4abb-108">若為不會產生相關值的運算式，則會使用 `unit` 類型的值。</span><span class="sxs-lookup"><span data-stu-id="e4abb-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="e4abb-109">`unit` 類型類似于C#和C++等語言中的 `void` 類型。</span><span class="sxs-lookup"><span data-stu-id="e4abb-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="e4abb-110">`unit` 類型具有單一值，且該值是由權杖 `()`所表示。</span><span class="sxs-lookup"><span data-stu-id="e4abb-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="e4abb-111">`unit` 類型的值通常用來進行程式F#設計，以保存語言語法需要值的位置，但不需要任何值或需要時。</span><span class="sxs-lookup"><span data-stu-id="e4abb-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="e4abb-112">範例可能是 `printf` 函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="e4abb-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="e4abb-113">因為 `printf` 作業的重要動作會在函式中發生，所以函式不需要傳回實際的值。</span><span class="sxs-lookup"><span data-stu-id="e4abb-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="e4abb-114">因此，傳回值的類型為 `unit`。</span><span class="sxs-lookup"><span data-stu-id="e4abb-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="e4abb-115">某些結構預期會有 `unit` 值。</span><span class="sxs-lookup"><span data-stu-id="e4abb-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="e4abb-116">例如，`do` 系結或模組最上層的任何程式碼，都應該評估為 `unit` 值。</span><span class="sxs-lookup"><span data-stu-id="e4abb-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="e4abb-117">當模組最上層的 `do` 系結或程式碼產生的結果不是未使用的 `unit` 值時，編譯器會報告警告，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e4abb-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="e4abb-118">此警告是功能性程式設計的特性;它不會出現在其他 .NET 程式設計語言中。</span><span class="sxs-lookup"><span data-stu-id="e4abb-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="e4abb-119">在純粹功能的程式中，函式沒有任何副作用，最後傳回的值是函式呼叫的唯一結果。</span><span class="sxs-lookup"><span data-stu-id="e4abb-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="e4abb-120">因此，忽略結果時，可能是程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="e4abb-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="e4abb-121">雖然F#不是純粹的功能性程式設計語言，但最好是盡可能遵循功能性程式設計風格。</span><span class="sxs-lookup"><span data-stu-id="e4abb-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4abb-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4abb-122">See also</span></span>

- [<span data-ttu-id="e4abb-123">橢圓</span><span class="sxs-lookup"><span data-stu-id="e4abb-123">Primitive</span></span>](basic-types.md)
- [<span data-ttu-id="e4abb-124">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e4abb-124">F# Language Reference</span></span>](index.md)
