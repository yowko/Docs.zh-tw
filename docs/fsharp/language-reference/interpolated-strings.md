---
title: 插入字串
description: '瞭解內插字串，這是一種特殊形式的字串，可讓您直接在其中內嵌 F # 運算式。'
ms.date: 11/12/2020
ms.openlocfilehash: a49d4e743306fd9bdabb1e019ec4e6c77e0e1f5a
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688596"
---
# <a name="interpolated-strings"></a><span data-ttu-id="9f2b4-103">插入字串</span><span class="sxs-lookup"><span data-stu-id="9f2b4-103">Interpolated strings</span></span>

<span data-ttu-id="9f2b4-104">內插字串是可讓您在其中內嵌 F # 運算式的 [字串](strings.md) 。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-104">Interpolated strings are [strings](strings.md) that allow you to embed F# expressions into them.</span></span> <span data-ttu-id="9f2b4-105">它們在各種案例中很有用，因為字串值可能會根據值或運算式的結果而變更。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-105">They are helpful in a wide range of scenarios where the value of a string may change based on the result of a value or expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f2b4-106">語法</span><span class="sxs-lookup"><span data-stu-id="9f2b4-106">Syntax</span></span>

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a><span data-ttu-id="9f2b4-107">備註</span><span class="sxs-lookup"><span data-stu-id="9f2b4-107">Remarks</span></span>

<span data-ttu-id="9f2b4-108">插補字串可讓您在字串常值內的「漏洞」內撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-108">Interpolated strings let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="9f2b4-109">以下是基本範例：</span><span class="sxs-lookup"><span data-stu-id="9f2b4-109">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="9f2b4-110">每個 `{}` 大括弧配對之間的內容可以是任何 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-110">The contents in between each `{}` brace pair can be any F# expression.</span></span>

<span data-ttu-id="9f2b4-111">若要對大括弧組進行換用 `{}` ，請撰寫兩個括弧，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9f2b4-111">To escape a `{}` brace pair, write two of them like so:</span></span>

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a><span data-ttu-id="9f2b4-112">具類型的插入字串</span><span class="sxs-lookup"><span data-stu-id="9f2b4-112">Typed interpolated strings</span></span>

<span data-ttu-id="9f2b4-113">內插字串也可以有 F # 格式規範，以強制執行型別 safey。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-113">Interpolated strings can also have F# format specifiers to enforce type safey.</span></span>

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="9f2b4-114">在上述範例中，程式碼會錯誤 `age` 地傳遞值 `name` ，其中應該是，反之亦然/反之亦然。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-114">In the previous example, the code mistakenly passes the `age` value where `name` should be, and vice/versa.</span></span> <span data-ttu-id="9f2b4-115">因為插入字串使用格式規範，所以這是編譯錯誤，而不是微妙的執行時間 bug。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-115">Because the interpolated strings use format specifiers, this is a compile error instead of a subtle runtime bug.</span></span>

<span data-ttu-id="9f2b4-116">[純文字格式](plaintext-formatting.md)中涵蓋的所有格式規範都是在插入字串內有效。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-116">All format specifiers covered in [plaintext formatting](plaintext-formatting.md) are valid inside of an interpolated string.</span></span>

## <a name="verbatim-interpolated-strings"></a><span data-ttu-id="9f2b4-117">逐字插補字串</span><span class="sxs-lookup"><span data-stu-id="9f2b4-117">Verbatim interpolated strings</span></span>

<span data-ttu-id="9f2b4-118">F # 支援以三個引號括住的逐字字串，讓您可以內嵌字串常值。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-118">F# supports verbatim interpolated strings with triple quotes so that you can embed string literals.</span></span>

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a><span data-ttu-id="9f2b4-119">對齊內插字串中的運算式</span><span class="sxs-lookup"><span data-stu-id="9f2b4-119">Aligning expressions in interpolated strings</span></span>

<span data-ttu-id="9f2b4-120">您可以在插入字串內將運算式靠左對齊或靠右對齊 `|` ，以及指定多少空間。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-120">You can left-align or right-align expressions inside interpolated strings with `|` and a specification of how many spaces.</span></span> <span data-ttu-id="9f2b4-121">下列插入字串會將左邊和右邊的運算式分別靠左和向右對齊7個空格。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-121">The following interpolated string aligns the left and right expressions to the left and right, respectively, by 7  spaces.</span></span>

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a><span data-ttu-id="9f2b4-122">字串插值和 `FormattableString` 格式</span><span class="sxs-lookup"><span data-stu-id="9f2b4-122">Interpolated strings and `FormattableString` formatting</span></span>

<span data-ttu-id="9f2b4-123">您也可以套用遵守下列規則的格式 <xref:System.FormattableString> ：</span><span class="sxs-lookup"><span data-stu-id="9f2b4-123">You can also apply formatting that adheres to the rules for <xref:System.FormattableString>:</span></span>

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

<span data-ttu-id="9f2b4-124">此外，您也可以透過類型注釋，將插入字串 typechecked 為 <xref:System.FormattableString> ：</span><span class="sxs-lookup"><span data-stu-id="9f2b4-124">Additionally, an interpolated string can also be typechecked as a <xref:System.FormattableString> via a type annotation:</span></span>

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

<span data-ttu-id="9f2b4-125">請注意，類型注釋必須在插入字串運算式本身。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-125">Note that the type annotation must be on the interpolated string expression itself.</span></span> <span data-ttu-id="9f2b4-126">F # 不會以隱含方式將內插字串轉換成 <xref:System.FormattableString> 。</span><span class="sxs-lookup"><span data-stu-id="9f2b4-126">F# does not implicitly convert an interpolated string into a <xref:System.FormattableString>.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f2b4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f2b4-127">See also</span></span>

* [<span data-ttu-id="9f2b4-128">字串</span><span class="sxs-lookup"><span data-stu-id="9f2b4-128">Strings</span></span>](strings.md)
