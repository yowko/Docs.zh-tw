---
title: 已區分的聯集
description: 瞭解如何使用 F# 歧視結合。
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400215"
---
# <a name="discriminated-unions"></a><span data-ttu-id="f9b06-103">已區分的聯集</span><span class="sxs-lookup"><span data-stu-id="f9b06-103">Discriminated Unions</span></span>

<span data-ttu-id="f9b06-104">歧視聯合為值提供支援，這些值可以是許多命名案例之一，可能每個值和類型不同。</span><span class="sxs-lookup"><span data-stu-id="f9b06-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="f9b06-105">受歧視結合對異構資料很有用;可能有特殊情況的資料，包括有效和錯誤案例;因類型而異的資料;並作為小物件層次結構的替代方案。</span><span class="sxs-lookup"><span data-stu-id="f9b06-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="f9b06-106">此外，遞迴區分結合用於表示樹資料結構。</span><span class="sxs-lookup"><span data-stu-id="f9b06-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9b06-107">語法</span><span class="sxs-lookup"><span data-stu-id="f9b06-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="f9b06-108">備註</span><span class="sxs-lookup"><span data-stu-id="f9b06-108">Remarks</span></span>

<span data-ttu-id="f9b06-109">歧視聯合與其他語言中的聯合類型類似，但存在差異。</span><span class="sxs-lookup"><span data-stu-id="f9b06-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="f9b06-110">與 C++ 中的聯合類型或 Visual Basic 中的變體類型一樣，存儲在值中的資料不是固定的;它可以是幾個不同的選項之一。</span><span class="sxs-lookup"><span data-stu-id="f9b06-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="f9b06-111">但是，與這些其他語言中的聯合不同，每個可能的選項都給定一個*案例識別碼*。</span><span class="sxs-lookup"><span data-stu-id="f9b06-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="f9b06-112">案例識別碼是此類型物件可能具有的各種可能類型的值的名稱;值是可選的。</span><span class="sxs-lookup"><span data-stu-id="f9b06-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="f9b06-113">如果不存在值，則大小寫等效于枚舉大小寫。</span><span class="sxs-lookup"><span data-stu-id="f9b06-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="f9b06-114">如果存在值，則每個值可以是指定類型的單個值，也可以是聚合相同或不同類型的多個欄位的元組。</span><span class="sxs-lookup"><span data-stu-id="f9b06-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="f9b06-115">您可以為單個欄位指定名稱，但該名稱是可選的，即使在同一情況下命名了其他欄位也是如此。</span><span class="sxs-lookup"><span data-stu-id="f9b06-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="f9b06-116">受歧視聯合的可訪問性`public`預設為 。</span><span class="sxs-lookup"><span data-stu-id="f9b06-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="f9b06-117">例如，請考慮以下形狀類型的聲明。</span><span class="sxs-lookup"><span data-stu-id="f9b06-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="f9b06-118">前面的代碼聲明一個受歧視的聯合形狀，它可以具有三種情況中的任何一個的值：矩形、圓體和棱鏡。</span><span class="sxs-lookup"><span data-stu-id="f9b06-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="f9b06-119">每個案例都有一組不同的欄位。</span><span class="sxs-lookup"><span data-stu-id="f9b06-119">Each case has a different set of fields.</span></span> <span data-ttu-id="f9b06-120">矩形大小寫有兩個命名欄位，兩個`float`命名欄位的類型，具有名稱寬度和長度。</span><span class="sxs-lookup"><span data-stu-id="f9b06-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="f9b06-121">圓大小寫只有一個命名欄位，半徑。</span><span class="sxs-lookup"><span data-stu-id="f9b06-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="f9b06-122">棱鏡大小寫有三個欄位，其中兩個欄位（寬度和高度）被命名為欄位。</span><span class="sxs-lookup"><span data-stu-id="f9b06-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="f9b06-123">未命名的欄位稱為匿名欄位。</span><span class="sxs-lookup"><span data-stu-id="f9b06-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="f9b06-124">通過根據以下示例為命名欄位和匿名欄位提供值來構造物件。</span><span class="sxs-lookup"><span data-stu-id="f9b06-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="f9b06-125">此代碼顯示，您可以在初始化中使用命名欄位，也可以依賴聲明中欄位的順序，並依次為每個欄位提供值。</span><span class="sxs-lookup"><span data-stu-id="f9b06-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="f9b06-126">上一個代碼`rect`中的建構函式調用使用命名欄位，但建構函式調用`circ`使用排序。</span><span class="sxs-lookup"><span data-stu-id="f9b06-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="f9b06-127">可以混合有序欄位和命名欄位，如 在 構造 中`prism`。</span><span class="sxs-lookup"><span data-stu-id="f9b06-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="f9b06-128">該`option`類型是 F# 核心庫中的簡單區分聯合。</span><span class="sxs-lookup"><span data-stu-id="f9b06-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="f9b06-129">類型`option`聲明如下。</span><span class="sxs-lookup"><span data-stu-id="f9b06-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="f9b06-130">前面的代碼指定類型`Option`是具有兩個案例的受歧視聯合，`Some`和`None`。</span><span class="sxs-lookup"><span data-stu-id="f9b06-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="f9b06-131">案例`Some`具有一個關聯值，該值由一個匿名欄位組成，其類型由類型`'a`參數表示。</span><span class="sxs-lookup"><span data-stu-id="f9b06-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="f9b06-132">案例`None`沒有關聯的值。</span><span class="sxs-lookup"><span data-stu-id="f9b06-132">The `None` case has no associated value.</span></span> <span data-ttu-id="f9b06-133">因此，`option`類型指定具有特定類型值或無值的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="f9b06-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="f9b06-134">類型`Option`還有一個小寫類型別名`option`，這是更常用的。</span><span class="sxs-lookup"><span data-stu-id="f9b06-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="f9b06-135">案例識別碼可用作區分聯合類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="f9b06-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="f9b06-136">例如，以下代碼用於創建`option`類型的值。</span><span class="sxs-lookup"><span data-stu-id="f9b06-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="f9b06-137">大小寫識別碼也用於模式匹配運算式。</span><span class="sxs-lookup"><span data-stu-id="f9b06-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="f9b06-138">在模式匹配運算式中，為與單個情況關聯的值提供識別碼。</span><span class="sxs-lookup"><span data-stu-id="f9b06-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="f9b06-139">例如，在以下代碼中，`x`是給定與`Some``option`類型大小寫關聯的值的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f9b06-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="f9b06-140">在模式匹配運算式中，可以使用命名欄位指定受區別的聯合匹配。</span><span class="sxs-lookup"><span data-stu-id="f9b06-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="f9b06-141">對於以前聲明的 Shape 類型，可以使用命名欄位，如以下代碼所示，以提取欄位的值。</span><span class="sxs-lookup"><span data-stu-id="f9b06-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

