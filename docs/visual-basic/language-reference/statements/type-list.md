---
title: "類型清單 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 35e72414b236615dc230b654ccfeed290841fb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="0abfd-102">類型清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0abfd-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="0abfd-103">指定*型別參數*如*泛型*程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="0abfd-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="0abfd-104">以逗號分隔多個參數。</span><span class="sxs-lookup"><span data-stu-id="0abfd-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="0abfd-105">以下是一個型別參數的語法。</span><span class="sxs-lookup"><span data-stu-id="0abfd-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0abfd-106">語法</span><span class="sxs-lookup"><span data-stu-id="0abfd-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="0abfd-107">組件</span><span class="sxs-lookup"><span data-stu-id="0abfd-107">Parts</span></span>  
  
|<span data-ttu-id="0abfd-108">詞彙</span><span class="sxs-lookup"><span data-stu-id="0abfd-108">Term</span></span>|<span data-ttu-id="0abfd-109">定義</span><span class="sxs-lookup"><span data-stu-id="0abfd-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="0abfd-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0abfd-110">Optional.</span></span> <span data-ttu-id="0abfd-111">可在泛型介面與委派中。</span><span class="sxs-lookup"><span data-stu-id="0abfd-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="0abfd-112">您可以宣告型別 covariant 使用[出](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)關鍵字或使用 contravariant[中](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0abfd-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="0abfd-113">請參閱 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0abfd-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="0abfd-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="0abfd-114">Required.</span></span> <span data-ttu-id="0abfd-115">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0abfd-115">Name of the type parameter.</span></span> <span data-ttu-id="0abfd-116">這是預留位置，以對應的型別引數所提供的定義類型所取代。</span><span class="sxs-lookup"><span data-stu-id="0abfd-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="0abfd-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0abfd-117">Optional.</span></span> <span data-ttu-id="0abfd-118">限制可以針對提供的資料類型的需求清單的`typename`。</span><span class="sxs-lookup"><span data-stu-id="0abfd-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="0abfd-119">如果您有多個條件約束，將其括在大括號 (`{ }`) 並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="0abfd-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="0abfd-120">您必須引入與條件約束清單[為](../../../visual-basic/language-reference/statements/as-clause.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0abfd-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="0abfd-121">您使用`As`只能出現一次，在清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="0abfd-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0abfd-122">備註</span><span class="sxs-lookup"><span data-stu-id="0abfd-122">Remarks</span></span>  
 <span data-ttu-id="0abfd-123">每個泛型的程式設計項目必須使用至少一個的類型參數。</span><span class="sxs-lookup"><span data-stu-id="0abfd-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="0abfd-124">型別參數是特定類型的預留位置 (*建構的項目*) 用戶端程式碼指定當它建立泛型類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0abfd-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="0abfd-125">您可以定義泛型類別、 結構、 介面、 程序或委派。</span><span class="sxs-lookup"><span data-stu-id="0abfd-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="0abfd-126">如需何時要定義泛型類型的詳細資訊，請參閱[Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0abfd-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="0abfd-127">如需型別參數名稱的詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="0abfd-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="0abfd-128">規則</span><span class="sxs-lookup"><span data-stu-id="0abfd-128">Rules</span></span>  
  
-   <span data-ttu-id="0abfd-129">**括號。**</span><span class="sxs-lookup"><span data-stu-id="0abfd-129">**Parentheses.**</span></span> <span data-ttu-id="0abfd-130">如果您提供型別參數清單，您必須將它括在括號內，而且您必須使用引入清單[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0abfd-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="0abfd-131">您使用`Of`只能出現一次，在清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="0abfd-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="0abfd-132">**條件約束。**</span><span class="sxs-lookup"><span data-stu-id="0abfd-132">**Constraints.**</span></span> <span data-ttu-id="0abfd-133">一份*條件約束*型別參數可以利用任意組合包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="0abfd-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="0abfd-134">任何數目的介面。</span><span class="sxs-lookup"><span data-stu-id="0abfd-134">Any number of interfaces.</span></span> <span data-ttu-id="0abfd-135">提供的型別必須實作每個介面，這份清單中。</span><span class="sxs-lookup"><span data-stu-id="0abfd-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="0abfd-136">最多一個類別。</span><span class="sxs-lookup"><span data-stu-id="0abfd-136">At most one class.</span></span> <span data-ttu-id="0abfd-137">提供的類型必須繼承自該類別。</span><span class="sxs-lookup"><span data-stu-id="0abfd-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="0abfd-138">`New` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0abfd-138">The `New` keyword.</span></span> <span data-ttu-id="0abfd-139">提供的型別必須公開您的泛型型別可存取的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="0abfd-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="0abfd-140">這是適用於限制由一或多個介面的型別參數。</span><span class="sxs-lookup"><span data-stu-id="0abfd-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="0abfd-141">實作介面的類型不一定要公開建構函式，並根據建構函式的存取層級，泛型型別中的程式碼可能無法存取它。</span><span class="sxs-lookup"><span data-stu-id="0abfd-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="0abfd-142">任一`Class`關鍵字或`Structure`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0abfd-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="0abfd-143">`Class`關鍵字的條件約束需要傳遞給它的任何型別引數是參考類型，例如字串、 陣列或委派，或從類別建立物件的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="0abfd-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="0abfd-144">`Structure`關鍵字限制泛型型別參數需要傳遞給它的任何型別引數是實值類型，例如結構、 列舉型別或基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="0abfd-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="0abfd-145">您不能同時包含`Class`和`Structure`在同一個`constraintlist`。</span><span class="sxs-lookup"><span data-stu-id="0abfd-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="0abfd-146">提供的型別必須滿足您包含在每一項需求`constraintlist`。</span><span class="sxs-lookup"><span data-stu-id="0abfd-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="0abfd-147">每個類型參數條件約束是獨立的其他型別參數的條件約束。</span><span class="sxs-lookup"><span data-stu-id="0abfd-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="0abfd-148">行為</span><span class="sxs-lookup"><span data-stu-id="0abfd-148">Behavior</span></span>  
  
-   <span data-ttu-id="0abfd-149">**編譯時期替代。**</span><span class="sxs-lookup"><span data-stu-id="0abfd-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="0abfd-150">當您從泛型的程式設計項目建立建構的類型時，您會提供每個類型參數定義的類型。</span><span class="sxs-lookup"><span data-stu-id="0abfd-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="0abfd-151">Visual Basic 編譯器會取代每個出現的該提供的型別`typename`泛型項目內。</span><span class="sxs-lookup"><span data-stu-id="0abfd-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="0abfd-152">**條件約束不存在。**</span><span class="sxs-lookup"><span data-stu-id="0abfd-152">**Absence of Constraints.**</span></span> <span data-ttu-id="0abfd-153">如果您未指定任何型別參數的條件約束，您的程式碼受到作業和成員受到[物件資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)給該類型參數。</span><span class="sxs-lookup"><span data-stu-id="0abfd-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0abfd-154">範例</span><span class="sxs-lookup"><span data-stu-id="0abfd-154">Example</span></span>  
 <span data-ttu-id="0abfd-155">下列範例顯示泛型字典類別，包括將新的項目新增至字典的基本架構函數的基本架構定義。</span><span class="sxs-lookup"><span data-stu-id="0abfd-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="0abfd-156">範例</span><span class="sxs-lookup"><span data-stu-id="0abfd-156">Example</span></span>  
 <span data-ttu-id="0abfd-157">因為`dictionary`是泛型，使用它的程式碼可以建立各種不同的物件，每個功能都相同，但根據不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0abfd-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="0abfd-158">下列範例示範建立的程式碼行`dictionary`物件`String`項目和`Integer`索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0abfd-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="0abfd-159">範例</span><span class="sxs-lookup"><span data-stu-id="0abfd-159">Example</span></span>  
 <span data-ttu-id="0abfd-160">下列範例會顯示對應的基本架構定義，先前範例所產生。</span><span class="sxs-lookup"><span data-stu-id="0abfd-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0abfd-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0abfd-161">See Also</span></span>  
 [<span data-ttu-id="0abfd-162">Of</span><span class="sxs-lookup"><span data-stu-id="0abfd-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="0abfd-163">New 運算子</span><span class="sxs-lookup"><span data-stu-id="0abfd-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="0abfd-164">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="0abfd-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="0abfd-165">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="0abfd-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="0abfd-166">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="0abfd-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="0abfd-167">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="0abfd-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="0abfd-168">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="0abfd-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="0abfd-169">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="0abfd-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="0abfd-170">共變數和反變數</span><span class="sxs-lookup"><span data-stu-id="0abfd-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="0abfd-171">In</span><span class="sxs-lookup"><span data-stu-id="0abfd-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="0abfd-172">Out</span><span class="sxs-lookup"><span data-stu-id="0abfd-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
