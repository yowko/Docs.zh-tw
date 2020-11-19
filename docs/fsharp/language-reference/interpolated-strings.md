---
title: 插入字串
description: '瞭解內插字串，這是一種特殊形式的字串，可讓您直接在其中內嵌 F # 運算式。'
ms.date: 11/12/2020
ms.openlocfilehash: 8c552b44cea7d6c51ec333b6bdd4d407c6f10da7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829683"
---
# <a name="interpolated-strings"></a><span data-ttu-id="f1216-103">插入字串</span><span class="sxs-lookup"><span data-stu-id="f1216-103">Interpolated strings</span></span>

<span data-ttu-id="f1216-104">內插字串是可讓您在其中內嵌 F # 運算式的 [字串](strings.md) 。</span><span class="sxs-lookup"><span data-stu-id="f1216-104">Interpolated strings are [strings](strings.md) that allow you to embed F# expressions into them.</span></span> <span data-ttu-id="f1216-105">它們在各種案例中很有用，因為字串值可能會根據值或運算式的結果而變更。</span><span class="sxs-lookup"><span data-stu-id="f1216-105">They are helpful in a wide range of scenarios where the value of a string may change based on the result of a value or expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1216-106">語法</span><span class="sxs-lookup"><span data-stu-id="f1216-106">Syntax</span></span>

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a><span data-ttu-id="f1216-107">備註</span><span class="sxs-lookup"><span data-stu-id="f1216-107">Remarks</span></span>

<span data-ttu-id="f1216-108">插補字串可讓您在字串常值內的「漏洞」內撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1216-108">Interpolated strings let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="f1216-109">以下是基本範例：</span><span class="sxs-lookup"><span data-stu-id="f1216-109">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="f1216-110">每個 `{}` 大括弧配對之間的內容可以是任何 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="f1216-110">The contents in between each `{}` brace pair can be any F# expression.</span></span>

<span data-ttu-id="f1216-111">若要對大括弧組進行換用 `{}` ，請撰寫兩個括弧，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f1216-111">To escape a `{}` brace pair, write two of them like so:</span></span>

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a><span data-ttu-id="f1216-112">具類型的插入字串</span><span class="sxs-lookup"><span data-stu-id="f1216-112">Typed interpolated strings</span></span>

<span data-ttu-id="f1216-113">插入字串也可以有 F # 格式規範來強制執行型別安全。</span><span class="sxs-lookup"><span data-stu-id="f1216-113">Interpolated strings can also have F# format specifiers to enforce type safety.</span></span>

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="f1216-114">在上述範例中，程式碼會錯誤 `age` 地傳遞值 `name` ，其中應該是，反之亦然/反之亦然。</span><span class="sxs-lookup"><span data-stu-id="f1216-114">In the previous example, the code mistakenly passes the `age` value where `name` should be, and vice/versa.</span></span> <span data-ttu-id="f1216-115">因為插入字串使用格式規範，所以這是編譯錯誤，而不是微妙的執行時間 bug。</span><span class="sxs-lookup"><span data-stu-id="f1216-115">Because the interpolated strings use format specifiers, this is a compile error instead of a subtle runtime bug.</span></span>

<span data-ttu-id="f1216-116">[純文字格式](plaintext-formatting.md)中涵蓋的所有格式規範都是在插入字串內有效。</span><span class="sxs-lookup"><span data-stu-id="f1216-116">All format specifiers covered in [plaintext formatting](plaintext-formatting.md) are valid inside of an interpolated string.</span></span>

## <a name="verbatim-interpolated-strings"></a><span data-ttu-id="f1216-117">逐字插補字串</span><span class="sxs-lookup"><span data-stu-id="f1216-117">Verbatim interpolated strings</span></span>

<span data-ttu-id="f1216-118">F # 支援以三個引號括住的逐字字串，讓您可以內嵌字串常值。</span><span class="sxs-lookup"><span data-stu-id="f1216-118">F# supports verbatim interpolated strings with triple quotes so that you can embed string literals.</span></span>

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a><span data-ttu-id="f1216-119">對齊內插字串中的運算式</span><span class="sxs-lookup"><span data-stu-id="f1216-119">Aligning expressions in interpolated strings</span></span>

<span data-ttu-id="f1216-120">您可以在插入字串內將運算式靠左對齊或靠右對齊 `|` ，以及指定多少空間。</span><span class="sxs-lookup"><span data-stu-id="f1216-120">You can left-align or right-align expressions inside interpolated strings with `|` and a specification of how many spaces.</span></span> <span data-ttu-id="f1216-121">下列插入字串會將左邊和右邊的運算式分別靠左和向右對齊七個空格。</span><span class="sxs-lookup"><span data-stu-id="f1216-121">The following interpolated string aligns the left and right expressions to the left and right, respectively, by seven spaces.</span></span>

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a><span data-ttu-id="f1216-122">字串插值和 `FormattableString` 格式</span><span class="sxs-lookup"><span data-stu-id="f1216-122">Interpolated strings and `FormattableString` formatting</span></span>

<span data-ttu-id="f1216-123">您也可以套用遵守下列規則的格式 <xref:System.FormattableString> ：</span><span class="sxs-lookup"><span data-stu-id="f1216-123">You can also apply formatting that adheres to the rules for <xref:System.FormattableString>:</span></span>

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

<span data-ttu-id="f1216-124">此外，您也可以透過類型注釋，將內插字串的類型檢查成 a <xref:System.FormattableString> ：</span><span class="sxs-lookup"><span data-stu-id="f1216-124">Additionally, an interpolated string can also be type checked as a <xref:System.FormattableString> via a type annotation:</span></span>

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

<span data-ttu-id="f1216-125">請注意，類型注釋必須在插入字串運算式本身。</span><span class="sxs-lookup"><span data-stu-id="f1216-125">Note that the type annotation must be on the interpolated string expression itself.</span></span> <span data-ttu-id="f1216-126">F # 不會以隱含方式將內插字串轉換成 <xref:System.FormattableString> 。</span><span class="sxs-lookup"><span data-stu-id="f1216-126">F# does not implicitly convert an interpolated string into a <xref:System.FormattableString>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1216-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1216-127">See also</span></span>

* [<span data-ttu-id="f1216-128">字串</span><span class="sxs-lookup"><span data-stu-id="f1216-128">Strings</span></span>](strings.md)
