---
title: 單位類型
description: 了解如何F#'unit' 類型通常用來保存其中值所需的語言語法所需或預期任何值時的位置。
ms.date: 05/16/2016
ms.openlocfilehash: f1866ff12f36f4f8d3eaa1275551c42fc4ade216
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611980"
---
# <a name="unit-type"></a><span data-ttu-id="5aabc-103">單位類型</span><span class="sxs-lookup"><span data-stu-id="5aabc-103">Unit Type</span></span>

<span data-ttu-id="5aabc-104">`unit`型別是一種類型，表示沒有特定的值;`unit`型別具有只能是單一數值，可做為預留位置，當沒有任何其他值，或不需要。</span><span class="sxs-lookup"><span data-stu-id="5aabc-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="5aabc-105">語法</span><span class="sxs-lookup"><span data-stu-id="5aabc-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="5aabc-106">備註</span><span class="sxs-lookup"><span data-stu-id="5aabc-106">Remarks</span></span>

<span data-ttu-id="5aabc-107">每個F#運算式必須評估為值。</span><span class="sxs-lookup"><span data-stu-id="5aabc-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="5aabc-108">不會產生值感興趣，類型的值，這個值的運算式`unit`用。</span><span class="sxs-lookup"><span data-stu-id="5aabc-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="5aabc-109">`unit`型別類似於`void`C# 和 c + + 等語言中的型別。</span><span class="sxs-lookup"><span data-stu-id="5aabc-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="5aabc-110">`unit`類型具有單一值，而該值由權杖`()`。</span><span class="sxs-lookup"><span data-stu-id="5aabc-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="5aabc-111">值`unit`型別通常會在F#程式設計語言語法中，需要值但所需或預期任何值時，保留位置。</span><span class="sxs-lookup"><span data-stu-id="5aabc-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="5aabc-112">可能的傳回值的範例。`printf`函式。</span><span class="sxs-lookup"><span data-stu-id="5aabc-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="5aabc-113">因為重要的動作`printf`作業發生在函數中，函式沒有傳回實際的值。</span><span class="sxs-lookup"><span data-stu-id="5aabc-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="5aabc-114">因此，傳回的值屬於類型`unit`。</span><span class="sxs-lookup"><span data-stu-id="5aabc-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="5aabc-115">某些建構預期`unit`值。</span><span class="sxs-lookup"><span data-stu-id="5aabc-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="5aabc-116">例如，`do`繫結或最上層模組的任何程式碼必須評估為`unit`值。</span><span class="sxs-lookup"><span data-stu-id="5aabc-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="5aabc-117">編譯器會回報警告時`do`繫結或最上層模組的程式碼產生的結果，而非`unit`未使用，如下列範例所示的值。</span><span class="sxs-lookup"><span data-stu-id="5aabc-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="5aabc-118">這項警告是功能性程式設計; 的特性它不會出現在其他.NET 程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="5aabc-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="5aabc-119">在純綷功能性程式中，在其中函式沒有任何副作用，最終的傳回值會是唯一的函式呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="5aabc-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="5aabc-120">因此，結果會被忽略，時，可能的程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="5aabc-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="5aabc-121">雖然F#不是純綷功能性程式設計語言，它是最好的作法是遵循盡可能的功能性程式設計樣式。</span><span class="sxs-lookup"><span data-stu-id="5aabc-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="5aabc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aabc-122">See also</span></span>

- [<span data-ttu-id="5aabc-123">基本</span><span class="sxs-lookup"><span data-stu-id="5aabc-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="5aabc-124">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="5aabc-124">F# Language Reference</span></span>](index.md)