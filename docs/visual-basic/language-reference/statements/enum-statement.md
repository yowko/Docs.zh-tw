---
title: Enum 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 89de51f2551437d102ccdc5a0f1ff5f23b53e47f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="70da6-102">Enum 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70da6-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="70da6-103">宣告列舉，並定義其成員的值。</span><span class="sxs-lookup"><span data-stu-id="70da6-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70da6-104">語法</span><span class="sxs-lookup"><span data-stu-id="70da6-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="70da6-105">組件</span><span class="sxs-lookup"><span data-stu-id="70da6-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="70da6-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="70da6-106">Optional.</span></span> <span data-ttu-id="70da6-107">套用至此列舉的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="70da6-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="70da6-108">您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)在角括號 ("`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="70da6-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="70da6-109"><xref:System.FlagsAttribute>屬性表示列舉型別的執行個體的值可以包含多個列舉成員，而且每個成員代表位元欄位中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="70da6-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="70da6-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="70da6-110">Optional.</span></span> <span data-ttu-id="70da6-111">指定哪些程式碼可以存取這個列舉型別。</span><span class="sxs-lookup"><span data-stu-id="70da6-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="70da6-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="70da6-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="70da6-113">Public</span><span class="sxs-lookup"><span data-stu-id="70da6-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="70da6-114">Protected</span><span class="sxs-lookup"><span data-stu-id="70da6-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="70da6-115">Friend</span><span class="sxs-lookup"><span data-stu-id="70da6-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="70da6-116">Private</span><span class="sxs-lookup"><span data-stu-id="70da6-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
     <span data-ttu-id="70da6-117">您可以指定`Protected``Friend`允許從列舉型別的類別，衍生的類別或相同組件內的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="70da6-117">You can specify `Protected``Friend` to allow access from code within the enumeration's class, a derived class, or the same assembly.</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="70da6-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="70da6-118">Optional.</span></span> <span data-ttu-id="70da6-119">指定此列舉型別會重新宣告並隱藏相同具名的程式設計項目或基底類別中的多載項目集。</span><span class="sxs-lookup"><span data-stu-id="70da6-119">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="70da6-120">您可以指定[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)只列舉型別本身，而非它的任何成員。</span><span class="sxs-lookup"><span data-stu-id="70da6-120">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="70da6-121">必要。</span><span class="sxs-lookup"><span data-stu-id="70da6-121">Required.</span></span> <span data-ttu-id="70da6-122">列舉型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="70da6-122">Name of the enumeration.</span></span> <span data-ttu-id="70da6-123">如需有效的名稱資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="70da6-123">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="70da6-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="70da6-124">Optional.</span></span> <span data-ttu-id="70da6-125">資料類型的列舉型別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="70da6-125">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="70da6-126">必要。</span><span class="sxs-lookup"><span data-stu-id="70da6-126">Required.</span></span> <span data-ttu-id="70da6-127">此陳述式所宣告的成員常數的清單。</span><span class="sxs-lookup"><span data-stu-id="70da6-127">List of member constants being declared in this statement.</span></span> <span data-ttu-id="70da6-128">多個成員會出現在個別的原始程式碼行。</span><span class="sxs-lookup"><span data-stu-id="70da6-128">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="70da6-129">每個`member`具有下列語法和組件： `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="70da6-129">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="70da6-130">組件</span><span class="sxs-lookup"><span data-stu-id="70da6-130">Part</span></span>|<span data-ttu-id="70da6-131">描述</span><span class="sxs-lookup"><span data-stu-id="70da6-131">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="70da6-132">必要。</span><span class="sxs-lookup"><span data-stu-id="70da6-132">Required.</span></span> <span data-ttu-id="70da6-133">這個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="70da6-133">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="70da6-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="70da6-134">Optional.</span></span> <span data-ttu-id="70da6-135">在編譯時期評估，以及指派給這個成員的運算式。</span><span class="sxs-lookup"><span data-stu-id="70da6-135">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="70da6-136">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="70da6-136">`End` `Enum`</span></span>  
  
     <span data-ttu-id="70da6-137">終止 `Enum` 區塊。</span><span class="sxs-lookup"><span data-stu-id="70da6-137">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70da6-138">備註</span><span class="sxs-lookup"><span data-stu-id="70da6-138">Remarks</span></span>  
 <span data-ttu-id="70da6-139">如果您有一組邏輯上彼此相關的不變值時，您可以定義它們一起列舉型別。</span><span class="sxs-lookup"><span data-stu-id="70da6-139">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="70da6-140">這提供有意義的名稱，列舉型別和成員，也就是您更輕鬆地記住比它們的值。</span><span class="sxs-lookup"><span data-stu-id="70da6-140">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="70da6-141">然後，您可以使用在許多地方列舉型別成員在您的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="70da6-141">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="70da6-142">使用列舉的優點包括：</span><span class="sxs-lookup"><span data-stu-id="70da6-142">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="70da6-143">減少調換或輸入數字的錯誤所造成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="70da6-143">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="70da6-144">可讓您輕鬆地在未來變更的值。</span><span class="sxs-lookup"><span data-stu-id="70da6-144">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="70da6-145">讓程式碼更方便閱讀，這表示它是比較不可能會導入錯誤。</span><span class="sxs-lookup"><span data-stu-id="70da6-145">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="70da6-146">可確保往後相容性。</span><span class="sxs-lookup"><span data-stu-id="70da6-146">Ensures forward compatibility.</span></span> <span data-ttu-id="70da6-147">如果您使用列舉型別時，程式碼就比較不可能失敗，如果有人在未來變更為成員名稱的對應值。</span><span class="sxs-lookup"><span data-stu-id="70da6-147">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="70da6-148">列舉型別具有名稱、 基礎的資料型別和成員集合。</span><span class="sxs-lookup"><span data-stu-id="70da6-148">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="70da6-149">每個成員表示常數。</span><span class="sxs-lookup"><span data-stu-id="70da6-149">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="70da6-150">在類別、 結構、 模組或介面層級，任何程序之外宣告列舉類型是*成員列舉*。</span><span class="sxs-lookup"><span data-stu-id="70da6-150">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="70da6-151">它是類別、 結構、 模組或介面宣告它的成員。</span><span class="sxs-lookup"><span data-stu-id="70da6-151">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="70da6-152">成員列舉型別可以從任何地方內存取其類別、 結構、 模組或介面。</span><span class="sxs-lookup"><span data-stu-id="70da6-152">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="70da6-153">程式碼外部類別、 結構或模組必須限定成員列舉型別的名稱，該類別、 結構或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="70da6-153">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="70da6-154">您可以避免需要使用完整限定的名稱，藉由新增[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)原始程式檔陳述式。</span><span class="sxs-lookup"><span data-stu-id="70da6-154">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="70da6-155">在命名空間層級，任何類別、 結構、 模組或介面外部宣告的列舉是在其出現的命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="70da6-155">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="70da6-156">*宣告內容*列舉型別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，並且不能在程序。</span><span class="sxs-lookup"><span data-stu-id="70da6-156">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="70da6-157">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="70da6-157">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="70da6-158">您可以將屬性套用至整個列舉，但不是屬於其成員個別。</span><span class="sxs-lookup"><span data-stu-id="70da6-158">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="70da6-159">屬性會提供組件的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="70da6-159">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="70da6-160">資料類型</span><span class="sxs-lookup"><span data-stu-id="70da6-160">Data Type</span></span>  
 <span data-ttu-id="70da6-161">`Enum`陳述式可以宣告列舉的資料類型。</span><span class="sxs-lookup"><span data-stu-id="70da6-161">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="70da6-162">每個成員會在列舉資料類型。</span><span class="sxs-lookup"><span data-stu-id="70da6-162">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="70da6-163">您可以指定`Byte`， `Integer`， `Long`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`。</span><span class="sxs-lookup"><span data-stu-id="70da6-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="70da6-164">如果您未指定`datatype`對於列舉型別，每個成員進行的資料型別其`initializer`。</span><span class="sxs-lookup"><span data-stu-id="70da6-164">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="70da6-165">如果您同時指定`datatype`和`initializer`的資料類型`initializer`必須可轉換為`datatype`。</span><span class="sxs-lookup"><span data-stu-id="70da6-165">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="70da6-166">如果沒有`datatype`也`initializer`沒有、 資料類型會預設為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="70da6-166">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="70da6-167">初始化成員</span><span class="sxs-lookup"><span data-stu-id="70da6-167">Initializing Members</span></span>  
 <span data-ttu-id="70da6-168">`Enum`陳述式可以初始化內容中選取成員的`memberlist`。</span><span class="sxs-lookup"><span data-stu-id="70da6-168">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="70da6-169">您使用`initializer`提供運算式，以指派的成員。</span><span class="sxs-lookup"><span data-stu-id="70da6-169">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="70da6-170">如果您未指定`initializer`成員，Visual Basic 將它初始化成零 (如果它是第一個`member`中`memberlist`)，或大於 1 以外的前置值`member`。</span><span class="sxs-lookup"><span data-stu-id="70da6-170">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="70da6-171">在每個提供的運算式`initializer`可以是常值、 已定義，其他常數和列舉成員已定義，包括先前的成員，這個列舉型別之任何組合。</span><span class="sxs-lookup"><span data-stu-id="70da6-171">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="70da6-172">您可以使用算術和邏輯運算子來結合這類項目。</span><span class="sxs-lookup"><span data-stu-id="70da6-172">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="70da6-173">您無法使用變數或函式中的`initializer`。</span><span class="sxs-lookup"><span data-stu-id="70da6-173">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="70da6-174">不過，您可以使用轉換關鍵字例如`CByte`和`CShort`。</span><span class="sxs-lookup"><span data-stu-id="70da6-174">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="70da6-175">您也可以使用`AscW`如果您呼叫與常數`String`或`Char`引數，因為，可以在編譯時期評估。</span><span class="sxs-lookup"><span data-stu-id="70da6-175">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="70da6-176">列舉型別不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="70da6-176">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="70da6-177">如果將浮點值指派給成員和`Option Strict`設為 on，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="70da6-177">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="70da6-178">如果`Option Strict`已關閉，值會自動轉換為`Enum`型別。</span><span class="sxs-lookup"><span data-stu-id="70da6-178">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="70da6-179">如果成員的值超過允許的範圍為基礎的資料類型，或如果您初始化基礎資料類型所允許的最大值的任何成員，編譯器會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="70da6-179">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="70da6-180">修飾詞</span><span class="sxs-lookup"><span data-stu-id="70da6-180">Modifiers</span></span>  
 <span data-ttu-id="70da6-181">類別、 結構、 模組和介面的成員列舉型別預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="70da6-181">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="70da6-182">您可以調整其存取層級，使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="70da6-182">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="70da6-183">命名空間成員列舉型別預設為 friend 存取權限。</span><span class="sxs-lookup"><span data-stu-id="70da6-183">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="70da6-184">您可以調整其存取層級為公開，但不是屬於私用或受保護。</span><span class="sxs-lookup"><span data-stu-id="70da6-184">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="70da6-185">如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="70da6-185">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="70da6-186">所有列舉型別成員具有公用存取，且您無法使用任何存取修飾詞在其上。</span><span class="sxs-lookup"><span data-stu-id="70da6-186">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="70da6-187">不過，如果列舉型別本身會有更多限制的存取層級，指定之列舉的存取層級會優先使用。</span><span class="sxs-lookup"><span data-stu-id="70da6-187">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="70da6-188">根據預設，所有列舉型別是型別，其欄位是常數。</span><span class="sxs-lookup"><span data-stu-id="70da6-188">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="70da6-189">因此`Shared`， `Static`，和`ReadOnly`宣告列舉型別或其成員時，就無法使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="70da6-189">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="70da6-190">指派多個值</span><span class="sxs-lookup"><span data-stu-id="70da6-190">Assigning Multiple Values</span></span>  
 <span data-ttu-id="70da6-191">列舉型別通常代表互斥的值。</span><span class="sxs-lookup"><span data-stu-id="70da6-191">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="70da6-192">藉由<xref:System.FlagsAttribute>屬性`Enum`宣告中，您可以改為將指派多個值執行個體的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="70da6-192">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="70da6-193"><xref:System.FlagsAttribute>屬性會指定列舉視為位元欄位，也就是一組旗標。</span><span class="sxs-lookup"><span data-stu-id="70da6-193">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="70da6-194">這種讀取稱為*位元*列舉型別。</span><span class="sxs-lookup"><span data-stu-id="70da6-194">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="70da6-195">當您使用宣告列舉<xref:System.FlagsAttribute>屬性，我們建議您使用是 2、 1、 2、 4、 8、 16 和等等的次方值。</span><span class="sxs-lookup"><span data-stu-id="70da6-195">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="70da6-196">我們也建議"None"是的成員，其值為 0 的名稱。</span><span class="sxs-lookup"><span data-stu-id="70da6-196">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="70da6-197">如需其他指導方針，請參閱<xref:System.FlagsAttribute>和<xref:System.Enum>。</span><span class="sxs-lookup"><span data-stu-id="70da6-197">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70da6-198">範例</span><span class="sxs-lookup"><span data-stu-id="70da6-198">Example</span></span>  
 <span data-ttu-id="70da6-199">下列範例示範如何使用`Enum`陳述式。</span><span class="sxs-lookup"><span data-stu-id="70da6-199">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="70da6-200">請注意，成員指`EggSizeEnum.Medium`，而不是`Medium`。</span><span class="sxs-lookup"><span data-stu-id="70da6-200">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="70da6-201">範例</span><span class="sxs-lookup"><span data-stu-id="70da6-201">Example</span></span>  
 <span data-ttu-id="70da6-202">下列範例中的方法是外部`Egg`類別。</span><span class="sxs-lookup"><span data-stu-id="70da6-202">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="70da6-203">因此，`EggSizeEnum`是完整限定為`Egg.EggSizeEnum`。</span><span class="sxs-lookup"><span data-stu-id="70da6-203">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="70da6-204">範例</span><span class="sxs-lookup"><span data-stu-id="70da6-204">Example</span></span>  
 <span data-ttu-id="70da6-205">下列範例會使用`Enum`陳述式來定義一組相關的具名常數的值。</span><span class="sxs-lookup"><span data-stu-id="70da6-205">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="70da6-206">在此案例中的值是設計為資料庫的資料輸入表單時，可能會選擇的色彩。</span><span class="sxs-lookup"><span data-stu-id="70da6-206">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="70da6-207">範例</span><span class="sxs-lookup"><span data-stu-id="70da6-207">Example</span></span>  
 <span data-ttu-id="70da6-208">下列範例顯示包含正數和負數的值。</span><span class="sxs-lookup"><span data-stu-id="70da6-208">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="70da6-209">範例</span><span class="sxs-lookup"><span data-stu-id="70da6-209">Example</span></span>  
 <span data-ttu-id="70da6-210">在下列範例中，`As`子句用來指定`datatype`的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="70da6-210">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="70da6-211">範例</span><span class="sxs-lookup"><span data-stu-id="70da6-211">Example</span></span>  
 <span data-ttu-id="70da6-212">下列範例會示範如何使用位元列舉。</span><span class="sxs-lookup"><span data-stu-id="70da6-212">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="70da6-213">多個值可以指派給位元列舉型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="70da6-213">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="70da6-214">`Enum`宣告包含<xref:System.FlagsAttribute>屬性，表示列舉型別可以視為一組旗標。</span><span class="sxs-lookup"><span data-stu-id="70da6-214">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="70da6-215">範例</span><span class="sxs-lookup"><span data-stu-id="70da6-215">Example</span></span>  
 <span data-ttu-id="70da6-216">下列範例會逐一列舉型別。</span><span class="sxs-lookup"><span data-stu-id="70da6-216">The following example iterates through an enumeration.</span></span> <span data-ttu-id="70da6-217">它會使用<xref:System.Enum.GetNames%2A>方法來擷取列舉中的成員名稱的陣列和<xref:System.Enum.GetValues%2A>擷取成員值的陣列。</span><span class="sxs-lookup"><span data-stu-id="70da6-217">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="70da6-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70da6-218">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="70da6-219">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="70da6-219">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="70da6-220">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="70da6-220">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="70da6-221">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="70da6-221">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="70da6-222">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="70da6-222">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="70da6-223">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="70da6-223">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
