---
title: 作用中的模式 (F#)
description: '了解如何使用定義細分 F # 程式設計語言中的輸入的資料的具名分割區的作用中的模式。'
ms.date: 05/16/2016
ms.openlocfilehash: 4fb7d3e2b9c7e6f1c1ed9d64a47728c7f40017c8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030638"
---
# <a name="active-patterns"></a><span data-ttu-id="9a596-103">現用模式</span><span class="sxs-lookup"><span data-stu-id="9a596-103">Active Patterns</span></span>

<span data-ttu-id="9a596-104">*作用中的模式*可讓您定義細分輸入的資料的具名資料分割，以便您可以使用這些名稱的模式比對運算式，就像您一樣的已區分的聯集。</span><span class="sxs-lookup"><span data-stu-id="9a596-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="9a596-105">您可以使用作用中的模式，以自訂方式分解每個部分的資料。</span><span class="sxs-lookup"><span data-stu-id="9a596-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a596-106">語法</span><span class="sxs-lookup"><span data-stu-id="9a596-106">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="9a596-107">備註</span><span class="sxs-lookup"><span data-stu-id="9a596-107">Remarks</span></span>

<span data-ttu-id="9a596-108">在先前語法中的識別項是名稱由輸入資料的資料分割*引數*，或者，換句話說，一組引數的所有值的子集的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a596-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="9a596-109">在使用中模式定義中可以有最多七個資料分割。</span><span class="sxs-lookup"><span data-stu-id="9a596-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="9a596-110">*運算式*描述用來將資料分解成表單。</span><span class="sxs-lookup"><span data-stu-id="9a596-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="9a596-111">您可以使用中模式，定義來定義規則，來判斷哪一個具名的資料分割的引數屬於所提供的值。</span><span class="sxs-lookup"><span data-stu-id="9a596-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="9a596-112">(| 和 |) 符號指*香蕉*並建立此類型的 let 繫結的函式會呼叫*作用中的辨識器*。</span><span class="sxs-lookup"><span data-stu-id="9a596-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="9a596-113">例如，請考慮下列的使用中模式，以引數。</span><span class="sxs-lookup"><span data-stu-id="9a596-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="9a596-114">您可以使用中模式的模式比對運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9a596-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="9a596-115">此程式的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a596-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="9a596-116">現用模式的另一個用途是將分解以多種方式，例如當相同的基礎資料有可能的各種表示相互轉換的資料類型。</span><span class="sxs-lookup"><span data-stu-id="9a596-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="9a596-117">比方說，`Color`物件無法分解成 RGB 或 HSB 表示法。</span><span class="sxs-lookup"><span data-stu-id="9a596-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="9a596-118">上述程式的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a596-118">The output of the above program is as follows:</span></span>

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

<span data-ttu-id="9a596-119">在組合，使用作用中模式的這兩種方式可讓您將資料分割將資料分解為適當的表單並最方便的計算表單中的適當資料上執行適當的計算。</span><span class="sxs-lookup"><span data-stu-id="9a596-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="9a596-120">產生的模式比對運算式可讓以便利的方式非常清楚易讀、 可大幅簡化的潛在複雜分支與資料分析程式碼所寫入的資料。</span><span class="sxs-lookup"><span data-stu-id="9a596-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="9a596-121">部分作用中的模式</span><span class="sxs-lookup"><span data-stu-id="9a596-121">Partial Active Patterns</span></span>

<span data-ttu-id="9a596-122">有時候，您需要資料分割的輸入空間的組件。</span><span class="sxs-lookup"><span data-stu-id="9a596-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="9a596-123">在此情況下，您撰寫一組部分模式，其中符合某些輸入，但無法符合其他輸入。</span><span class="sxs-lookup"><span data-stu-id="9a596-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="9a596-124">永遠不會產生值的使用中模式稱為*部分作用中的模式*; 它們有傳回值，選項類型。</span><span class="sxs-lookup"><span data-stu-id="9a596-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="9a596-125">若要定義部分的使用中模式，您可以使用萬用字元 (\_) 的內部香蕉的模式清單結尾。</span><span class="sxs-lookup"><span data-stu-id="9a596-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="9a596-126">下列程式碼說明如何使用部分中的模式。</span><span class="sxs-lookup"><span data-stu-id="9a596-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="9a596-127">上述範例的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a596-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="9a596-128">在使用部分作用中的模式時，有時個別選擇可以是脫離或互斥，但它們不一定要是。</span><span class="sxs-lookup"><span data-stu-id="9a596-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="9a596-129">在下列範例中，模式平方和 Cube 的模式不是脫離的因為一些數字是平方和 cube，例如 64。</span><span class="sxs-lookup"><span data-stu-id="9a596-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="9a596-130">下列程式會列印出所有整數達 1000000 平方和 cube。</span><span class="sxs-lookup"><span data-stu-id="9a596-130">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="9a596-131">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="9a596-131">The output is as follows:</span></span>

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

## <a name="parameterized-active-patterns"></a><span data-ttu-id="9a596-132">參數化現用模式</span><span class="sxs-lookup"><span data-stu-id="9a596-132">Parameterized Active Patterns</span></span>

<span data-ttu-id="9a596-133">作用中的模式一定會採用要比對的項目至少一個引數，但它們可能需要額外的引數，在此情況下名稱*參數化現用模式*套用。</span><span class="sxs-lookup"><span data-stu-id="9a596-133">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="9a596-134">其他引數可讓特製化的一般模式。</span><span class="sxs-lookup"><span data-stu-id="9a596-134">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="9a596-135">比方說，作用中的模式使用規則運算式剖析字串通常包含規則運算式做為額外的參數，如下列程式碼，這也會使用部分的現用模式`Integer`先前的程式碼範例中所定義。</span><span class="sxs-lookup"><span data-stu-id="9a596-135">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="9a596-136">在此範例中，使用規則運算式進行各種不同的日期格式的字串會提供給自訂一般 ParseRegex 現用模式。</span><span class="sxs-lookup"><span data-stu-id="9a596-136">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="9a596-137">整數中的模式用來比對的字串轉換成可以傳遞給 DateTime 建構函式的整數。</span><span class="sxs-lookup"><span data-stu-id="9a596-137">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="9a596-138">先前的程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a596-138">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="9a596-139">作用中的模式不只限於模式比對運算式，您也可以使用它們可讓繫結上。</span><span class="sxs-lookup"><span data-stu-id="9a596-139">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="9a596-140">先前的程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a596-140">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="9a596-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a596-141">See also</span></span>

- [<span data-ttu-id="9a596-142">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="9a596-142">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9a596-143">比對運算式</span><span class="sxs-lookup"><span data-stu-id="9a596-143">Match Expressions</span></span>](match-expressions.md)
