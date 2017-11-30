---
title: "資料錄 (F#)"
description: "了解 F # 記錄代表具名的值，選擇性地具有成員的簡單彙總的方式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: f5ade1db39431d99f10eb6967f02335123b83d34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="records"></a><span data-ttu-id="35936-104">資料錄</span><span class="sxs-lookup"><span data-stu-id="35936-104">Records</span></span>

<span data-ttu-id="35936-105">記錄表示具名值的簡單彙總，並選擇性地搭配成員。</span><span class="sxs-lookup"><span data-stu-id="35936-105">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="35936-106">從 F # 4.1 開始，它們可以是結構或參考類型。</span><span class="sxs-lookup"><span data-stu-id="35936-106">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="35936-107">它們都是預設的參考類型。</span><span class="sxs-lookup"><span data-stu-id="35936-107">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="35936-108">語法</span><span class="sxs-lookup"><span data-stu-id="35936-108">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="35936-109">備註</span><span class="sxs-lookup"><span data-stu-id="35936-109">Remarks</span></span>
<span data-ttu-id="35936-110">在先前的語法， *typename*是記錄型別名稱*label1*和*label2*是名稱的值，稱為*標籤*，和*type1*和*type2*是這些值的類型。</span><span class="sxs-lookup"><span data-stu-id="35936-110">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="35936-111">*成員清單*是選用的成員類型的清單。</span><span class="sxs-lookup"><span data-stu-id="35936-111">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="35936-112">您可以使用`[<Struct>]`屬性來建立結構記錄，而不是參考類型的記錄。</span><span class="sxs-lookup"><span data-stu-id="35936-112">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="35936-113">以下是一些範例。</span><span class="sxs-lookup"><span data-stu-id="35936-113">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="35936-114">在不同行的每個標籤時，分號是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="35936-114">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="35936-115">您可以設定值，在運算式中稱為*記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="35936-115">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="35936-116">編譯器會推斷的型別與使用 （如果將標籤是完全不同於其他記錄類型的項目） 的標籤。</span><span class="sxs-lookup"><span data-stu-id="35936-116">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="35936-117">大括號 （{}） 括住記錄運算式。</span><span class="sxs-lookup"><span data-stu-id="35936-117">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="35936-118">下列程式碼示範初始化的記錄包含三個具有標籤浮動元素的記錄運算式`x`，`y`和`z`。</span><span class="sxs-lookup"><span data-stu-id="35936-118">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="35936-119">請勿使用縮短形式，如果可能有另一個型別也有相同的標籤。</span><span class="sxs-lookup"><span data-stu-id="35936-119">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="35936-120">之標籤的 最近宣告的型別會優先於先前宣告的型別，因此在上述範例中，`mypoint3D`就會推斷`Point3D`。</span><span class="sxs-lookup"><span data-stu-id="35936-120">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="35936-121">您可以明確指定記錄類型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="35936-121">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="35936-122">方法只適用於類別類型的記錄類型定義。</span><span class="sxs-lookup"><span data-stu-id="35936-122">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="35936-123">使用記錄運算式建立的記錄</span><span class="sxs-lookup"><span data-stu-id="35936-123">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="35936-124">您可以使用記錄中所定義的標籤，來初始化記錄。</span><span class="sxs-lookup"><span data-stu-id="35936-124">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="35936-125">此運算式指*記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="35936-125">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="35936-126">使用大括號括住記錄運算式，並以分號作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="35936-126">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="35936-127">下列範例會示範如何建立記錄。</span><span class="sxs-lookup"><span data-stu-id="35936-127">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="35936-128">分號之後記錄運算式和型別定義中的最後一個欄位是選擇性的不論是否在一行中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="35936-128">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="35936-129">當您建立一筆記錄時，您必須提供每個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="35936-129">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="35936-130">您不能參考任何欄位的初始化運算式中的其他欄位的值。</span><span class="sxs-lookup"><span data-stu-id="35936-130">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="35936-131">下列程式碼的型別`myRecord2`推斷從欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="35936-131">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="35936-132">（選擇性） 您可以明確指定的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="35936-132">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="35936-133">當您必須複製現有的記錄，並可能變更的某些欄位值時，記錄建構的另一種很有用。</span><span class="sxs-lookup"><span data-stu-id="35936-133">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="35936-134">下列程式碼說明這點。</span><span class="sxs-lookup"><span data-stu-id="35936-134">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="35936-135">這種記錄運算式形式呼叫*複製並更新記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="35936-135">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="35936-136">記錄是不可變的預設值;不過，您可以使用複製並更新運算式輕鬆地建立已修改的記錄。</span><span class="sxs-lookup"><span data-stu-id="35936-136">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="35936-137">您可以同時也可以明確指定可變動的欄位。</span><span class="sxs-lookup"><span data-stu-id="35936-137">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="35936-138">請不要使用記錄欄位 DefaultValue 屬性。</span><span class="sxs-lookup"><span data-stu-id="35936-138">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="35936-139">更好的方法是定義為預設值初始化的欄位與記錄的預設執行個體然後使用複製和更新記錄運算式來設定所有預設值不同的欄位。</span><span class="sxs-lookup"><span data-stu-id="35936-139">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="35936-140">模式比對與記錄</span><span class="sxs-lookup"><span data-stu-id="35936-140">Pattern Matching with Records</span></span>
<span data-ttu-id="35936-141">記錄可以搭配模式比對。</span><span class="sxs-lookup"><span data-stu-id="35936-141">Records can be used with pattern matching.</span></span> <span data-ttu-id="35936-142">您可以明確地指定某些欄位，並提供變數的相符項目時要指派其他欄位。</span><span class="sxs-lookup"><span data-stu-id="35936-142">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="35936-143">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="35936-143">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="35936-144">此程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="35936-144">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="35936-145">記錄和類別之間的差異</span><span class="sxs-lookup"><span data-stu-id="35936-145">Differences Between Records and Classes</span></span>
<span data-ttu-id="35936-146">也就是說，它們會自動公開為屬性，並且它們是用於建立和複製的記錄與類別不同記錄欄位。</span><span class="sxs-lookup"><span data-stu-id="35936-146">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="35936-147">資料錄建構也不同於類別建構。</span><span class="sxs-lookup"><span data-stu-id="35936-147">Record construction also differs from class construction.</span></span> <span data-ttu-id="35936-148">在記錄類型，您無法定義建構函式。</span><span class="sxs-lookup"><span data-stu-id="35936-148">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="35936-149">相反地，適用於本主題中所述的建構語法。</span><span class="sxs-lookup"><span data-stu-id="35936-149">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="35936-150">類別具有建構函式參數、 欄位和屬性之間沒有直接關聯性。</span><span class="sxs-lookup"><span data-stu-id="35936-150">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="35936-151">等位和結構的類型，例如記錄都有結構相等語意。</span><span class="sxs-lookup"><span data-stu-id="35936-151">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="35936-152">類別具有參考相等語意。</span><span class="sxs-lookup"><span data-stu-id="35936-152">Classes have reference equality semantics.</span></span> <span data-ttu-id="35936-153">下列程式碼範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="35936-153">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="35936-154">如果您撰寫的類別相同的程式碼，兩個類別物件會是不相等因為兩個值代表在堆積上的兩個物件，並會比較的地址 (除非類別類型覆寫`System.Object.Equals`方法)。</span><span class="sxs-lookup"><span data-stu-id="35936-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="35936-155">如果您需要參考相等的記錄，將屬性加入`[<ReferenceEquality>]`上述記錄。</span><span class="sxs-lookup"><span data-stu-id="35936-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="35936-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35936-156">See Also</span></span>
[<span data-ttu-id="35936-157">F# 類型</span><span class="sxs-lookup"><span data-stu-id="35936-157">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="35936-158">類別</span><span class="sxs-lookup"><span data-stu-id="35936-158">Classes</span></span>](classes.md)

[<span data-ttu-id="35936-159">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="35936-159">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="35936-160">參考相等</span><span class="sxs-lookup"><span data-stu-id="35936-160">Reference-Equality</span></span>](https://msdn.microsoft.com/en-us/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="35936-161">模式比對</span><span class="sxs-lookup"><span data-stu-id="35936-161">Pattern Matching</span></span>](pattern-matching.md)