<span data-ttu-id="f9b06-142">通常，可以使用案例識別碼，而無需使用聯合名稱對其進行限定。</span><span class="sxs-lookup"><span data-stu-id="f9b06-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="f9b06-143">如果希望名稱始終與聯合的名稱限定，則可以將["需要限定Access"](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp])屬性應用於聯合類型定義。</span><span class="sxs-lookup"><span data-stu-id="f9b06-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="f9b06-144">未包裝的受歧視聯合</span><span class="sxs-lookup"><span data-stu-id="f9b06-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="f9b06-145">在 F# 中，區分聯合通常用於域建模，用於包裝單個類型。</span><span class="sxs-lookup"><span data-stu-id="f9b06-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="f9b06-146">通過模式匹配也很容易提取基礎值。</span><span class="sxs-lookup"><span data-stu-id="f9b06-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="f9b06-147">不需要對單個情況使用匹配運算式：</span><span class="sxs-lookup"><span data-stu-id="f9b06-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="f9b06-148">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="f9b06-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="f9b06-149">模式匹配也直接允許在函數參數中進行，因此您可以在那裡打開單個大小寫：</span><span class="sxs-lookup"><span data-stu-id="f9b06-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="f9b06-150">結構歧視聯盟</span><span class="sxs-lookup"><span data-stu-id="f9b06-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="f9b06-151">您還可以將"受歧視聯合"表示為結構。</span><span class="sxs-lookup"><span data-stu-id="f9b06-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="f9b06-152">這使用屬性`[<Struct>]`完成。</span><span class="sxs-lookup"><span data-stu-id="f9b06-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="f9b06-153">由於這些數值型別而不是參考型別，因此與引用區分結合相比，存在額外的注意事項：</span><span class="sxs-lookup"><span data-stu-id="f9b06-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="f9b06-154">它們作為數值型別複製，並且具有數值型別語義。</span><span class="sxs-lookup"><span data-stu-id="f9b06-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="f9b06-155">不能使用具有多大小寫結構的區分聯合的遞迴類型定義。</span><span class="sxs-lookup"><span data-stu-id="f9b06-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="f9b06-156">您必須為多大小寫結構區分聯合提供唯一的案例名稱。</span><span class="sxs-lookup"><span data-stu-id="f9b06-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="f9b06-157">使用可區分聯合而不是物件層次結構</span><span class="sxs-lookup"><span data-stu-id="f9b06-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="f9b06-158">通常可以使用受歧視的聯合作為小物件層次結構的更簡單的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f9b06-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="f9b06-159">例如，可以使用以下受歧視聯合來代替具有圓、平方等`Shape`派生類型的基類。</span><span class="sxs-lookup"><span data-stu-id="f9b06-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="f9b06-160">可以使用模式匹配到分支到適當的公式來計算這些數量，而不是像在物件導向的實現中使用那樣計算區域或週邊的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="f9b06-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="f9b06-161">在下面的示例中，使用不同的公式來計算區域，具體取決於形狀。</span><span class="sxs-lookup"><span data-stu-id="f9b06-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="f9b06-162">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="f9b06-162">The output is as follows:</span></span>

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="f9b06-163">對樹資料結構使用區分聯合</span><span class="sxs-lookup"><span data-stu-id="f9b06-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="f9b06-164">可進行遞迴，這意味著工會本身可以包含在一個或多個案例的類型中。</span><span class="sxs-lookup"><span data-stu-id="f9b06-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="f9b06-165">遞迴區分結合可用於創建樹結構，這些結構用於對程式設計語言中的運算式建模。</span><span class="sxs-lookup"><span data-stu-id="f9b06-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="f9b06-166">在以下代碼中，遞迴區分聯合用於創建二進位樹資料結構。</span><span class="sxs-lookup"><span data-stu-id="f9b06-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="f9b06-167">聯合由兩個案例組成，`Node`即具有整數值的節點和左右子樹，以及`Tip`終止樹。</span><span class="sxs-lookup"><span data-stu-id="f9b06-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="f9b06-168">在前面的代碼中，`resultSumTree`具有值 10。</span><span class="sxs-lookup"><span data-stu-id="f9b06-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="f9b06-169">下圖顯示了 的`myTree`樹結構。</span><span class="sxs-lookup"><span data-stu-id="f9b06-169">The following illustration shows the tree structure for `myTree`.</span></span>

