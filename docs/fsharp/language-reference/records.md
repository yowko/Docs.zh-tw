---
title: 資料錄
description: 了解如何F#記錄代表具名的值，並選擇性地使用成員的簡單彙總。
ms.date: 05/16/2016
ms.openlocfilehash: a499755383654ddaf76af12776ee93f27834b7b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795417"
---
# <a name="records"></a><span data-ttu-id="3ac8f-103">資料錄</span><span class="sxs-lookup"><span data-stu-id="3ac8f-103">Records</span></span>

<span data-ttu-id="3ac8f-104">記錄表示具名值的簡單彙總，並選擇性地搭配成員。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-104">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="3ac8f-105">開頭為F#4.1，它們可以是結構或參考類型。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-105">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="3ac8f-106">它們是預設的參考型別。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ac8f-107">語法</span><span class="sxs-lookup"><span data-stu-id="3ac8f-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="3ac8f-108">備註</span><span class="sxs-lookup"><span data-stu-id="3ac8f-108">Remarks</span></span>

<span data-ttu-id="3ac8f-109">在先前語法中， *typename*是記錄型別名稱*label1*並*label2*名稱的值，稱為*標籤*，並*type1*並*type2*是這些值的類型。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="3ac8f-110">*成員清單*是選用的 成員類型的清單。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="3ac8f-111">您可以使用`[<Struct>]`屬性來建立結構的記錄，而不是參考類型的記錄。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="3ac8f-112">以下是一些範例。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="3ac8f-113">在不同行上每個標籤時，分號是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="3ac8f-114">您可以設定值，在運算式中稱為*記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="3ac8f-115">編譯器會推斷的型別與使用 （如果標籤為完全不同於其他記錄類型的項目） 的標籤。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="3ac8f-116">大括號 （{}） 括住記錄運算式。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="3ac8f-117">下列程式碼會顯示記錄運算式初始化的記錄中包含三個標籤的 float 元素`x`，`y`和`z`。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="3ac8f-118">如果可能有另一個型別也有相同的標籤，請務必使用縮短的格式。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="3ac8f-119">最近宣告之型別的標籤優先於先前宣告的型別，因此在上述範例中，`mypoint3D`被推斷為`Point3D`。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="3ac8f-120">您可以明確指定記錄類型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="3ac8f-121">可以定義方法，如同類別類型的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="3ac8f-122">使用記錄運算式建立記錄</span><span class="sxs-lookup"><span data-stu-id="3ac8f-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="3ac8f-123">您可以使用記錄中所定義的標籤，來初始化記錄。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="3ac8f-124">此運算式指*記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="3ac8f-125">使用大括號括住記錄運算式，並以分號作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="3ac8f-126">下列範例示範如何建立記錄。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="3ac8f-127">記錄運算式和型別定義中的最後一個欄位之後分號是選擇性的不論是否在一行中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="3ac8f-128">當您建立一筆記錄時，您必須提供每個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="3ac8f-129">您不能參考任何欄位的初始化運算式中的其他欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="3ac8f-130">下列程式碼的型別`myRecord2`從欄位的名稱來推斷。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="3ac8f-131">（選擇性） 您也可以明確指定的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="3ac8f-132">您必須複製現有的記錄，並可能變更的某些欄位值時，記錄建構的另一種很有用。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="3ac8f-133">下列程式碼說明這點。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="3ac8f-134">這種形式的記錄運算式稱為*複製並更新記錄運算式*。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="3ac8f-135">記錄是不可變的預設值;不過，您可以使用複製和更新的運算式來輕鬆建立修改過的記錄。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="3ac8f-136">您也可以明確指定的可變動的欄位。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="3ac8f-137">不使用記錄欄位的 DefaultValue 屬性。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="3ac8f-138">更好的方法是定義預設執行個體的記錄與欄位初始化為預設值然後使用複製和更新記錄運算式來設定不同的預設值的任何欄位。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

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

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="3ac8f-139">建立相互遞迴記錄</span><span class="sxs-lookup"><span data-stu-id="3ac8f-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="3ac8f-140">一段時間建立時的記錄，您可以將它取決於您想要定義之後的另一個類型。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="3ac8f-141">這是編譯錯誤，除非您定義要相互遞迴的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="3ac8f-142">使用者相互定義遞迴記錄利用`and`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="3ac8f-143">這可讓您將 2 個或更多記錄類型連結在一起。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="3ac8f-144">例如，下列程式碼定義`Person`和`Address`相互遞迴類型：</span><span class="sxs-lookup"><span data-stu-id="3ac8f-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string }
```

<span data-ttu-id="3ac8f-145">如果您要定義不含先前的範例`and`關鍵字，則不進行編譯。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="3ac8f-146">`and`關鍵字是為了相互遞迴定義。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="3ac8f-147">模式比對與記錄</span><span class="sxs-lookup"><span data-stu-id="3ac8f-147">Pattern Matching with Records</span></span>

<span data-ttu-id="3ac8f-148">記錄可以搭配模式比對。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="3ac8f-149">您可以明確指定某些欄位，並提供變數的相符項目，就會發生時要指派其他欄位。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="3ac8f-150">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="3ac8f-151">此程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-151">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="3ac8f-152">記錄和類別之間的差異</span><span class="sxs-lookup"><span data-stu-id="3ac8f-152">Differences Between Records and Classes</span></span>

<span data-ttu-id="3ac8f-153">記錄欄位和類別不同，它們會自動公開為屬性，而且它們是用於建立和複製的記錄。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-153">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="3ac8f-154">記錄建構也不同於類別的建構。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-154">Record construction also differs from class construction.</span></span> <span data-ttu-id="3ac8f-155">在 記錄類型，您無法定義建構函式。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-155">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="3ac8f-156">相反地，適用於本主題中所述的建構語法。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-156">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="3ac8f-157">類別具有建構函式參數、 欄位和屬性之間沒有直接關聯性。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-157">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="3ac8f-158">等位和結構類型，例如記錄都有結構相等語意。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-158">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="3ac8f-159">類別具有參考相等語意。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-159">Classes have reference equality semantics.</span></span> <span data-ttu-id="3ac8f-160">下列程式碼範例示範此工作。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-160">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="3ac8f-161">此程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="3ac8f-161">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="3ac8f-162">因為兩個值代表在堆積上的兩個物件，而且只有位址會相較，兩個類別物件如果您撰寫相同的程式碼使用類別時，應該不相等 (除非覆寫的類別型別`System.Object.Equals`方法)。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-162">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="3ac8f-163">如果您需要參考記錄的等號比較，請將屬性加入`[<ReferenceEquality>]`上述記錄。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-163">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ac8f-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ac8f-164">See also</span></span>

- [<span data-ttu-id="3ac8f-165">F# 類型</span><span class="sxs-lookup"><span data-stu-id="3ac8f-165">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="3ac8f-166">類別</span><span class="sxs-lookup"><span data-stu-id="3ac8f-166">Classes</span></span>](classes.md)
- [<span data-ttu-id="3ac8f-167">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="3ac8f-167">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="3ac8f-168">Reference-Equality</span><span class="sxs-lookup"><span data-stu-id="3ac8f-168">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="3ac8f-169">模式比對</span><span class="sxs-lookup"><span data-stu-id="3ac8f-169">Pattern Matching</span></span>](pattern-matching.md)
