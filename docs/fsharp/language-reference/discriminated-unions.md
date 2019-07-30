---
title: 已區分的聯集
description: 瞭解如何使用F#區分等位。
ms.date: 05/16/2016
ms.openlocfilehash: 940bc51f49e283c31846dd2047b749769b919838
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630356"
---
# <a name="discriminated-unions"></a><span data-ttu-id="9c75d-103">已區分的聯集</span><span class="sxs-lookup"><span data-stu-id="9c75d-103">Discriminated Unions</span></span>

<span data-ttu-id="9c75d-104">相異聯集提供的值, 可能是其中一個已命名的案例, 可能會有不同的值和類型。</span><span class="sxs-lookup"><span data-stu-id="9c75d-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="9c75d-105">區分等位適用于異質資料;可以有特殊案例的資料, 包括有效和錯誤的案例;從一個實例到另一個實例的類型不同的資料;和作為小型物件階層的替代方案。</span><span class="sxs-lookup"><span data-stu-id="9c75d-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="9c75d-106">此外, 遞迴的區分等位是用來表示樹狀結構的資料結構。</span><span class="sxs-lookup"><span data-stu-id="9c75d-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c75d-107">語法</span><span class="sxs-lookup"><span data-stu-id="9c75d-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="9c75d-108">備註</span><span class="sxs-lookup"><span data-stu-id="9c75d-108">Remarks</span></span>

