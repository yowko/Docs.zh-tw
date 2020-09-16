---
title: 變數宣告
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
ms.openlocfilehash: e3e2b6173a36490328801afd7fe711f1a003e2ae
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557472"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="9f01f-102">Visual Basic 中的變數宣告</span><span class="sxs-lookup"><span data-stu-id="9f01f-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="9f01f-103">您可以宣告變數來指定其名稱和特性。</span><span class="sxs-lookup"><span data-stu-id="9f01f-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="9f01f-104">變數的宣告語句是 [Dim 語句](../../../language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9f01f-104">The declaration statement for variables is the [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="9f01f-105">其位置和內容會決定變數的特性。</span><span class="sxs-lookup"><span data-stu-id="9f01f-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="9f01f-106">如需變數命名規則和考慮，請參閱宣告的 [元素名稱](../declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="9f01f-106">For variable naming rules and considerations, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="9f01f-107">宣告層級</span><span class="sxs-lookup"><span data-stu-id="9f01f-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="9f01f-108">本機和成員變數</span><span class="sxs-lookup"><span data-stu-id="9f01f-108">Local and Member Variables</span></span>  
 <span data-ttu-id="9f01f-109">區域變數是在程式中宣告的 *變數* 。</span><span class="sxs-lookup"><span data-stu-id="9f01f-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="9f01f-110">*成員變數*是 Visual Basic 類型的成員;它是在模組層級、類別、結構或模組內宣告，而不是在該類別、結構或模組內部的任何程式內進行宣告。</span><span class="sxs-lookup"><span data-stu-id="9f01f-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="9f01f-111">共用和執行個體變數</span><span class="sxs-lookup"><span data-stu-id="9f01f-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="9f01f-112">在類別或結構中，成員變數的類別取決於它是否為共用。</span><span class="sxs-lookup"><span data-stu-id="9f01f-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="9f01f-113">如果它是以 [shared](../../../language-reference/modifiers/shared.md) 關鍵字宣告，它就是 *共用變數*，而且存在於類別或結構的所有實例之間共用的單一複本中。</span><span class="sxs-lookup"><span data-stu-id="9f01f-113">If it is declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="9f01f-114">否則，它是 *執行個體變數*，並且會為類別或結構的每個實例建立個別的複本。</span><span class="sxs-lookup"><span data-stu-id="9f01f-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="9f01f-115">執行個體變數的指定複本只適用于建立該實例之類別或結構的實例。</span><span class="sxs-lookup"><span data-stu-id="9f01f-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="9f01f-116">它獨立于類別或結構的任何其他實例中的執行個體變數複本。</span><span class="sxs-lookup"><span data-stu-id="9f01f-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="9f01f-117">宣告資料類型</span><span class="sxs-lookup"><span data-stu-id="9f01f-117">Declaring Data Type</span></span>  
 <span data-ttu-id="9f01f-118">宣告語句中的 [As](../../../language-reference/statements/as-clause.md) 子句可讓您定義您所宣告之變數的資料類型或物件類型。</span><span class="sxs-lookup"><span data-stu-id="9f01f-118">The [As](../../../language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="9f01f-119">您可以為變數指定下列任何一種類型：</span><span class="sxs-lookup"><span data-stu-id="9f01f-119">You can specify any of the following types for a variable:</span></span>  
  
- <span data-ttu-id="9f01f-120">基本資料類型，例如 `Boolean` 、 `Long` 或 `Decimal`</span><span class="sxs-lookup"><span data-stu-id="9f01f-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
- <span data-ttu-id="9f01f-121">複合資料型別，例如陣列或結構</span><span class="sxs-lookup"><span data-stu-id="9f01f-121">A composite data type, such as an array or structure</span></span>  
  
- <span data-ttu-id="9f01f-122">在您的應用程式或其他應用程式中定義的物件類型或類別</span><span class="sxs-lookup"><span data-stu-id="9f01f-122">An object type, or class, defined either in your application or in another application</span></span>  
  
- <span data-ttu-id="9f01f-123">.NET Framework 類別，例如 <xref:System.Windows.Forms.Label> 或 <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="9f01f-123">A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
- <span data-ttu-id="9f01f-124">介面類別型，例如 <xref:System.IComparable> 或 <xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="9f01f-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="9f01f-125">您可以在一個語句中宣告數個變數，而不需要重複資料類型。</span><span class="sxs-lookup"><span data-stu-id="9f01f-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="9f01f-126">在下列語句中，變數 `i` 、和 `j` 會宣告 `k` 為型別 `Integer` ，以及 `l` `m` as、and `Long` `x` 和 `y` as `Single` ：</span><span class="sxs-lookup"><span data-stu-id="9f01f-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="9f01f-127">如需資料類型的詳細資訊，請參閱 [資料類型](../data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9f01f-127">For more information on data types, see [Data Types](../data-types/index.md).</span></span> <span data-ttu-id="9f01f-128">如需物件的詳細資訊，請參閱 [物件和類別](../objects-and-classes/index.md) 以及 [使用元件](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="9f01f-128">For more information on objects, see [Objects and Classes](../objects-and-classes/index.md) and [Programming with Components](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="9f01f-129">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="9f01f-129">Local Type Inference</span></span>  
 <span data-ttu-id="9f01f-130">*型別推斷* 用來判斷不使用子句宣告的區域變數資料類型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="9f01f-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="9f01f-131">編譯器會從初始化運算式的類型推斷變數的類型。</span><span class="sxs-lookup"><span data-stu-id="9f01f-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="9f01f-132">這可讓您宣告變數，而不需要明確地指出類型。</span><span class="sxs-lookup"><span data-stu-id="9f01f-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="9f01f-133">在下列範例中， `num1` 和 `num2` 都是強型別為整數。</span><span class="sxs-lookup"><span data-stu-id="9f01f-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="9f01f-134">如果您想要使用區欄位型別推斷， `Option Infer` 必須將設定為 `On` 。</span><span class="sxs-lookup"><span data-stu-id="9f01f-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="9f01f-135">如需詳細資訊，請參閱[區域型別推斷](local-type-inference.md)和 [Option Infer 陳述式](../../../language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9f01f-135">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="9f01f-136">宣告變數的特性</span><span class="sxs-lookup"><span data-stu-id="9f01f-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="9f01f-137">變數的 *存留* 期是可供使用的時間週期。</span><span class="sxs-lookup"><span data-stu-id="9f01f-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="9f01f-138">一般情況下，只要宣告 (的專案（如程式或類別）) 繼續存在，變數就會存在。</span><span class="sxs-lookup"><span data-stu-id="9f01f-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="9f01f-139">如果變數不需要在其包含元素的存留期之外繼續存在，您就不需要在宣告中執行任何特殊動作。</span><span class="sxs-lookup"><span data-stu-id="9f01f-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="9f01f-140">如果變數需要繼續比其包含元素更長的時間，您可以 `Static` `Shared` 在其語句中包含或關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="9f01f-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="9f01f-141">如需詳細資訊，請參閱 [Visual Basic 中的存留期](../declared-elements/lifetime.md)。</span><span class="sxs-lookup"><span data-stu-id="9f01f-141">For more information, see [Lifetime in Visual Basic](../declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="9f01f-142">變數的 *範圍* 是一組可以參考的程式碼，但不符合其名稱。</span><span class="sxs-lookup"><span data-stu-id="9f01f-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="9f01f-143">變數的範圍取決於其宣告位置。</span><span class="sxs-lookup"><span data-stu-id="9f01f-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="9f01f-144">位於指定區域中的程式碼可以使用在該區域中定義的變數，而不需限定其名稱。</span><span class="sxs-lookup"><span data-stu-id="9f01f-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="9f01f-145">如需詳細資訊，請參閱 [Scope in Visual Basic](../declared-elements/scope.md)。</span><span class="sxs-lookup"><span data-stu-id="9f01f-145">For more information, see [Scope in Visual Basic](../declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="9f01f-146">變數的 *存取層級* 是具有存取權的程式碼範圍。</span><span class="sxs-lookup"><span data-stu-id="9f01f-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="9f01f-147">這取決於存取修飾詞 (例如您在語句中使用的 [公用](../../../language-reference/modifiers/public.md) 或 [私](../../../language-reference/modifiers/private.md) 用) `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="9f01f-147">This is determined by the access modifier (such as [Public](../../../language-reference/modifiers/public.md) or [Private](../../../language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="9f01f-148">如需詳細資訊，請參閱 [Visual Basic 中的存取層級](../declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9f01f-148">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f01f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f01f-149">See also</span></span>

- [<span data-ttu-id="9f01f-150">如何：建立新的變數</span><span class="sxs-lookup"><span data-stu-id="9f01f-150">How to: Create a New Variable</span></span>](how-to-create-a-new-variable.md)
- [<span data-ttu-id="9f01f-151">如何：移入和移出變數資料</span><span class="sxs-lookup"><span data-stu-id="9f01f-151">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="9f01f-152">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="9f01f-152">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="9f01f-153">保護</span><span class="sxs-lookup"><span data-stu-id="9f01f-153">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="9f01f-154">Friend</span><span class="sxs-lookup"><span data-stu-id="9f01f-154">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="9f01f-155">靜態</span><span class="sxs-lookup"><span data-stu-id="9f01f-155">Static</span></span>](../../../language-reference/modifiers/static.md)
- [<span data-ttu-id="9f01f-156">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="9f01f-156">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="9f01f-157">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="9f01f-157">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="9f01f-158">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="9f01f-158">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
