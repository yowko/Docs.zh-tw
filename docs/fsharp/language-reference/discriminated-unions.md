---
title: "已區分的聯集 (F#)"
description: "了解如何使用 F # 差別等位。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e2a011-c785-48c8-859f-79df7f3a0e29
ms.openlocfilehash: a374f521bcde7506bb3a9eebb627eaffcd8b94a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="discriminated-unions"></a><span data-ttu-id="0cb96-104">已區分的聯集</span><span class="sxs-lookup"><span data-stu-id="0cb96-104">Discriminated Unions</span></span>

<span data-ttu-id="0cb96-105">差別等位可以是其中一個具名的情況下，可能各有不同的值和類型的數字的值提供支援。</span><span class="sxs-lookup"><span data-stu-id="0cb96-105">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="0cb96-106">差別等位是適用於異質資料，特殊案例，包括有效和錯誤的情況下，可以有的資料變化為另一個，從一個執行個體的型別中的資料並為小型物件階層架構的替代選項。</span><span class="sxs-lookup"><span data-stu-id="0cb96-106">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="0cb96-107">此外，遞迴差別等位用來表示樹狀目錄中的資料結構。</span><span class="sxs-lookup"><span data-stu-id="0cb96-107">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="0cb96-108">語法</span><span class="sxs-lookup"><span data-stu-id="0cb96-108">Syntax</span></span>

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a><span data-ttu-id="0cb96-109">備註</span><span class="sxs-lookup"><span data-stu-id="0cb96-109">Remarks</span></span>
<span data-ttu-id="0cb96-110">差別等位類似於聯集類型在其他語言中，但有一些差異。</span><span class="sxs-lookup"><span data-stu-id="0cb96-110">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="0cb96-111">做為與 c + + 中的等位型別或在 Visual Basic 中的之變數類型的值中所儲存的資料不被固定;它可以是其中幾個不同的選項。</span><span class="sxs-lookup"><span data-stu-id="0cb96-111">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="0cb96-112">不同於這些其他語言中的等位，不過，每個可能的選項擁有*案例識別碼*。</span><span class="sxs-lookup"><span data-stu-id="0cb96-112">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="0cb96-113">大小寫的識別項是各種可能的值，這個類型的物件; 類型名稱值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="0cb96-113">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="0cb96-114">如果值不存在，就有一個情況相當於列舉案例。</span><span class="sxs-lookup"><span data-stu-id="0cb96-114">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="0cb96-115">如果值存在，每個值可以是單一值的指定的類型或彙總多個欄位的相同或不同類型的 tuple。</span><span class="sxs-lookup"><span data-stu-id="0cb96-115">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="0cb96-116">為準，F # 3.1，您可以指定個別欄位的名稱，但名稱是選擇性的即使名為相同的大小寫的其他欄位。</span><span class="sxs-lookup"><span data-stu-id="0cb96-116">As of F# 3.1, you can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="0cb96-117">例如，請考慮下列的圖形類型宣告。</span><span class="sxs-lookup"><span data-stu-id="0cb96-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="0cb96-118">上述程式碼會宣告差別聯集圖形，可以有三種情況的任何值： 矩形、 圓形和角柱。</span><span class="sxs-lookup"><span data-stu-id="0cb96-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="0cb96-119">每個案例具有一組不同的欄位。</span><span class="sxs-lookup"><span data-stu-id="0cb96-119">Each case has a different set of fields.</span></span> <span data-ttu-id="0cb96-120">欄位案例有兩個具名的矩形，這兩個型別`float`，具有名稱寬度和長度。</span><span class="sxs-lookup"><span data-stu-id="0cb96-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="0cb96-121">圓形案例有一個具名的欄位，radius。</span><span class="sxs-lookup"><span data-stu-id="0cb96-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="0cb96-122">角柱案例有三個欄位，其中的 （寬度和高度） 兩個名為欄位。</span><span class="sxs-lookup"><span data-stu-id="0cb96-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="0cb96-123">未命名的欄位稱為匿名的欄位。</span><span class="sxs-lookup"><span data-stu-id="0cb96-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="0cb96-124">您可以根據下列範例為具名和匿名欄位提供值，以建構物件。</span><span class="sxs-lookup"><span data-stu-id="0cb96-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="0cb96-125">此程式碼示範您可以使用具名的欄位初始化，或您可以依賴的宣告中的欄位順序，並只接著每個欄位提供值。</span><span class="sxs-lookup"><span data-stu-id="0cb96-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="0cb96-126">建構函式呼叫，如`rect`先前的程式碼會使用具名的欄位，但建構函式呼叫，如`circ`使用順序。</span><span class="sxs-lookup"><span data-stu-id="0cb96-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="0cb96-127">您可以混合的已排序的欄位和欄位，如所示建構`prism`。</span><span class="sxs-lookup"><span data-stu-id="0cb96-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="0cb96-128">`option`類型是簡單的差別等位在 F # 核心程式庫。</span><span class="sxs-lookup"><span data-stu-id="0cb96-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="0cb96-129">`option`型別宣告，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0cb96-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="0cb96-130">先前的程式碼指定的型別`Option`是有兩種情況下，差別聯集`Some`和`None`。</span><span class="sxs-lookup"><span data-stu-id="0cb96-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="0cb96-131">`Some`案例有關聯的值是由一個型別由型別參數的匿名欄位組成`'a`。</span><span class="sxs-lookup"><span data-stu-id="0cb96-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="0cb96-132">`None`案例有沒有相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="0cb96-132">The `None` case has no associated value.</span></span> <span data-ttu-id="0cb96-133">因此`option`類型指定的泛型類型，都有某些型別或任何值的值。</span><span class="sxs-lookup"><span data-stu-id="0cb96-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="0cb96-134">型別`Option`也有一個小寫類型別名`option`，也就是多常用。</span><span class="sxs-lookup"><span data-stu-id="0cb96-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="0cb96-135">大小寫的識別項可以作為差別聯集類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="0cb96-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="0cb96-136">例如，下列程式碼用來建立的值`option`型別。</span><span class="sxs-lookup"><span data-stu-id="0cb96-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="0cb96-137">模式比對運算式中，也會使用大小寫的識別項。</span><span class="sxs-lookup"><span data-stu-id="0cb96-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="0cb96-138">在模式比對運算式中，識別項可供個別案例與相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="0cb96-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="0cb96-139">例如，在下列程式碼，`x`識別項的值會指定相關聯`Some`案例`option`型別。</span><span class="sxs-lookup"><span data-stu-id="0cb96-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="0cb96-140">在模式比對運算式中，您可以使用具名的欄位來指定差別聯集的相符項目。</span><span class="sxs-lookup"><span data-stu-id="0cb96-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="0cb96-141">針對先前已宣告的圖形類型，您可以使用具名的欄位，如下列程式碼所示來擷取欄位的值。</span><span class="sxs-lookup"><span data-stu-id="0cb96-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="0cb96-142">一般來說，大小寫的識別項可以利用不含限定聯集的名稱。</span><span class="sxs-lookup"><span data-stu-id="0cb96-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="0cb96-143">如果您想要一律以聯集的名稱限定的名稱，您可以套用[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)等位型別定義此屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb96-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="0cb96-144">解除包裝的差別等位</span><span class="sxs-lookup"><span data-stu-id="0cb96-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="0cb96-145">F # 差別等位中通常用於在網域模型包裝單一類型。</span><span class="sxs-lookup"><span data-stu-id="0cb96-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="0cb96-146">所以可以輕鬆地擷取透過以及模式比對的基礎值。</span><span class="sxs-lookup"><span data-stu-id="0cb96-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="0cb96-147">您不需要使用比對運算式針對單一案例：</span><span class="sxs-lookup"><span data-stu-id="0cb96-147">You don't need to use a match expression for a single case:</span></span>
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="0cb96-148">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="0cb96-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="0cb96-149">結構的差別等位</span><span class="sxs-lookup"><span data-stu-id="0cb96-149">Struct Discriminated Unions</span></span>

