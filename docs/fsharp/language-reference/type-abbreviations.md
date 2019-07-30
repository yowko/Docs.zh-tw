---
title: 類型縮寫
description: 瞭解F#類型縮寫, 為類型提供更有意義的名稱, 以便讓程式碼更容易閱讀。
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630209"
---
# <a name="type-abbreviations"></a><span data-ttu-id="a3d68-103">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="a3d68-103">Type Abbreviations</span></span>

<span data-ttu-id="a3d68-104">*類型縮寫*是類型的別名或替代名稱。</span><span class="sxs-lookup"><span data-stu-id="a3d68-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3d68-105">語法</span><span class="sxs-lookup"><span data-stu-id="a3d68-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="a3d68-106">備註</span><span class="sxs-lookup"><span data-stu-id="a3d68-106">Remarks</span></span>

<span data-ttu-id="a3d68-107">您可以使用類型縮寫來為類型提供更有意義的名稱, 以便讓程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="a3d68-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="a3d68-108">您也可以使用它們來建立容易使用的名稱, 以用於不需要寫出的其他類型。此外, 您可以使用類型縮寫, 讓變更基礎類型變得更容易, 而不需要變更使用該類型的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="a3d68-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="a3d68-109">以下是簡單的類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="a3d68-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="a3d68-110">縮寫類型的存取範圍預設`public`為。</span><span class="sxs-lookup"><span data-stu-id="a3d68-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="a3d68-111">類型縮寫可以包含泛型參數, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a3d68-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="a3d68-112">在先前的程式碼`Transform`中, 是類型縮寫, 代表接受任何類型的單一引數, 並傳回該相同類型之單一值的函式。</span><span class="sxs-lookup"><span data-stu-id="a3d68-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="a3d68-113">類型縮寫不會保留在 .NET Framework 的 MSIL 程式碼中。</span><span class="sxs-lookup"><span data-stu-id="a3d68-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="a3d68-114">因此, 當您使用另F#一個 .NET Framework 語言的元件時, 您必須使用基礎類型名稱做為類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="a3d68-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="a3d68-115">類型縮寫也可以用在測量單位上。</span><span class="sxs-lookup"><span data-stu-id="a3d68-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="a3d68-116">如需詳細資訊, 請參閱[測量單位](units-of-measure.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d68-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3d68-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3d68-117">See also</span></span>

- [<span data-ttu-id="a3d68-118">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a3d68-118">F# Language Reference</span></span>](index.md)
