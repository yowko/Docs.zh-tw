---
title: "Dim 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a428f8be7b62600ca8fffd3160039c1de911e34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="17f9d-102">Dim 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17f9d-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="17f9d-103">宣告，並針對一個或多個變數配置儲存空間。</span><span class="sxs-lookup"><span data-stu-id="17f9d-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17f9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="17f9d-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="17f9d-105">組件</span><span class="sxs-lookup"><span data-stu-id="17f9d-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="17f9d-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-106">Optional.</span></span> <span data-ttu-id="17f9d-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="17f9d-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-108">Optional.</span></span> <span data-ttu-id="17f9d-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="17f9d-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="17f9d-110">Public</span><span class="sxs-lookup"><span data-stu-id="17f9d-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="17f9d-111">Protected</span><span class="sxs-lookup"><span data-stu-id="17f9d-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="17f9d-112">Friend</span><span class="sxs-lookup"><span data-stu-id="17f9d-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="17f9d-113">Private</span><span class="sxs-lookup"><span data-stu-id="17f9d-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="17f9d-114">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="17f9d-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-115">Optional.</span></span> <span data-ttu-id="17f9d-116">請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="17f9d-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-117">Optional.</span></span> <span data-ttu-id="17f9d-118">請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="17f9d-119">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-119">Optional.</span></span> <span data-ttu-id="17f9d-120">請參閱[靜態](../../../visual-basic/language-reference/modifiers/static.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="17f9d-121">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-121">Optional.</span></span> <span data-ttu-id="17f9d-122">請參閱[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="17f9d-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-123">Optional.</span></span> <span data-ttu-id="17f9d-124">指定這些物件變數參照可引發事件的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="17f9d-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="17f9d-125">請參閱[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="17f9d-126">必要項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-126">Required.</span></span> <span data-ttu-id="17f9d-127">此陳述式所宣告的變數清單。</span><span class="sxs-lookup"><span data-stu-id="17f9d-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="17f9d-128">每個 `variable` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="17f9d-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="17f9d-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="17f9d-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="17f9d-130">組件</span><span class="sxs-lookup"><span data-stu-id="17f9d-130">Part</span></span>|<span data-ttu-id="17f9d-131">說明</span><span class="sxs-lookup"><span data-stu-id="17f9d-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="17f9d-132">必要項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-132">Required.</span></span> <span data-ttu-id="17f9d-133">變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="17f9d-133">Name of the variable.</span></span> <span data-ttu-id="17f9d-134">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="17f9d-135">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-135">Optional.</span></span> <span data-ttu-id="17f9d-136">陣列變數的每個維度的界限清單。</span><span class="sxs-lookup"><span data-stu-id="17f9d-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="17f9d-137">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-137">Optional.</span></span> <span data-ttu-id="17f9d-138">建立類別的新執行個體時`Dim`陳述式執行。</span><span class="sxs-lookup"><span data-stu-id="17f9d-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="17f9d-139">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-139">Optional.</span></span> <span data-ttu-id="17f9d-140">變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="17f9d-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="17f9d-141">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-141">Optional.</span></span> <span data-ttu-id="17f9d-142">導入了物件初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="17f9d-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="17f9d-143">選擇項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-143">Optional.</span></span> <span data-ttu-id="17f9d-144">在類別中屬性的名稱進行執行個體。</span><span class="sxs-lookup"><span data-stu-id="17f9d-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="17f9d-145">之後所需`propertyname`=。</span><span class="sxs-lookup"><span data-stu-id="17f9d-145">Required after `propertyname` =.</span></span> <span data-ttu-id="17f9d-146">運算式評估，以及指派給屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="17f9d-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="17f9d-147">選擇性若`New`未指定。</span><span class="sxs-lookup"><span data-stu-id="17f9d-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="17f9d-148">運算式評估，以及在建立時指派給變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17f9d-149">備註</span><span class="sxs-lookup"><span data-stu-id="17f9d-149">Remarks</span></span>  
 <span data-ttu-id="17f9d-150">Visual Basic 編譯器使用`Dim`陳述式來判斷變數的資料類型和其他資訊，例如哪些程式碼可以存取的變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="17f9d-151">下列範例宣告變數，以保留`Integer`值。</span><span class="sxs-lookup"><span data-stu-id="17f9d-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="17f9d-152">您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="17f9d-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="17f9d-153">在您使用參考類型，如`New`關鍵字來建立類別的新執行個體，或結構的資料類型所指定。</span><span class="sxs-lookup"><span data-stu-id="17f9d-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="17f9d-154">如果您使用`New`，您不使用初始設定式運算式。</span><span class="sxs-lookup"><span data-stu-id="17f9d-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="17f9d-155">相反地，您提供的引數，若有需要，建立變數類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="17f9d-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="17f9d-156">您可以宣告程序、 區塊、 類別、 結構或模組中的變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="17f9d-157">您無法宣告的原始程式檔、 命名空間或介面中的變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="17f9d-158">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="17f9d-159">在模組層級，任何程序之外宣告的變數是*成員變數*或*欄位*。</span><span class="sxs-lookup"><span data-stu-id="17f9d-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="17f9d-160">成員變數是在範圍中的類別、 結構或模組。</span><span class="sxs-lookup"><span data-stu-id="17f9d-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="17f9d-161">程序層級宣告的變數是*區域變數*。</span><span class="sxs-lookup"><span data-stu-id="17f9d-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="17f9d-162">本機變數是在範圍內，只有在其程序或區塊內。</span><span class="sxs-lookup"><span data-stu-id="17f9d-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="17f9d-163">下列存取修飾詞用來宣告變數的程序之外： `Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="17f9d-164">如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-164">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="17f9d-165">`Dim`關鍵字是選擇性，而且如果您指定任何下列修飾詞，通常省略： `Public`， `Protected`， `Friend`， `Protected Friend`， `Private`， `Shared`， `Shadows`， `Static`，`ReadOnly`，或`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="17f9d-166">如果`Option Explicit`是編譯器 （預設值），針對每一個您所使用的變數需要的宣告。</span><span class="sxs-lookup"><span data-stu-id="17f9d-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="17f9d-167">如需詳細資訊，請參閱[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="17f9d-168">指定一個初始值</span><span class="sxs-lookup"><span data-stu-id="17f9d-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="17f9d-169">在建立時，您可以指派值給變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="17f9d-170">實值類型，您用於*初始設定式*提供要指派給變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="17f9d-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="17f9d-171">運算式必須評估為常數，可以在編譯時期計算。</span><span class="sxs-lookup"><span data-stu-id="17f9d-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="17f9d-172">如果已指定初始設定式和資料型別中未指定`As`子句，*型別推斷*用來推斷資料型別，以從初始設定式。</span><span class="sxs-lookup"><span data-stu-id="17f9d-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="17f9d-173">在下列範例中，同時`num1`和`num2`強型別為整數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="17f9d-174">在第二個宣告中，型別推斷會推斷的值是 3 中的型別。</span><span class="sxs-lookup"><span data-stu-id="17f9d-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="17f9d-175">在程序層級，套用類型推斷。</span><span class="sxs-lookup"><span data-stu-id="17f9d-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="17f9d-176">它不會套用在類別、 結構、 模組或介面中的程序之外。</span><span class="sxs-lookup"><span data-stu-id="17f9d-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="17f9d-177">如需型別推斷的詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="17f9d-178">如未指定初始設定式或資料類型時，會發生什麼情況的相關資訊，請參閱[預設資料類型和值](../../../visual-basic/language-reference/statements/dim-statement.md#default)本主題稍後。</span><span class="sxs-lookup"><span data-stu-id="17f9d-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="17f9d-179">您可以使用*物件初始設定式*來宣告具名和匿名類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="17f9d-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="17f9d-180">下列程式碼建立的執行個體`Student`類別，並使用物件初始設定式來初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="17f9d-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="17f9d-181">如需物件初始設定式的詳細資訊，請參閱[How to： 使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)，[物件初始設定式： 具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)，和[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="17f9d-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="17f9d-182">宣告多個變數</span><span class="sxs-lookup"><span data-stu-id="17f9d-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="17f9d-183">您可以宣告一個宣告陳述式中，數個變數使用括號指定每個與下列每個陣列名稱的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="17f9d-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="17f9d-184">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="17f9d-185">如果您宣告一個以上的變數，其中包含一個`As`子句，您不能提供初始設定式的變數，該群組。</span><span class="sxs-lookup"><span data-stu-id="17f9d-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="17f9d-186">您可以指定不同的變數的不同資料類型使用個別`As`子句宣告每個變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="17f9d-187">每個變數會指定第一個範圍中的資料類型`As`子句之後，發生其`variablename`組件。</span><span class="sxs-lookup"><span data-stu-id="17f9d-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="17f9d-188">陣列</span><span class="sxs-lookup"><span data-stu-id="17f9d-188">Arrays</span></span>  
 <span data-ttu-id="17f9d-189">您可以宣告變數，以保留*陣列*，而可以包含多個值。</span><span class="sxs-lookup"><span data-stu-id="17f9d-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="17f9d-190">若要指定變數會保存陣列，請遵循其`variablename`立即以括號。</span><span class="sxs-lookup"><span data-stu-id="17f9d-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="17f9d-191">如需陣列的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="17f9d-192">您可以指定的下限與上限，每個維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="17f9d-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="17f9d-193">若要這樣做，請包含`boundslist`在括號內。</span><span class="sxs-lookup"><span data-stu-id="17f9d-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="17f9d-194">針對每個維度，`boundslist`指定上限，以及選擇性的下限。</span><span class="sxs-lookup"><span data-stu-id="17f9d-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="17f9d-195">下限一律為零，是否有您不指定。</span><span class="sxs-lookup"><span data-stu-id="17f9d-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="17f9d-196">每個索引從零到其上限值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="17f9d-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="17f9d-197">下列兩個陳述式是相等的。</span><span class="sxs-lookup"><span data-stu-id="17f9d-197">The following two statements are equivalent.</span></span> <span data-ttu-id="17f9d-198">每個陳述式會宣告陣列的 21`Integer`項目。</span><span class="sxs-lookup"><span data-stu-id="17f9d-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="17f9d-199">當您存取陣列時，索引可能會因 0 到 20。</span><span class="sxs-lookup"><span data-stu-id="17f9d-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="17f9d-200">下列陳述式會宣告類型的二維陣列`Double`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="17f9d-201">陣列中有 4 個資料列 (3 + 1) 的 6 個資料行 (5 + 1)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="17f9d-202">請注意，上限則是代表索引，而不是維度的長度最大的可能值。</span><span class="sxs-lookup"><span data-stu-id="17f9d-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="17f9d-203">維度長度是上限加 1。</span><span class="sxs-lookup"><span data-stu-id="17f9d-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="17f9d-204">陣列可以有 1 到 32 個維度。</span><span class="sxs-lookup"><span data-stu-id="17f9d-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="17f9d-205">您可以將所有界限都保留為空白陣列宣告中。</span><span class="sxs-lookup"><span data-stu-id="17f9d-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="17f9d-206">如果您這麼做時，陣列中有指定，維度的數目，但未初始化。</span><span class="sxs-lookup"><span data-stu-id="17f9d-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="17f9d-207">它的值為`Nothing`直到您至少初始化其項目的部分。</span><span class="sxs-lookup"><span data-stu-id="17f9d-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="17f9d-208">`Dim`陳述式必須指定所有的維度或維度的界限。</span><span class="sxs-lookup"><span data-stu-id="17f9d-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="17f9d-209">如果陣列中有多個維度，您必須包含括號來表示的維度數目之間的逗號。</span><span class="sxs-lookup"><span data-stu-id="17f9d-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="17f9d-210">您可以宣告*零長度陣列*藉由宣告一個陣列的維度為-1。</span><span class="sxs-lookup"><span data-stu-id="17f9d-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="17f9d-211">保存為零長度陣列的變數沒有值`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="17f9d-212">某些 common language runtime 函數所需長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="17f9d-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="17f9d-213">如果您嘗試存取這類陣列時，就會發生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="17f9d-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="17f9d-214">如需詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="17f9d-215">您可以使用陣列常值來初始化陣列的值。</span><span class="sxs-lookup"><span data-stu-id="17f9d-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="17f9d-216">若要這樣做，初始設定值，以括號括住 (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="17f9d-217">對於多維度陣列，每個個別維度初始化是大括弧括住外部維度中。</span><span class="sxs-lookup"><span data-stu-id="17f9d-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="17f9d-218">以列為主要順序中指定的項目。</span><span class="sxs-lookup"><span data-stu-id="17f9d-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="17f9d-219">如需陣列常值的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a><span data-ttu-id="17f9d-220">預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="17f9d-220">Default Data Types and Values</span></span>  
 <span data-ttu-id="17f9d-221">下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。</span><span class="sxs-lookup"><span data-stu-id="17f9d-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="17f9d-222">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="17f9d-222">Data type specified?</span></span>|<span data-ttu-id="17f9d-223">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="17f9d-223">Initializer specified?</span></span>|<span data-ttu-id="17f9d-224">範例</span><span class="sxs-lookup"><span data-stu-id="17f9d-224">Example</span></span>|<span data-ttu-id="17f9d-225">結果</span><span class="sxs-lookup"><span data-stu-id="17f9d-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="17f9d-226">否</span><span class="sxs-lookup"><span data-stu-id="17f9d-226">No</span></span>|<span data-ttu-id="17f9d-227">否</span><span class="sxs-lookup"><span data-stu-id="17f9d-227">No</span></span>|`Dim qty`|<span data-ttu-id="17f9d-228">如果[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)是此變數設為 off （預設值）， `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="17f9d-229">如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="17f9d-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="17f9d-230">否</span><span class="sxs-lookup"><span data-stu-id="17f9d-230">No</span></span>|<span data-ttu-id="17f9d-231">是</span><span class="sxs-lookup"><span data-stu-id="17f9d-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="17f9d-232">如果[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)是 on （預設值），此變數會採用資料類型的初始設定式。</span><span class="sxs-lookup"><span data-stu-id="17f9d-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="17f9d-233">請參閱[區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="17f9d-234">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="17f9d-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="17f9d-235">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="17f9d-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="17f9d-236">是</span><span class="sxs-lookup"><span data-stu-id="17f9d-236">Yes</span></span>|<span data-ttu-id="17f9d-237">否</span><span class="sxs-lookup"><span data-stu-id="17f9d-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="17f9d-238">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="17f9d-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="17f9d-239">請參閱本節稍後的表格。</span><span class="sxs-lookup"><span data-stu-id="17f9d-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="17f9d-240">是</span><span class="sxs-lookup"><span data-stu-id="17f9d-240">Yes</span></span>|<span data-ttu-id="17f9d-241">是</span><span class="sxs-lookup"><span data-stu-id="17f9d-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="17f9d-242">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="17f9d-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="17f9d-243">如果您指定的資料類型，但未指定初始設定式，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]將變數初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="17f9d-243">If you specify a data type but do not specify an initializer, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="17f9d-244">下表顯示的預設初始化值。</span><span class="sxs-lookup"><span data-stu-id="17f9d-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="17f9d-245">資料類型</span><span class="sxs-lookup"><span data-stu-id="17f9d-245">Data type</span></span>|<span data-ttu-id="17f9d-246">預設值</span><span class="sxs-lookup"><span data-stu-id="17f9d-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="17f9d-247">所有數字類型 (包括`Byte`和`SByte`)</span><span class="sxs-lookup"><span data-stu-id="17f9d-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="17f9d-248">0</span><span class="sxs-lookup"><span data-stu-id="17f9d-248">0</span></span>|  
|`Char`|<span data-ttu-id="17f9d-249">二進位的 0</span><span class="sxs-lookup"><span data-stu-id="17f9d-249">Binary 0</span></span>|  
|<span data-ttu-id="17f9d-250">所有參考型別 (包括`Object`， `String`，和所有陣列)</span><span class="sxs-lookup"><span data-stu-id="17f9d-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="17f9d-251">1 年 1 年的 12:00 AM (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="17f9d-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="17f9d-252">結構的每個項目都會被視為個別的變數它初始化。</span><span class="sxs-lookup"><span data-stu-id="17f9d-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="17f9d-253">如果您宣告陣列的長度，但不是會初始化其項目，就好像個別的變數初始化每個項目。</span><span class="sxs-lookup"><span data-stu-id="17f9d-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="17f9d-254">靜態的本機變數存留期</span><span class="sxs-lookup"><span data-stu-id="17f9d-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="17f9d-255">A`Static`本機變數具有較長的存留期比宣告它的程序。</span><span class="sxs-lookup"><span data-stu-id="17f9d-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="17f9d-256">變數的存留期的範圍取決於宣告程序的位置，以及它是否`Shared`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="17f9d-257">程序宣告</span><span class="sxs-lookup"><span data-stu-id="17f9d-257">Procedure declaration</span></span>|<span data-ttu-id="17f9d-258">初始化變數</span><span class="sxs-lookup"><span data-stu-id="17f9d-258">Variable initialized</span></span>|<span data-ttu-id="17f9d-259">變數會停止現有的</span><span class="sxs-lookup"><span data-stu-id="17f9d-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="17f9d-260">在模組中</span><span class="sxs-lookup"><span data-stu-id="17f9d-260">In a module</span></span>|<span data-ttu-id="17f9d-261">第一次呼叫程序</span><span class="sxs-lookup"><span data-stu-id="17f9d-261">The first time the procedure is called</span></span>|<span data-ttu-id="17f9d-262">當您的程式停止執行</span><span class="sxs-lookup"><span data-stu-id="17f9d-262">When your program stops execution</span></span>|  
|<span data-ttu-id="17f9d-263">程序是在類別或結構中，`Shared`</span><span class="sxs-lookup"><span data-stu-id="17f9d-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="17f9d-264">第一次呼叫程序的特定執行個體或類別或結構本身</span><span class="sxs-lookup"><span data-stu-id="17f9d-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="17f9d-265">當您的程式停止執行</span><span class="sxs-lookup"><span data-stu-id="17f9d-265">When your program stops execution</span></span>|  
|<span data-ttu-id="17f9d-266">在類別或結構中，程序不是`Shared`</span><span class="sxs-lookup"><span data-stu-id="17f9d-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="17f9d-267">第一次在特定的執行個體呼叫程序</span><span class="sxs-lookup"><span data-stu-id="17f9d-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="17f9d-268">釋放執行個體進行記憶體回收 (GC)</span><span class="sxs-lookup"><span data-stu-id="17f9d-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="17f9d-269">屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="17f9d-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="17f9d-270">您可以將屬性套用只以成員變數，而非區域變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="17f9d-271">屬性會提供資訊給組件的中繼資料，不是有意義的暫存儲存體，例如本機變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="17f9d-272">在模組層級，您無法使用`Static`修飾詞來宣告成員變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="17f9d-273">在程序層級，您無法使用`Shared`， `Shadows`， `ReadOnly`， `WithEvents`，或任何存取修飾詞來宣告本機變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="17f9d-274">您可以指定哪些程式碼可以存取的變數，藉由提供`accessmodifier`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="17f9d-275">類別和模組成員 （在外的任何程序） 的變數預設為私用存取，而結構成員變數預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="17f9d-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="17f9d-276">您可以調整其存取層級，使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="17f9d-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="17f9d-277">您無法使用存取修飾詞 （程序） 內的區域變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="17f9d-278">您可以指定`WithEvents`只能在成員變數上，而不是程序內的區域變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="17f9d-279">如果您指定`WithEvents`，變數的資料型別必須不是特定類別類型， `Object`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="17f9d-280">您無法宣告陣列`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="17f9d-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="17f9d-281">如需有關事件的詳細資訊，請參閱[事件](../../../visual-basic/programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17f9d-282">程式碼外部類別、 結構或模組必須限定成員變數的名稱，該類別、 結構或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="17f9d-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="17f9d-283">程序或區塊不能參考該程序或區塊內任何區域變數的外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="17f9d-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="17f9d-284">釋放 Managed 的資源</span><span class="sxs-lookup"><span data-stu-id="17f9d-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="17f9d-285">.NET Framework 記憶體回收行程不含任何額外撰寫程式碼處置 managed 資源。</span><span class="sxs-lookup"><span data-stu-id="17f9d-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="17f9d-286">不過，您可以強制受管理的資源，而不是等待記憶體回收行程的處置。</span><span class="sxs-lookup"><span data-stu-id="17f9d-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="17f9d-287">如果類別保有特別重要，且很少的資源 （例如資料庫連接或檔案控制代碼），您可能不想等到下一個記憶體回收以清除不再使用的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="17f9d-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="17f9d-288">類別可以實作<xref:System.IDisposable>介面，以提供一個方式來釋放回收之前的資源。</span><span class="sxs-lookup"><span data-stu-id="17f9d-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="17f9d-289">實作該介面的類別會公開`Dispose`強制立即發行寶貴的資源，可以呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="17f9d-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="17f9d-290">`Using`陳述式自動化的程序取得資源、 執行一組陳述式，並再處置的資源。</span><span class="sxs-lookup"><span data-stu-id="17f9d-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="17f9d-291">不過，資源必須實作<xref:System.IDisposable>介面。</span><span class="sxs-lookup"><span data-stu-id="17f9d-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="17f9d-292">如需詳細資訊，請參閱 [Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="17f9d-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17f9d-293">範例</span><span class="sxs-lookup"><span data-stu-id="17f9d-293">Example</span></span>  
 <span data-ttu-id="17f9d-294">下列範例宣告變數，方法是使用`Dim`陳述式搭配各種選項。</span><span class="sxs-lookup"><span data-stu-id="17f9d-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="17f9d-295">範例</span><span class="sxs-lookup"><span data-stu-id="17f9d-295">Example</span></span>  
 <span data-ttu-id="17f9d-296">下列範例會列出質數介於 1 到 30 之間。</span><span class="sxs-lookup"><span data-stu-id="17f9d-296">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="17f9d-297">本機變數的範圍是程式碼註解中所述。</span><span class="sxs-lookup"><span data-stu-id="17f9d-297">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="17f9d-298">範例</span><span class="sxs-lookup"><span data-stu-id="17f9d-298">Example</span></span>  
 <span data-ttu-id="17f9d-299">在下列範例中，`speedValue`類別層級中宣告變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-299">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="17f9d-300">`Private`關鍵字用來宣告變數。</span><span class="sxs-lookup"><span data-stu-id="17f9d-300">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="17f9d-301">中的任何程序可以存取這個變數`Car`類別。</span><span class="sxs-lookup"><span data-stu-id="17f9d-301">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="17f9d-302">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17f9d-302">See Also</span></span>  
 [<span data-ttu-id="17f9d-303">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="17f9d-303">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="17f9d-304">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="17f9d-304">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="17f9d-305">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="17f9d-305">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="17f9d-306">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="17f9d-306">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="17f9d-307">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="17f9d-307">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="17f9d-308">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17f9d-308">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="17f9d-309">變數宣告</span><span class="sxs-lookup"><span data-stu-id="17f9d-309">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="17f9d-310">陣列</span><span class="sxs-lookup"><span data-stu-id="17f9d-310">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="17f9d-311">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="17f9d-311">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="17f9d-312">匿名類型</span><span class="sxs-lookup"><span data-stu-id="17f9d-312">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="17f9d-313">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="17f9d-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="17f9d-314">如何：使用物件初始設定式宣告物件</span><span class="sxs-lookup"><span data-stu-id="17f9d-314">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="17f9d-315">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="17f9d-315">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
