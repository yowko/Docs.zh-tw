---
title: 運算子多載 (F#)
description: '了解如何多載算術的運算子，在類別或記錄類型，然後在 F # 中的全域層級。'
ms.date: 05/16/2016
ms.openlocfilehash: 6232ebf215289e6a22b9d77fbd5fa67b82460486
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44087295"
---
# <a name="operator-overloading"></a><span data-ttu-id="7589f-103">運算子多載</span><span class="sxs-lookup"><span data-stu-id="7589f-103">Operator Overloading</span></span>

<span data-ttu-id="7589f-104">本主題描述如何多載算術的運算子，在類別或記錄類型，並在全域層級。</span><span class="sxs-lookup"><span data-stu-id="7589f-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="7589f-105">語法</span><span class="sxs-lookup"><span data-stu-id="7589f-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="7589f-106">備註</span><span class="sxs-lookup"><span data-stu-id="7589f-106">Remarks</span></span>

<span data-ttu-id="7589f-107">在先前的語法*運算子符號*是其中一個`+`， `-`， `*`， `/`， `=`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="7589f-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="7589f-108">*參數清單*它們出現的一般語法中該運算子的順序指定的運算元。</span><span class="sxs-lookup"><span data-stu-id="7589f-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="7589f-109">*方法主體*建構所產生的值。</span><span class="sxs-lookup"><span data-stu-id="7589f-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="7589f-110">運算子多載運算子都必須是靜態的。</span><span class="sxs-lookup"><span data-stu-id="7589f-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="7589f-111">運算子多載的一元運算子，例如`+`並`-`，必須使用波狀符號 (`~`) 中*運算子符號*表示的運算子是一元運算子和二元的運算子，如中所示下列宣告。</span><span class="sxs-lookup"><span data-stu-id="7589f-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="7589f-112">下列程式碼說明只有兩個運算子的向量類別，一個運算子用於一元減號運算，一個運算子用於純量乘法。</span><span class="sxs-lookup"><span data-stu-id="7589f-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="7589f-113">在範例中，因為不論向量和純量出現的順序必須一起使用的運算子需要兩個多載用於純量乘法。</span><span class="sxs-lookup"><span data-stu-id="7589f-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="7589f-114">建立新的運算子</span><span class="sxs-lookup"><span data-stu-id="7589f-114">Creating New Operators</span></span>

<span data-ttu-id="7589f-115">您可以多載所有標準的運算子，但您也可以建立新的運算子，從特定的字元序列。</span><span class="sxs-lookup"><span data-stu-id="7589f-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="7589f-116">允許為運算子字元`!`， `%`， `&`， `*`， `+`， `-`， `.`， `/`， `<`， `=`， `>`， `?`， `@`， `^`， `|`，和`~`。</span><span class="sxs-lookup"><span data-stu-id="7589f-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="7589f-117">`~`字元具有特殊意義，讓操作員一元 （unary），且不是運算子字元序列的一部分。</span><span class="sxs-lookup"><span data-stu-id="7589f-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="7589f-118">並非所有運算子都可以都進行一元 （unary）。</span><span class="sxs-lookup"><span data-stu-id="7589f-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="7589f-119">根據您所使用的確切的字元順序，請您運算子會有特定優先順序和關聯性。</span><span class="sxs-lookup"><span data-stu-id="7589f-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="7589f-120">關聯性可以可能是從左至右或由右至左，而用時的相同層級的優先順序的運算子會出現在不含括弧的順序。</span><span class="sxs-lookup"><span data-stu-id="7589f-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="7589f-121">運算子字元`.`並不會影響優先順序，因此，比方說，如果您想要定義您自己的版本具有相同的優先順序和順序關聯性與一般的乘法的乘法的您可以建立運算子，例如`.*`.</span><span class="sxs-lookup"><span data-stu-id="7589f-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="7589f-122">只有運算子`?`並`?<-`可能會開始`?`。</span><span class="sxs-lookup"><span data-stu-id="7589f-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="7589f-123">顯示所有的運算子優先順序 F # 中的資料表可以位於[符號和運算子參考](symbol-and-operator-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7589f-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="7589f-124">多載的運算子名稱</span><span class="sxs-lookup"><span data-stu-id="7589f-124">Overloaded Operator Names</span></span>

<span data-ttu-id="7589f-125">當 F # 編譯器編譯的運算子的運算式時，它會產生具有編譯器產生的名稱，該運算子的方法。</span><span class="sxs-lookup"><span data-stu-id="7589f-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="7589f-126">這是出現在方法中的 Microsoft intermediate language (MSIL)，也在反映和 IntelliSense 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7589f-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="7589f-127">您通常不需要在 F # 程式碼中使用這些名稱。</span><span class="sxs-lookup"><span data-stu-id="7589f-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="7589f-128">下表顯示標準的運算子和其對應產生的名稱。</span><span class="sxs-lookup"><span data-stu-id="7589f-128">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="7589f-129">運算子</span><span class="sxs-lookup"><span data-stu-id="7589f-129">Operator</span></span>|<span data-ttu-id="7589f-130">產生的名稱</span><span class="sxs-lookup"><span data-stu-id="7589f-130">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

<span data-ttu-id="7589f-131">其他這裡未列出的運算子字元的組合可以用作運算子，並藉由串連下表中的個別字元的名稱所組成的名稱。</span><span class="sxs-lookup"><span data-stu-id="7589f-131">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="7589f-132">例如，+ ！</span><span class="sxs-lookup"><span data-stu-id="7589f-132">For example, +!</span></span> <span data-ttu-id="7589f-133">會變成`op_PlusBang`。</span><span class="sxs-lookup"><span data-stu-id="7589f-133">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="7589f-134">運算子字元</span><span class="sxs-lookup"><span data-stu-id="7589f-134">Operator character</span></span>|<span data-ttu-id="7589f-135">名稱</span><span class="sxs-lookup"><span data-stu-id="7589f-135">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="7589f-136">前置詞和中置運算子</span><span class="sxs-lookup"><span data-stu-id="7589f-136">Prefix and Infix Operators</span></span>

<span data-ttu-id="7589f-137">*前置詞*運算子應該位於運算元或運算元，如同函式。</span><span class="sxs-lookup"><span data-stu-id="7589f-137">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="7589f-138">*中置*運算子有兩個運算元之間放置。</span><span class="sxs-lookup"><span data-stu-id="7589f-138">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="7589f-139">只有特定運算子可用來當做前置運算子。</span><span class="sxs-lookup"><span data-stu-id="7589f-139">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="7589f-140">有些運算子永遠前置運算子，其他人可以是中置或前置詞，而且其餘部分會一律中置運算子。</span><span class="sxs-lookup"><span data-stu-id="7589f-140">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="7589f-141">開頭為 `!` 的運算子 (不包括 `!=`) 以及 `~` 運算子或 `~` 的重複序列一律為前置運算子。</span><span class="sxs-lookup"><span data-stu-id="7589f-141">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="7589f-142">運算子`+`， `-`， `+.`， `-.`， `&`， `&&`， `%`，以及`%%`可以是前置運算子或中置運算子。</span><span class="sxs-lookup"><span data-stu-id="7589f-142">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="7589f-143">您從 中置版本區分這些運算子的前置版本加上`~`前置運算子所定義的開頭。</span><span class="sxs-lookup"><span data-stu-id="7589f-143">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="7589f-144">`~`時您使用運算子，它會定義時，才不會使用。</span><span class="sxs-lookup"><span data-stu-id="7589f-144">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="7589f-145">範例</span><span class="sxs-lookup"><span data-stu-id="7589f-145">Example</span></span>

<span data-ttu-id="7589f-146">下列程式碼說明如何使用運算子多載實作分數型別。</span><span class="sxs-lookup"><span data-stu-id="7589f-146">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="7589f-147">表示分數的分子和分母。</span><span class="sxs-lookup"><span data-stu-id="7589f-147">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="7589f-148">此函式`hcf`用來判斷最高常見因素，用來減少片段。</span><span class="sxs-lookup"><span data-stu-id="7589f-148">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="7589f-149">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="7589f-149">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="7589f-150">在全域層級的運算子</span><span class="sxs-lookup"><span data-stu-id="7589f-150">Operators at the Global Level</span></span>

<span data-ttu-id="7589f-151">您也可以定義在全域層級的運算子。</span><span class="sxs-lookup"><span data-stu-id="7589f-151">You can also define operators at the global level.</span></span> <span data-ttu-id="7589f-152">下列程式碼定義了運算子`+?`。</span><span class="sxs-lookup"><span data-stu-id="7589f-152">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="7589f-153">上述程式碼的輸出是`12`。</span><span class="sxs-lookup"><span data-stu-id="7589f-153">The output of the above code is `12`.</span></span>

<span data-ttu-id="7589f-154">您可以重新定義一般的算術運算子，以這種方式，因為 F # 的範圍規則可讓您指定的新定義的運算子的優先順序高於內建運算子。</span><span class="sxs-lookup"><span data-stu-id="7589f-154">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="7589f-155">關鍵字`inline`通常會搭配全域運算子，而這通常是最適合整合至呼叫端程式碼的小型函式。</span><span class="sxs-lookup"><span data-stu-id="7589f-155">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="7589f-156">讓運算子函式內嵌也可讓它們使用來產生以統計方式解析的一般程式碼以統計方式解析的型別參數。</span><span class="sxs-lookup"><span data-stu-id="7589f-156">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="7589f-157">如需詳細資訊，請參閱 <<c0> [ 內嵌函式](functions/inline-functions.md)並[以靜態方式解析的類型參數](generics/statically-resolved-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7589f-157">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7589f-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7589f-158">See also</span></span>

- [<span data-ttu-id="7589f-159">成員</span><span class="sxs-lookup"><span data-stu-id="7589f-159">Members</span></span>](members/index.md)
