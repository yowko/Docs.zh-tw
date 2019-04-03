---
title: 類型清單 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: d071e59d94e51ca55167983d0ee3098bd5c7dd8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843626"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="711a0-102">類型清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="711a0-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="711a0-103">指定*型別參數*for*泛型*程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="711a0-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="711a0-104">以逗號分隔多個參數。</span><span class="sxs-lookup"><span data-stu-id="711a0-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="711a0-105">以下是一種型別參數的語法。</span><span class="sxs-lookup"><span data-stu-id="711a0-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="711a0-106">語法</span><span class="sxs-lookup"><span data-stu-id="711a0-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="711a0-107">組件</span><span class="sxs-lookup"><span data-stu-id="711a0-107">Parts</span></span>  
  
|<span data-ttu-id="711a0-108">詞彙</span><span class="sxs-lookup"><span data-stu-id="711a0-108">Term</span></span>|<span data-ttu-id="711a0-109">定義</span><span class="sxs-lookup"><span data-stu-id="711a0-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="711a0-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="711a0-110">Optional.</span></span> <span data-ttu-id="711a0-111">可以只用於泛型介面和委派。</span><span class="sxs-lookup"><span data-stu-id="711a0-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="711a0-112">您可以宣告型別 covariant 利用[出](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)關鍵字或使用 contravariant[在](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="711a0-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="711a0-113">請參閱 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="711a0-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="711a0-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="711a0-114">Required.</span></span> <span data-ttu-id="711a0-115">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="711a0-115">Name of the type parameter.</span></span> <span data-ttu-id="711a0-116">這是預留位置，以將其取代對應的型別引數所提供已定義的類型。</span><span class="sxs-lookup"><span data-stu-id="711a0-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="711a0-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="711a0-117">Optional.</span></span> <span data-ttu-id="711a0-118">限制可以提供的資料類型的需求清單`typename`。</span><span class="sxs-lookup"><span data-stu-id="711a0-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="711a0-119">如果您有多個條件約束，將其括在大括號 (`{ }`) 並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="711a0-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="711a0-120">您必須導入的條件約束清單[做為](../../../visual-basic/language-reference/statements/as-clause.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="711a0-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="711a0-121">您使用`As`一次，在清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="711a0-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="711a0-122">備註</span><span class="sxs-lookup"><span data-stu-id="711a0-122">Remarks</span></span>  
 <span data-ttu-id="711a0-123">每個一般的程式設計項目必須採用至少一個類型的參數。</span><span class="sxs-lookup"><span data-stu-id="711a0-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="711a0-124">型別參數是特定類型的預留位置 (*建構的項目*) 用戶端程式碼，指定當它建立泛型類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="711a0-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="711a0-125">您可以定義泛型類別、 結構、 介面、 程序，或委派。</span><span class="sxs-lookup"><span data-stu-id="711a0-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="711a0-126">如需何時要定義泛型類型的詳細資訊，請參閱[在 Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="711a0-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="711a0-127">如需有關型別參數名稱的詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="711a0-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="711a0-128">規則</span><span class="sxs-lookup"><span data-stu-id="711a0-128">Rules</span></span>  
  
-   <span data-ttu-id="711a0-129">**括號。**</span><span class="sxs-lookup"><span data-stu-id="711a0-129">**Parentheses.**</span></span> <span data-ttu-id="711a0-130">如果您提供類型參數清單，您必須將它括在括號內，而且必須導入的清單[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="711a0-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="711a0-131">您使用`Of`一次，在清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="711a0-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="711a0-132">**條件約束。**</span><span class="sxs-lookup"><span data-stu-id="711a0-132">**Constraints.**</span></span> <span data-ttu-id="711a0-133">一份*條件約束*的類型參數可以任意組合包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="711a0-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="711a0-134">任意數目的介面。</span><span class="sxs-lookup"><span data-stu-id="711a0-134">Any number of interfaces.</span></span> <span data-ttu-id="711a0-135">提供的型別必須實作每個介面，這份清單中。</span><span class="sxs-lookup"><span data-stu-id="711a0-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="711a0-136">最多一個類別。</span><span class="sxs-lookup"><span data-stu-id="711a0-136">At most one class.</span></span> <span data-ttu-id="711a0-137">提供的類型必須繼承自該類別。</span><span class="sxs-lookup"><span data-stu-id="711a0-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="711a0-138">`New` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="711a0-138">The `New` keyword.</span></span> <span data-ttu-id="711a0-139">提供的型別必須公開您的泛型型別可存取的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="711a0-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="711a0-140">這非常有用，如果您限制一或多個介面的型別參數。</span><span class="sxs-lookup"><span data-stu-id="711a0-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="711a0-141">實作介面的類型不一定要公開建構函式，並根據建構函式的存取層級，泛型型別中的程式碼可能無法存取它。</span><span class="sxs-lookup"><span data-stu-id="711a0-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="711a0-142">任一`Class`關鍵字或`Structure`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="711a0-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="711a0-143">`Class`關鍵字限制需要傳遞給它的任何類型引數是參考類型，例如字串、 陣列或委派，或從類別建立物件的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="711a0-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="711a0-144">`Structure`關鍵字泛型類型參數限制為要求傳遞給它的任何型別引數是實值類型，例如結構、 列舉型別或基本資料輸入。</span><span class="sxs-lookup"><span data-stu-id="711a0-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="711a0-145">您不能同時包含`Class`並`Structure`在同一個`constraintlist`。</span><span class="sxs-lookup"><span data-stu-id="711a0-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="711a0-146">提供的型別必須滿足您包含在每一項需求`constraintlist`。</span><span class="sxs-lookup"><span data-stu-id="711a0-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="711a0-147">每個類型參數條件約束是獨立於其他型別參數的條件約束。</span><span class="sxs-lookup"><span data-stu-id="711a0-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="711a0-148">行為</span><span class="sxs-lookup"><span data-stu-id="711a0-148">Behavior</span></span>  
  
-   <span data-ttu-id="711a0-149">**編譯時期替代。**</span><span class="sxs-lookup"><span data-stu-id="711a0-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="711a0-150">當您建立建構的類型從一般的程式設計項目時，您會提供已定義的類型，每個類型參數。</span><span class="sxs-lookup"><span data-stu-id="711a0-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="711a0-151">Visual Basic 編譯器會取代每次出現的該提供的型別`typename`內的泛用的項目。</span><span class="sxs-lookup"><span data-stu-id="711a0-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="711a0-152">**條件約束不存在。**</span><span class="sxs-lookup"><span data-stu-id="711a0-152">**Absence of Constraints.**</span></span> <span data-ttu-id="711a0-153">如果您未指定任何條件約束的型別參數，您的程式碼是限制為作業和成員受到[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)給該類型參數。</span><span class="sxs-lookup"><span data-stu-id="711a0-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="711a0-154">範例</span><span class="sxs-lookup"><span data-stu-id="711a0-154">Example</span></span>  
 <span data-ttu-id="711a0-155">下列範例示範泛型字典類別，包括將新的項目新增至字典的基本架構函數的基本架構定義。</span><span class="sxs-lookup"><span data-stu-id="711a0-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="711a0-156">範例</span><span class="sxs-lookup"><span data-stu-id="711a0-156">Example</span></span>  
 <span data-ttu-id="711a0-157">因為`dictionary`是泛型，使用它的程式碼可以建立各種不同的物件，每個具有相同的功能，但根據不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="711a0-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="711a0-158">下列範例顯示建立的程式碼行`dictionary`物件`String`項目和`Integer`索引鍵。</span><span class="sxs-lookup"><span data-stu-id="711a0-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="711a0-159">範例</span><span class="sxs-lookup"><span data-stu-id="711a0-159">Example</span></span>  
 <span data-ttu-id="711a0-160">下列範例顯示對等的基本架構定義，上述範例中所產生。</span><span class="sxs-lookup"><span data-stu-id="711a0-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="711a0-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="711a0-161">See also</span></span>

- [<span data-ttu-id="711a0-162">Of</span><span class="sxs-lookup"><span data-stu-id="711a0-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="711a0-163">New 運算子</span><span class="sxs-lookup"><span data-stu-id="711a0-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="711a0-164">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="711a0-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="711a0-165">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="711a0-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="711a0-166">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="711a0-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="711a0-167">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="711a0-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="711a0-168">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="711a0-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="711a0-169">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="711a0-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="711a0-170">共變數和反變數</span><span class="sxs-lookup"><span data-stu-id="711a0-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="711a0-171">In</span><span class="sxs-lookup"><span data-stu-id="711a0-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="711a0-172">Out</span><span class="sxs-lookup"><span data-stu-id="711a0-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
