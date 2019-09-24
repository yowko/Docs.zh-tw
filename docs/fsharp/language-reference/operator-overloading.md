---
title: 運算子多載
description: 瞭解如何在類別或記錄類型和中F#的全域層級上多載算術運算子。
ms.date: 05/16/2016
ms.openlocfilehash: d902a06193481ed87131b3336cd8a2ff54b811b4
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216842"
---
# <a name="operator-overloading"></a><span data-ttu-id="9577c-103">運算子多載</span><span class="sxs-lookup"><span data-stu-id="9577c-103">Operator Overloading</span></span>

<span data-ttu-id="9577c-104">本主題描述如何在類別或記錄類型，以及在全域層級上多載算術運算子。</span><span class="sxs-lookup"><span data-stu-id="9577c-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="9577c-105">語法</span><span class="sxs-lookup"><span data-stu-id="9577c-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="9577c-106">備註</span><span class="sxs-lookup"><span data-stu-id="9577c-106">Remarks</span></span>

<span data-ttu-id="9577c-107">在先前的語法中，*運算子-符號*是`+` `=`、 `-`、 `*` `/`、、等其中一個。</span><span class="sxs-lookup"><span data-stu-id="9577c-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="9577c-108">*參數清單*會以它們在該運算子的一般語法中出現的順序來指定運算元。</span><span class="sxs-lookup"><span data-stu-id="9577c-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="9577c-109">*方法主體*會結構產生的值。</span><span class="sxs-lookup"><span data-stu-id="9577c-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="9577c-110">運算子的運算子多載必須是靜態的。</span><span class="sxs-lookup"><span data-stu-id="9577c-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="9577c-111">一元運算子的運算子多載（例如`+`和`-`）必須在*運算子符號*中`~`使用波狀符號（），以表示運算子是一元運算子，而不是二元運算子，如下所示清點.</span><span class="sxs-lookup"><span data-stu-id="9577c-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="9577c-112">下列程式碼說明只有兩個運算子的向量類別，一個運算子用於一元減號運算，一個運算子用於純量乘法。</span><span class="sxs-lookup"><span data-stu-id="9577c-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="9577c-113">在此範例中，需要兩個純量的多載，因為不論向量和純量的出現順序為何，運算子都必須可行。</span><span class="sxs-lookup"><span data-stu-id="9577c-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="9577c-114">建立新的運算子</span><span class="sxs-lookup"><span data-stu-id="9577c-114">Creating New Operators</span></span>

<span data-ttu-id="9577c-115">您可以多載所有標準運算子，但您也可以從特定字元序列中建立新的運算子。</span><span class="sxs-lookup"><span data-stu-id="9577c-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="9577c-116">允許的運算子字元`!`為`%`、 `&` `*` `+` 、`-`、、、 、、`.`、、、、 `/` `<` `=` `>` `?` 、`@`、 、`^`和`~`。 `|`</span><span class="sxs-lookup"><span data-stu-id="9577c-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="9577c-117">`~`字元具有建立運算子一元的特殊意義，而不是運算子字元序列的一部分。</span><span class="sxs-lookup"><span data-stu-id="9577c-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="9577c-118">並非所有運算子都可以成為一元。</span><span class="sxs-lookup"><span data-stu-id="9577c-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="9577c-119">視您使用的確切字元順序而定，您的運算子會有特定的優先順序和關聯性。</span><span class="sxs-lookup"><span data-stu-id="9577c-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="9577c-120">關聯性可以由左至右或由右至左，並且會在每次相同優先順序的運算子以不含括弧的順序顯示時使用。</span><span class="sxs-lookup"><span data-stu-id="9577c-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="9577c-121">運算子字元`.`不會影響優先順序，因此，舉例來說，如果您想要定義自己的乘法版本，且其優先順序和關聯性與一般乘法相同，您可以建立運算子，例如`.*`.</span><span class="sxs-lookup"><span data-stu-id="9577c-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="9577c-122">只有運算子`?`和`?<-`可以從開始`?`。</span><span class="sxs-lookup"><span data-stu-id="9577c-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="9577c-123">在F# [符號和運算子參考](./symbol-and-operator-reference/index.md)中，可以找到顯示所有運算子優先順序的資料表。</span><span class="sxs-lookup"><span data-stu-id="9577c-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](./symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="9577c-124">多載的運算子名稱</span><span class="sxs-lookup"><span data-stu-id="9577c-124">Overloaded Operator Names</span></span>

<span data-ttu-id="9577c-125">F#當編譯器編譯運算子運算式時，它會產生具有編譯器為該運算子所產生之名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="9577c-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="9577c-126">這是在方法的 Microsoft 中繼語言（MSIL）中顯示的名稱，也是在反映和 IntelliSense 中。</span><span class="sxs-lookup"><span data-stu-id="9577c-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="9577c-127">您通常不需要在程式碼中F#使用這些名稱。</span><span class="sxs-lookup"><span data-stu-id="9577c-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="9577c-128">下表顯示標準運算子及其對應的產生名稱。</span><span class="sxs-lookup"><span data-stu-id="9577c-128">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="9577c-129">運算子</span><span class="sxs-lookup"><span data-stu-id="9577c-129">Operator</span></span>|<span data-ttu-id="9577c-130">產生的名稱</span><span class="sxs-lookup"><span data-stu-id="9577c-130">Generated name</span></span>|
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

