---
title: 單位類型
description: F#瞭解「單位」類型通常用來存放語言語法在不需要任何值或需要時需要值的位置。
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630170"
---
# <a name="unit-type"></a><span data-ttu-id="86926-103">單位類型</span><span class="sxs-lookup"><span data-stu-id="86926-103">Unit Type</span></span>

<span data-ttu-id="86926-104">類型是一種類型, 表示沒有特定的值。此`unit`類型只有單一值, 當沒有其他值存在或需要時, 會做為預留位置。 `unit`</span><span class="sxs-lookup"><span data-stu-id="86926-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="86926-105">語法</span><span class="sxs-lookup"><span data-stu-id="86926-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="86926-106">備註</span><span class="sxs-lookup"><span data-stu-id="86926-106">Remarks</span></span>

<span data-ttu-id="86926-107">每F#個運算式都必須評估為值。</span><span class="sxs-lookup"><span data-stu-id="86926-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="86926-108">若為不會產生相關值的運算式, 則會使用類型`unit`的值。</span><span class="sxs-lookup"><span data-stu-id="86926-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="86926-109">類型類似于C#和`void` C++等語言中的類型。 `unit`</span><span class="sxs-lookup"><span data-stu-id="86926-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="86926-110">此`unit`類型具有單一值, 且該值是由標記`()`表示。</span><span class="sxs-lookup"><span data-stu-id="86926-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="86926-111">`unit`類型的值通常用於程式F#設計, 以保存語言語法需要值的位置, 但不需要或不需要任何值時。</span><span class="sxs-lookup"><span data-stu-id="86926-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="86926-112">範例可能是`printf`函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="86926-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="86926-113">因為作業的重要動作`printf`會在函式中發生, 所以函式不需要傳回實際的值。</span><span class="sxs-lookup"><span data-stu-id="86926-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="86926-114">因此, 傳回值的類型`unit`為。</span><span class="sxs-lookup"><span data-stu-id="86926-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="86926-115">某些結構預期會`unit`有值。</span><span class="sxs-lookup"><span data-stu-id="86926-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="86926-116">例如, 位於模組`do`最上層的系結或任何程式碼, 都應該評估`unit`為值。</span><span class="sxs-lookup"><span data-stu-id="86926-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="86926-117">當模組最上層的系結`do`或程式碼產生的結果`unit`不是未使用的值時, 編譯器會報告警告, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="86926-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="86926-118">此警告是功能性程式設計的特性;它不會出現在其他 .NET 程式設計語言中。</span><span class="sxs-lookup"><span data-stu-id="86926-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="86926-119">在純粹功能的程式中, 函式沒有任何副作用, 最後傳回的值是函式呼叫的唯一結果。</span><span class="sxs-lookup"><span data-stu-id="86926-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="86926-120">因此, 忽略結果時, 可能是程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="86926-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="86926-121">雖然F#不是純粹的功能性程式設計語言, 但最好是盡可能遵循功能性程式設計風格。</span><span class="sxs-lookup"><span data-stu-id="86926-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="86926-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86926-122">See also</span></span>

- [<span data-ttu-id="86926-123">橢圓</span><span class="sxs-lookup"><span data-stu-id="86926-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="86926-124">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="86926-124">F# Language Reference</span></span>](index.md)
