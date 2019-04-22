---
title: Visual Basic 中的變數宣告
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 699737ffbe0b136af8862931fadacec26772b928
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833278"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="6a7b5-102">Visual Basic 中的變數宣告</span><span class="sxs-lookup"><span data-stu-id="6a7b5-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="6a7b5-103">您宣告變數，以指定其名稱和特性。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="6a7b5-104">變數的宣告陳述式是[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-104">The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="6a7b5-105">其位置及內容會決定變數的特性。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="6a7b5-106">如需變數的命名規則和考量，請參閱[宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-106">For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="6a7b5-107">宣告層級</span><span class="sxs-lookup"><span data-stu-id="6a7b5-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="6a7b5-108">本機和成員變數</span><span class="sxs-lookup"><span data-stu-id="6a7b5-108">Local and Member Variables</span></span>  
 <span data-ttu-id="6a7b5-109">A*區域變數*是宣告程序內的其中一個。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="6a7b5-110">A*成員變數*成員的 Visual Basic 型別; 在模組層級，在類別、 結構或模組，但不是會在內部，該類別、 結構或模組的任何程序宣告。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="6a7b5-111">共用和執行個體變數</span><span class="sxs-lookup"><span data-stu-id="6a7b5-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="6a7b5-112">在類別或結構中，成員變數的類別取決於共用。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="6a7b5-113">如果它以宣告[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)關鍵字，它是*共用的變數*，且它存在於類別或結構的所有執行個體之間共用的單一複本。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-113">If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="6a7b5-114">否則，它會*執行個體變數*，和另一份它建立類別或結構的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="6a7b5-115">指定的複本的執行個體變數是僅適用於類別或結構建立所在的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="6a7b5-116">它是複本的獨立的執行個體變數，在類別或結構的任何其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="6a7b5-117">宣告的資料類型</span><span class="sxs-lookup"><span data-stu-id="6a7b5-117">Declaring Data Type</span></span>  
 <span data-ttu-id="6a7b5-118">[做為](../../../../visual-basic/language-reference/statements/as-clause.md)宣告陳述式中的子句可讓您定義資料型別或物件類型所宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-118">The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="6a7b5-119">您可以指定任何下列類型的變數：</span><span class="sxs-lookup"><span data-stu-id="6a7b5-119">You can specify any of the following types for a variable:</span></span>  
  
-   <span data-ttu-id="6a7b5-120">基本資料類型，例如`Boolean`， `Long`，或 `Decimal`</span><span class="sxs-lookup"><span data-stu-id="6a7b5-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
-   <span data-ttu-id="6a7b5-121">複合資料類型，例如陣列或結構</span><span class="sxs-lookup"><span data-stu-id="6a7b5-121">A composite data type, such as an array or structure</span></span>  
  
-   <span data-ttu-id="6a7b5-122">物件類型或在您的應用程式或另一個應用程式中所定義的類別</span><span class="sxs-lookup"><span data-stu-id="6a7b5-122">An object type, or class, defined either in your application or in another application</span></span>  
  
-   <span data-ttu-id="6a7b5-123">A[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別，例如<xref:System.Windows.Forms.Label>或 <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="6a7b5-123">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
-   <span data-ttu-id="6a7b5-124">介面類型，例如<xref:System.IComparable>或 <xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="6a7b5-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="6a7b5-125">您可以宣告一個陳述式中的數個變數，而不必重複的資料類型。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="6a7b5-126">下列陳述式的變數`i`， `j`，和`k`宣告為類型`Integer`，`l`並`m`做為`Long`，並`x`和`y`為`Single`:</span><span class="sxs-lookup"><span data-stu-id="6a7b5-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="6a7b5-127">如需有關資料類型的詳細資訊，請參閱 <<c0> [ 資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-127">For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span></span> <span data-ttu-id="6a7b5-128">如需有關物件的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)並[使用元件進行程式設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-128">For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="6a7b5-129">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="6a7b5-129">Local Type Inference</span></span>  
 <span data-ttu-id="6a7b5-130">*型別推斷*用來判斷資料型別，而不需要宣告之區域變數的`As`子句。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="6a7b5-131">編譯器會推斷變數的初始化運算式的類型的類型。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="6a7b5-132">這可讓您宣告變數而不用明確陳述的類型。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="6a7b5-133">在下列範例中，同時`num1`和`num2`強型別為整數。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="6a7b5-134">如果您想要使用區域型別推斷`Option Infer`必須設為`On`。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="6a7b5-135">如需詳細資訊，請參閱[區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-135">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="6a7b5-136">宣告變數的特性</span><span class="sxs-lookup"><span data-stu-id="6a7b5-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="6a7b5-137">*存留期*的變數是一段時間期間它是可供使用。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="6a7b5-138">一般情況下，變數存在，只要將其宣告 （例如程序或類別） 的項目就會繼續存在。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="6a7b5-139">如果變數不需要繼續存在，其包含項目存留期過後，您不需要採取任何特別動作宣告中。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="6a7b5-140">如果變數需要繼續存在時間超過其包含項目，您可以包含`Static`或是`Shared`關鍵字，在其`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="6a7b5-141">如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-141">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="6a7b5-142">*範圍*變數是可參考未限定其名稱的所有程式碼的集合。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="6a7b5-143">變數的範圍取決於宣告的位置。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="6a7b5-144">位於指定的區域中的程式碼可以使用定義在該區域中，而不需要限定其名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="6a7b5-145">如需詳細資訊，請參閱 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-145">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="6a7b5-146">變數的*存取層級*是有權存取它的程式碼的範圍。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="6a7b5-147">這取決於存取修飾詞 (例如[公用](../../../../visual-basic/language-reference/modifiers/public.md)或是[私人](../../../../visual-basic/language-reference/modifiers/private.md)) 中使用`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-147">This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="6a7b5-148">如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b5-148">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7b5-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a7b5-149">See also</span></span>

- [<span data-ttu-id="6a7b5-150">如何：建立新的變數</span><span class="sxs-lookup"><span data-stu-id="6a7b5-150">How to: Create a New Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [<span data-ttu-id="6a7b5-151">如何：移入和移出變數資料</span><span class="sxs-lookup"><span data-stu-id="6a7b5-151">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="6a7b5-152">資料類型</span><span class="sxs-lookup"><span data-stu-id="6a7b5-152">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="6a7b5-153">Protected</span><span class="sxs-lookup"><span data-stu-id="6a7b5-153">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="6a7b5-154">Friend</span><span class="sxs-lookup"><span data-stu-id="6a7b5-154">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="6a7b5-155">Static</span><span class="sxs-lookup"><span data-stu-id="6a7b5-155">Static</span></span>](../../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="6a7b5-156">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="6a7b5-156">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="6a7b5-157">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="6a7b5-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="6a7b5-158">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="6a7b5-158">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
