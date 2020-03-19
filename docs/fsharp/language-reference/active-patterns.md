---
title: 現用模式
description: 瞭解如何使用活動模式定義在 F# 程式設計語言中細分輸入資料的命名分區。
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187064"
---
# <a name="active-patterns"></a><span data-ttu-id="b2f89-103">現用模式</span><span class="sxs-lookup"><span data-stu-id="b2f89-103">Active Patterns</span></span>

<span data-ttu-id="b2f89-104">*活動模式*使您能夠定義細分輸入資料的命名分區，以便可以在模式匹配運算式中使用這些名稱，就像對受歧視聯合一樣。</span><span class="sxs-lookup"><span data-stu-id="b2f89-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="b2f89-105">您可以使用作用中的模式，以自訂方式分解每個部分的資料。</span><span class="sxs-lookup"><span data-stu-id="b2f89-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2f89-106">語法</span><span class="sxs-lookup"><span data-stu-id="b2f89-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="b2f89-107">備註</span><span class="sxs-lookup"><span data-stu-id="b2f89-107">Remarks</span></span>

<span data-ttu-id="b2f89-108">在前面的語法中，識別碼是由*參數*表示的輸入資料分區的名稱，或者換句話說，是參數所有值集的子集的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2f89-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="b2f89-109">活動模式定義中最多隻能有七個分區。</span><span class="sxs-lookup"><span data-stu-id="b2f89-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="b2f89-110">運算式*描述*要將資料分解到的表單。</span><span class="sxs-lookup"><span data-stu-id="b2f89-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="b2f89-111">可以使用活動模式定義定義規則，以確定作為參數給定的值屬於哪個命名分區。</span><span class="sxs-lookup"><span data-stu-id="b2f89-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="b2f89-112">（\* 和 |） 符號稱為*香蕉剪輯*，這種類型的 let 綁定創建的函數稱為*活動識別器*。</span><span class="sxs-lookup"><span data-stu-id="b2f89-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="b2f89-113">例如，請考慮以下具有參數的活動模式。</span><span class="sxs-lookup"><span data-stu-id="b2f89-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="b2f89-114">您可以在模式匹配運算式中使用活動模式，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="b2f89-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="b2f89-115">此程式的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="b2f89-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="b2f89-116">活動模式的另一個用途是以多種方式分解資料類型，例如當同一基礎資料具有各種可能的表示形式時。</span><span class="sxs-lookup"><span data-stu-id="b2f89-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="b2f89-117">例如，`Color`物件可以分解為 RGB 表示形式或滙豐表示形式。</span><span class="sxs-lookup"><span data-stu-id="b2f89-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="b2f89-118">上述程式的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="b2f89-118">The output of the above program is as follows:</span></span>

```console
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="b2f89-119">結合，這兩種使用活動模式的方法使您能夠將資料分區和分解為適當的形式，並在最方便的計算形式中對適當的資料執行適當的計算。</span><span class="sxs-lookup"><span data-stu-id="b2f89-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="b2f89-120">生成的模式匹配運算式使資料能夠以易於讀的便捷方式寫入，從而大大簡化了潛在的複雜分支和資料分析代碼。</span><span class="sxs-lookup"><span data-stu-id="b2f89-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="b2f89-121">部分活動模式</span><span class="sxs-lookup"><span data-stu-id="b2f89-121">Partial Active Patterns</span></span>

<span data-ttu-id="b2f89-122">有時，您只需要分區部分輸入空間。</span><span class="sxs-lookup"><span data-stu-id="b2f89-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="b2f89-123">在這種情況下，您編寫一組部分模式，每個模式與某些輸入匹配，但無法匹配其他輸入。</span><span class="sxs-lookup"><span data-stu-id="b2f89-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="b2f89-124">並不總是生成值的活動模式稱為*部分活動模式*;它們具有作為選項類型的傳回值。</span><span class="sxs-lookup"><span data-stu-id="b2f89-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="b2f89-125">要定義部分活動模式，請使用在香蕉夾內模式清單末尾\_的萬用字元 （ ） 。</span><span class="sxs-lookup"><span data-stu-id="b2f89-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="b2f89-126">以下代碼說明了部分活動模式的使用。</span><span class="sxs-lookup"><span data-stu-id="b2f89-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="b2f89-127">上一個示例的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2f89-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="b2f89-128">使用部分活動模式時，有時各個選項可以是脫節的，也可以是互斥的，但它們不需要。</span><span class="sxs-lookup"><span data-stu-id="b2f89-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="b2f89-129">在下面的示例中，模式方形和模式立方體並不脫節，因為某些數位既是正方形，也是立方體，如 64。</span><span class="sxs-lookup"><span data-stu-id="b2f89-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="b2f89-130">以下程式使用 AND 模式組合方形和立方體模式。</span><span class="sxs-lookup"><span data-stu-id="b2f89-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="b2f89-131">它列印出所有整數最多 1000 個，這些整數既是正方形和立方體，也是僅多維資料集的整數。</span><span class="sxs-lookup"><span data-stu-id="b2f89-131">It prints out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="b2f89-132">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2f89-132">The output is as follows:</span></span>

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="b2f89-133">參數化活動模式</span><span class="sxs-lookup"><span data-stu-id="b2f89-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="b2f89-134">活動模式始終對要匹配的項至少採用一個參數，但它們也可能採用其他參數，在這種情況下，名稱*參數化的活動模式*適用。</span><span class="sxs-lookup"><span data-stu-id="b2f89-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="b2f89-135">其他參數允許將常規模式專門化。</span><span class="sxs-lookup"><span data-stu-id="b2f89-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="b2f89-136">例如，使用正則運算式解析字串的活動模式通常包括正則運算式作為額外參數，如以下代碼，該代碼還使用前一個代碼示例中定義的部分活動模式`Integer`。</span><span class="sxs-lookup"><span data-stu-id="b2f89-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="b2f89-137">在此示例中，為各種日期格式提供正則運算式的字串用於自訂常規 ParseRegex 活動模式。</span><span class="sxs-lookup"><span data-stu-id="b2f89-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="b2f89-138">整數活動模式用於將匹配的字串轉換為可傳遞給 DateTime 建構函式的整數。</span><span class="sxs-lookup"><span data-stu-id="b2f89-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="b2f89-139">前一個代碼的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="b2f89-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="b2f89-140">活動模式不僅局限于模式匹配運算式，還可以在 let 綁定上使用它們。</span><span class="sxs-lookup"><span data-stu-id="b2f89-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="b2f89-141">前一個代碼的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="b2f89-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="b2f89-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2f89-142">See also</span></span>

- [<span data-ttu-id="b2f89-143">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="b2f89-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b2f89-144">比對運算式</span><span class="sxs-lookup"><span data-stu-id="b2f89-144">Match Expressions</span></span>](match-expressions.md)
