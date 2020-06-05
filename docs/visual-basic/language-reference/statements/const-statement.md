---
title: Const 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 3b05d4067ef99e03df07d2c316c982051180d961
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382103"
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="3308e-102">Const 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3308e-102">Const Statement (Visual Basic)</span></span>

<span data-ttu-id="3308e-103">宣告並定義一或多個常數。</span><span class="sxs-lookup"><span data-stu-id="3308e-103">Declares and defines one or more constants.</span></span>

## <a name="syntax"></a><span data-ttu-id="3308e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3308e-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a><span data-ttu-id="3308e-105">組件</span><span class="sxs-lookup"><span data-stu-id="3308e-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="3308e-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3308e-106">Optional.</span></span> <span data-ttu-id="3308e-107">套用至此語句中宣告之所有常數的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="3308e-107">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="3308e-108">請[Attribute List](attribute-list.md)參閱以角括弧（" `<` " 和 ""）括住的屬性清單 `>` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-108">See [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`accessmodifier`  
<span data-ttu-id="3308e-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3308e-109">Optional.</span></span> <span data-ttu-id="3308e-110">使用此項來指定哪些程式碼可以存取這些常數。</span><span class="sxs-lookup"><span data-stu-id="3308e-110">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="3308e-111">可以是[公用](../modifiers/public.md)、[受保護](../modifiers/protected.md)、 [Friend](../modifiers/friend.md)、[受保護的 Friend](../modifiers/protected-friend.md)、[私](../modifiers/private.md)用或[私用保護](../modifiers/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="3308e-111">Can be [Public](../modifiers/public.md), [Protected](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md), or [Private Protected](../modifiers/private-protected.md).</span></span>

`Shadows`  
<span data-ttu-id="3308e-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3308e-112">Optional.</span></span> <span data-ttu-id="3308e-113">使用此專案來重新宣告和隱藏基類中的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="3308e-113">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="3308e-114">請參閱[Shadows](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="3308e-114">See [Shadows](../modifiers/shadows.md).</span></span>

`constantlist`  
<span data-ttu-id="3308e-115">必要。</span><span class="sxs-lookup"><span data-stu-id="3308e-115">Required.</span></span> <span data-ttu-id="3308e-116">在此語句中宣告的常數清單。</span><span class="sxs-lookup"><span data-stu-id="3308e-116">List of constants being declared in this statement.</span></span>

<span data-ttu-id="3308e-117">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="3308e-117">`constant` `[ ,` `constant` `... ]`</span></span>

<span data-ttu-id="3308e-118">每個 `constant` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="3308e-118">Each `constant` has the following syntax and parts:</span></span>

<span data-ttu-id="3308e-119">`constantname` `[ As` `datatype` `] =` `initializer`</span><span class="sxs-lookup"><span data-stu-id="3308e-119">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>

|<span data-ttu-id="3308e-120">部分</span><span class="sxs-lookup"><span data-stu-id="3308e-120">Part</span></span>|<span data-ttu-id="3308e-121">描述</span><span class="sxs-lookup"><span data-stu-id="3308e-121">Description</span></span>|
|----------|-----------------|
|`constantname`|<span data-ttu-id="3308e-122">必要。</span><span class="sxs-lookup"><span data-stu-id="3308e-122">Required.</span></span> <span data-ttu-id="3308e-123">常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3308e-123">Name of the constant.</span></span> <span data-ttu-id="3308e-124">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3308e-124">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`datatype`|<span data-ttu-id="3308e-125">如果 `Option Strict` 為，則為必要 `On` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-125">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="3308e-126">常數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3308e-126">Data type of the constant.</span></span>|
|`initializer`|<span data-ttu-id="3308e-127">必要。</span><span class="sxs-lookup"><span data-stu-id="3308e-127">Required.</span></span> <span data-ttu-id="3308e-128">在編譯時期評估並指派給常數的運算式。</span><span class="sxs-lookup"><span data-stu-id="3308e-128">Expression that is evaluated at compile time and assigned to the constant.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3308e-129">備註</span><span class="sxs-lookup"><span data-stu-id="3308e-129">Remarks</span></span>

<span data-ttu-id="3308e-130">如果您的應用程式中有永不變更的值，您可以定義已命名的常數，並將其取代為常值。</span><span class="sxs-lookup"><span data-stu-id="3308e-130">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="3308e-131">名稱比值更容易記住。</span><span class="sxs-lookup"><span data-stu-id="3308e-131">A name is easier to remember than a value.</span></span> <span data-ttu-id="3308e-132">您可以只定義常數一次，並將其用於程式碼中的許多位置。</span><span class="sxs-lookup"><span data-stu-id="3308e-132">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="3308e-133">如果在較新的版本中，您需要重新定義值，則 `Const` 語句是您唯一需要進行變更的位置。</span><span class="sxs-lookup"><span data-stu-id="3308e-133">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>

<span data-ttu-id="3308e-134">您 `Const` 只能在模組或程式層級使用。</span><span class="sxs-lookup"><span data-stu-id="3308e-134">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="3308e-135">這表示變數的宣告*內容*必須是類別、結構、模組、程式或區塊，而且不能是原始程式檔、命名空間或介面。</span><span class="sxs-lookup"><span data-stu-id="3308e-135">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="3308e-136">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3308e-136">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="3308e-137">本機常數（在程式內）預設為公用存取，而且您不能在其上使用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="3308e-137">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="3308e-138">類別和模組成員常數（在任何程式之外）預設為私用存取，而結構成員常數則預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="3308e-138">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="3308e-139">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="3308e-139">You can adjust their access levels with the access modifiers.</span></span>

## <a name="rules"></a><span data-ttu-id="3308e-140">規則</span><span class="sxs-lookup"><span data-stu-id="3308e-140">Rules</span></span>

- <span data-ttu-id="3308e-141">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="3308e-141">**Declaration Context.**</span></span> <span data-ttu-id="3308e-142">在任何程式以外的模組層級宣告的常數是*成員常數*;它是宣告它的類別、結構或模組的成員。</span><span class="sxs-lookup"><span data-stu-id="3308e-142">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>

  <span data-ttu-id="3308e-143">在程式層級宣告的常數是*本機常數*;它是在宣告它的程式或區塊的本機。</span><span class="sxs-lookup"><span data-stu-id="3308e-143">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>

- <span data-ttu-id="3308e-144">**特性.**</span><span class="sxs-lookup"><span data-stu-id="3308e-144">**Attributes.**</span></span> <span data-ttu-id="3308e-145">您只能將屬性套用至成員常數，而不能套用至本機常數。</span><span class="sxs-lookup"><span data-stu-id="3308e-145">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="3308e-146">屬性會將資訊提供給元件的中繼資料，這對暫存儲存體（例如本機常數）沒有意義。</span><span class="sxs-lookup"><span data-stu-id="3308e-146">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>

- <span data-ttu-id="3308e-147">**修改.**</span><span class="sxs-lookup"><span data-stu-id="3308e-147">**Modifiers.**</span></span> <span data-ttu-id="3308e-148">根據預設，所有常數都是 `Shared` 、 `Static` 和 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-148">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="3308e-149">宣告常數時，您無法使用任何這些關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3308e-149">You cannot use any of these keywords when declaring a constant.</span></span>

  <span data-ttu-id="3308e-150">在程式層級上，您不能使用 `Shadows` 或任何存取修飾詞來宣告本機常數。</span><span class="sxs-lookup"><span data-stu-id="3308e-150">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>

- <span data-ttu-id="3308e-151">**多個常數。**</span><span class="sxs-lookup"><span data-stu-id="3308e-151">**Multiple Constants.**</span></span> <span data-ttu-id="3308e-152">您可以在同一個宣告語句中宣告數個常數， `constantname` 為每個常數指定元件。</span><span class="sxs-lookup"><span data-stu-id="3308e-152">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="3308e-153">以逗號分隔多個常數。</span><span class="sxs-lookup"><span data-stu-id="3308e-153">Multiple constants are separated by commas.</span></span>

## <a name="data-type-rules"></a><span data-ttu-id="3308e-154">資料類型規則</span><span class="sxs-lookup"><span data-stu-id="3308e-154">Data Type Rules</span></span>

- <span data-ttu-id="3308e-155">**資料類型。**</span><span class="sxs-lookup"><span data-stu-id="3308e-155">**Data Types.**</span></span> <span data-ttu-id="3308e-156">`Const`語句可以宣告變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3308e-156">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="3308e-157">您可以指定任何資料類型或列舉的名稱。</span><span class="sxs-lookup"><span data-stu-id="3308e-157">You can specify any data type or the name of an enumeration.</span></span>

- <span data-ttu-id="3308e-158">**預設類型。**</span><span class="sxs-lookup"><span data-stu-id="3308e-158">**Default Type.**</span></span> <span data-ttu-id="3308e-159">如果您未指定 `datatype` ，常數會接受的資料類型 `initializer` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-159">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="3308e-160">如果您同時指定 `datatype` 和 `initializer` ，則的資料類型 `initializer` 必須可轉換為 `datatype` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-160">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="3308e-161">如果 `datatype` 和 `initializer` 都不存在，資料類型會預設為 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-161">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>

- <span data-ttu-id="3308e-162">**不同的類型。**</span><span class="sxs-lookup"><span data-stu-id="3308e-162">**Different Types.**</span></span> <span data-ttu-id="3308e-163">您可以 `As` 針對您所宣告的每個變數使用個別的子句，為不同的常數指定不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3308e-163">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="3308e-164">但是，您無法使用通用子句，將數個常數宣告為相同類型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-164">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>

- <span data-ttu-id="3308e-165">**初始.**</span><span class="sxs-lookup"><span data-stu-id="3308e-165">**Initialization.**</span></span> <span data-ttu-id="3308e-166">您必須初始化中每個常數的值 `constantlist` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-166">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="3308e-167">您可以使用 `initializer` 來提供要指派給常數的運算式。</span><span class="sxs-lookup"><span data-stu-id="3308e-167">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="3308e-168">運算式可以是常值的任何組合、已定義的其他常數，以及已定義的列舉成員。</span><span class="sxs-lookup"><span data-stu-id="3308e-168">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="3308e-169">您可以使用算術和邏輯運算子來結合這類元素。</span><span class="sxs-lookup"><span data-stu-id="3308e-169">You can use arithmetic and logical operators to combine such elements.</span></span>

  <span data-ttu-id="3308e-170">您不能在中使用變數或函數 `initializer` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-170">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="3308e-171">不過，您可以使用轉換關鍵字（例如 `CByte` 和） `CShort` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-171">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="3308e-172">`AscW`如果您以常數或引數呼叫它，您也可以使用 `String` `Char` ，因為它可以在編譯時期進行評估。</span><span class="sxs-lookup"><span data-stu-id="3308e-172">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

## <a name="behavior"></a><span data-ttu-id="3308e-173">行為</span><span class="sxs-lookup"><span data-stu-id="3308e-173">Behavior</span></span>

- <span data-ttu-id="3308e-174">**範圍.**</span><span class="sxs-lookup"><span data-stu-id="3308e-174">**Scope.**</span></span> <span data-ttu-id="3308e-175">本機常數只能從其程式或區塊記憶體取。</span><span class="sxs-lookup"><span data-stu-id="3308e-175">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="3308e-176">成員常數可從其類別、結構或模組內的任何位置存取。</span><span class="sxs-lookup"><span data-stu-id="3308e-176">Member constants are accessible from anywhere within their class, structure, or module.</span></span>

- <span data-ttu-id="3308e-177">**加.**</span><span class="sxs-lookup"><span data-stu-id="3308e-177">**Qualification.**</span></span> <span data-ttu-id="3308e-178">類別、結構或模組之外的程式碼必須使用該類別、結構或模組的名稱來限定成員常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3308e-178">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="3308e-179">程式或區塊外的程式碼無法參考該程式或區塊中的任何本機常數。</span><span class="sxs-lookup"><span data-stu-id="3308e-179">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>

## <a name="example"></a><span data-ttu-id="3308e-180">範例</span><span class="sxs-lookup"><span data-stu-id="3308e-180">Example</span></span>

<span data-ttu-id="3308e-181">下列範例會使用 `Const` 語句來宣告用來取代常值的常數。</span><span class="sxs-lookup"><span data-stu-id="3308e-181">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a><span data-ttu-id="3308e-182">範例</span><span class="sxs-lookup"><span data-stu-id="3308e-182">Example</span></span>

<span data-ttu-id="3308e-183">如果您定義具有資料類型的常數 `Object` ，Visual Basic 編譯器會提供它的類型 `initializer` ，而不是 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-183">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="3308e-184">在下列範例中，常數 `naturalLogBase` 具有執行時間類型 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-184">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

<span data-ttu-id="3308e-185">上述範例 <xref:System.Type.ToString%2A> <xref:System.Type> 會在[GetType 運算子](../operators/gettype-operator.md)傳回的物件上使用方法，因為 <xref:System.Type> 無法使用轉換成 `String` `CStr` 。</span><span class="sxs-lookup"><span data-stu-id="3308e-185">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3308e-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3308e-186">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="3308e-187">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="3308e-187">Enum Statement</span></span>](enum-statement.md)
- [<span data-ttu-id="3308e-188">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="3308e-188">#Const Directive</span></span>](../directives/const-directive.md)
- [<span data-ttu-id="3308e-189">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="3308e-189">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="3308e-190">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="3308e-190">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="3308e-191">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="3308e-191">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="3308e-192">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="3308e-192">Constants and Enumerations</span></span>](../../programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="3308e-193">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="3308e-193">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="3308e-194">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="3308e-194">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