<span data-ttu-id="9577c-131">此處未列出的其他運算子字元組合可以做為運算子使用，並透過串連下表中個別字元的名稱來建立名稱。</span><span class="sxs-lookup"><span data-stu-id="9577c-131">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="9577c-132">例如，+！</span><span class="sxs-lookup"><span data-stu-id="9577c-132">For example, +!</span></span> <span data-ttu-id="9577c-133">會`op_PlusBang`變成。</span><span class="sxs-lookup"><span data-stu-id="9577c-133">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="9577c-134">運算子字元</span><span class="sxs-lookup"><span data-stu-id="9577c-134">Operator character</span></span>|<span data-ttu-id="9577c-135">名稱</span><span class="sxs-lookup"><span data-stu-id="9577c-135">Name</span></span>|
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

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="9577c-136">前置詞和中綴運算子</span><span class="sxs-lookup"><span data-stu-id="9577c-136">Prefix and Infix Operators</span></span>

<span data-ttu-id="9577c-137">*前置*運算子應該放在運算元或運算元的前方，非常類似于函式。</span><span class="sxs-lookup"><span data-stu-id="9577c-137">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="9577c-138">中*綴*運算子應該放在兩個運算元之間。</span><span class="sxs-lookup"><span data-stu-id="9577c-138">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="9577c-139">只有特定運算子可以當做前置詞運算子使用。</span><span class="sxs-lookup"><span data-stu-id="9577c-139">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="9577c-140">有些運算子一律是前置詞運算子，有些則可以是中置或前置詞，而其餘的則一律是中綴運算子。</span><span class="sxs-lookup"><span data-stu-id="9577c-140">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="9577c-141">開頭為 `!` 的運算子 (不包括 `!=`) 以及 `~` 運算子或 `~` 的重複序列一律為前置運算子。</span><span class="sxs-lookup"><span data-stu-id="9577c-141">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="9577c-142">`+`運算子、`&`、、 、`%`、、和`%%`可以是前置運算子或中綴運算子。 `&&` `-` `+.` `-.`</span><span class="sxs-lookup"><span data-stu-id="9577c-142">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="9577c-143">您可以將這些運算子的前置詞版本與`~`上綴版本區別，方法是在定義前置詞運算子的開頭新增。</span><span class="sxs-lookup"><span data-stu-id="9577c-143">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="9577c-144">當您使用運算子時，只有在定義時才會使用。`~`</span><span class="sxs-lookup"><span data-stu-id="9577c-144">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="9577c-145">範例</span><span class="sxs-lookup"><span data-stu-id="9577c-145">Example</span></span>

<span data-ttu-id="9577c-146">下列程式碼說明如何使用運算子多載來執行分數類型。</span><span class="sxs-lookup"><span data-stu-id="9577c-146">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="9577c-147">分數是以分子和分母表示。</span><span class="sxs-lookup"><span data-stu-id="9577c-147">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="9577c-148">函數`hcf`是用來判斷最常見的因素，這是用來減少分數。</span><span class="sxs-lookup"><span data-stu-id="9577c-148">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="9577c-149">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="9577c-149">**Output:**</span></span>

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="9577c-150">全域層級的運算子</span><span class="sxs-lookup"><span data-stu-id="9577c-150">Operators at the Global Level</span></span>

<span data-ttu-id="9577c-151">您也可以在全域層級定義運算子。</span><span class="sxs-lookup"><span data-stu-id="9577c-151">You can also define operators at the global level.</span></span> <span data-ttu-id="9577c-152">下列程式碼會定義運算子`+?`。</span><span class="sxs-lookup"><span data-stu-id="9577c-152">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="9577c-153">上述程式碼的輸出為`12`。</span><span class="sxs-lookup"><span data-stu-id="9577c-153">The output of the above code is `12`.</span></span>

<span data-ttu-id="9577c-154">您可以用這種方式重新定義一般算術運算子，因為的範圍F#規則會規定新定義的運算子優先于內建的運算子。</span><span class="sxs-lookup"><span data-stu-id="9577c-154">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="9577c-155">關鍵字`inline`通常與全域運算子搭配使用，這通常是很小的函式，最適合與呼叫程式碼整合。</span><span class="sxs-lookup"><span data-stu-id="9577c-155">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="9577c-156">讓運算子函式內嵌也可以讓它們使用靜態解析的類型參數，以產生靜態解析的泛型程式碼。</span><span class="sxs-lookup"><span data-stu-id="9577c-156">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="9577c-157">如需詳細資訊，請參閱[內嵌](./functions/inline-functions.md)函式和以[靜態方式解析的類型參數](./generics/statically-resolved-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9577c-157">For more information, see [Inline Functions](./functions/inline-functions.md) and [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9577c-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9577c-158">See also</span></span>

- [<span data-ttu-id="9577c-159">成員</span><span class="sxs-lookup"><span data-stu-id="9577c-159">Members</span></span>](./members/index.md)
