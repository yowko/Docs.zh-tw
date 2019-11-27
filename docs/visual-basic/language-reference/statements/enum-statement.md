---
title: End 陳述式
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
ms.openlocfilehash: 48220fd1e88cf38e67db5dd3a2ad90638eb6b6df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343719"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="c40c4-102">Enum 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c40c4-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="c40c4-103">宣告列舉，並定義其成員的值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="c40c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="c40c4-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="c40c4-105">組件</span><span class="sxs-lookup"><span data-stu-id="c40c4-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="c40c4-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c40c4-106">Optional.</span></span> <span data-ttu-id="c40c4-107">套用至此列舉的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="c40c4-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="c40c4-108">您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)放在角括弧中（「`<`」和「`>`」）。</span><span class="sxs-lookup"><span data-stu-id="c40c4-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="c40c4-109"><xref:System.FlagsAttribute> 屬性指出列舉實例的值可以包含多個列舉成員，而且每個成員都代表列舉值中的位欄位。</span><span class="sxs-lookup"><span data-stu-id="c40c4-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="c40c4-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c40c4-110">Optional.</span></span> <span data-ttu-id="c40c4-111">指定哪些程式碼可以存取此列舉。</span><span class="sxs-lookup"><span data-stu-id="c40c4-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="c40c4-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c40c4-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="c40c4-113">Public</span><span class="sxs-lookup"><span data-stu-id="c40c4-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="c40c4-114">Protected</span><span class="sxs-lookup"><span data-stu-id="c40c4-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="c40c4-115">Friend</span><span class="sxs-lookup"><span data-stu-id="c40c4-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="c40c4-116">Private</span><span class="sxs-lookup"><span data-stu-id="c40c4-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="c40c4-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c40c4-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="c40c4-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="c40c4-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="c40c4-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c40c4-119">Optional.</span></span> <span data-ttu-id="c40c4-120">指定在基類中，這個列舉會重新宣告並隱藏名稱相同的程式設計項目，或一組多載元素。</span><span class="sxs-lookup"><span data-stu-id="c40c4-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="c40c4-121">您只能在列舉本身（而不是其任何成員）上指定[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) 。</span><span class="sxs-lookup"><span data-stu-id="c40c4-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="c40c4-122">必要。</span><span class="sxs-lookup"><span data-stu-id="c40c4-122">Required.</span></span> <span data-ttu-id="c40c4-123">列舉的名稱。</span><span class="sxs-lookup"><span data-stu-id="c40c4-123">Name of the enumeration.</span></span> <span data-ttu-id="c40c4-124">如需有效名稱的資訊，請參閱宣告的[元素名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="c40c4-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="c40c4-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c40c4-125">Optional.</span></span> <span data-ttu-id="c40c4-126">列舉及其所有成員的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c40c4-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="c40c4-127">必要。</span><span class="sxs-lookup"><span data-stu-id="c40c4-127">Required.</span></span> <span data-ttu-id="c40c4-128">在此語句中宣告的成員常數清單。</span><span class="sxs-lookup"><span data-stu-id="c40c4-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="c40c4-129">多個成員會出現在個別的源程式碼上。</span><span class="sxs-lookup"><span data-stu-id="c40c4-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="c40c4-130">每個 `member` 都具有下列語法和部分： `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="c40c4-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="c40c4-131">組件</span><span class="sxs-lookup"><span data-stu-id="c40c4-131">Part</span></span>|<span data-ttu-id="c40c4-132">描述</span><span class="sxs-lookup"><span data-stu-id="c40c4-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="c40c4-133">必要。</span><span class="sxs-lookup"><span data-stu-id="c40c4-133">Required.</span></span> <span data-ttu-id="c40c4-134">這個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="c40c4-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="c40c4-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c40c4-135">Optional.</span></span> <span data-ttu-id="c40c4-136">在編譯時期評估並指派給這個成員的運算式。</span><span class="sxs-lookup"><span data-stu-id="c40c4-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="c40c4-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="c40c4-137">`End` `Enum`</span></span>

  <span data-ttu-id="c40c4-138">終止 `Enum` 區塊。</span><span class="sxs-lookup"><span data-stu-id="c40c4-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="c40c4-139">備註</span><span class="sxs-lookup"><span data-stu-id="c40c4-139">Remarks</span></span>

<span data-ttu-id="c40c4-140">如果您有一組不變的值是以邏輯方式相互關聯，您可以在列舉中將它們定義在一起。</span><span class="sxs-lookup"><span data-stu-id="c40c4-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="c40c4-141">這會為列舉及其成員提供有意義的名稱，這比它們的值更容易記住。</span><span class="sxs-lookup"><span data-stu-id="c40c4-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="c40c4-142">然後您可以在程式碼中的許多地方使用列舉成員。</span><span class="sxs-lookup"><span data-stu-id="c40c4-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="c40c4-143">使用列舉的優點包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="c40c4-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="c40c4-144">減少因轉置或錯誤的數位而造成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c40c4-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="c40c4-145">可讓您在未來輕鬆變更值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="c40c4-146">可讓程式碼更容易閱讀，這表示不太可能會引進錯誤。</span><span class="sxs-lookup"><span data-stu-id="c40c4-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="c40c4-147">確保向前相容性。</span><span class="sxs-lookup"><span data-stu-id="c40c4-147">Ensures forward compatibility.</span></span> <span data-ttu-id="c40c4-148">如果您使用列舉，當未來有人變更對應至成員名稱的值時，您的程式碼較不可能失敗。</span><span class="sxs-lookup"><span data-stu-id="c40c4-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="c40c4-149">列舉具有名稱、基礎資料類型和一組成員。</span><span class="sxs-lookup"><span data-stu-id="c40c4-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="c40c4-150">每個成員都代表一個常數。</span><span class="sxs-lookup"><span data-stu-id="c40c4-150">Each member represents a constant.</span></span>

<span data-ttu-id="c40c4-151">在任何程式之外的類別、結構、模組或介面層級宣告的列舉是*成員列舉*。</span><span class="sxs-lookup"><span data-stu-id="c40c4-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="c40c4-152">它是宣告它的類別、結構、模組或介面的成員。</span><span class="sxs-lookup"><span data-stu-id="c40c4-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="c40c4-153">成員列舉可以從其類別、結構、模組或介面中的任何位置存取。</span><span class="sxs-lookup"><span data-stu-id="c40c4-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="c40c4-154">類別、結構或模組之外的程式碼必須使用該類別、結構或模組的名稱來限定成員列舉的名稱。</span><span class="sxs-lookup"><span data-stu-id="c40c4-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="c40c4-155">您可以藉由將[Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)語句加入至原始程式檔，來避免需要使用完整名稱。</span><span class="sxs-lookup"><span data-stu-id="c40c4-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="c40c4-156">在命名空間層級（在任何類別、結構、模組或介面外）宣告的列舉，是其出現所在之命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="c40c4-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="c40c4-157">列舉的宣告*內容*必須是原始程式檔、命名空間、類別、結構、模組或介面，而且不能是程式。</span><span class="sxs-lookup"><span data-stu-id="c40c4-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="c40c4-158">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c40c4-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="c40c4-159">您可以將屬性套用至整個列舉，但不能個別套用到其成員。</span><span class="sxs-lookup"><span data-stu-id="c40c4-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="c40c4-160">屬性會將資訊提供給元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c40c4-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="c40c4-161">資料類型</span><span class="sxs-lookup"><span data-stu-id="c40c4-161">Data Type</span></span>

<span data-ttu-id="c40c4-162">`Enum` 語句可以宣告列舉的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c40c4-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="c40c4-163">每個成員都會採用列舉的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c40c4-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="c40c4-164">您可以指定 `Byte`、`Integer`、`Long`、`SByte`、`Short`、`UInteger`、`ULong`或 `UShort`。</span><span class="sxs-lookup"><span data-stu-id="c40c4-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="c40c4-165">如果您未指定列舉的 `datatype`，每個成員都會接受其 `initializer`的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c40c4-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="c40c4-166">如果您同時指定 `datatype` 和 `initializer`，`initializer` 的資料類型必須可轉換為 `datatype`。</span><span class="sxs-lookup"><span data-stu-id="c40c4-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="c40c4-167">如果 `datatype` 或 `initializer` 都不存在，則資料類型會預設為 [`Integer`]。</span><span class="sxs-lookup"><span data-stu-id="c40c4-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="c40c4-168">初始化成員</span><span class="sxs-lookup"><span data-stu-id="c40c4-168">Initializing Members</span></span>

<span data-ttu-id="c40c4-169">`Enum` 語句可以初始化 `memberlist`中所選取成員的內容。</span><span class="sxs-lookup"><span data-stu-id="c40c4-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="c40c4-170">您可以使用 `initializer` 來提供要指派給成員的運算式。</span><span class="sxs-lookup"><span data-stu-id="c40c4-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="c40c4-171">如果您未指定成員的 `initializer`，Visual Basic 會將它初始化為零（如果它是 `memberlist`中的第一個 `member`），或設為大於前一個 `member`的值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="c40c4-172">每個 `initializer` 中提供的運算式可以是常值的任何組合、其他已定義的常數，以及已定義的列舉成員，包括此列舉的上一個成員。</span><span class="sxs-lookup"><span data-stu-id="c40c4-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="c40c4-173">您可以使用算術和邏輯運算子來結合這類元素。</span><span class="sxs-lookup"><span data-stu-id="c40c4-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="c40c4-174">您不能在 `initializer`中使用變數或函數。</span><span class="sxs-lookup"><span data-stu-id="c40c4-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="c40c4-175">不過，您可以使用轉換關鍵字，例如 `CByte` 和 `CShort`。</span><span class="sxs-lookup"><span data-stu-id="c40c4-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="c40c4-176">如果您以常數 `String` 或 `Char` 引數呼叫它，您也可以使用 `AscW`，因為這可以在編譯時期進行評估。</span><span class="sxs-lookup"><span data-stu-id="c40c4-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="c40c4-177">列舉不能有浮點值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="c40c4-178">如果將浮點值指派給成員，且 `Option Strict` 設為 on，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c40c4-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="c40c4-179">如果 `Option Strict` 為 off，則此值會自動轉換成 `Enum` 類型。</span><span class="sxs-lookup"><span data-stu-id="c40c4-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="c40c4-180">如果成員的值超過基礎資料類型允許的範圍，或是您將任何成員初始化為基礎資料類型所允許的最大值，則編譯器會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="c40c4-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="c40c4-181">修飾詞</span><span class="sxs-lookup"><span data-stu-id="c40c4-181">Modifiers</span></span>

<span data-ttu-id="c40c4-182">類別、結構、模組和介面成員列舉預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="c40c4-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="c40c4-183">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="c40c4-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="c40c4-184">命名空間成員列舉預設為 friend 存取。</span><span class="sxs-lookup"><span data-stu-id="c40c4-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="c40c4-185">您可以將其存取層級調整為 [公用]，而不是 [私人] 或 [受保護]。</span><span class="sxs-lookup"><span data-stu-id="c40c4-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="c40c4-186">如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c40c4-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="c40c4-187">所有列舉成員都具有公用存取權，而且您不能在其上使用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c40c4-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="c40c4-188">不過，如果列舉本身具有更受限制的存取層級，則會優先使用指定的列舉存取層級。</span><span class="sxs-lookup"><span data-stu-id="c40c4-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="c40c4-189">根據預設，所有列舉都是類型，而其欄位是常數。</span><span class="sxs-lookup"><span data-stu-id="c40c4-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="c40c4-190">因此，在宣告列舉或其成員時，不能使用 `Shared`、`Static`和 `ReadOnly` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c40c4-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="c40c4-191">指派多個值</span><span class="sxs-lookup"><span data-stu-id="c40c4-191">Assigning Multiple Values</span></span>

<span data-ttu-id="c40c4-192">列舉通常代表互斥的值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="c40c4-193">藉由在 `Enum` 宣告中包含 <xref:System.FlagsAttribute> 屬性，您可以改為將多個值指派給列舉的實例。</span><span class="sxs-lookup"><span data-stu-id="c40c4-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="c40c4-194"><xref:System.FlagsAttribute> 屬性指定將列舉視為位欄位，也就是一組旗標。</span><span class="sxs-lookup"><span data-stu-id="c40c4-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="c40c4-195">這些稱為*位*列舉。</span><span class="sxs-lookup"><span data-stu-id="c40c4-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="c40c4-196">當您使用 <xref:System.FlagsAttribute> 屬性宣告列舉時，我們建議您使用2的乘冪（也就是1、2、4、8、16等等）來取得值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="c40c4-197">我們也建議 "None" 是值為0的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="c40c4-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="c40c4-198">如需其他指導方針，請參閱 <xref:System.FlagsAttribute> 和 <xref:System.Enum>。</span><span class="sxs-lookup"><span data-stu-id="c40c4-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="c40c4-199">範例</span><span class="sxs-lookup"><span data-stu-id="c40c4-199">Example</span></span>

<span data-ttu-id="c40c4-200">下列範例顯示如何使用 `Enum` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c40c4-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="c40c4-201">請注意，成員稱為 `EggSizeEnum.Medium`，而不是 `Medium`。</span><span class="sxs-lookup"><span data-stu-id="c40c4-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="c40c4-202">範例</span><span class="sxs-lookup"><span data-stu-id="c40c4-202">Example</span></span>

<span data-ttu-id="c40c4-203">下列範例中的方法是在 `Egg` 類別之外。</span><span class="sxs-lookup"><span data-stu-id="c40c4-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="c40c4-204">因此，`EggSizeEnum` 完全符合 `Egg.EggSizeEnum`。</span><span class="sxs-lookup"><span data-stu-id="c40c4-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="c40c4-205">範例</span><span class="sxs-lookup"><span data-stu-id="c40c4-205">Example</span></span>

<span data-ttu-id="c40c4-206">下列範例會使用 `Enum` 語句來定義一組相關的已命名常數值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="c40c4-207">在此情況下，這些值是您可能選擇用來設計資料庫之資料輸入表單的色彩。</span><span class="sxs-lookup"><span data-stu-id="c40c4-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="c40c4-208">範例</span><span class="sxs-lookup"><span data-stu-id="c40c4-208">Example</span></span>

<span data-ttu-id="c40c4-209">下列範例會顯示包含正數和負數的值。</span><span class="sxs-lookup"><span data-stu-id="c40c4-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="c40c4-210">範例</span><span class="sxs-lookup"><span data-stu-id="c40c4-210">Example</span></span>

<span data-ttu-id="c40c4-211">在下列範例中，會使用 `As` 子句來指定列舉的 `datatype`。</span><span class="sxs-lookup"><span data-stu-id="c40c4-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="c40c4-212">範例</span><span class="sxs-lookup"><span data-stu-id="c40c4-212">Example</span></span>

<span data-ttu-id="c40c4-213">下列範例顯示如何使用位列舉。</span><span class="sxs-lookup"><span data-stu-id="c40c4-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="c40c4-214">可以將多個值指派給位列舉的實例。</span><span class="sxs-lookup"><span data-stu-id="c40c4-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="c40c4-215">`Enum` 宣告包含 <xref:System.FlagsAttribute> 屬性，這表示列舉可視為一組旗標。</span><span class="sxs-lookup"><span data-stu-id="c40c4-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="c40c4-216">範例</span><span class="sxs-lookup"><span data-stu-id="c40c4-216">Example</span></span>

<span data-ttu-id="c40c4-217">下列範例會逐一查看列舉。</span><span class="sxs-lookup"><span data-stu-id="c40c4-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="c40c4-218">它會使用 <xref:System.Enum.GetNames%2A> 方法來抓取列舉中的成員名稱陣列，並 <xref:System.Enum.GetValues%2A> 來抓取成員值的陣列。</span><span class="sxs-lookup"><span data-stu-id="c40c4-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="c40c4-219">請參閱</span><span class="sxs-lookup"><span data-stu-id="c40c4-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="c40c4-220">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="c40c4-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="c40c4-221">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="c40c4-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="c40c4-222">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="c40c4-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c40c4-223">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="c40c4-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c40c4-224">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="c40c4-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
