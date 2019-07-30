---
title: 現用模式
description: 瞭解如何使用現用模式來定義以程式F#設計語言細分輸入資料的命名分割區。
ms.date: 05/16/2016
ms.openlocfilehash: 12f423abe05e649e0b527ed04124b991feb5d592
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629957"
---
# <a name="active-patterns"></a><span data-ttu-id="cd104-103">現用模式</span><span class="sxs-lookup"><span data-stu-id="cd104-103">Active Patterns</span></span>

<span data-ttu-id="cd104-104">*現用模式*可讓您定義用來細分輸入資料的命名分割, 如此一來, 您就可以在模式比對運算式中使用這些名稱, 就像您針對區分聯集所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="cd104-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="cd104-105">您可以使用作用中的模式，以自訂方式分解每個部分的資料。</span><span class="sxs-lookup"><span data-stu-id="cd104-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd104-106">語法</span><span class="sxs-lookup"><span data-stu-id="cd104-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="cd104-107">備註</span><span class="sxs-lookup"><span data-stu-id="cd104-107">Remarks</span></span>

<span data-ttu-id="cd104-108">在先前的語法中, 識別碼是以*引數*表示之輸入資料的資料分割名稱, 換句話說, 是引數的所有值集合的子集名稱。</span><span class="sxs-lookup"><span data-stu-id="cd104-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="cd104-109">現用模式定義中最多可以有七個數據分割。</span><span class="sxs-lookup"><span data-stu-id="cd104-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="cd104-110">*運算式*描述要將資料分解成的表單。</span><span class="sxs-lookup"><span data-stu-id="cd104-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="cd104-111">您可以使用現用模式定義來定義規則, 以判斷指定為引數的值屬於哪些已命名的分割區。</span><span class="sxs-lookup"><span data-stu-id="cd104-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="cd104-112">(| 和 |) 符號稱為*香蕉剪輯*, 而這種類型的 let 系結所建立的函式稱為作用中辨識*器*。</span><span class="sxs-lookup"><span data-stu-id="cd104-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="cd104-113">例如, 請考慮下列具有引數的現用模式。</span><span class="sxs-lookup"><span data-stu-id="cd104-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="cd104-114">您可以使用模式比對運算式中的現用模式, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cd104-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="cd104-115">此程式的輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="cd104-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="cd104-116">使用中模式的另一種用法是以多種方式分解資料類型, 例如, 當相同的基礎資料有各種可能的標記法時。</span><span class="sxs-lookup"><span data-stu-id="cd104-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="cd104-117">例如, `Color`物件可能會分解成 RGB 標記法或 HSB 標記法。</span><span class="sxs-lookup"><span data-stu-id="cd104-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="cd104-118">上述程式的輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="cd104-118">The output of the above program is as follows:</span></span>

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

<span data-ttu-id="cd104-119">結合使用現用模式時, 這兩種方式可讓您將資料分割和分解成適當的形式, 並針對計算最方便的形式, 在適當的資料上執行適當的計算。</span><span class="sxs-lookup"><span data-stu-id="cd104-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="cd104-120">產生的模式比對運算式可讓您以方便閱讀的方式寫入資料, 大幅簡化可能複雜的分支和資料分析程式碼。</span><span class="sxs-lookup"><span data-stu-id="cd104-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="cd104-121">部分現用模式</span><span class="sxs-lookup"><span data-stu-id="cd104-121">Partial Active Patterns</span></span>

<span data-ttu-id="cd104-122">有時候, 您只需要分割部分的輸入空間。</span><span class="sxs-lookup"><span data-stu-id="cd104-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="cd104-123">在這種情況下, 您會撰寫一組符合某些輸入但無法符合其他輸入的部分模式。</span><span class="sxs-lookup"><span data-stu-id="cd104-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="cd104-124">不一定會產生值的現用模式稱為「*部分現用模式*」;它們具有屬於選項類型的傳回值。</span><span class="sxs-lookup"><span data-stu-id="cd104-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="cd104-125">若要定義部分現用模式, 請在香蕉剪輯內的\_模式清單結尾使用萬用字元 ()。</span><span class="sxs-lookup"><span data-stu-id="cd104-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="cd104-126">下列程式碼說明如何使用部分現用模式。</span><span class="sxs-lookup"><span data-stu-id="cd104-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="cd104-127">上一個範例的輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="cd104-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="cd104-128">使用部分現用模式時, 有時個別的選擇可能不相鄰或互斥, 但它們不需要。</span><span class="sxs-lookup"><span data-stu-id="cd104-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="cd104-129">在下列範例中, 模式正方形和模式 Cube 不是連續的, 因為有些數位同時為正方形和 cube, 例如64。</span><span class="sxs-lookup"><span data-stu-id="cd104-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="cd104-130">下列程式會使用和模式來結合正方形和 Cube 模式。</span><span class="sxs-lookup"><span data-stu-id="cd104-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="cd104-131">它會列印出最多1000的所有整數, 其中同時為正方形和 cube, 以及僅為 cube。</span><span class="sxs-lookup"><span data-stu-id="cd104-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span> 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="cd104-132">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="cd104-132">The output is as follows:</span></span>

```
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

## <a name="parameterized-active-patterns"></a><span data-ttu-id="cd104-133">參數化現用模式</span><span class="sxs-lookup"><span data-stu-id="cd104-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="cd104-134">現用模式一律會針對要比對的專案使用至少一個引數, 但它們也可能會採用其他引數, 在此情況下, 會套用*參數化現用模式*的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd104-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="cd104-135">其他引數可讓一般模式特製化。</span><span class="sxs-lookup"><span data-stu-id="cd104-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="cd104-136">例如, 使用正則運算式來剖析字串的現用模式通常會包含正則運算式做為額外的參數, 如下列程式碼所示, 這也會使用`Integer`先前程式碼範例中定義的部分現用模式。</span><span class="sxs-lookup"><span data-stu-id="cd104-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="cd104-137">在此範例中, 會提供使用適用于各種日期格式之正則運算式的字串, 以自訂一般 ParseRegex 現用模式。</span><span class="sxs-lookup"><span data-stu-id="cd104-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="cd104-138">整數現用模式是用來將相符的字串轉換成可傳遞至 DateTime 函數的整數。</span><span class="sxs-lookup"><span data-stu-id="cd104-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="cd104-139">先前程式碼的輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="cd104-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="cd104-140">現用模式不限於模式比對運算式, 您也可以在 let-系結上使用它們。</span><span class="sxs-lookup"><span data-stu-id="cd104-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="cd104-141">先前程式碼的輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="cd104-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="cd104-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd104-142">See also</span></span>

- [<span data-ttu-id="cd104-143">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="cd104-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cd104-144">比對運算式</span><span class="sxs-lookup"><span data-stu-id="cd104-144">Match Expressions</span></span>](match-expressions.md)
