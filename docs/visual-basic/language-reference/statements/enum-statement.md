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
ms.openlocfilehash: f1086fdc26f1909e751617b78e0cd31f2a8b1b95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656657"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="d5bc4-102">Enum 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5bc4-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="d5bc4-103">宣告列舉，並定義其成員的值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5bc4-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5bc4-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="d5bc4-105">組件</span><span class="sxs-lookup"><span data-stu-id="d5bc4-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="d5bc4-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-106">Optional.</span></span> <span data-ttu-id="d5bc4-107">這個列舉型別所套用的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="d5bc4-108">您必須將括[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧 ("`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="d5bc4-109"><xref:System.FlagsAttribute>屬性表示列舉型別的執行個體的值可以包含多個列舉成員，而且每個成員，代表在列舉值的位元欄位。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="d5bc4-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-110">Optional.</span></span> <span data-ttu-id="d5bc4-111">指定哪些程式碼可以存取此列舉型別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="d5bc4-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d5bc4-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="d5bc4-113">Public</span><span class="sxs-lookup"><span data-stu-id="d5bc4-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="d5bc4-114">Protected</span><span class="sxs-lookup"><span data-stu-id="d5bc4-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="d5bc4-115">Friend</span><span class="sxs-lookup"><span data-stu-id="d5bc4-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="d5bc4-116">Private</span><span class="sxs-lookup"><span data-stu-id="d5bc4-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="d5bc4-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="d5bc4-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="d5bc4-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="d5bc4-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="d5bc4-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-119">Optional.</span></span> <span data-ttu-id="d5bc4-120">指定此列舉型別重新宣告，並隱藏的名稱相同的程式設計項目或一組多載的項目，基底類別中。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="d5bc4-121">您可以指定[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)只在列舉型別本身，而不是在它的任何成員。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="d5bc4-122">必要項。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-122">Required.</span></span> <span data-ttu-id="d5bc4-123">列舉型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-123">Name of the enumeration.</span></span> <span data-ttu-id="d5bc4-124">如需有效的名稱，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="d5bc4-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-125">Optional.</span></span> <span data-ttu-id="d5bc4-126">列舉型別及其所有成員的資料型別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="d5bc4-127">必要項。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-127">Required.</span></span> <span data-ttu-id="d5bc4-128">此陳述式所宣告的成員常數的清單。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="d5bc4-129">多個成員會出現在個別的原始程式碼行。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="d5bc4-130">每個`member`具有下列語法和組成部分： `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="d5bc4-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="d5bc4-131">組件</span><span class="sxs-lookup"><span data-stu-id="d5bc4-131">Part</span></span>|<span data-ttu-id="d5bc4-132">描述</span><span class="sxs-lookup"><span data-stu-id="d5bc4-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="d5bc4-133">必要項。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-133">Required.</span></span> <span data-ttu-id="d5bc4-134">這個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="d5bc4-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-135">Optional.</span></span> <span data-ttu-id="d5bc4-136">在編譯時期評估，以及指派給這個成員的運算式。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="d5bc4-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="d5bc4-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="d5bc4-138">終止 `Enum` 區塊。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5bc4-139">備註</span><span class="sxs-lookup"><span data-stu-id="d5bc4-139">Remarks</span></span>  
 <span data-ttu-id="d5bc4-140">如果您有一組彼此邏輯相關的不變值時，可以在列舉型別一起定義它們。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="d5bc4-141">這會提供有意義的名稱，列舉型別和其成員，也就是容易記住它們的值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="d5bc4-142">然後，您可以使用在許多地方列舉型別成員在您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="d5bc4-143">使用列舉的優點包括：</span><span class="sxs-lookup"><span data-stu-id="d5bc4-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="d5bc4-144">減少調換，或輸入數字的錯誤所造成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="d5bc4-145">可讓您輕鬆地在未來變更的值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="d5bc4-146">讓程式碼更方便閱讀，這表示它不太可能會導入錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="d5bc4-147">可確保往後相容性。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-147">Ensures forward compatibility.</span></span> <span data-ttu-id="d5bc4-148">如果您使用列舉型別時，您的程式碼是比較不可能失敗，如果有人在未來變更為成員名稱的對應值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="d5bc4-149">列舉型別具有名稱、 基礎資料類型和一組的成員。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="d5bc4-150">每一個成員代表的常數。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="d5bc4-151">在類別、 結構、 模組或介面層級，任何程序中，外部宣告的列舉型別是*成員的列舉型別*。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="d5bc4-152">它是類別、 結構、 模組或介面會宣告它的成員。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="d5bc4-153">成員的列舉型別可以從任何位置內存取他們的類別、 結構、 模組或介面。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="d5bc4-154">程式碼類別之外，結構或模組必須限定成員列舉型別的名稱，該類別、 結構或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="d5bc4-155">您可以避免需要使用完整限定的名稱加上[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)原始程式檔陳述式。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="d5bc4-156">在命名空間層級，任何類別、 結構、 模組或介面外部宣告的列舉型別是在出現的命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="d5bc4-157">*宣告內容*列舉型別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，並不是程序。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="d5bc4-158">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="d5bc4-159">您可以將屬性套用至整個列舉型別而非其成員個別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="d5bc4-160">屬性會提供資訊給組件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="d5bc4-161">資料類型</span><span class="sxs-lookup"><span data-stu-id="d5bc4-161">Data Type</span></span>  
 <span data-ttu-id="d5bc4-162">`Enum`陳述式可以宣告列舉的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="d5bc4-163">每個成員會在列舉的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="d5bc4-164">您可以指定`Byte`， `Integer`， `Long`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="d5bc4-165">如果您未指定`datatype`列舉中，每個成員都會採用的資料型別其`initializer`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="d5bc4-166">如果您同時指定`datatype`並`initializer`的資料類型`initializer`必須可轉換成`datatype`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="d5bc4-167">如果既未`datatype`也`initializer`已存在，將資料類型會預設為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="d5bc4-168">初始化成員</span><span class="sxs-lookup"><span data-stu-id="d5bc4-168">Initializing Members</span></span>  
 <span data-ttu-id="d5bc4-169">`Enum`陳述式可以初始化中的所選成員的內容`memberlist`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="d5bc4-170">您使用`initializer`提供要指派給成員的運算式。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="d5bc4-171">如果您未指定`initializer`成員，Visual Basic 將它初始化為零 (如果它是第一個`member`中`memberlist`)，或值比前一大`member`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="d5bc4-172">在每個所提供的運算式`initializer`可以是常值、 已定義，其他常數和列舉成員已定義，包括先前的成員，這個列舉型別的任何組合。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="d5bc4-173">您可以使用算術和邏輯運算子來結合這類項目。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="d5bc4-174">您無法使用變數或函式中的`initializer`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="d5bc4-175">不過，您可以使用轉換關鍵字這類`CByte`和`CShort`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="d5bc4-176">您也可以使用`AscW`如果您呼叫它具有常數`String`或`Char`引數，因為，可以在編譯時期評估。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="d5bc4-177">列舉型別不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="d5bc4-178">如果將成員指派為浮點數值和`Option Strict`設定為 on，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="d5bc4-179">如果`Option Strict`已關閉，值會自動轉換為`Enum`型別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="d5bc4-180">如果成員的值超過允許的範圍為基礎的資料類型，或如果您初始化任何成員為基礎的資料類型所允許的最大值時，編譯器會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="d5bc4-181">修飾詞</span><span class="sxs-lookup"><span data-stu-id="d5bc4-181">Modifiers</span></span>  
 <span data-ttu-id="d5bc4-182">類別、 結構、 模組和介面成員列舉型別的預設值為公用存取。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="d5bc4-183">您可以調整它們的存取層級，使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="d5bc4-184">命名空間成員列舉型別預設為 friend 存取權限。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="d5bc4-185">您可以調整其存取層級 public，但不是屬於私用或受保護。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="d5bc4-186">如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="d5bc4-187">所有的列舉型別成員具有公用存取，而且您無法使用任何存取修飾詞在其上。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="d5bc4-188">不過，如果列舉型別本身具有更具限制性的存取層級，指定的列舉存取層級會優先。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="d5bc4-189">根據預設，所有列舉都是型別，而且其欄位都是常數。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="d5bc4-190">因此`Shared`， `Static`，和`ReadOnly`宣告列舉型別或其成員時，就無法使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="d5bc4-191">指派多個值</span><span class="sxs-lookup"><span data-stu-id="d5bc4-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="d5bc4-192">列舉型別通常代表互斥的值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="d5bc4-193">加<xref:System.FlagsAttribute>屬性中`Enum`宣告中，您可以改為將指派多個值給列舉型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="d5bc4-194"><xref:System.FlagsAttribute>屬性會指定列舉型別視為位元欄位，也就是一組旗標。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="d5bc4-195">這些稱為*位元*列舉型別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="d5bc4-196">當您使用宣告列舉<xref:System.FlagsAttribute>屬性，我們建議您使用 2，可為、 1、 2、 4、 8、 16，並依此類推的次方的值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="d5bc4-197">我們也建議 「 無 」 是的成員，其值為 0 的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="d5bc4-198">如需其他指導方針，請參閱<xref:System.FlagsAttribute>和<xref:System.Enum>。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5bc4-199">範例</span><span class="sxs-lookup"><span data-stu-id="d5bc4-199">Example</span></span>  
 <span data-ttu-id="d5bc4-200">下列範例顯示如何使用 `Enum` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="d5bc4-201">請注意，成員指`EggSizeEnum.Medium`，而不是`Medium`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="d5bc4-202">範例</span><span class="sxs-lookup"><span data-stu-id="d5bc4-202">Example</span></span>  
 <span data-ttu-id="d5bc4-203">下列範例中的方法將會超出`Egg`類別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="d5bc4-204">因此，`EggSizeEnum`完整限定為`Egg.EggSizeEnum`。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="d5bc4-205">範例</span><span class="sxs-lookup"><span data-stu-id="d5bc4-205">Example</span></span>  
 <span data-ttu-id="d5bc4-206">下列範例會使用`Enum`陳述式來定義一組相關的具名常數的值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="d5bc4-207">在此情況下，值會是您可能會選擇設計資料庫的資料輸入表單的色彩。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="d5bc4-208">範例</span><span class="sxs-lookup"><span data-stu-id="d5bc4-208">Example</span></span>  
 <span data-ttu-id="d5bc4-209">下列範例顯示包含正數和負數數字的值。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="d5bc4-210">範例</span><span class="sxs-lookup"><span data-stu-id="d5bc4-210">Example</span></span>  
 <span data-ttu-id="d5bc4-211">在下列範例中，`As`子句來指定`datatype`的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="d5bc4-212">範例</span><span class="sxs-lookup"><span data-stu-id="d5bc4-212">Example</span></span>  
 <span data-ttu-id="d5bc4-213">下列範例示範如何使用的位元列舉。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="d5bc4-214">多個值可以指派給位元的列舉型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="d5bc4-215">`Enum`宣告包含<xref:System.FlagsAttribute>屬性，表示列舉型別，可以視為一組旗標。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="d5bc4-216">範例</span><span class="sxs-lookup"><span data-stu-id="d5bc4-216">Example</span></span>  
 <span data-ttu-id="d5bc4-217">下列範例會逐一列舉型別。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="d5bc4-218">它會使用<xref:System.Enum.GetNames%2A>方法來擷取列舉的成員名稱的陣列和<xref:System.Enum.GetValues%2A>擷取成員值的陣列。</span><span class="sxs-lookup"><span data-stu-id="d5bc4-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d5bc4-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5bc4-219">See also</span></span>
- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="d5bc4-220">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="d5bc4-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="d5bc4-221">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="d5bc4-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="d5bc4-222">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="d5bc4-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="d5bc4-223">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="d5bc4-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d5bc4-224">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="d5bc4-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
