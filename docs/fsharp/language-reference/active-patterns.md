---
title: "作用中的模式 (F#)"
description: "了解如何定義具名細分 F # 程式語言中的輸入的資料的資料分割使用作用中的模式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 11a724ff-f9ff-4056-b5e0-87e9ed986f4a
ms.openlocfilehash: 845184e6150cf0b93393038ca3d39f0e6d898a2e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="active-patterns"></a><span data-ttu-id="2a2f8-104">現用模式</span><span class="sxs-lookup"><span data-stu-id="2a2f8-104">Active Patterns</span></span>

<span data-ttu-id="2a2f8-105">*現用模式*讓您定義具名的資料分割細分輸入的資料，好讓您可以使用這些名稱在模式比對運算式一樣，差別等位的。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-105">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="2a2f8-106">您可以使用作用中的模式，以自訂方式分解每個部分的資料。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-106">You can use active patterns to decompose data in a customized manner for each partition.</span></span>


## <a name="syntax"></a><span data-ttu-id="2a2f8-107">語法</span><span class="sxs-lookup"><span data-stu-id="2a2f8-107">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="2a2f8-108">備註</span><span class="sxs-lookup"><span data-stu-id="2a2f8-108">Remarks</span></span>
<span data-ttu-id="2a2f8-109">在上一個語法中的識別項是輸入所表示之資料分割的名稱*引數*，或，也就是說，針對一組引數的所有值的子集的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-109">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="2a2f8-110">現用模式定義中可以有最多七個資料分割。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-110">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="2a2f8-111">*運算式*說明用來將資料分解成表單。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-111">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="2a2f8-112">現用模式定義可用來定義規則，以判斷其中一個具名的資料分割指定為引數屬於的值。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-112">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="2a2f8-113">(| 和 |) 的符號指*banana 短片*，這種類型的 let 繫結所建立的函式稱為*現用辨識器*。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-113">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="2a2f8-114">例如，請考慮下列的現用模式的引數。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-114">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="2a2f8-115">您可以使用現用模式中的模式比對運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-115">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="2a2f8-116">這個程式的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a2f8-116">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="2a2f8-117">現用模式的另一個用途是分解以多種方式，例如當相同的基礎資料有可能的各種表示相互轉換的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-117">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="2a2f8-118">例如，`Color`物件無法分解成代表的 RGB 或 HSB 表示法。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-118">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="2a2f8-119">上述程式的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a2f8-119">The output of the above program is as follows:</span></span>

```
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

<span data-ttu-id="2a2f8-120">在組合，這兩種方式使用使用中模式的資料分割可讓您將資料分解成適當的表單並在最方便的計算表單中的適當資料上執行適當的計算。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-120">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="2a2f8-121">產生的模式比對運算式啟用便利的方式，是很容易閱讀，大幅簡化的潛在的複雜分支 」 和 「 資料分析程式碼中撰寫的資料。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-121">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>


## <a name="partial-active-patterns"></a><span data-ttu-id="2a2f8-122">部分現用模式</span><span class="sxs-lookup"><span data-stu-id="2a2f8-122">Partial Active Patterns</span></span>
<span data-ttu-id="2a2f8-123">有時候，您需要資料分割中只有部分輸入的空間。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-123">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="2a2f8-124">在此情況下，您撰寫一組部分模式，其中符合某些輸入，但無法比對其他輸入。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-124">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="2a2f8-125">作用中永遠不會產生值的模式稱為*部分現用模式*; 它們具有傳回值的選項類型。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-125">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="2a2f8-126">若要定義部分的現用模式，您可以使用萬用字元 (_) 內 banana 短片模式的清單結尾處。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-126">To define a partial active pattern, you use a wildcard character (_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="2a2f8-127">下列程式碼說明如何使用部分的現用模式。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-127">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="2a2f8-128">前一個範例的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a2f8-128">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="2a2f8-129">當使用部分現用模式時，有時個別選擇可以脫離或互斥的但它們不需要是。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-129">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="2a2f8-130">在下列範例中，模式平方和 Cube 的模式不是脫離的因為一些數字是平方和 cube，例如 64。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-130">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="2a2f8-131">下列程式會列印出所有整數最多 1000000 的平方和 cube。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-131">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="2a2f8-132">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="2a2f8-132">The output is as follows:</span></span>

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="2a2f8-133">參數化的現用模式</span><span class="sxs-lookup"><span data-stu-id="2a2f8-133">Parameterized Active Patterns</span></span>
<span data-ttu-id="2a2f8-134">作用中的模式都需要至少一個引數的項目相符，但它們可能需要其他引數，在此情況下名稱*參數化的現用模式*套用。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="2a2f8-135">其他引數可讓一般模式將特製化。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="2a2f8-136">例如，作用中的模式，可用於規則運算式剖析字串通常包含規則運算式做為額外的參數，如下列程式碼，也會使用部分現用模式`Integer`先前的程式碼範例中所定義。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="2a2f8-137">在此範例中，使用規則運算式進行各種日期格式的字串給自訂一般 ParseRegex 現用模式。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="2a2f8-138">整數現用模式用來比對的字串轉換為可以傳遞給 DateTime 建構函式的整數。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="2a2f8-139">先前的程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a2f8-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="2a2f8-140">現用模式不只限於模式比對運算式，您也可以使用它們 let 繫結上。</span><span class="sxs-lookup"><span data-stu-id="2a2f8-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="2a2f8-141">先前的程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a2f8-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="2a2f8-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a2f8-142">See Also</span></span>
[<span data-ttu-id="2a2f8-143">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="2a2f8-143">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="2a2f8-144">比對運算式</span><span class="sxs-lookup"><span data-stu-id="2a2f8-144">Match Expressions</span></span>](match-expressions.md)

