---
title: "類型縮寫 (F#)"
description: "深入了解 F # 類型縮寫來提供型別更有意義的名稱以使程式碼更容易讀取。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a><span data-ttu-id="9bb6c-104">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="9bb6c-104">Type Abbreviations</span></span>

<span data-ttu-id="9bb6c-105">A*類型縮寫*是別名或替代名稱的類型。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-105">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bb6c-106">語法</span><span class="sxs-lookup"><span data-stu-id="9bb6c-106">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="9bb6c-107">備註</span><span class="sxs-lookup"><span data-stu-id="9bb6c-107">Remarks</span></span>
<span data-ttu-id="9bb6c-108">您可以使用類型縮寫來提供型別更有意義的名稱，以使程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-108">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="9bb6c-109">您也可以使用它們建立易於使用，否則會寫出麻煩型別的名稱。此外，您可以讓您更輕鬆地變更的基礎類型，而不需要變更使用類型的所有程式碼使用類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-109">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="9bb6c-110">以下是簡單類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-110">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="9bb6c-111">類型縮寫可以包含泛型參數，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="9bb6c-112">先前的程式碼，`Transform`是代表任何類型的單一引數的函式類型縮寫，並傳回該相同類型的單一值。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="9bb6c-113">類型縮寫不會保留在.NET Framework MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="9bb6c-114">因此，當您使用 F # 組件從另一種.NET Framework 語言，您必須使用的基礎類型縮寫的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="9bb6c-115">類型縮寫也可用在測量單位。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="9bb6c-116">如需詳細資訊，請參閱[測量單位](units-of-measure.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb6c-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="9bb6c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bb6c-117">See Also</span></span>
[<span data-ttu-id="9bb6c-118">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="9bb6c-118">F# Language Reference</span></span>](index.md)

