---
title: Const 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: a5842e284eaa858e7a66160060123edc21858a3a
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233843"
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="60806-102">Const 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60806-102">Const Statement (Visual Basic)</span></span>
<span data-ttu-id="60806-103">宣告並定義一或多個常數。</span><span class="sxs-lookup"><span data-stu-id="60806-103">Declares and defines one or more constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60806-104">語法</span><span class="sxs-lookup"><span data-stu-id="60806-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a><span data-ttu-id="60806-105">組件</span><span class="sxs-lookup"><span data-stu-id="60806-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="60806-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="60806-106">Optional.</span></span> <span data-ttu-id="60806-107">此陳述式中宣告的屬性套用至所有常數清單。</span><span class="sxs-lookup"><span data-stu-id="60806-107">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="60806-108">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)在角括號 ("`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="60806-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="60806-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="60806-109">Optional.</span></span> <span data-ttu-id="60806-110">使用此選項來指定哪些程式碼可以存取這些常數。</span><span class="sxs-lookup"><span data-stu-id="60806-110">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="60806-111">可以是[公用](../../../visual-basic/language-reference/modifiers/public.md)，[保護](../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../visual-basic/language-reference/modifiers/friend.md)， [Protected Friend](../modifiers/protected-friend.md)，[私人](../../../visual-basic/language-reference/modifiers/private.md)，或[受保護的私用](../../language-reference/modifiers/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="60806-111">Can be [Public](../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../../../visual-basic/language-reference/modifiers/private.md), or [Private Protected](../../language-reference/modifiers/private-protected.md).</span></span>
  
 `Shadows`  
 <span data-ttu-id="60806-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="60806-112">Optional.</span></span> <span data-ttu-id="60806-113">使用此選項，重新宣告並隱藏基底類別中的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="60806-113">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="60806-114">請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="60806-114">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `constantlist`  
 <span data-ttu-id="60806-115">必要。</span><span class="sxs-lookup"><span data-stu-id="60806-115">Required.</span></span> <span data-ttu-id="60806-116">常數，此陳述式所宣告的清單。</span><span class="sxs-lookup"><span data-stu-id="60806-116">List of constants being declared in this statement.</span></span>  
  
 <span data-ttu-id="60806-117">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="60806-117">`constant` `[ ,` `constant` `... ]`</span></span>  
  
 <span data-ttu-id="60806-118">每個 `constant` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="60806-118">Each `constant` has the following syntax and parts:</span></span>  
  
 <span data-ttu-id="60806-119">`constantname` `[ As` `datatype` `] =` `initializer`</span><span class="sxs-lookup"><span data-stu-id="60806-119">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>  
  
|<span data-ttu-id="60806-120">組件</span><span class="sxs-lookup"><span data-stu-id="60806-120">Part</span></span>|<span data-ttu-id="60806-121">描述</span><span class="sxs-lookup"><span data-stu-id="60806-121">Description</span></span>|  
|----------|-----------------|  
|`constantname`|<span data-ttu-id="60806-122">必要。</span><span class="sxs-lookup"><span data-stu-id="60806-122">Required.</span></span> <span data-ttu-id="60806-123">常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="60806-123">Name of the constant.</span></span> <span data-ttu-id="60806-124">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="60806-124">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`datatype`|<span data-ttu-id="60806-125">若`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="60806-125">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="60806-126">資料類型的常數。</span><span class="sxs-lookup"><span data-stu-id="60806-126">Data type of the constant.</span></span>|  
|`initializer`|<span data-ttu-id="60806-127">必要。</span><span class="sxs-lookup"><span data-stu-id="60806-127">Required.</span></span> <span data-ttu-id="60806-128">在編譯時期評估，以及指派給常數的運算式。</span><span class="sxs-lookup"><span data-stu-id="60806-128">Expression that is evaluated at compile time and assigned to the constant.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60806-129">備註</span><span class="sxs-lookup"><span data-stu-id="60806-129">Remarks</span></span>  
 <span data-ttu-id="60806-130">如果您將永遠不會變更值在您的應用程式時，您可以定義的具名的常數，並使用它來取代常值的值。</span><span class="sxs-lookup"><span data-stu-id="60806-130">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="60806-131">名稱不容易記住的值。</span><span class="sxs-lookup"><span data-stu-id="60806-131">A name is easier to remember than a value.</span></span> <span data-ttu-id="60806-132">您可以一次定義常數和程式碼中使用在許多地方。</span><span class="sxs-lookup"><span data-stu-id="60806-132">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="60806-133">如果您需要較新版本中重新定義值，`Const`陳述式是唯一您需要進行變更。</span><span class="sxs-lookup"><span data-stu-id="60806-133">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>  
  
 <span data-ttu-id="60806-134">您可以使用`Const`只能在模組或程序層級。</span><span class="sxs-lookup"><span data-stu-id="60806-134">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="60806-135">這表示*宣告內容*變數必須是類別、 結構、 模組、 程序或區塊，而且不能是原始程式檔、 命名空間或介面。</span><span class="sxs-lookup"><span data-stu-id="60806-135">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="60806-136">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="60806-136">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="60806-137">區域常數 （在程序） 預設為公用存取，因此您無法在其上使用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="60806-137">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="60806-138">類別和模組成員常數 （以外的任何程序） 預設為私用存取，而結構成員常數預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="60806-138">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="60806-139">您可以調整其存取層級，使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="60806-139">You can adjust their access levels with the access modifiers.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="60806-140">規則</span><span class="sxs-lookup"><span data-stu-id="60806-140">Rules</span></span>  
  
-   <span data-ttu-id="60806-141">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="60806-141">**Declaration Context.**</span></span> <span data-ttu-id="60806-142">常數的宣告是在模組層級以外的任何程序，而是*成員常數*; 它是類別、 結構成員或模組宣告它。</span><span class="sxs-lookup"><span data-stu-id="60806-142">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>  
  
     <span data-ttu-id="60806-143">在程序層級宣告的常數是*區域常數*; 它是本機程序或宣告它的區塊。</span><span class="sxs-lookup"><span data-stu-id="60806-143">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>  
  
-   <span data-ttu-id="60806-144">**屬性。**</span><span class="sxs-lookup"><span data-stu-id="60806-144">**Attributes.**</span></span> <span data-ttu-id="60806-145">您可以將屬性套用到成員常數，而非區域常數。</span><span class="sxs-lookup"><span data-stu-id="60806-145">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="60806-146">屬性會提供資訊給組件的中繼資料，不是有意義的暫存儲存體，例如區域常數。</span><span class="sxs-lookup"><span data-stu-id="60806-146">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>  
  
-   <span data-ttu-id="60806-147">**修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="60806-147">**Modifiers.**</span></span> <span data-ttu-id="60806-148">根據預設，所有的常數是`Shared`， `Static`，和`ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="60806-148">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="60806-149">宣告常數時，您無法使用這些關鍵字。</span><span class="sxs-lookup"><span data-stu-id="60806-149">You cannot use any of these keywords when declaring a constant.</span></span>  
  
     <span data-ttu-id="60806-150">在程序層級，您無法使用`Shadows`或任何存取修飾詞來宣告區域常數。</span><span class="sxs-lookup"><span data-stu-id="60806-150">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>  
  
-   <span data-ttu-id="60806-151">**多個常數。**</span><span class="sxs-lookup"><span data-stu-id="60806-151">**Multiple Constants.**</span></span> <span data-ttu-id="60806-152">您可以宣告在相同的宣告陳述式中，數個常數指定`constantname`針對每個部分。</span><span class="sxs-lookup"><span data-stu-id="60806-152">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="60806-153">以逗號分隔多個常數。</span><span class="sxs-lookup"><span data-stu-id="60806-153">Multiple constants are separated by commas.</span></span>  
  
## <a name="data-type-rules"></a><span data-ttu-id="60806-154">資料類型的規則</span><span class="sxs-lookup"><span data-stu-id="60806-154">Data Type Rules</span></span>  
  
-   <span data-ttu-id="60806-155">**資料型別。**</span><span class="sxs-lookup"><span data-stu-id="60806-155">**Data Types.**</span></span> <span data-ttu-id="60806-156">`Const`陳述式可以宣告一個變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="60806-156">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="60806-157">您可以指定任何資料類型或列舉型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="60806-157">You can specify any data type or the name of an enumeration.</span></span>  
  
-   <span data-ttu-id="60806-158">**預設類型。**</span><span class="sxs-lookup"><span data-stu-id="60806-158">**Default Type.**</span></span> <span data-ttu-id="60806-159">如果您未指定`datatype`，常數會採用的資料型別`initializer`。</span><span class="sxs-lookup"><span data-stu-id="60806-159">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="60806-160">如果您同時指定`datatype`和`initializer`的資料類型`initializer`必須可轉換為`datatype`。</span><span class="sxs-lookup"><span data-stu-id="60806-160">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="60806-161">如果沒有`datatype`也`initializer`沒有、 資料類型會預設為`Object`。</span><span class="sxs-lookup"><span data-stu-id="60806-161">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>  
  
-   <span data-ttu-id="60806-162">**型別不同。**</span><span class="sxs-lookup"><span data-stu-id="60806-162">**Different Types.**</span></span> <span data-ttu-id="60806-163">您可以指定不同的常數的不同資料類型使用個別`As`子句宣告每個變數。</span><span class="sxs-lookup"><span data-stu-id="60806-163">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="60806-164">不過，您無法宣告為相同的型別使用一個通用的數個常數`As`子句。</span><span class="sxs-lookup"><span data-stu-id="60806-164">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>  
  
-   <span data-ttu-id="60806-165">**初始化。**</span><span class="sxs-lookup"><span data-stu-id="60806-165">**Initialization.**</span></span> <span data-ttu-id="60806-166">您必須先初始化中的每個常數值`constantlist`。</span><span class="sxs-lookup"><span data-stu-id="60806-166">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="60806-167">您使用`initializer`提供要指派給常數的運算式。</span><span class="sxs-lookup"><span data-stu-id="60806-167">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="60806-168">運算式可以是常值、 已定義，其他常數和列舉型別成員已經定義的任何組合。</span><span class="sxs-lookup"><span data-stu-id="60806-168">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="60806-169">您可以使用算術和邏輯運算子來結合這類項目。</span><span class="sxs-lookup"><span data-stu-id="60806-169">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
     <span data-ttu-id="60806-170">您無法使用變數或函式中的`initializer`。</span><span class="sxs-lookup"><span data-stu-id="60806-170">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="60806-171">不過，您可以使用轉換關鍵字例如`CByte`和`CShort`。</span><span class="sxs-lookup"><span data-stu-id="60806-171">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="60806-172">您也可以使用`AscW`如果您呼叫與常數`String`或`Char`引數，因為，可以在編譯時期評估。</span><span class="sxs-lookup"><span data-stu-id="60806-172">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="60806-173">行為</span><span class="sxs-lookup"><span data-stu-id="60806-173">Behavior</span></span>  
  
-   <span data-ttu-id="60806-174">**範圍。**</span><span class="sxs-lookup"><span data-stu-id="60806-174">**Scope.**</span></span> <span data-ttu-id="60806-175">區域常數是只能從其程序或區塊內存取。</span><span class="sxs-lookup"><span data-stu-id="60806-175">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="60806-176">成員常數是可從其類別、 結構或模組內的任何位置存取。</span><span class="sxs-lookup"><span data-stu-id="60806-176">Member constants are accessible from anywhere within their class, structure, or module.</span></span>  
  
-   <span data-ttu-id="60806-177">**限定性條件。**</span><span class="sxs-lookup"><span data-stu-id="60806-177">**Qualification.**</span></span> <span data-ttu-id="60806-178">程式碼外部類別、 結構或模組必須限定成員常數的名稱，該類別、 結構或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="60806-178">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="60806-179">程式碼的外部程序或區塊不能參考該程序或區塊內的任何區域常數。</span><span class="sxs-lookup"><span data-stu-id="60806-179">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60806-180">範例</span><span class="sxs-lookup"><span data-stu-id="60806-180">Example</span></span>  
 <span data-ttu-id="60806-181">下列範例會使用`Const`陳述式來宣告常數取代常值。</span><span class="sxs-lookup"><span data-stu-id="60806-181">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="60806-182">範例</span><span class="sxs-lookup"><span data-stu-id="60806-182">Example</span></span>  
 <span data-ttu-id="60806-183">如果您定義資料類型的常數`Object`，Visual Basic 編譯器會提供其類型`initializer`，而不是`Object`。</span><span class="sxs-lookup"><span data-stu-id="60806-183">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="60806-184">在下列範例中，常數`naturalLogBase`具有執行階段類型`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="60806-184">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 <span data-ttu-id="60806-185">上述範例會使用<xref:System.Type.ToString%2A>方法<xref:System.Type>所傳回物件[GetType 運算子](../../../visual-basic/language-reference/operators/gettype-operator.md)，因為<xref:System.Type>無法轉換成`String`使用`CStr`。</span><span class="sxs-lookup"><span data-stu-id="60806-185">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60806-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60806-186">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="60806-187">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="60806-187">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="60806-188">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="60806-188">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="60806-189">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="60806-189">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="60806-190">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="60806-190">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="60806-191">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="60806-191">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="60806-192">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="60806-192">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [<span data-ttu-id="60806-193">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="60806-193">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="60806-194">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="60806-194">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
