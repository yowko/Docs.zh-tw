---
title: 類型縮寫
description: 深入了解F#類型可以提供更有意義的名稱以使程式碼更容易讀取的縮寫。
ms.date: 05/16/2016
ms.openlocfilehash: 0deaef789367aad413e5a537bf7164034e1275c0
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613345"
---
# <a name="type-abbreviations"></a><span data-ttu-id="fb060-103">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="fb060-103">Type Abbreviations</span></span>

<span data-ttu-id="fb060-104">A*類型縮寫*是別名或替代名稱的型別。</span><span class="sxs-lookup"><span data-stu-id="fb060-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb060-105">語法</span><span class="sxs-lookup"><span data-stu-id="fb060-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="fb060-106">備註</span><span class="sxs-lookup"><span data-stu-id="fb060-106">Remarks</span></span>

<span data-ttu-id="fb060-107">您可以使用類型縮寫可以提供更有意義的名稱，以使程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="fb060-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="fb060-108">您也可以使用它們來建立簡單易用的類型，否則就會很麻煩，寫出名稱。此外，您可以使用類型縮寫，讓您更輕鬆地變更的基礎類型，而不需要變更使用類型的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="fb060-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="fb060-109">以下是簡單類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="fb060-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="fb060-110">類型縮寫的存取範圍預設為`public`。</span><span class="sxs-lookup"><span data-stu-id="fb060-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="fb060-111">類型縮寫可以包含一般的參數，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="fb060-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="fb060-112">在先前的程式碼`Transform`是類型縮寫表示接受任何類型的單一引數的函式並傳回該相同型別的單一值。</span><span class="sxs-lookup"><span data-stu-id="fb060-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="fb060-113">在.NET Framework MSIL 程式碼中，不會保留類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="fb060-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="fb060-114">因此，當您使用F#組件從另一種.NET Framework 語言，您必須使用類型縮寫的基礎類型名稱。</span><span class="sxs-lookup"><span data-stu-id="fb060-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="fb060-115">類型縮寫也可用的量值單位上。</span><span class="sxs-lookup"><span data-stu-id="fb060-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="fb060-116">如需詳細資訊，請參閱 <<c0> [ 量值單位](units-of-measure.md)。</span><span class="sxs-lookup"><span data-stu-id="fb060-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb060-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb060-117">See also</span></span>

- [<span data-ttu-id="fb060-118">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="fb060-118">F# Language Reference</span></span>](index.md)