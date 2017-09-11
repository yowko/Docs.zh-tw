---
title: "Enum 陳述式 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Enum
dev_langs:
- VB
helpviewer_keywords:
- enumerated constants
- Enum statement
- Private keyword, Enum statements
- Public keyword, in Enum statement
- variables [Visual Basic], enumeration
- constants, enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: 44
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ff075349756bd4c568833d049b50b3c3721d1b08
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="5c5d6-102">Enum 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c5d6-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="5c5d6-103">宣告列舉，並定義其成員的值。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c5d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c5d6-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="5c5d6-105">組件</span><span class="sxs-lookup"><span data-stu-id="5c5d6-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="5c5d6-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-106">Optional.</span></span> <span data-ttu-id="5c5d6-107">這個列舉型別所套用的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="5c5d6-108">您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧括住 (「`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="5c5d6-109"><xref:System.FlagsAttribute>屬性表示列舉型別的執行個體的值可以包含多個列舉成員，而且每個成員代表列舉值的位元欄位。</xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5c5d6-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="5c5d6-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-110">Optional.</span></span> <span data-ttu-id="5c5d6-111">指定哪些程式碼可以存取這個列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="5c5d6-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="5c5d6-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="5c5d6-113">Public</span><span class="sxs-lookup"><span data-stu-id="5c5d6-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="5c5d6-114">Protected</span><span class="sxs-lookup"><span data-stu-id="5c5d6-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="5c5d6-115">Friend</span><span class="sxs-lookup"><span data-stu-id="5c5d6-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="5c5d6-116">Private</span><span class="sxs-lookup"><span data-stu-id="5c5d6-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
     <span data-ttu-id="5c5d6-117">您可以指定`Protected``Friend`以允許從列舉型別的類別，衍生的類別或相同的組件內的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-117">You can specify `Protected``Friend` to allow access from code within the enumeration's class, a derived class, or the same assembly.</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="5c5d6-118">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-118">Optional.</span></span> <span data-ttu-id="5c5d6-119">指定此列舉型別會重新宣告，並隱藏同名的程式設計項目或在基底類別中的多載項目集。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-119">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="5c5d6-120">您可以指定[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)只列舉型別本身，而非其任何成員。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-120">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="5c5d6-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-121">Required.</span></span> <span data-ttu-id="5c5d6-122">列舉型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-122">Name of the enumeration.</span></span> <span data-ttu-id="5c5d6-123">如需有效的名稱，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-123">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="5c5d6-124">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-124">Optional.</span></span> <span data-ttu-id="5c5d6-125">列舉型別及其所有成員的資料型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-125">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="5c5d6-126">必要項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-126">Required.</span></span> <span data-ttu-id="5c5d6-127">此陳述式所宣告的成員常數的清單。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-127">List of member constants being declared in this statement.</span></span> <span data-ttu-id="5c5d6-128">多個成員會出現在個別的原始程式碼行。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-128">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="5c5d6-129">每個`member`具有以下的語法和組件︰`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="5c5d6-129">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="5c5d6-130">組件</span><span class="sxs-lookup"><span data-stu-id="5c5d6-130">Part</span></span>|<span data-ttu-id="5c5d6-131">說明</span><span class="sxs-lookup"><span data-stu-id="5c5d6-131">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="5c5d6-132">必要項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-132">Required.</span></span> <span data-ttu-id="5c5d6-133">這個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-133">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="5c5d6-134">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-134">Optional.</span></span> <span data-ttu-id="5c5d6-135">在編譯時期評估，以及指派給這個成員的運算式。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-135">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="5c5d6-136">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="5c5d6-136">`End` `Enum`</span></span>  
  
     <span data-ttu-id="5c5d6-137">終止 `Enum` 區塊。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-137">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c5d6-138">備註</span><span class="sxs-lookup"><span data-stu-id="5c5d6-138">Remarks</span></span>  
 <span data-ttu-id="5c5d6-139">如果您有一組不會變更將彼此邏輯相關的值，您可以定義它們一起列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-139">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="5c5d6-140">這提供有意義的列舉型別和成員，也就是比它們的值更好記名稱。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-140">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="5c5d6-141">然後，您可以使用在許多地方列舉型別成員在您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-141">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="5c5d6-142">使用列舉的優點包括︰</span><span class="sxs-lookup"><span data-stu-id="5c5d6-142">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="5c5d6-143">減少因調換或輸錯數字的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-143">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="5c5d6-144">可讓您輕鬆地在未來變更的值。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-144">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="5c5d6-145">讓程式碼更方便閱讀，這表示它是比較不可能會導入錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-145">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="5c5d6-146">可確保往後相容性。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-146">Ensures forward compatibility.</span></span> <span data-ttu-id="5c5d6-147">如果您使用列舉型別，程式碼就比較不可能失敗，如果有人在未來變更為成員名稱的對應值。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-147">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="5c5d6-148">列舉型別具有名稱、 基礎的資料型別和成員集合。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-148">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="5c5d6-149">每個成員代表一個常數。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-149">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="5c5d6-150">類別、 結構、 模組或介面層級以外的任何程序，在宣告列舉類型是*成員列舉*。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-150">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="5c5d6-151">它是類別、 結構、 模組或介面宣告它的成員。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-151">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="5c5d6-152">成員列舉型別可以從任何地方來存取其類別、 結構、 模組或介面中。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-152">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="5c5d6-153">程式碼類別之外，結構或模組必須限定成員列舉型別的名稱，該類別、 結構或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-153">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="5c5d6-154">您可以不需要使用完整限定的名稱加上[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)陳述式的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-154">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="5c5d6-155">命名空間層級以外任何類別、 結構、 模組或介面，在宣告列舉型別是命名空間中的成員。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-155">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="5c5d6-156">*宣告內容*列舉型別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，而且不能是程序。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-156">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="5c5d6-157">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-157">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="5c5d6-158">您可以分別套用在屬性列舉型別整體而言，但不是屬於其成員。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-158">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="5c5d6-159">屬性會提供組件的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-159">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="5c5d6-160">資料類型</span><span class="sxs-lookup"><span data-stu-id="5c5d6-160">Data Type</span></span>  
 <span data-ttu-id="5c5d6-161">`Enum`陳述式可以宣告列舉的資料型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-161">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="5c5d6-162">每個成員會在列舉資料類型。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-162">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="5c5d6-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span><span class="sxs-lookup"><span data-stu-id="5c5d6-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="5c5d6-164">如果您未指定`datatype`列舉，每個成員都會採用的資料型別其`initializer`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-164">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="5c5d6-165">如果您同時指定`datatype`和`initializer`，資料類型`initializer`必須轉換成`datatype`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-165">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="5c5d6-166">如果沒有`datatype`也`initializer`的話，資料類型的預設值為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-166">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="5c5d6-167">初始化成員</span><span class="sxs-lookup"><span data-stu-id="5c5d6-167">Initializing Members</span></span>  
 <span data-ttu-id="5c5d6-168">`Enum`陳述式可以初始化內容中選取之成員的`memberlist`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-168">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="5c5d6-169">您使用`initializer`提供要指派給成員的運算式。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-169">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="5c5d6-170">如果您未指定`initializer`成員時，Visual Basic 將它初始化為零 (如果是第一個`member`中`memberlist`)，或值大一比前面`member`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-170">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="5c5d6-171">提供在每個運算式`initializer`可以是常值、 其他已定義的常數和列舉型別成員已經定義，包括先前的這個列舉型別成員的任何組合。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-171">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="5c5d6-172">您可以使用算術和邏輯運算子來結合這類項目。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-172">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="5c5d6-173">您無法使用變數或函式中的`initializer`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-173">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="5c5d6-174">不過，您可以使用轉換關鍵字例如`CByte`和`CShort`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-174">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="5c5d6-175">您也可以使用`AscW`如果您呼叫與常數`String`或`Char`引數，因為可以在編譯時期評估的。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-175">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="5c5d6-176">列舉型別不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-176">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="5c5d6-177">如果成員指派的浮點值和`Option Strict`設定為 on，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-177">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="5c5d6-178">如果`Option Strict`值會自動轉換為已關閉，`Enum`型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-178">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="5c5d6-179">如果成員的值超過允許的範圍為基礎的資料型別，或是初始化為基礎的資料類型所允許的最大值的任何成員，編譯器會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-179">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="5c5d6-180">修飾詞</span><span class="sxs-lookup"><span data-stu-id="5c5d6-180">Modifiers</span></span>  
 <span data-ttu-id="5c5d6-181">類別、 結構、 模組和介面的成員列舉型別預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-181">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="5c5d6-182">您可以調整存取層級的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-182">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="5c5d6-183">命名空間成員列舉型別預設為 friend 存取權限。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-183">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="5c5d6-184">您可以調整為公開，但不是屬於私用或受保護的存取層。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-184">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="5c5d6-185">如需詳細資訊，請參閱[在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-185">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="5c5d6-186">所有列舉型別成員具有公用存取，且您無法使用任何存取修飾詞上面。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-186">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="5c5d6-187">不過，如果列舉型別本身具有較嚴格的存取層級，指定列舉型別存取層級的優先順序。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-187">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="5c5d6-188">根據預設，所有列舉型別是類型，其欄位是常數。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-188">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="5c5d6-189">因此`Shared`， `Static`，和`ReadOnly`宣告列舉型別或其成員時，就不能使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-189">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="5c5d6-190">指派多個值</span><span class="sxs-lookup"><span data-stu-id="5c5d6-190">Assigning Multiple Values</span></span>  
 <span data-ttu-id="5c5d6-191">列舉型別通常代表互斥的值。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-191">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="5c5d6-192">藉由<xref:System.FlagsAttribute>屬性中`Enum`宣告中，您可以改為指派多個值給列舉型別的執行個體。</xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5c5d6-192">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="5c5d6-193"><xref:System.FlagsAttribute>屬性會指定列舉型別視為位元欄位，也就是一組旗標。</xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5c5d6-193">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="5c5d6-194">這些稱為*位元*列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-194">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="5c5d6-195">當您宣告列舉型別使用<xref:System.FlagsAttribute>屬性，我們建議您使用是 2、 1、 2、 4、 8、 16 和等等的次方值。</xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5c5d6-195">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="5c5d6-196">我們也建議 「 無 」 成員，其值為 0 的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-196">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="5c5d6-197">如需其他指導方針，請參閱<xref:System.FlagsAttribute>和<xref:System.Enum>.</xref:System.Enum> </xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5c5d6-197">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5d6-198">範例</span><span class="sxs-lookup"><span data-stu-id="5c5d6-198">Example</span></span>  
 <span data-ttu-id="5c5d6-199">下列範例示範如何使用`Enum`陳述式。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-199">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="5c5d6-200">請注意，成員指`EggSizeEnum.Medium`，而不是`Medium`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-200">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 <span data-ttu-id="5c5d6-201">[!code-vb[VbEnumsTask #&41;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c5d6-201">[!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5d6-202">範例</span><span class="sxs-lookup"><span data-stu-id="5c5d6-202">Example</span></span>  
 <span data-ttu-id="5c5d6-203">下列範例中的方法已超出`Egg`類別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="5c5d6-204">因此，`EggSizeEnum`完整限定為`Egg.EggSizeEnum`。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 <span data-ttu-id="5c5d6-205">[!code-vb[VbEnumsTask #&42;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c5d6-205">[!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5d6-206">範例</span><span class="sxs-lookup"><span data-stu-id="5c5d6-206">Example</span></span>  
 <span data-ttu-id="5c5d6-207">下列範例會使用`Enum`陳述式來定義一組相關的具名常數的值。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-207">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="5c5d6-208">在此情況下，值會是您可以選擇設計資料庫的資料輸入表單的色彩。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-208">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 <span data-ttu-id="5c5d6-209">[!code-vb[VbEnumsTask #&30;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c5d6-209">[!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5d6-210">範例</span><span class="sxs-lookup"><span data-stu-id="5c5d6-210">Example</span></span>  
 <span data-ttu-id="5c5d6-211">下列範例包含正數和負數的值。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-211">The following example shows values that include both positive and negative numbers.</span></span>  
  
 <span data-ttu-id="5c5d6-212">[!code-vb[VbEnumsTask #&31;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c5d6-212">[!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5d6-213">範例</span><span class="sxs-lookup"><span data-stu-id="5c5d6-213">Example</span></span>  
 <span data-ttu-id="5c5d6-214">在下列範例中，`As`子句用來指定`datatype`的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-214">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 <span data-ttu-id="5c5d6-215">[!code-vb[VbEnumsTask #&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c5d6-215">[!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5d6-216">範例</span><span class="sxs-lookup"><span data-stu-id="5c5d6-216">Example</span></span>  
 <span data-ttu-id="5c5d6-217">下列範例示範如何使用位元的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-217">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="5c5d6-218">多個值可以指派給位元的列舉型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-218">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="5c5d6-219">`Enum`宣告包含<xref:System.FlagsAttribute>屬性，表示列舉型別可以視為一組旗標。</xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5c5d6-219">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 <span data-ttu-id="5c5d6-220">[!code-vb[VbEnumsTask #&61;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c5d6-220">[!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5d6-221">範例</span><span class="sxs-lookup"><span data-stu-id="5c5d6-221">Example</span></span>  
 <span data-ttu-id="5c5d6-222">下列範例會逐一列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5c5d6-222">The following example iterates through an enumeration.</span></span> <span data-ttu-id="5c5d6-223">它會使用<xref:System.Enum.GetNames%2A>方法來擷取列舉中的成員名稱的陣列和<xref:System.Enum.GetValues%2A>擷取成員值的陣列。</xref:System.Enum.GetValues%2A> </xref:System.Enum.GetNames%2A></span><span class="sxs-lookup"><span data-stu-id="5c5d6-223">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 <span data-ttu-id="5c5d6-224">[!code-vb[VbEnumsTask #&51;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c5d6-224">[!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5d6-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c5d6-225">See Also</span></span>  
 <span data-ttu-id="5c5d6-226"><xref:System.Enum></xref:System.Enum></span><span class="sxs-lookup"><span data-stu-id="5c5d6-226"><xref:System.Enum></span></span>   
 <span data-ttu-id="5c5d6-227"><xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="5c5d6-227"><xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>   
<span data-ttu-id="5c5d6-228"> [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5c5d6-228"> [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="5c5d6-229"> [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5c5d6-229"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="5c5d6-230"> [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="5c5d6-230"> [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="5c5d6-231"> [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="5c5d6-231"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="5c5d6-232"> [常數和列舉](../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="5c5d6-232"> [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
