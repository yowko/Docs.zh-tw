---
title: 模式比對 (F#)
description: '了解模式如何在 F # 中用來比較具有邏輯結構的資料、 將資料分解為構成部分，或從資料擷取資訊。'
ms.date: 05/16/2016
ms.openlocfilehash: 5ad3d3e1a78246afdfa2948fd0fb84fa04686d30
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668479"
---
# <a name="pattern-matching"></a><span data-ttu-id="88811-103">模式比對</span><span class="sxs-lookup"><span data-stu-id="88811-103">Pattern Matching</span></span>

<span data-ttu-id="88811-104">模式是轉換輸入的資料的規則。</span><span class="sxs-lookup"><span data-stu-id="88811-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="88811-105">它們可在 F # 語言比較具有邏輯結構或結構的資料、 將資料分解為構成部分，或以各種方式從資料擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="88811-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="88811-106">備註</span><span class="sxs-lookup"><span data-stu-id="88811-106">Remarks</span></span>

<span data-ttu-id="88811-107">模式可用於許多語言建構，例如`match`運算式。</span><span class="sxs-lookup"><span data-stu-id="88811-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="88811-108">您正在處理中的函式的引數時，它們會使用`let`繫結、 lambda 運算式，並與相關聯的例外狀況處理常式中`try...with`運算式。</span><span class="sxs-lookup"><span data-stu-id="88811-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="88811-109">如需詳細資訊，請參閱 <<c0> [ 比對運算式](match-expressions.md)， [let 繫結](functions/let-bindings.md)， [Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)，以及[例外狀況： `try...with`運算式](exception-handling/the-try-with-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="88811-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="88811-110">例如，在`match`運算式*模式*是什麼位於管道符號後面。</span><span class="sxs-lookup"><span data-stu-id="88811-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="88811-111">每個模式做為轉換以某種方式輸入的規則。</span><span class="sxs-lookup"><span data-stu-id="88811-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="88811-112">在 `match`運算式中，每個模式會接著檢查輸入的資料是否與模式相容。</span><span class="sxs-lookup"><span data-stu-id="88811-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="88811-113">如果找到相符項目，則會執行結果運算式。</span><span class="sxs-lookup"><span data-stu-id="88811-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="88811-114">如果找不到相符項目，則會測試下一個模式規則。</span><span class="sxs-lookup"><span data-stu-id="88811-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="88811-115">選擇性 when*條件*組件會說明[比對運算式](match-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="88811-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="88811-116">下表顯示支援的模式。</span><span class="sxs-lookup"><span data-stu-id="88811-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="88811-117">在執行階段，針對每個資料表中列出的順序中的下列模式輸入測試和模式，遞迴地套用，從第一次到最後一個出現在您的程式碼，並從左到右的模式，便在每一行。</span><span class="sxs-lookup"><span data-stu-id="88811-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="88811-118">名稱</span><span class="sxs-lookup"><span data-stu-id="88811-118">Name</span></span>|<span data-ttu-id="88811-119">描述</span><span class="sxs-lookup"><span data-stu-id="88811-119">Description</span></span>|<span data-ttu-id="88811-120">範例</span><span class="sxs-lookup"><span data-stu-id="88811-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="88811-121">常數模式</span><span class="sxs-lookup"><span data-stu-id="88811-121">Constant pattern</span></span>|<span data-ttu-id="88811-122">任何數值、 字元或字串常值、 列舉常數或定義的常值識別項</span><span class="sxs-lookup"><span data-stu-id="88811-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="88811-123">`1.0`、`"test"`、`30``Color.Red`</span><span class="sxs-lookup"><span data-stu-id="88811-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="88811-124">識別項模式</span><span class="sxs-lookup"><span data-stu-id="88811-124">Identifier pattern</span></span>|<span data-ttu-id="88811-125">已區分的聯集、 例外狀況標籤或作用中模式案例的情況下，值</span><span class="sxs-lookup"><span data-stu-id="88811-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="88811-126">變數模式</span><span class="sxs-lookup"><span data-stu-id="88811-126">Variable pattern</span></span>|<span data-ttu-id="88811-127">*identifier*</span><span class="sxs-lookup"><span data-stu-id="88811-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="88811-128">`as` 模式</span><span class="sxs-lookup"><span data-stu-id="88811-128">`as` pattern</span></span>|<span data-ttu-id="88811-129">*圖樣*做為*識別碼*</span><span class="sxs-lookup"><span data-stu-id="88811-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="88811-130">或模式</span><span class="sxs-lookup"><span data-stu-id="88811-130">OR pattern</span></span>|<span data-ttu-id="88811-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="88811-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="88811-132">和模式</span><span class="sxs-lookup"><span data-stu-id="88811-132">AND pattern</span></span>|<span data-ttu-id="88811-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="88811-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="88811-134">Cons 模式</span><span class="sxs-lookup"><span data-stu-id="88811-134">Cons pattern</span></span>|<span data-ttu-id="88811-135">*識別項*::*清單識別碼*</span><span class="sxs-lookup"><span data-stu-id="88811-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="88811-136">清單模式</span><span class="sxs-lookup"><span data-stu-id="88811-136">List pattern</span></span>|<span data-ttu-id="88811-137">[ *pattern_1*;...&lt;*pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="88811-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="88811-138">陣列模式</span><span class="sxs-lookup"><span data-stu-id="88811-138">Array pattern</span></span>|<span data-ttu-id="88811-139">[&#124; *pattern_1*;..;*pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="88811-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="88811-140">括號模式</span><span class="sxs-lookup"><span data-stu-id="88811-140">Parenthesized pattern</span></span>|<span data-ttu-id="88811-141">(*模式*)</span><span class="sxs-lookup"><span data-stu-id="88811-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="88811-142">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="88811-142">Tuple pattern</span></span>|<span data-ttu-id="88811-143">( *pattern_1*，...， *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="88811-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="88811-144">記錄模式</span><span class="sxs-lookup"><span data-stu-id="88811-144">Record pattern</span></span>|<span data-ttu-id="88811-145">{ *identifier1* = *pattern_1*;...&lt;*identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="88811-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="88811-146">萬用字元模式</span><span class="sxs-lookup"><span data-stu-id="88811-146">Wildcard pattern</span></span>|<span data-ttu-id="88811-147">_</span><span class="sxs-lookup"><span data-stu-id="88811-147">_</span></span>|`_`|
|<span data-ttu-id="88811-148">搭配類型附註的模式</span><span class="sxs-lookup"><span data-stu-id="88811-148">Pattern together with type annotation</span></span>|<span data-ttu-id="88811-149">*圖樣*:*類型*</span><span class="sxs-lookup"><span data-stu-id="88811-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="88811-150">類型測試模式</span><span class="sxs-lookup"><span data-stu-id="88811-150">Type test pattern</span></span>|<span data-ttu-id="88811-151">:?</span><span class="sxs-lookup"><span data-stu-id="88811-151">:?</span></span> <span data-ttu-id="88811-152">*型別*[做為*識別碼*]</span><span class="sxs-lookup"><span data-stu-id="88811-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="88811-153">Null 模式</span><span class="sxs-lookup"><span data-stu-id="88811-153">Null pattern</span></span>|<span data-ttu-id="88811-154">null</span><span class="sxs-lookup"><span data-stu-id="88811-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="88811-155">常數模式</span><span class="sxs-lookup"><span data-stu-id="88811-155">Constant Patterns</span></span>

<span data-ttu-id="88811-156">常數模式是 （使用包含列舉型別名稱） 的數值、 字元和字串常值、 列舉常數。</span><span class="sxs-lookup"><span data-stu-id="88811-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="88811-157">A`match`只有常數模式的運算式好比其他語言的 case 陳述式。</span><span class="sxs-lookup"><span data-stu-id="88811-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="88811-158">與常值進行比較的輸入和模式比對的值是否相等。</span><span class="sxs-lookup"><span data-stu-id="88811-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="88811-159">常值類型必須與輸入的類型相容。</span><span class="sxs-lookup"><span data-stu-id="88811-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="88811-160">下列範例會示範如何使用常值的模式，並也會使用變數模式和 OR 模式。</span><span class="sxs-lookup"><span data-stu-id="88811-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="88811-161">常值模式的另一個範例是基於列舉常數的模式。</span><span class="sxs-lookup"><span data-stu-id="88811-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="88811-162">當您使用列舉常數時，您必須指定列舉型別名稱。</span><span class="sxs-lookup"><span data-stu-id="88811-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="88811-163">識別項模式</span><span class="sxs-lookup"><span data-stu-id="88811-163">Identifier Patterns</span></span>

<span data-ttu-id="88811-164">如果模式是形成有效識別碼字元的字串，識別項的格式會決定如何比對的模式。</span><span class="sxs-lookup"><span data-stu-id="88811-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="88811-165">如果識別項的長度大於單一字元，且開頭為大寫的字元，編譯器會嘗試比對識別項模式。</span><span class="sxs-lookup"><span data-stu-id="88811-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="88811-166">此模式的識別項可能是常值的屬性、 差別的聯集、 例外狀況識別項或現用模式案例所標記的值。</span><span class="sxs-lookup"><span data-stu-id="88811-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="88811-167">如果不找到任何相符的識別項，則比對失敗下, 一個模式規則，該變數的模式，相較於輸入。</span><span class="sxs-lookup"><span data-stu-id="88811-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="88811-168">已區分的聯集模式可以是簡單的具名案例，或可以有一個值或包含多個值的 tuple。</span><span class="sxs-lookup"><span data-stu-id="88811-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="88811-169">如果沒有值，您必須指定值的識別碼。</span><span class="sxs-lookup"><span data-stu-id="88811-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="88811-170">如果是 tuple，您必須提供 tuple 模式 tuple 的每個元素的識別碼或識別項使用欄位名稱，其中一個或多個具名聯合欄位。</span><span class="sxs-lookup"><span data-stu-id="88811-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="88811-171">請參閱本節的範例中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="88811-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="88811-172">`option`型別是具有兩個案例的已區分聯集`Some`和`None`。</span><span class="sxs-lookup"><span data-stu-id="88811-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="88811-173">其中一個案例 (`Some`) 有值，但其他 (`None`) 只是具名的案例。</span><span class="sxs-lookup"><span data-stu-id="88811-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="88811-174">因此，`Some`必須有相關聯的值的變數`Some`案例，但`None`必須單獨出現。</span><span class="sxs-lookup"><span data-stu-id="88811-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="88811-175">下列程式碼中，變數`var1`的值會指定所比對，以取得`Some`案例。</span><span class="sxs-lookup"><span data-stu-id="88811-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="88811-176">在下列範例中，`PersonName`差別等位包含字串和字元，表示可能名稱形式的混合。</span><span class="sxs-lookup"><span data-stu-id="88811-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="88811-177">已區分的聯集的情況下都`FirstOnly`， `LastOnly`，和`FirstLast`。</span><span class="sxs-lookup"><span data-stu-id="88811-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="88811-178">針對擁有具名欄位的差別聯集，您可以使用等號 （=） 擷取具名欄位的值。</span><span class="sxs-lookup"><span data-stu-id="88811-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="88811-179">比方說，請考慮使用的宣告，如下所示的已區分聯集。</span><span class="sxs-lookup"><span data-stu-id="88811-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="88811-180">您可以使用模式比對運算式中的具名的欄位，如下所示。</span><span class="sxs-lookup"><span data-stu-id="88811-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="88811-181">具名欄位的使用是選擇性的因此在上述範例中，同時`Circle(r)`和`Circle(radius = r)`有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="88811-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="88811-182">當您指定多個欄位時，請使用分號 （;） 做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="88811-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="88811-183">作用中的模式可讓您定義更複雜的自訂模式比對。</span><span class="sxs-lookup"><span data-stu-id="88811-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="88811-184">如需有關使用中模式的詳細資訊，請參閱[作用中的模式](active-patterns.md)。</span><span class="sxs-lookup"><span data-stu-id="88811-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="88811-185">識別項例外狀況的情況用於模式比對的例外狀況處理常式內容中。</span><span class="sxs-lookup"><span data-stu-id="88811-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="88811-186">模式比對的例外狀況處理的相關資訊，請參閱[例外狀況：`try...with`運算式](exception-handling/the-try-with-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="88811-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="88811-187">變數模式</span><span class="sxs-lookup"><span data-stu-id="88811-187">Variable Patterns</span></span>

<span data-ttu-id="88811-188">變數模式會將符合變數的名稱，就可用於執行運算式右邊的值指派`->`符號。</span><span class="sxs-lookup"><span data-stu-id="88811-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="88811-189">變數模式本身會符合任何輸入，但是變數模式通常會出現在其他模式，因此可讓更複雜的結構，例如 tuple 和分解為變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="88811-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="88811-190">下列範例會示範 tuple 模式中的變數模式。</span><span class="sxs-lookup"><span data-stu-id="88811-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="88811-191">as 模式</span><span class="sxs-lookup"><span data-stu-id="88811-191">as Pattern</span></span>

<span data-ttu-id="88811-192">`as`模式是具有模式`as`子句附加到它。</span><span class="sxs-lookup"><span data-stu-id="88811-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="88811-193">`as`子句將相符的值繫結至可用的執行運算式中的名稱`match`運算式，或在此模式中的使用案例中`let`繫結，名稱會加入為區域範圍繫結。</span><span class="sxs-lookup"><span data-stu-id="88811-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="88811-194">下列範例會使用`as`模式。</span><span class="sxs-lookup"><span data-stu-id="88811-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="88811-195">或模式</span><span class="sxs-lookup"><span data-stu-id="88811-195">OR Pattern</span></span>

<span data-ttu-id="88811-196">時輸入的資料可以符合多個模式，而且您想要執行相同的程式碼，如此一來，就會使用 OR 模式。</span><span class="sxs-lookup"><span data-stu-id="88811-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="88811-197">OR 模式兩邊的類型必須相容。</span><span class="sxs-lookup"><span data-stu-id="88811-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="88811-198">下列範例會示範 OR 模式。</span><span class="sxs-lookup"><span data-stu-id="88811-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="88811-199">和模式</span><span class="sxs-lookup"><span data-stu-id="88811-199">AND Pattern</span></span>

<span data-ttu-id="88811-200">AND 模式要求輸入應符合兩個模式。</span><span class="sxs-lookup"><span data-stu-id="88811-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="88811-201">AND 模式兩邊的類型必須相容。</span><span class="sxs-lookup"><span data-stu-id="88811-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="88811-202">下列範例很相似`detectZeroTuple`示[Tuple 模式](https://msdn.microsoft.com/library/#tuple)稍後本主題中，但在此節`var1`和`var2`透過 AND 模式取得的值。</span><span class="sxs-lookup"><span data-stu-id="88811-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="88811-203">Cons 模式</span><span class="sxs-lookup"><span data-stu-id="88811-203">Cons Pattern</span></span>

<span data-ttu-id="88811-204">Cons 模式用來將清單分解為第一個項目中， *head*，以及包含其餘的項目，清單*結尾*。</span><span class="sxs-lookup"><span data-stu-id="88811-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="88811-205">清單模式</span><span class="sxs-lookup"><span data-stu-id="88811-205">List Pattern</span></span>

<span data-ttu-id="88811-206">清單模式可讓清單分解為的項目數目。</span><span class="sxs-lookup"><span data-stu-id="88811-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="88811-207">清單模式本身可以比對只列出特定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="88811-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="88811-208">陣列模式</span><span class="sxs-lookup"><span data-stu-id="88811-208">Array Pattern</span></span>

<span data-ttu-id="88811-209">陣列模式類似於清單模式，並可用於分解特定長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="88811-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="88811-210">括號模式</span><span class="sxs-lookup"><span data-stu-id="88811-210">Parenthesized Pattern</span></span>

<span data-ttu-id="88811-211">括號可括住模式，達到所需的關聯性。</span><span class="sxs-lookup"><span data-stu-id="88811-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="88811-212">在下列範例中，會使用括號控制 AND 模式和 cons 模式之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="88811-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="88811-213">Tuple 模式</span><span class="sxs-lookup"><span data-stu-id="88811-213">Tuple Pattern</span></span>

<span data-ttu-id="88811-214">Tuple 模式比對 tuple 形式的輸入，並讓 tuple 分解為其構成項目使用模式比對 tuple 中的每個位置的變數。</span><span class="sxs-lookup"><span data-stu-id="88811-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="88811-215">下列範例會示範 tuple 模式，並也會使用常值模式、 變數模式和萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="88811-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="88811-216">記錄模式</span><span class="sxs-lookup"><span data-stu-id="88811-216">Record Pattern</span></span>

<span data-ttu-id="88811-217">記錄模式用來分解記錄以擷取欄位的值。</span><span class="sxs-lookup"><span data-stu-id="88811-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="88811-218">此模式不需要參考記錄; 的所有欄位只要任何省略的欄位不會參與比對，並不會擷取。</span><span class="sxs-lookup"><span data-stu-id="88811-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="88811-219">萬用字元模式</span><span class="sxs-lookup"><span data-stu-id="88811-219">Wildcard Pattern</span></span>

<span data-ttu-id="88811-220">萬用字元模式以底線 (`_`) 字元和符合任何輸入，如同變數模式中，不同之處在於將輸入捨棄而不是指派給變數。</span><span class="sxs-lookup"><span data-stu-id="88811-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="88811-221">萬用字元模式通常用來在其他模式做為預留位置值右邊的運算式中不需要`->`符號。</span><span class="sxs-lookup"><span data-stu-id="88811-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="88811-222">萬用字元模式也常使用的模式清單結尾來比對任何不相符的輸入。</span><span class="sxs-lookup"><span data-stu-id="88811-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="88811-223">本主題中的許多程式碼範例將示範萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="88811-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="88811-224">請參閱上述的程式碼取得一例。</span><span class="sxs-lookup"><span data-stu-id="88811-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="88811-225">具有類型附註的模式</span><span class="sxs-lookup"><span data-stu-id="88811-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="88811-226">模式可以有類型註解。</span><span class="sxs-lookup"><span data-stu-id="88811-226">Patterns can have type annotations.</span></span> <span data-ttu-id="88811-227">這些行為類似其他型別註解，會指引推斷等其他型別註解。</span><span class="sxs-lookup"><span data-stu-id="88811-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="88811-228">在模式中的型別附註前後需要括號。</span><span class="sxs-lookup"><span data-stu-id="88811-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="88811-229">下列程式碼會顯示有類型註釋的模式。</span><span class="sxs-lookup"><span data-stu-id="88811-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="88811-230">類型測試模式</span><span class="sxs-lookup"><span data-stu-id="88811-230">Type Test Pattern</span></span>

<span data-ttu-id="88811-231">類型測試模式用來比對類型。</span><span class="sxs-lookup"><span data-stu-id="88811-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="88811-232">如果輸入的類型比對 （或衍生的型別） 中的模式比對指定的類型就會成功。</span><span class="sxs-lookup"><span data-stu-id="88811-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="88811-233">下列範例將示範類型測試模式。</span><span class="sxs-lookup"><span data-stu-id="88811-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="88811-234">Null 模式</span><span class="sxs-lookup"><span data-stu-id="88811-234">Null Pattern</span></span>

<span data-ttu-id="88811-235">Null 模式比對您正在使用允許 null 值的類型，可能會出現 null 值。</span><span class="sxs-lookup"><span data-stu-id="88811-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="88811-236">Null 模式常用於與.NET Framework 程式碼交互作用時。</span><span class="sxs-lookup"><span data-stu-id="88811-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="88811-237">例如，.NET API 的傳回值可能的輸入`match`運算式。</span><span class="sxs-lookup"><span data-stu-id="88811-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="88811-238">您可以控制是否傳回的值為 null，同時也會在傳回值的其他特性為基礎的程式流程。</span><span class="sxs-lookup"><span data-stu-id="88811-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="88811-239">您可以使用 null 模式，以防止將 null 值傳播至程式其餘部分。</span><span class="sxs-lookup"><span data-stu-id="88811-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="88811-240">下列範例會使用 null 模式和變數模式。</span><span class="sxs-lookup"><span data-stu-id="88811-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="88811-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88811-241">See also</span></span>

- [<span data-ttu-id="88811-242">比對運算式</span><span class="sxs-lookup"><span data-stu-id="88811-242">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="88811-243">使用中模式</span><span class="sxs-lookup"><span data-stu-id="88811-243">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="88811-244">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="88811-244">F# Language Reference</span></span>](index.md)