![顯示 MyTree 的樹形結構的圖表。](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="f9b06-171">如果樹中的節點是異構的，則區分結合可以很好地工作。</span><span class="sxs-lookup"><span data-stu-id="f9b06-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="f9b06-172">在以下代碼中，類型`Expression`表示運算式的抽象語法樹，該語言支援數位和變數的添加和乘法。</span><span class="sxs-lookup"><span data-stu-id="f9b06-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="f9b06-173">某些聯合案例不是遞迴的，表示數位 （`Number`） 或變數 （`Variable`） 。</span><span class="sxs-lookup"><span data-stu-id="f9b06-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="f9b06-174">其他情況是遞迴的，並表示操作 （`Add`和`Multiply`），其中運算元也是運算式。</span><span class="sxs-lookup"><span data-stu-id="f9b06-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="f9b06-175">函數`Evaluate`使用匹配運算式遞迴處理語法樹。</span><span class="sxs-lookup"><span data-stu-id="f9b06-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="f9b06-176">執行此代碼時，值`result`為 5。</span><span class="sxs-lookup"><span data-stu-id="f9b06-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="f9b06-177">成員</span><span class="sxs-lookup"><span data-stu-id="f9b06-177">Members</span></span>

<span data-ttu-id="f9b06-178">可以定義受歧視工會的成員。</span><span class="sxs-lookup"><span data-stu-id="f9b06-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="f9b06-179">下面的示例演示如何定義屬性和實現介面：</span><span class="sxs-lookup"><span data-stu-id="f9b06-179">The following example shows how to define a property and implement an interface:</span></span>

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

## <a name="common-attributes"></a><span data-ttu-id="f9b06-180">常見屬性</span><span class="sxs-lookup"><span data-stu-id="f9b06-180">Common attributes</span></span>

<span data-ttu-id="f9b06-181">以下屬性常見於受歧視聯合：</span><span class="sxs-lookup"><span data-stu-id="f9b06-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="f9b06-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9b06-182">See also</span></span>

- [<span data-ttu-id="f9b06-183">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="f9b06-183">F# Language Reference</span></span>](index.md)
