---
title: 已區分的聯集
description: '瞭解如何使用 F # 區分等位。'
ms.date: 08/15/2020
ms.openlocfilehash: 3f8ac656bd00b1022b2b13ee1be7ca5c98f68db5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812129"
---
# <a name="discriminated-unions"></a><span data-ttu-id="e700f-103">已區分的聯集</span><span class="sxs-lookup"><span data-stu-id="e700f-103">Discriminated Unions</span></span>

<span data-ttu-id="e700f-104">差異聯集可支援可能是數個命名案例之一的值，可能是每個都有不同的值和類型。</span><span class="sxs-lookup"><span data-stu-id="e700f-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="e700f-105">相異聯集適用于異質資料;可能具有特殊案例的資料，包括有效和錯誤案例;從某個實例到另一個實例的類型不同的資料;以及做為小型物件階層的替代方案。</span><span class="sxs-lookup"><span data-stu-id="e700f-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="e700f-106">此外，遞迴差異聯集用來表示樹狀結構資料結構。</span><span class="sxs-lookup"><span data-stu-id="e700f-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="e700f-107">語法</span><span class="sxs-lookup"><span data-stu-id="e700f-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="e700f-108">備註</span><span class="sxs-lookup"><span data-stu-id="e700f-108">Remarks</span></span>

<span data-ttu-id="e700f-109">相異聯集與其他語言的等位類型類似，但有一些差異。</span><span class="sxs-lookup"><span data-stu-id="e700f-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="e700f-110">如同 c + + 中的等位類型或 Visual Basic 中的 variant 類型，儲存在值中的資料不是固定的;它可以是數個不同選項的其中一個。</span><span class="sxs-lookup"><span data-stu-id="e700f-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="e700f-111">不過，不同于這些其他語言的等位，每個可能的選項都會獲得一個 *案例識別碼*。</span><span class="sxs-lookup"><span data-stu-id="e700f-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="e700f-112">案例識別碼是適用于各種可能類型之值的名稱，這些類型的物件可能是：這些值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e700f-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="e700f-113">如果值不存在，則案例相當於列舉案例。</span><span class="sxs-lookup"><span data-stu-id="e700f-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="e700f-114">如果有值，每個值都可以是指定類型的單一值，或是匯總多個相同或不同類型之欄位的元組。</span><span class="sxs-lookup"><span data-stu-id="e700f-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="e700f-115">您可以提供個別欄位的名稱，但名稱是選擇性的，即使相同案例中的其他欄位已命名也一樣。</span><span class="sxs-lookup"><span data-stu-id="e700f-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="e700f-116">區分等位的協助工具預設為 `public` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="e700f-117">例如，請考慮下列圖形類型的宣告。</span><span class="sxs-lookup"><span data-stu-id="e700f-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="e700f-118">上述程式碼會宣告差異聯集圖形，其值可以是下列三種情況之一：矩形、圓形和 Prism。</span><span class="sxs-lookup"><span data-stu-id="e700f-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="e700f-119">每個案例都有一組不同的欄位。</span><span class="sxs-lookup"><span data-stu-id="e700f-119">Each case has a different set of fields.</span></span> <span data-ttu-id="e700f-120">矩形大小寫有兩個名稱為的欄位，兩者都 `float` 有名稱寬度和長度的型別。</span><span class="sxs-lookup"><span data-stu-id="e700f-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="e700f-121">圓形案例只有一個命名欄位，半徑。</span><span class="sxs-lookup"><span data-stu-id="e700f-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="e700f-122">Prism 案例有三個欄位，其中兩個 (寬度和高度) 命名為 [欄位]。</span><span class="sxs-lookup"><span data-stu-id="e700f-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="e700f-123">未命名的欄位稱為匿名欄位。</span><span class="sxs-lookup"><span data-stu-id="e700f-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="e700f-124">您可以根據下列範例提供已命名和匿名欄位的值來建立物件。</span><span class="sxs-lookup"><span data-stu-id="e700f-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="e700f-125">這段程式碼顯示您可以在初始化中使用已命名的欄位，也可以依賴宣告中的欄位順序，然後再依序提供每個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="e700f-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="e700f-126">先前程式碼中的函式呼叫會 `rect` 使用命名欄位，但的函式呼叫會 `circ` 使用排序。</span><span class="sxs-lookup"><span data-stu-id="e700f-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="e700f-127">您可以混用已排序的欄位和命名欄位，就像在的結構中一樣 `prism` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="e700f-128">此 `option` 類型是 F # 核心程式庫中的簡單差異聯集。</span><span class="sxs-lookup"><span data-stu-id="e700f-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="e700f-129">型別宣告 `option` 如下。</span><span class="sxs-lookup"><span data-stu-id="e700f-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="e700f-130">先前的程式碼指定類型 `Option` 是具有兩個案例的差異聯集， `Some` 以及 `None` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="e700f-131">`Some`案例具有相關聯的值，其中包含一個匿名欄位，而該欄位的型別是由型別參數表示 `'a` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="e700f-132">`None`案例沒有相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="e700f-132">The `None` case has no associated value.</span></span> <span data-ttu-id="e700f-133">因此， `option` 型別會指定具有某個類型值或沒有任何值的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e700f-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="e700f-134">此類型 `Option` 也有較常用的小寫類型別名 `option` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="e700f-135">案例識別碼可用來當做差異聯集類型的函式。</span><span class="sxs-lookup"><span data-stu-id="e700f-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="e700f-136">例如，下列程式碼會用來建立類型的值 `option` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="e700f-137">案例識別碼也會在模式比對運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="e700f-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="e700f-138">在模式比對運算式中，會提供與個別案例相關聯之值的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e700f-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="e700f-139">例如，在下列程式碼中， `x` 是提供與型別案例相關聯之值的識別碼 `Some` `option` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="e700f-140">在模式比對運算式中，您可以使用指定的欄位來指定差異聯集相符專案。</span><span class="sxs-lookup"><span data-stu-id="e700f-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="e700f-141">針對先前宣告的圖形類型，您可以使用命名欄位，如下列程式碼所示，用來將欄位的值解壓縮。</span><span class="sxs-lookup"><span data-stu-id="e700f-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

