---
title: 資料錄 (F#)
description: '了解 F # 記錄代表具名的值，並選擇性地使用成員的簡單彙總的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 6103d96b6b80a9e2ed168755958dbe800f7fa862
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638546"
---
# <a name="records"></a><span data-ttu-id="e6f39-103">資料錄</span><span class="sxs-lookup"><span data-stu-id="e6f39-103">Records</span></span>

<span data-ttu-id="e6f39-104">記錄表示具名值的簡單彙總，並選擇性地搭配成員。</span><span class="sxs-lookup"><span data-stu-id="e6f39-104">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="e6f39-105">從 F # 4.1 開始，它們可以是結構或參考類型。</span><span class="sxs-lookup"><span data-stu-id="e6f39-105">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="e6f39-106">它們是預設的參考型別。</span><span class="sxs-lookup"><span data-stu-id="e6f39-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6f39-107">語法</span><span class="sxs-lookup"><span data-stu-id="e6f39-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="e6f39-108">備註</span><span class="sxs-lookup"><span data-stu-id="e6f39-108">Remarks</span></span>

<span data-ttu-id="e6f39-109">在先前語法中， *typename*是記錄型別名稱*label1*並*label2*名稱的值，稱為*標籤*，並*type1*並*type2*是這些值的類型。</span><span class="sxs-lookup"><span data-stu-id="e6f39-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="e6f39-110">*成員清單*是選用的 成員類型的清單。</span><span class="sxs-lookup"><span data-stu-id="e6f39-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="e6f39-111">您可以使用`[<Struct>]`屬性來建立結構的記錄，而不是參考類型的記錄。</span><span class="sxs-lookup"><span data-stu-id="e6f39-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="e6f39-112">以下是一些範例。</span><span class="sxs-lookup"><span data-stu-id="e6f39-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="e6f39-113">在不同行上每個標籤時，分號是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e6f39-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="e6f39-114">您可以設定值，在運算式中稱為*記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="e6f39-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="e6f39-115">編譯器會推斷的型別與使用 （如果標籤為完全不同於其他記錄類型的項目） 的標籤。</span><span class="sxs-lookup"><span data-stu-id="e6f39-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="e6f39-116">大括號 （{}） 括住記錄運算式。</span><span class="sxs-lookup"><span data-stu-id="e6f39-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="e6f39-117">下列程式碼會顯示記錄運算式初始化的記錄中包含三個標籤的 float 元素`x`，`y`和`z`。</span><span class="sxs-lookup"><span data-stu-id="e6f39-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="e6f39-118">如果可能有另一個型別也有相同的標籤，請務必使用縮短的格式。</span><span class="sxs-lookup"><span data-stu-id="e6f39-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="e6f39-119">最近宣告之型別的標籤優先於先前宣告的型別，因此在上述範例中，`mypoint3D`被推斷為`Point3D`。</span><span class="sxs-lookup"><span data-stu-id="e6f39-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="e6f39-120">您可以明確指定記錄類型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e6f39-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="e6f39-121">可以定義方法，如同類別類型的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="e6f39-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="e6f39-122">使用記錄運算式建立記錄</span><span class="sxs-lookup"><span data-stu-id="e6f39-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="e6f39-123">您可以使用記錄中所定義的標籤，來初始化記錄。</span><span class="sxs-lookup"><span data-stu-id="e6f39-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="e6f39-124">此運算式指*記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="e6f39-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="e6f39-125">使用大括號括住記錄運算式，並以分號作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e6f39-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="e6f39-126">下列範例示範如何建立記錄。</span><span class="sxs-lookup"><span data-stu-id="e6f39-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="e6f39-127">記錄運算式和型別定義中的最後一個欄位之後分號是選擇性的不論是否在一行中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="e6f39-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="e6f39-128">當您建立一筆記錄時，您必須提供每個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="e6f39-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="e6f39-129">您不能參考任何欄位的初始化運算式中的其他欄位的值。</span><span class="sxs-lookup"><span data-stu-id="e6f39-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="e6f39-130">下列程式碼的型別`myRecord2`從欄位的名稱來推斷。</span><span class="sxs-lookup"><span data-stu-id="e6f39-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="e6f39-131">（選擇性） 您也可以明確指定的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f39-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="e6f39-132">您必須複製現有的記錄，並可能變更的某些欄位值時，記錄建構的另一種很有用。</span><span class="sxs-lookup"><span data-stu-id="e6f39-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="e6f39-133">下列程式碼說明這點。</span><span class="sxs-lookup"><span data-stu-id="e6f39-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="e6f39-134">這種形式的記錄運算式稱為*複製並更新記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="e6f39-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="e6f39-135">記錄是不可變的預設值;不過，您可以使用複製和更新的運算式來輕鬆建立修改過的記錄。</span><span class="sxs-lookup"><span data-stu-id="e6f39-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="e6f39-136">您也可以明確指定的可變動的欄位。</span><span class="sxs-lookup"><span data-stu-id="e6f39-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="e6f39-137">不使用記錄欄位的 DefaultValue 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f39-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="e6f39-138">更好的方法是定義預設執行個體的記錄與欄位初始化為預設值然後使用複製和更新記錄運算式來設定不同的預設值的任何欄位。</span><span class="sxs-lookup"><span data-stu-id="e6f39-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="e6f39-139">模式比對與記錄</span><span class="sxs-lookup"><span data-stu-id="e6f39-139">Pattern Matching with Records</span></span>

<span data-ttu-id="e6f39-140">記錄可以搭配模式比對。</span><span class="sxs-lookup"><span data-stu-id="e6f39-140">Records can be used with pattern matching.</span></span> <span data-ttu-id="e6f39-141">您可以明確指定某些欄位，並提供變數的相符項目，就會發生時要指派其他欄位。</span><span class="sxs-lookup"><span data-stu-id="e6f39-141">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="e6f39-142">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="e6f39-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="e6f39-143">此程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="e6f39-143">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="e6f39-144">記錄和類別之間的差異</span><span class="sxs-lookup"><span data-stu-id="e6f39-144">Differences Between Records and Classes</span></span>

<span data-ttu-id="e6f39-145">記錄欄位和類別不同，它們會自動公開為屬性，而且它們是用於建立和複製的記錄。</span><span class="sxs-lookup"><span data-stu-id="e6f39-145">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="e6f39-146">記錄建構也不同於類別的建構。</span><span class="sxs-lookup"><span data-stu-id="e6f39-146">Record construction also differs from class construction.</span></span> <span data-ttu-id="e6f39-147">在 記錄類型，您無法定義建構函式。</span><span class="sxs-lookup"><span data-stu-id="e6f39-147">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="e6f39-148">相反地，適用於本主題中所述的建構語法。</span><span class="sxs-lookup"><span data-stu-id="e6f39-148">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="e6f39-149">類別具有建構函式參數、 欄位和屬性之間沒有直接關聯性。</span><span class="sxs-lookup"><span data-stu-id="e6f39-149">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="e6f39-150">等位和結構類型，例如記錄都有結構相等語意。</span><span class="sxs-lookup"><span data-stu-id="e6f39-150">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="e6f39-151">類別具有參考相等語意。</span><span class="sxs-lookup"><span data-stu-id="e6f39-151">Classes have reference equality semantics.</span></span> <span data-ttu-id="e6f39-152">下列程式碼範例示範此工作。</span><span class="sxs-lookup"><span data-stu-id="e6f39-152">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="e6f39-153">此程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6f39-153">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="e6f39-154">因為兩個值代表在堆積上的兩個物件，而且只有位址會相較，兩個類別物件如果您撰寫相同的程式碼使用類別時，應該不相等 (除非覆寫的類別型別`System.Object.Equals`方法)。</span><span class="sxs-lookup"><span data-stu-id="e6f39-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="e6f39-155">如果您需要參考記錄的等號比較，請將屬性加入`[<ReferenceEquality>]`上述記錄。</span><span class="sxs-lookup"><span data-stu-id="e6f39-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6f39-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f39-156">See also</span></span>

- [<span data-ttu-id="e6f39-157">F# 類型</span><span class="sxs-lookup"><span data-stu-id="e6f39-157">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="e6f39-158">類別</span><span class="sxs-lookup"><span data-stu-id="e6f39-158">Classes</span></span>](classes.md)
- [<span data-ttu-id="e6f39-159">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e6f39-159">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e6f39-160">參考相等</span><span class="sxs-lookup"><span data-stu-id="e6f39-160">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="e6f39-161">模式比對</span><span class="sxs-lookup"><span data-stu-id="e6f39-161">Pattern Matching</span></span>](pattern-matching.md)
