---
title: Type List
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
ms.openlocfilehash: 7e22ad6e32ec13f081391e1d47a80df8b1e65063
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412984"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="c1406-102">類型清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1406-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="c1406-103">指定*泛型*程式設計項目的*類型參數*。</span><span class="sxs-lookup"><span data-stu-id="c1406-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="c1406-104">多個參數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="c1406-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="c1406-105">以下是一個型別參數的語法。</span><span class="sxs-lookup"><span data-stu-id="c1406-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1406-106">語法</span><span class="sxs-lookup"><span data-stu-id="c1406-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="c1406-107">組件</span><span class="sxs-lookup"><span data-stu-id="c1406-107">Parts</span></span>

|<span data-ttu-id="c1406-108">詞彙</span><span class="sxs-lookup"><span data-stu-id="c1406-108">Term</span></span>|<span data-ttu-id="c1406-109">定義</span><span class="sxs-lookup"><span data-stu-id="c1406-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="c1406-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c1406-110">Optional.</span></span> <span data-ttu-id="c1406-111">只能在泛型介面和委派中使用。</span><span class="sxs-lookup"><span data-stu-id="c1406-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="c1406-112">您可以使用[Out](../modifiers/out-generic-modifier.md)關鍵字或逆變性來宣告類型的協變數，方法是使用[In](../modifiers/in-generic-modifier.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1406-112">You can declare a type covariant by using the [Out](../modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="c1406-113">請參閱 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c1406-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="c1406-114">必要。</span><span class="sxs-lookup"><span data-stu-id="c1406-114">Required.</span></span> <span data-ttu-id="c1406-115">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1406-115">Name of the type parameter.</span></span> <span data-ttu-id="c1406-116">這是預留位置，要由對應的類型引數所提供的已定義類型取代。</span><span class="sxs-lookup"><span data-stu-id="c1406-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="c1406-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c1406-117">Optional.</span></span> <span data-ttu-id="c1406-118">限制可提供之資料類型的需求清單 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="c1406-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="c1406-119">如果您有多個條件約束，請以大括弧（）括住， `{ }` 並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="c1406-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="c1406-120">您必須使用[As](as-clause.md)關鍵字來引進條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="c1406-120">You must introduce the constraint list with the [As](as-clause.md) keyword.</span></span> <span data-ttu-id="c1406-121">您 `As` 只會在清單的開頭使用一次。</span><span class="sxs-lookup"><span data-stu-id="c1406-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1406-122">備註</span><span class="sxs-lookup"><span data-stu-id="c1406-122">Remarks</span></span>

<span data-ttu-id="c1406-123">每個泛型程式設計項目都必須採用至少一個型別參數。</span><span class="sxs-lookup"><span data-stu-id="c1406-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="c1406-124">類型參數是用戶端程式代碼在建立泛型型別的實例時所指定之特定類型（*結構化元素*）的預留位置。</span><span class="sxs-lookup"><span data-stu-id="c1406-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="c1406-125">您可以定義泛型類別、結構、介面、程式或委派。</span><span class="sxs-lookup"><span data-stu-id="c1406-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="c1406-126">如需何時定義泛型型別的詳細資訊，請參閱[Visual Basic 中的泛型型別](../../programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c1406-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="c1406-127">如需型別參數名稱的詳細資訊，請參閱宣告的[元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="c1406-127">For more information on type parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="c1406-128">規則</span><span class="sxs-lookup"><span data-stu-id="c1406-128">Rules</span></span>

- <span data-ttu-id="c1406-129">**後.**</span><span class="sxs-lookup"><span data-stu-id="c1406-129">**Parentheses.**</span></span> <span data-ttu-id="c1406-130">如果您提供型別參數清單，您必須將它括在括弧中，而且您必須使用關鍵字[來](of-clause.md)引進清單。</span><span class="sxs-lookup"><span data-stu-id="c1406-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="c1406-131">您 `Of` 只會在清單的開頭使用一次。</span><span class="sxs-lookup"><span data-stu-id="c1406-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="c1406-132">**條件.**</span><span class="sxs-lookup"><span data-stu-id="c1406-132">**Constraints.**</span></span> <span data-ttu-id="c1406-133">類型參數的*條件約束*清單可以包含下列任何組合中的專案：</span><span class="sxs-lookup"><span data-stu-id="c1406-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="c1406-134">任何數目的介面。</span><span class="sxs-lookup"><span data-stu-id="c1406-134">Any number of interfaces.</span></span> <span data-ttu-id="c1406-135">提供的類型必須執行此清單中的每個介面。</span><span class="sxs-lookup"><span data-stu-id="c1406-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="c1406-136">最多一個類別。</span><span class="sxs-lookup"><span data-stu-id="c1406-136">At most one class.</span></span> <span data-ttu-id="c1406-137">提供的類型必須繼承自該類別。</span><span class="sxs-lookup"><span data-stu-id="c1406-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="c1406-138">`New` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1406-138">The `New` keyword.</span></span> <span data-ttu-id="c1406-139">提供的型別必須公開您的泛型型別可以存取的無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="c1406-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="c1406-140">如果您透過一或多個介面來限制型別參數，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="c1406-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="c1406-141">實介面的型別不一定會公開一個函式，而視函式的存取層級而定，泛型型別中的程式碼可能無法存取它。</span><span class="sxs-lookup"><span data-stu-id="c1406-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="c1406-142">`Class`關鍵字或 `Structure` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1406-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="c1406-143">`Class`關鍵字會限制泛型型別參數，要求傳遞給它的任何型別引數都是參考型別，例如字串、陣列或委派，或是從類別建立的物件。</span><span class="sxs-lookup"><span data-stu-id="c1406-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="c1406-144">`Structure`關鍵字會限制泛型型別參數，要求傳遞給它的任何型別引數都是實值型別，例如結構、列舉或基本資料型別。</span><span class="sxs-lookup"><span data-stu-id="c1406-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="c1406-145">您不能同時 `Class` `Structure` 在相同的中同時包含和 `constraintlist` 。</span><span class="sxs-lookup"><span data-stu-id="c1406-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="c1406-146">提供的類型必須滿足您在中包含的每個需求 `constraintlist` 。</span><span class="sxs-lookup"><span data-stu-id="c1406-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="c1406-147">每個型別參數的條件約束與其他型別參數上的條件約束無關。</span><span class="sxs-lookup"><span data-stu-id="c1406-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="c1406-148">行為</span><span class="sxs-lookup"><span data-stu-id="c1406-148">Behavior</span></span>

- <span data-ttu-id="c1406-149">**編譯時間替代。**</span><span class="sxs-lookup"><span data-stu-id="c1406-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="c1406-150">當您從泛型程式設計專案建立結構化型別時，您會為每個型別參數提供一個已定義的型別。</span><span class="sxs-lookup"><span data-stu-id="c1406-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="c1406-151">Visual Basic 編譯器會針對泛型元素中的每個出現專案，替代提供的類型 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="c1406-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="c1406-152">**沒有條件約束。**</span><span class="sxs-lookup"><span data-stu-id="c1406-152">**Absence of Constraints.**</span></span> <span data-ttu-id="c1406-153">如果您未在類型參數上指定任何條件約束，則您的程式碼會限制為該類型參數的[Object 資料類型](../data-types/object-data-type.md)所支援的作業和成員。</span><span class="sxs-lookup"><span data-stu-id="c1406-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="c1406-154">範例</span><span class="sxs-lookup"><span data-stu-id="c1406-154">Example</span></span>

<span data-ttu-id="c1406-155">下列範例顯示泛型字典類別的基本架構定義，包括將新專案加入字典的基本架構函數。</span><span class="sxs-lookup"><span data-stu-id="c1406-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="c1406-156">範例</span><span class="sxs-lookup"><span data-stu-id="c1406-156">Example</span></span>

<span data-ttu-id="c1406-157">因為 `dictionary` 是泛型，所以使用它的程式碼可以從它建立各種不同的物件，而每一個都具有相同的功能，但作用於不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c1406-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="c1406-158">下列範例顯示的程式程式碼，會建立 `dictionary` 具有 `String` 專案和索引鍵的物件 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="c1406-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="c1406-159">範例</span><span class="sxs-lookup"><span data-stu-id="c1406-159">Example</span></span>

<span data-ttu-id="c1406-160">下列範例會顯示上述範例所產生的對等基本架構定義。</span><span class="sxs-lookup"><span data-stu-id="c1406-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="c1406-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1406-161">See also</span></span>

- [<span data-ttu-id="c1406-162">的</span><span class="sxs-lookup"><span data-stu-id="c1406-162">Of</span></span>](of-clause.md)
- [<span data-ttu-id="c1406-163">New 運算子</span><span class="sxs-lookup"><span data-stu-id="c1406-163">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="c1406-164">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="c1406-164">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c1406-165">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="c1406-165">Object Data Type</span></span>](../data-types/object-data-type.md)
- [<span data-ttu-id="c1406-166">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="c1406-166">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="c1406-167">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="c1406-167">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="c1406-168">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="c1406-168">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="c1406-169">作法：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="c1406-169">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="c1406-170">共變數和反變數</span><span class="sxs-lookup"><span data-stu-id="c1406-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="c1406-171">位於</span><span class="sxs-lookup"><span data-stu-id="c1406-171">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="c1406-172">脫銷</span><span class="sxs-lookup"><span data-stu-id="c1406-172">Out</span></span>](../modifiers/out-generic-modifier.md)