<span data-ttu-id="e700f-142">一般情況下，您可以使用案例識別碼，而不使用聯集的名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="e700f-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="e700f-143">如果您想要使用聯集的名稱來限定名稱，您可以將 [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) 屬性套用至聯集類型定義。</span><span class="sxs-lookup"><span data-stu-id="e700f-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="e700f-144">解除包裝區分等位</span><span class="sxs-lookup"><span data-stu-id="e700f-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="e700f-145">在 F # 差異等位中，通常用於包裝單一型別的網域模型。</span><span class="sxs-lookup"><span data-stu-id="e700f-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="e700f-146">您也可以透過模式比對，輕鬆地將基礎值解壓縮。</span><span class="sxs-lookup"><span data-stu-id="e700f-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="e700f-147">單一案例不需要使用 match 運算式：</span><span class="sxs-lookup"><span data-stu-id="e700f-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="e700f-148">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="e700f-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="e700f-149">也可以直接在函式參數中使用模式比對，因此您可以在該處解除包裝單一案例：</span><span class="sxs-lookup"><span data-stu-id="e700f-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="e700f-150">結構區分等位</span><span class="sxs-lookup"><span data-stu-id="e700f-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="e700f-151">您也可以將區分等位表示為結構。</span><span class="sxs-lookup"><span data-stu-id="e700f-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="e700f-152">這是透過屬性來完成 `[<Struct>]` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="e700f-153">因為這些是實值型別，而不是參考型別，所以相較于參考差異聯集，還有其他考慮：</span><span class="sxs-lookup"><span data-stu-id="e700f-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="e700f-154">它們會複製為實數值型別，並具有實數值型別的語義。</span><span class="sxs-lookup"><span data-stu-id="e700f-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="e700f-155">您無法使用具有 multicase 結構差異聯集的遞迴型別定義。</span><span class="sxs-lookup"><span data-stu-id="e700f-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="e700f-156">您必須為 multicase 結構差異聯集提供唯一的案例名稱。</span><span class="sxs-lookup"><span data-stu-id="e700f-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="e700f-157">使用區分聯集而非物件階層</span><span class="sxs-lookup"><span data-stu-id="e700f-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="e700f-158">您通常可以使用差異聯集做為小型物件階層的較簡單替代項。</span><span class="sxs-lookup"><span data-stu-id="e700f-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="e700f-159">例如，您可以使用下列差異聯集，而不是 `Shape` 具有圓形、正方形等衍生類型的基類。</span><span class="sxs-lookup"><span data-stu-id="e700f-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="e700f-160">您可以使用模式比對來分支至適當的公式來計算這些數量，而不是使用虛擬方法來計算區域或周邊。</span><span class="sxs-lookup"><span data-stu-id="e700f-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="e700f-161">在下列範例中，根據圖形，使用不同的公式來計算區域。</span><span class="sxs-lookup"><span data-stu-id="e700f-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="e700f-162">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="e700f-162">The output is as follows:</span></span>

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="e700f-163">針對樹狀結構資料結構使用區分聯集</span><span class="sxs-lookup"><span data-stu-id="e700f-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="e700f-164">差異聯集可以是遞迴的，也就是說，等位本身可以包含在一或多個案例的型別中。</span><span class="sxs-lookup"><span data-stu-id="e700f-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="e700f-165">遞迴差異聯集可以用來建立樹狀結構，用來建立程式設計語言中的運算式模型。</span><span class="sxs-lookup"><span data-stu-id="e700f-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="e700f-166">在下列程式碼中，會使用遞迴差異聯集來建立二進位樹狀結構資料結構。</span><span class="sxs-lookup"><span data-stu-id="e700f-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="e700f-167">Union 包含兩個案例，也 `Node` 就是具有整數值、左和右樹系的節點，以及用 `Tip` 來終止樹狀結構的節點。</span><span class="sxs-lookup"><span data-stu-id="e700f-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="e700f-168">在先前的程式碼中， `resultSumTree` 的值為10。</span><span class="sxs-lookup"><span data-stu-id="e700f-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="e700f-169">下圖顯示的樹狀結構 `myTree` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-169">The following illustration shows the tree structure for `myTree`.</span></span>

