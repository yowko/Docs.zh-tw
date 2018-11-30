---
title: 已區分的聯集 (F#)
description: 了解如何使用F#差別聯集。
ms.date: 05/16/2016
ms.openlocfilehash: f833539f2e31ffc6db4182bdbd2088e6dc2bb2cc
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2018
ms.locfileid: "52672241"
---
# <a name="discriminated-unions"></a><span data-ttu-id="29f73-103">已區分的聯集</span><span class="sxs-lookup"><span data-stu-id="29f73-103">Discriminated Unions</span></span>

<span data-ttu-id="29f73-104">差別等位可以是其中一個具名案例數，而每個不同的值和類型的值提供支援。</span><span class="sxs-lookup"><span data-stu-id="29f73-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="29f73-105">差別等位是適用於異質資料，可以有特殊的情況下，包括有效和錯誤案例的資料為另一個，從一個執行個體的型別中改變資料並為小型物件階層架構的替代方式。</span><span class="sxs-lookup"><span data-stu-id="29f73-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="29f73-106">此外，遞迴的已區分聯集用來代表樹狀資料結構。</span><span class="sxs-lookup"><span data-stu-id="29f73-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="29f73-107">語法</span><span class="sxs-lookup"><span data-stu-id="29f73-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="29f73-108">備註</span><span class="sxs-lookup"><span data-stu-id="29f73-108">Remarks</span></span>

<span data-ttu-id="29f73-109">差別聯的集是以其他語言的聯集類型類似，但有一些差異。</span><span class="sxs-lookup"><span data-stu-id="29f73-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="29f73-110">做為與 c + + 中的等位型別或在 Visual Basic 中的變數類型的值中儲存的資料不被固定;它可以是多個相異選項的其中一個。</span><span class="sxs-lookup"><span data-stu-id="29f73-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="29f73-111">不同於其他語言的聯集，不過，每個可能的選項基於*寫的識別項*。</span><span class="sxs-lookup"><span data-stu-id="29f73-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="29f73-112">案例識別項是各種可能的可能是此類型的物件; 的值類型的名稱值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="29f73-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="29f73-113">如果值不存在，它就相當於列舉案例。</span><span class="sxs-lookup"><span data-stu-id="29f73-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="29f73-114">如果值存在，每個值可以是單一值的指定的類型或彙總相同或不同類型的多個欄位的 tuple。</span><span class="sxs-lookup"><span data-stu-id="29f73-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="29f73-115">您可以為個別欄位的名稱，但名稱是選擇性的即使在相同的情況下的其他欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="29f73-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="29f73-116">差別聯集的存取範圍預設為`public`。</span><span class="sxs-lookup"><span data-stu-id="29f73-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="29f73-117">例如，請考慮下列 Shape 類型的宣告。</span><span class="sxs-lookup"><span data-stu-id="29f73-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="29f73-118">上述的程式碼宣告差別等位圖形，它可以有三種情況下的任何值： 矩形、 圓形和角柱。</span><span class="sxs-lookup"><span data-stu-id="29f73-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="29f73-119">每個案例中有一組不同的欄位。</span><span class="sxs-lookup"><span data-stu-id="29f73-119">Each case has a different set of fields.</span></span> <span data-ttu-id="29f73-120">矩形案例有兩個具名欄位，都屬於型別`float`，具有名稱寬度和長度。</span><span class="sxs-lookup"><span data-stu-id="29f73-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="29f73-121">圓形案例有只有一個具名的欄位，radius。</span><span class="sxs-lookup"><span data-stu-id="29f73-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="29f73-122">角柱案例有三個欄位，其中的 （寬度和高度） 兩個名為欄位。</span><span class="sxs-lookup"><span data-stu-id="29f73-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="29f73-123">未命名的欄位稱為匿名欄位。</span><span class="sxs-lookup"><span data-stu-id="29f73-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="29f73-124">您所提供的具名和匿名的欄位，根據下列範例值建構物件。</span><span class="sxs-lookup"><span data-stu-id="29f73-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="29f73-125">此程式碼示範您可以使用具名的欄位初始化，或您可以依賴宣告中的欄位順序，並只接著每個欄位提供值。</span><span class="sxs-lookup"><span data-stu-id="29f73-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="29f73-126">建構函式呼叫`rect`在先前的程式碼會使用具名的欄位，但建構函式呼叫的`circ`使用順序。</span><span class="sxs-lookup"><span data-stu-id="29f73-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="29f73-127">您可以混合排序的欄位，並命名為欄位，如建構`prism`。</span><span class="sxs-lookup"><span data-stu-id="29f73-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="29f73-128">`option`類型是簡單的已區分聯集，在F#核心程式庫。</span><span class="sxs-lookup"><span data-stu-id="29f73-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="29f73-129">`option`類型宣告，如下所示。</span><span class="sxs-lookup"><span data-stu-id="29f73-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="29f73-130">先前的程式碼指定型別`Option`是具有兩個案例的已區分聯集`Some`和`None`。</span><span class="sxs-lookup"><span data-stu-id="29f73-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="29f73-131">`Some`案例有相關聯的值，其中包含型別由型別參數的一個匿名欄位`'a`。</span><span class="sxs-lookup"><span data-stu-id="29f73-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="29f73-132">`None`案例沒有任何相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="29f73-132">The `None` case has no associated value.</span></span> <span data-ttu-id="29f73-133">因此`option`型別指定值為 some 類型或沒有值的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="29f73-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="29f73-134">型別`Option`也有小寫類型別名`option`，也就是較常使用。</span><span class="sxs-lookup"><span data-stu-id="29f73-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="29f73-135">案例識別項可以作為已區分的聯集類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="29f73-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="29f73-136">比方說，下列程式碼用來建立值`option`型別。</span><span class="sxs-lookup"><span data-stu-id="29f73-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="29f73-137">案例識別項也用於模式比對運算式。</span><span class="sxs-lookup"><span data-stu-id="29f73-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="29f73-138">在模式比對運算式中，會提供識別項的個別案例相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="29f73-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="29f73-139">例如，在下列程式碼中，`x`識別項的值會指定相關聯`Some`案例`option`型別。</span><span class="sxs-lookup"><span data-stu-id="29f73-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="29f73-140">在模式比對運算式中，您可以使用具名的欄位來指定差別聯集的相符項目。</span><span class="sxs-lookup"><span data-stu-id="29f73-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="29f73-141">對於先前宣告的圖形類型，您可以使用具名的欄位，如下列程式碼所示擷取欄位的值。</span><span class="sxs-lookup"><span data-stu-id="29f73-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="29f73-142">通常，案例識別項可不搭配聯集的名稱來限定它們。</span><span class="sxs-lookup"><span data-stu-id="29f73-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="29f73-143">如果您想要一律以聯集的名稱限定的名稱，您可以套用[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)等位型別定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="29f73-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="29f73-144">解除包裝的差別聯的集</span><span class="sxs-lookup"><span data-stu-id="29f73-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="29f73-145">在F#差別聯集通常用於在領域模型中包裝單一類型。</span><span class="sxs-lookup"><span data-stu-id="29f73-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="29f73-146">它可輕易擷取透過模式比對以及基礎值。</span><span class="sxs-lookup"><span data-stu-id="29f73-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="29f73-147">您不需要使用比對運算式，針對單一案例：</span><span class="sxs-lookup"><span data-stu-id="29f73-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="29f73-148">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="29f73-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="29f73-149">模式比對也允許直接在函式參數，所以您可以解除包裝單一案例那里：</span><span class="sxs-lookup"><span data-stu-id="29f73-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="29f73-150">結構差別聯集</span><span class="sxs-lookup"><span data-stu-id="29f73-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="29f73-151">開頭為F#4.1，您也可以表示差別等位做為結構。</span><span class="sxs-lookup"><span data-stu-id="29f73-151">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="29f73-152">做法是使用`[<Struct>]`屬性。</span><span class="sxs-lookup"><span data-stu-id="29f73-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="29f73-153">因為這些是實值型別，而且未參考的型別，所以會有額外考量相較於參考差別聯集：</span><span class="sxs-lookup"><span data-stu-id="29f73-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="29f73-154">它們會複製為實值型別，並且具有實值型別語意。</span><span class="sxs-lookup"><span data-stu-id="29f73-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="29f73-155">您無法使用 multicase 結構 Discriminated Union 的遞迴類型定義。</span><span class="sxs-lookup"><span data-stu-id="29f73-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="29f73-156">您必須提供 Discriminated Union multicase 結構案例的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="29f73-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="29f73-157">使用已區分的聯集而非物件階層</span><span class="sxs-lookup"><span data-stu-id="29f73-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="29f73-158">您通常可以使用已區分的聯集為小型物件階層的簡單替代方式。</span><span class="sxs-lookup"><span data-stu-id="29f73-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="29f73-159">例如，可以使用下列已區分的聯集而不是`Shape`基底類別具有衍生型別的 circle、，方形，依此類推。</span><span class="sxs-lookup"><span data-stu-id="29f73-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="29f73-160">若要計算區域或周邊的虛擬方法，為您是使用物件導向實作中，您可以使用模式比對分支至適當的公式來計算這些數量。</span><span class="sxs-lookup"><span data-stu-id="29f73-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="29f73-161">在下列範例中，不同的公式來計算區域中的，根據形狀。</span><span class="sxs-lookup"><span data-stu-id="29f73-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="29f73-162">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="29f73-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="29f73-163">差別聯的集用於樹狀資料結構</span><span class="sxs-lookup"><span data-stu-id="29f73-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="29f73-164">差別等位可以是遞迴的這表示聯集本身可以納入一或多個案例的型別。</span><span class="sxs-lookup"><span data-stu-id="29f73-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="29f73-165">遞迴差別聯的集可以用來建立樹狀結構，用來在程式設計語言中的模型運算式。</span><span class="sxs-lookup"><span data-stu-id="29f73-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="29f73-166">下列程式碼中，遞迴的已區分聯集用來建立二進位樹狀資料結構。</span><span class="sxs-lookup"><span data-stu-id="29f73-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="29f73-167">聯集是由兩個案例所組成`Node`，這是整數值與和左右子節點和`Tip`，可結束樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="29f73-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="29f73-168">在先前的程式碼`resultSumTree`具有值為 10。</span><span class="sxs-lookup"><span data-stu-id="29f73-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="29f73-169">下圖顯示的樹狀結構`myTree`。</span><span class="sxs-lookup"><span data-stu-id="29f73-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Mytree 的樹狀結構](../media/TreeStructureDiagram.png)

<span data-ttu-id="29f73-171">在樹狀目錄中的節點是異質也運作差別聯的集。</span><span class="sxs-lookup"><span data-stu-id="29f73-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="29f73-172">下列程式碼類型`Expression`代表抽象語法樹狀目錄中的運算式中簡單的程式設計語言支援新增和相乘的數字和變數。</span><span class="sxs-lookup"><span data-stu-id="29f73-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="29f73-173">部分聯集案例不是遞迴和代表數字 (`Number`) 或變數 (`Variable`)。</span><span class="sxs-lookup"><span data-stu-id="29f73-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="29f73-174">其他情況下是遞迴的而且代表運算 (`Add`和`Multiply`)，其中運算元也是運算式。</span><span class="sxs-lookup"><span data-stu-id="29f73-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="29f73-175">`Evaluate`函式會使用比對運算式來遞迴處理語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="29f73-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="29f73-176">此程式碼執行時，值`result`為 5。</span><span class="sxs-lookup"><span data-stu-id="29f73-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="29f73-177">常見屬性</span><span class="sxs-lookup"><span data-stu-id="29f73-177">Common Attributes</span></span>

<span data-ttu-id="29f73-178">差別聯集中，常見的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="29f73-178">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a><span data-ttu-id="29f73-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29f73-179">See also</span></span>

- [<span data-ttu-id="29f73-180">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="29f73-180">F# Language Reference</span></span>](index.md)