<span data-ttu-id="9c75d-109">區分聯集與其他語言的等位類型類似, 但有差異。</span><span class="sxs-lookup"><span data-stu-id="9c75d-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="9c75d-110">如同中C++的聯集類型或 Visual Basic 中的 variant 類型, 儲存在值中的資料不會固定;它可以是幾個不同選項的其中一個。</span><span class="sxs-lookup"><span data-stu-id="9c75d-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="9c75d-111">不同于這些其他語言的等位, 每個可能的選項都會被賦予一個*案例識別碼*。</span><span class="sxs-lookup"><span data-stu-id="9c75d-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="9c75d-112">案例識別碼是此類型之物件的各種可能數值型別的名稱。這些值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9c75d-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="9c75d-113">如果值不存在, 則案例相當於列舉案例。</span><span class="sxs-lookup"><span data-stu-id="9c75d-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="9c75d-114">如果有值, 每個值都可以是指定類型的單一值, 或是匯總相同或不同類型之多個欄位的元組。</span><span class="sxs-lookup"><span data-stu-id="9c75d-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="9c75d-115">您可以為個別的欄位指定名稱, 但名稱是選擇性的, 即使相同案例中的其他欄位命名也一樣。</span><span class="sxs-lookup"><span data-stu-id="9c75d-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="9c75d-116">區分等位的協助工具`public`預設為。</span><span class="sxs-lookup"><span data-stu-id="9c75d-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="9c75d-117">例如, 請考慮下列圖形類型的宣告。</span><span class="sxs-lookup"><span data-stu-id="9c75d-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="9c75d-118">上述程式碼會宣告一個區分聯集圖形, 其值可以是下列三種情況的其中一種:矩形、圓形和 Prism。</span><span class="sxs-lookup"><span data-stu-id="9c75d-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="9c75d-119">每個案例都有一組不同的欄位。</span><span class="sxs-lookup"><span data-stu-id="9c75d-119">Each case has a different set of fields.</span></span> <span data-ttu-id="9c75d-120">矩形案例有兩個名為的欄位, 兩`float`個都是類型, 其名稱為 width 和 length。</span><span class="sxs-lookup"><span data-stu-id="9c75d-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="9c75d-121">圓形案例只有一個命名欄位 [半徑]。</span><span class="sxs-lookup"><span data-stu-id="9c75d-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="9c75d-122">Prism 案例有三個欄位, 其中兩個 (寬度和高度) 為欄位。</span><span class="sxs-lookup"><span data-stu-id="9c75d-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="9c75d-123">未命名的欄位稱為「匿名欄位」。</span><span class="sxs-lookup"><span data-stu-id="9c75d-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="9c75d-124">您可以根據下列範例, 提供已命名和匿名欄位的值來建立物件。</span><span class="sxs-lookup"><span data-stu-id="9c75d-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="9c75d-125">這段程式碼顯示您可以在初始化中使用已命名的欄位, 或者您可以依賴宣告中的欄位順序, 然後只提供每個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="9c75d-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="9c75d-126">先前程式`rect`代碼中的函式呼叫會使用已命名的欄位, 但的函數`circ`調用會使用排序。</span><span class="sxs-lookup"><span data-stu-id="9c75d-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="9c75d-127">您可以混合使用已排序的欄位和命名欄位, 如同的結構`prism`。</span><span class="sxs-lookup"><span data-stu-id="9c75d-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="9c75d-128">類型是F#核心程式庫中的簡單區分聯集。 `option`</span><span class="sxs-lookup"><span data-stu-id="9c75d-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="9c75d-129">類型`option`的宣告方式如下。</span><span class="sxs-lookup"><span data-stu-id="9c75d-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="9c75d-130">先前的程式碼指定類型`Option`為具有兩個案例的區分聯集, `Some`和。 `None`</span><span class="sxs-lookup"><span data-stu-id="9c75d-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="9c75d-131">案例有一個相關聯的值, 其中包含一個匿名欄位, 其型別是由型`'a`別參數表示。 `Some`</span><span class="sxs-lookup"><span data-stu-id="9c75d-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="9c75d-132">案例`None`沒有相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="9c75d-132">The `None` case has no associated value.</span></span> <span data-ttu-id="9c75d-133">因此, `option`此型別會指定具有某個型別值或沒有值的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="9c75d-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="9c75d-134">此類型`Option`也有一個較常用的小寫`option`類型別名。</span><span class="sxs-lookup"><span data-stu-id="9c75d-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="9c75d-135">案例識別碼可用來做為區分聯集類型的構造函式。</span><span class="sxs-lookup"><span data-stu-id="9c75d-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="9c75d-136">例如, 下列程式碼是用來建立`option`型別的值。</span><span class="sxs-lookup"><span data-stu-id="9c75d-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="9c75d-137">案例識別碼也會用於模式比對運算式。</span><span class="sxs-lookup"><span data-stu-id="9c75d-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="9c75d-138">在模式比對運算式中, 會提供與個別案例相關聯之值的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9c75d-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="9c75d-139">例如, 在下列程式碼中, `x`是指定`Some`與`option`類型案例相關聯之值的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9c75d-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="9c75d-140">在模式比對運算式中, 您可以使用命名欄位來指定區分聯集的相符專案。</span><span class="sxs-lookup"><span data-stu-id="9c75d-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="9c75d-141">針對先前宣告的圖形類型, 您可以使用已命名的欄位, 如下列程式碼所示, 以解壓縮欄位的值。</span><span class="sxs-lookup"><span data-stu-id="9c75d-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="9c75d-142">一般來說, 您可以使用案例識別碼, 而不需要使用聯集的名稱來加以限定。</span><span class="sxs-lookup"><span data-stu-id="9c75d-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="9c75d-143">如果您想要讓名稱一律以聯集的名稱限定, 可以將[RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp])屬性套用至 union 類型定義。</span><span class="sxs-lookup"><span data-stu-id="9c75d-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="9c75d-144">解除包裝區分等位</span><span class="sxs-lookup"><span data-stu-id="9c75d-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="9c75d-145">在F#區分等位中, 通常會在用來包裝單一類型的網域模型中使用。</span><span class="sxs-lookup"><span data-stu-id="9c75d-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="9c75d-146">您也可以透過模式比對, 輕鬆地將基礎值解壓縮。</span><span class="sxs-lookup"><span data-stu-id="9c75d-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="9c75d-147">您不需要在單一案例中使用 match 運算式:</span><span class="sxs-lookup"><span data-stu-id="9c75d-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="9c75d-148">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="9c75d-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="9c75d-149">函式參數中也可直接使用模式比對, 因此您可以將單一案例解除包裝在該處:</span><span class="sxs-lookup"><span data-stu-id="9c75d-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="9c75d-150">結構區分等位</span><span class="sxs-lookup"><span data-stu-id="9c75d-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="9c75d-151">您也可以將區分等位當做結構來表示。</span><span class="sxs-lookup"><span data-stu-id="9c75d-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="9c75d-152">這是使用`[<Struct>]`屬性來完成的。</span><span class="sxs-lookup"><span data-stu-id="9c75d-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="9c75d-153">因為這些是實值型別, 而不是參考型別, 所以相較于參考區分等位, 會有額外的考慮:</span><span class="sxs-lookup"><span data-stu-id="9c75d-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="9c75d-154">它們會複製為實值型別, 並具有實數值型別的語義。</span><span class="sxs-lookup"><span data-stu-id="9c75d-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="9c75d-155">您不能將遞迴型別定義與 multicase 結構區分聯集搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9c75d-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="9c75d-156">您必須為 multicase 結構區分聯集提供唯一的案例名稱。</span><span class="sxs-lookup"><span data-stu-id="9c75d-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="9c75d-157">使用區分聯集, 而不是物件階層</span><span class="sxs-lookup"><span data-stu-id="9c75d-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="9c75d-158">您通常可以使用區分聯集作為小型物件階層的較簡單替代方式。</span><span class="sxs-lookup"><span data-stu-id="9c75d-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="9c75d-159">例如, 您可以使用下列的區分聯集, 而不`Shape`是具有 circle、方形等衍生類型的基類。</span><span class="sxs-lookup"><span data-stu-id="9c75d-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="9c75d-160">除了用來計算區域或周邊的虛擬方法之外, 您也可以在物件導向的執行中使用模式比對, 以適當的公式分支來計算這些數量。</span><span class="sxs-lookup"><span data-stu-id="9c75d-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="9c75d-161">在下列範例中, 會使用不同的公式來計算區域, 視圖形而定。</span><span class="sxs-lookup"><span data-stu-id="9c75d-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="9c75d-162">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="9c75d-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="9c75d-163">使用樹狀資料結構的區分等位</span><span class="sxs-lookup"><span data-stu-id="9c75d-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="9c75d-164">區分聯集可以是遞迴的, 這表示等位本身可以包含在一或多個案例的類型中。</span><span class="sxs-lookup"><span data-stu-id="9c75d-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="9c75d-165">遞迴的區分等位可以用來建立樹狀結構, 用來以程式設計語言將運算式模型。</span><span class="sxs-lookup"><span data-stu-id="9c75d-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="9c75d-166">在下列程式碼中, 會使用遞迴的區分聯集來建立二進位樹狀結構資料結構。</span><span class="sxs-lookup"><span data-stu-id="9c75d-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="9c75d-167">聯集包含兩個案例, `Node`也就是具有整數值和左和右子樹的節點, 以及`Tip`終止樹狀結構的。</span><span class="sxs-lookup"><span data-stu-id="9c75d-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="9c75d-168">在先前的程式碼`resultSumTree`中, 的值為10。</span><span class="sxs-lookup"><span data-stu-id="9c75d-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="9c75d-169">下圖顯示的樹狀結構`myTree`。</span><span class="sxs-lookup"><span data-stu-id="9c75d-169">The following illustration shows the tree structure for `myTree`.</span></span>