<span data-ttu-id="0cb96-150">從 F # 4.1 開始，您也可以代表差別等位為結構。</span><span class="sxs-lookup"><span data-stu-id="0cb96-150">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="0cb96-151">做法是使用`[<Struct>]`屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb96-151">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of string
    | Case2 of int
    | Case3 of double
```

<span data-ttu-id="0cb96-152">由於這些是實值類型和參考型別時，會有額外考量相較於參考差別等位：</span><span class="sxs-lookup"><span data-stu-id="0cb96-152">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="0cb96-153">可複製為實值類型，並且具有實值類型語意。</span><span class="sxs-lookup"><span data-stu-id="0cb96-153">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="0cb96-154">您無法使用 multicase 結構 Discriminated Union 的遞迴類型定義。</span><span class="sxs-lookup"><span data-stu-id="0cb96-154">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="0cb96-155">您必須提供 Discriminated Union multicase 結構案例的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="0cb96-155">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="0cb96-156">使用差別聯的集而不物件階層架構</span><span class="sxs-lookup"><span data-stu-id="0cb96-156">Using Discriminated Unions Instead of Object Hierarchies</span></span>
<span data-ttu-id="0cb96-157">您通常可以使用差別聯集為小型物件階層簡單的替代方案。</span><span class="sxs-lookup"><span data-stu-id="0cb96-157">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="0cb96-158">例如，下列差別聯集無法使用而不是`Shape`基底類別具有衍生類型的圓形，方形，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0cb96-158">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="0cb96-159">虛擬方法，以計算區域或周邊，您會改用物件導向的實作中，您可以使用模式比對分支到適當的公式來計算這些數量。</span><span class="sxs-lookup"><span data-stu-id="0cb96-159">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="0cb96-160">在下列範例中，不同的公式用來計算區域中的，根據圖形。</span><span class="sxs-lookup"><span data-stu-id="0cb96-160">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="0cb96-161">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="0cb96-161">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="0cb96-162">使用資料的樹狀結構的差別等位</span><span class="sxs-lookup"><span data-stu-id="0cb96-162">Using Discriminated Unions for Tree Data Structures</span></span>
<span data-ttu-id="0cb96-163">差別等位可以是遞迴的這表示等位本身可以納入一或多個案例的型別。</span><span class="sxs-lookup"><span data-stu-id="0cb96-163">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="0cb96-164">遞迴差別等位可以用來建立樹狀結構，可用來程式設計語言中的模型運算式。</span><span class="sxs-lookup"><span data-stu-id="0cb96-164">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="0cb96-165">下列程式碼中，遞迴差別聯集用來建立二元樹狀資料結構。</span><span class="sxs-lookup"><span data-stu-id="0cb96-165">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="0cb96-166">聯集包含兩種情況下， `Node`，這是整數值與左邊和右邊子樹節點和`Tip`，這會終止在樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0cb96-166">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="0cb96-167">先前的程式碼，`resultSumTree`具有值為 10。</span><span class="sxs-lookup"><span data-stu-id="0cb96-167">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="0cb96-168">下圖顯示的樹狀結構`myTree`。</span><span class="sxs-lookup"><span data-stu-id="0cb96-168">The following illustration shows the tree structure for `myTree`.</span></span>

![MyTree 的樹狀結構](../media/TreeStructureDiagram.png)

<span data-ttu-id="0cb96-170">差別等位工作樹狀結構中的節點都是異質性的情況。</span><span class="sxs-lookup"><span data-stu-id="0cb96-170">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="0cb96-171">下列程式碼類型`Expression`代表抽象語法樹狀目錄的運算式中簡單的程式設計語言支援加法和乘法的數字和變數。</span><span class="sxs-lookup"><span data-stu-id="0cb96-171">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="0cb96-172">部分聯集的情況下無法遞迴且代表其中一個數字 (`Number`) 或變數 (`Variable`)。</span><span class="sxs-lookup"><span data-stu-id="0cb96-172">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="0cb96-173">其他情況下都是遞迴，而且代表作業 (`Add`和`Multiply`)，其中運算元也是運算式。</span><span class="sxs-lookup"><span data-stu-id="0cb96-173">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="0cb96-174">`Evaluate`函式會使用遞迴程序的語法樹狀目錄的比對運算式。</span><span class="sxs-lookup"><span data-stu-id="0cb96-174">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="0cb96-175">此程式碼執行時，值`result`為 5。</span><span class="sxs-lookup"><span data-stu-id="0cb96-175">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="0cb96-176">常見屬性</span><span class="sxs-lookup"><span data-stu-id="0cb96-176">Common Attributes</span></span>

<span data-ttu-id="0cb96-177">差別等位中，常見的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0cb96-177">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* <span data-ttu-id="0cb96-178">`[Struct]`（F # 4.1 和更新版本）</span><span class="sxs-lookup"><span data-stu-id="0cb96-178">`[Struct]` (F# 4.1 and higher)</span></span>

## <a name="see-also"></a><span data-ttu-id="0cb96-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cb96-179">See Also</span></span>
[<span data-ttu-id="0cb96-180">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="0cb96-180">F# Language Reference</span></span>](index.md)