![顯示 myTree 樹狀結構的圖表。](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="e700f-171">如果樹狀結構中的節點是異類的，則區分聯集的運作效果很好。</span><span class="sxs-lookup"><span data-stu-id="e700f-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="e700f-172">在下列程式碼中，類型 `Expression` 以簡單的程式設計語言表示運算式的抽象語法樹狀結構，支援數位和變數的加法和乘法。</span><span class="sxs-lookup"><span data-stu-id="e700f-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="e700f-173">某些聯集案例不是遞迴的，且代表 `Number` () 的 () 或變數 `Variable` 。</span><span class="sxs-lookup"><span data-stu-id="e700f-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="e700f-174">其他案例是遞迴的，表示作業 (`Add` 和 `Multiply`) ，其中運算元也是運算式。</span><span class="sxs-lookup"><span data-stu-id="e700f-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="e700f-175">`Evaluate`函數會使用 match 運算式以遞迴方式處理語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e700f-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="e700f-176">執行此程式碼時，的值 `result` 為5。</span><span class="sxs-lookup"><span data-stu-id="e700f-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="e700f-177">成員</span><span class="sxs-lookup"><span data-stu-id="e700f-177">Members</span></span>

<span data-ttu-id="e700f-178">您可以定義區分等位的成員。</span><span class="sxs-lookup"><span data-stu-id="e700f-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="e700f-179">下列範例顯示如何定義屬性並執行介面：</span><span class="sxs-lookup"><span data-stu-id="e700f-179">The following example shows how to define a property and implement an interface:</span></span>

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

## <a name="common-attributes"></a><span data-ttu-id="e700f-180">通用屬性</span><span class="sxs-lookup"><span data-stu-id="e700f-180">Common attributes</span></span>

<span data-ttu-id="e700f-181">下列屬性通常會出現在區分等位中：</span><span class="sxs-lookup"><span data-stu-id="e700f-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="e700f-182">請參閱</span><span class="sxs-lookup"><span data-stu-id="e700f-182">See also</span></span>

- [<span data-ttu-id="e700f-183">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="e700f-183">F# Language Reference</span></span>](index.md)