![顯示 myTree 樹狀結構的圖表。](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="9c75d-171">如果樹狀結構中的節點是異類的, 則區分聯集的運作良好。</span><span class="sxs-lookup"><span data-stu-id="9c75d-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="9c75d-172">在下列程式碼中, 類型`Expression`會以簡單的程式設計語言, 表示運算式的抽象語法樹狀結構, 以支援數位和變數的加法和乘法。</span><span class="sxs-lookup"><span data-stu-id="9c75d-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="9c75d-173">某些聯集案例不是遞迴的, 而是代表數位`Number`() 或變數`Variable`()。</span><span class="sxs-lookup"><span data-stu-id="9c75d-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="9c75d-174">其他情況則是遞迴的, 表示作業`Add` ( `Multiply`和), 其中的運算元也是運算式。</span><span class="sxs-lookup"><span data-stu-id="9c75d-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="9c75d-175">`Evaluate`函式會使用 match 運算式來以遞迴方式處理語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="9c75d-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="9c75d-176">執行此程式碼時, 的值`result`會是5。</span><span class="sxs-lookup"><span data-stu-id="9c75d-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="9c75d-177">成員</span><span class="sxs-lookup"><span data-stu-id="9c75d-177">Members</span></span>

<span data-ttu-id="9c75d-178">您可以在區分等位上定義成員。</span><span class="sxs-lookup"><span data-stu-id="9c75d-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="9c75d-179">下列範例顯示如何定義屬性和實作為介面:</span><span class="sxs-lookup"><span data-stu-id="9c75d-179">The following example shows how to define a property and implement an interface:</span></span>

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a><span data-ttu-id="9c75d-180">通用屬性</span><span class="sxs-lookup"><span data-stu-id="9c75d-180">Common attributes</span></span>

<span data-ttu-id="9c75d-181">下列屬性通常會出現在區分等位中:</span><span class="sxs-lookup"><span data-stu-id="9c75d-181">The following attributes are commonly seen in discriminated unions:</span></span>

* `[<RequireQualifiedAccess>]`
* `[<NoEquality>]`
* `[<NoComparison>]`
* `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="9c75d-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c75d-182">See also</span></span>

- [<span data-ttu-id="9c75d-183">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="9c75d-183">F# Language Reference</span></span>](index.md)
