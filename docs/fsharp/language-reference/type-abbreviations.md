---
title: 類型縮寫 (F#)
description: '深入了解 F # 類型縮寫來提供型別更有意義的名稱以使程式碼更容易讀取。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bf17ee9795947fdc11fe958f09d52f5730b95bf8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="type-abbreviations"></a><span data-ttu-id="d1eb2-103">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="d1eb2-103">Type Abbreviations</span></span>

<span data-ttu-id="d1eb2-104">A*類型縮寫*是別名或替代名稱的類型。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1eb2-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1eb2-105">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="d1eb2-106">備註</span><span class="sxs-lookup"><span data-stu-id="d1eb2-106">Remarks</span></span>
<span data-ttu-id="d1eb2-107">您可以使用類型縮寫來提供型別更有意義的名稱，以使程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="d1eb2-108">您也可以使用它們建立易於使用，否則會寫出麻煩型別的名稱。此外，您可以讓您更輕鬆地變更的基礎類型，而不需要變更使用類型的所有程式碼使用類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="d1eb2-109">以下是簡單類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-109">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="d1eb2-110">類型縮寫可以包含泛型參數，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-110">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="d1eb2-111">先前的程式碼，`Transform`是代表任何類型的單一引數的函式類型縮寫，並傳回該相同類型的單一值。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-111">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="d1eb2-112">類型縮寫不會保留在.NET Framework MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-112">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="d1eb2-113">因此，當您使用 F # 組件從另一種.NET Framework 語言，您必須使用的基礎類型縮寫的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-113">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="d1eb2-114">類型縮寫也可用在測量單位。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-114">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="d1eb2-115">如需詳細資訊，請參閱[測量單位](units-of-measure.md)。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-115">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="d1eb2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1eb2-116">See Also</span></span>
[<span data-ttu-id="d1eb2-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="d1eb2-117">F# Language Reference</span></span>](index.md)

