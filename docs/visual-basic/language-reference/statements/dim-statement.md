---
title: "Dim 陳述式 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, in Dim statement
- Dim statement
- fixed-length strings, declaring
- variables [Visual Basic], declaring
- WithEvents keyword, Dim statement
- dynamic arrays, Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields, as member variables
- declarations, dynamic arrays
- member variables
- default values
- data types [Visual Basic], assigning
- braces {}
- As keyword, in Dim statement
- arrays [Visual Basic], declaring
- New keyword, Dim statement
- To keyword, in Dim statement
- storage, allocating
- local variables
- declaration statements
- Dim statement, syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: 72
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 049ab1e82bac6c9f94bc411cd3e7c859e334d739
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="5a7f4-102">Dim 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a7f4-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="5a7f4-103">宣告和配置儲存空間的一或多個變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a7f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a7f4-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="5a7f4-105">組件</span><span class="sxs-lookup"><span data-stu-id="5a7f4-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="5a7f4-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-106">Optional.</span></span> <span data-ttu-id="5a7f4-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="5a7f4-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-108">Optional.</span></span> <span data-ttu-id="5a7f4-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="5a7f4-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="5a7f4-110">Public</span><span class="sxs-lookup"><span data-stu-id="5a7f4-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="5a7f4-111">Protected</span><span class="sxs-lookup"><span data-stu-id="5a7f4-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="5a7f4-112">Friend</span><span class="sxs-lookup"><span data-stu-id="5a7f4-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="5a7f4-113">Private</span><span class="sxs-lookup"><span data-stu-id="5a7f4-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="5a7f4-114">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-114">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="5a7f4-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-115">Optional.</span></span> <span data-ttu-id="5a7f4-116">請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="5a7f4-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-117">Optional.</span></span> <span data-ttu-id="5a7f4-118">請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="5a7f4-119">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-119">Optional.</span></span> <span data-ttu-id="5a7f4-120">請參閱[靜態](../../../visual-basic/language-reference/modifiers/static.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="5a7f4-121">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-121">Optional.</span></span> <span data-ttu-id="5a7f4-122">請參閱[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="5a7f4-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-123">Optional.</span></span> <span data-ttu-id="5a7f4-124">指定這些是可以引發事件的類別執行個體參考的物件變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="5a7f4-125">請參閱[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="5a7f4-126">必要項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-126">Required.</span></span> <span data-ttu-id="5a7f4-127">此陳述式所宣告的變數清單。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="5a7f4-128">每個 `variable` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="5a7f4-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="5a7f4-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="5a7f4-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="5a7f4-130">組件</span><span class="sxs-lookup"><span data-stu-id="5a7f4-130">Part</span></span>|<span data-ttu-id="5a7f4-131">描述</span><span class="sxs-lookup"><span data-stu-id="5a7f4-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="5a7f4-132">必要項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-132">Required.</span></span> <span data-ttu-id="5a7f4-133">變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-133">Name of the variable.</span></span> <span data-ttu-id="5a7f4-134">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="5a7f4-135">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-135">Optional.</span></span> <span data-ttu-id="5a7f4-136">每個維度的陣列變數的範圍清單。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="5a7f4-137">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-137">Optional.</span></span> <span data-ttu-id="5a7f4-138">建立類別的新執行個體時`Dim`陳述式執行。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="5a7f4-139">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-139">Optional.</span></span> <span data-ttu-id="5a7f4-140">變數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="5a7f4-141">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-141">Optional.</span></span> <span data-ttu-id="5a7f4-142">引入物件初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="5a7f4-143">選擇項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-143">Optional.</span></span> <span data-ttu-id="5a7f4-144">在類別中屬性的名稱就製作執行的個體。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="5a7f4-145">後需要`propertyname`=。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-145">Required after `propertyname` =.</span></span> <span data-ttu-id="5a7f4-146">運算式評估，以及指派給屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="5a7f4-147">若`New`未指定。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="5a7f4-148">運算式評估，以及建立時指派給變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a7f4-149">備註</span><span class="sxs-lookup"><span data-stu-id="5a7f4-149">Remarks</span></span>  
 <span data-ttu-id="5a7f4-150">Visual Basic 編譯器會使用`Dim`陳述式，判斷變數的資料類型和其他資訊，例如程式碼可存取的變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="5a7f4-151">下列範例宣告一個變數來保存`Integer`值。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="5a7f4-152">您可以指定任何資料型別或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="5a7f4-153">參考型別中，使用`New`關鍵字來建立類別的新執行個體或結構，指定資料型別。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="5a7f4-154">如果您使用`New`，您不使用初始設定式運算式。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="5a7f4-155">相反地，您提供的引數，如有必要，建立變數之類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="5a7f4-156">您可以宣告程序、 區塊、 類別、 結構或模組中的變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="5a7f4-157">您無法宣告在原始程式檔、 命名空間或介面中的變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="5a7f4-158">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="5a7f4-159">任何程序外的模組層級宣告的變數是*成員變數*或*欄位*。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="5a7f4-160">成員變數是在範圍中的類別、 結構或模組。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="5a7f4-161">程序層級宣告的變數是*區域變數*。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="5a7f4-162">本機變數是在其程序或區塊內的範圍內。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="5a7f4-163">下列存取修飾詞用來宣告變數的程序之外︰ `Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="5a7f4-164">如需詳細資訊，請參閱[在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-164">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="5a7f4-165">`Dim`關鍵字是選擇性，如果您指定下列任何修飾詞，通常可省略︰ `Public`， `Protected`， `Friend`， `Protected Friend`， `Private`， `Shared`， `Shadows`， `Static`， `ReadOnly`，或`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="5a7f4-166">如果`Option Explicit`是 （預設值），編譯器會需要宣告為每個您所使用的變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="5a7f4-167">如需詳細資訊，請參閱[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="5a7f4-168">指定的初始值</span><span class="sxs-lookup"><span data-stu-id="5a7f4-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="5a7f4-169">在建立時，您可以指派值給變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="5a7f4-170">在您使用的實值型別*初始設定式*提供要指派給變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="5a7f4-171">運算式必須評估為常數，可以在編譯時期計算。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="5a7f4-172">如果指定初始設定式和資料型別中未指定`As`子句，*型別推斷*用來推斷資料型別初始設定式。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="5a7f4-173">在下列範例中，同時`num1`和`num2`強型別為整數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="5a7f4-174">在第二個宣告中，型別推斷來推斷值 3 的類型。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="5a7f4-175">型別推斷會套用在程序層級。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="5a7f4-176">不適用的類別、 結構、 模組或介面中的程序之外。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="5a7f4-177">如需型別推斷的詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[本機的型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="5a7f4-178">若未指定資料型別或初始設定式發生狀況的詳細資訊，請參閱[預設資料類型和值](../../../visual-basic/language-reference/statements/dim-statement.md#default)稍後在本主題中。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="5a7f4-179">您可以使用*物件初始設定式*宣告具名和匿名型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="5a7f4-180">下列程式碼建立的執行個體`Student`類別，並使用物件初始設定式初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="5a7f4-181">如需物件初始設定式的詳細資訊，請參閱[How to︰ 使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)，[物件初始設定式︰ 具名和匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)，和[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="5a7f4-182">宣告多個變數</span><span class="sxs-lookup"><span data-stu-id="5a7f4-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="5a7f4-183">您可以宣告數個變數，在一個宣告陳述式，使用括號指定每個與下列每個陣列名稱的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="5a7f4-184">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="5a7f4-185">如果您宣告一個以上的變數，其中一個`As`子句中，您無法提供該群組的變數初始設定式。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="5a7f4-186">您可以指定不同的資料類型為不同的變數使用個別`As`子句的每個宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="5a7f4-187">每個變數會在第一個指定的資料類型`As`後發生的子句其`variablename`組件。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="5a7f4-188">陣列</span><span class="sxs-lookup"><span data-stu-id="5a7f4-188">Arrays</span></span>  
 <span data-ttu-id="5a7f4-189">您可以宣告一個變數來保存*陣列*，可儲存多個值。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="5a7f4-190">若要指定的變數會保留一個陣列，請遵循其`variablename`立即以括號括住。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="5a7f4-191">如需陣列的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="5a7f4-192">您可以指定陣列的每個維度的下限與上限。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="5a7f4-193">若要這樣做，請包含`boundslist`在括號內。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="5a7f4-194">針對每個維度，`boundslist`指定上限，以及選擇性的下限。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="5a7f4-195">下限永遠為零，是否有您不指定。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="5a7f4-196">每個索引從零到上限值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="5a7f4-197">下列兩個陳述式是相等的。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-197">The following two statements are equivalent.</span></span> <span data-ttu-id="5a7f4-198">每個陳述式會宣告陣列 21`Integer`項目。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="5a7f4-199">當您存取陣列時，索引可以改變從 0 到 20。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="5a7f4-200">下列陳述式會宣告類型的二維陣列`Double`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="5a7f4-201">陣列有 4 個資料列 (3 + 1) 的 6 個資料行 (5 + 1)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="5a7f4-202">請注意上限，代表索引，而不是維度的長度最高的可能值。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="5a7f4-203">維度的長度是上限加一。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="5a7f4-204">陣列可以有 1 到 32 個維度。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="5a7f4-205">您可以將所有界限都保留為空白陣列宣告中。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="5a7f4-206">如果您這麼做，則表示陣列有指定，維度的數目，但尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="5a7f4-207">它的值為`Nothing`直到您至少初始化部分元素。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="5a7f4-208">`Dim`陳述式必須指定所有維度或沒有維度的界限。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="5a7f4-209">如果陣列有多個維度，您必須包含括號來表示的維度數目之間的逗號。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="5a7f4-210">您可以宣告*長度零的陣列*宣告一個陣列的維度為-1。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="5a7f4-211">此變數會保存長度為零的陣列沒有值`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="5a7f4-212">某些 common language runtime 函數所需長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="5a7f4-213">如果您嘗試存取這類陣列時，就會發生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="5a7f4-214">如需詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="5a7f4-215">您可以使用陣列常值初始化陣列的值。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="5a7f4-216">若要這樣做，圍繞用大括號 (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="5a7f4-217">多維陣列時，針對每個個別維度初始化以層的維度中的括號括住。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="5a7f4-218">以列為主要順序中指定的元素。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="5a7f4-219">如需陣列常值的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <span data-ttu-id="5a7f4-220"><a name="default"></a>預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="5a7f4-220"><a name="default"></a> Default Data Types and Values</span></span>  
 <span data-ttu-id="5a7f4-221">下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="5a7f4-222">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="5a7f4-222">Data type specified?</span></span>|<span data-ttu-id="5a7f4-223">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="5a7f4-223">Initializer specified?</span></span>|<span data-ttu-id="5a7f4-224">範例</span><span class="sxs-lookup"><span data-stu-id="5a7f4-224">Example</span></span>|<span data-ttu-id="5a7f4-225">結果</span><span class="sxs-lookup"><span data-stu-id="5a7f4-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="5a7f4-226">否</span><span class="sxs-lookup"><span data-stu-id="5a7f4-226">No</span></span>|<span data-ttu-id="5a7f4-227">否</span><span class="sxs-lookup"><span data-stu-id="5a7f4-227">No</span></span>|`Dim qty`|<span data-ttu-id="5a7f4-228">如果[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)是 off （預設值），此變數設為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="5a7f4-229">如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="5a7f4-230">否</span><span class="sxs-lookup"><span data-stu-id="5a7f4-230">No</span></span>|<span data-ttu-id="5a7f4-231">是</span><span class="sxs-lookup"><span data-stu-id="5a7f4-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="5a7f4-232">如果[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)已開啟 （預設值），此變數會採用資料類型的初始設定式。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="5a7f4-233">請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="5a7f4-234">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="5a7f4-235">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="5a7f4-236">是</span><span class="sxs-lookup"><span data-stu-id="5a7f4-236">Yes</span></span>|<span data-ttu-id="5a7f4-237">否</span><span class="sxs-lookup"><span data-stu-id="5a7f4-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="5a7f4-238">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="5a7f4-239">請參閱本節稍後的表格。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="5a7f4-240">是</span><span class="sxs-lookup"><span data-stu-id="5a7f4-240">Yes</span></span>|<span data-ttu-id="5a7f4-241">是</span><span class="sxs-lookup"><span data-stu-id="5a7f4-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="5a7f4-242">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="5a7f4-243">如果您指定資料型別，但未指定初始設定式，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將變數初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-243">If you specify a data type but do not specify an initializer, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="5a7f4-244">下表顯示的預設初始設定值。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="5a7f4-245">資料類型</span><span class="sxs-lookup"><span data-stu-id="5a7f4-245">Data type</span></span>|<span data-ttu-id="5a7f4-246">預設值</span><span class="sxs-lookup"><span data-stu-id="5a7f4-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="5a7f4-247">所有數字型別 (包括`Byte`和`SByte`)</span><span class="sxs-lookup"><span data-stu-id="5a7f4-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="5a7f4-248">0</span><span class="sxs-lookup"><span data-stu-id="5a7f4-248">0</span></span>|  
|`Char`|<span data-ttu-id="5a7f4-249">二進位的 0</span><span class="sxs-lookup"><span data-stu-id="5a7f4-249">Binary 0</span></span>|  
|<span data-ttu-id="5a7f4-250">所有參考型別 (包括`Object`， `String`，和所有陣列)</span><span class="sxs-lookup"><span data-stu-id="5a7f4-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="5a7f4-251">1 年 1 年的 12:00 AM (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="5a7f4-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="5a7f4-252">結構的每個項目都會被視為個別的變數它初始化。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="5a7f4-253">如果您宣告陣列的長度，但無法初始化其項目，如同它是個別的變數初始化每個項目。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="5a7f4-254">靜態本機變數存留期</span><span class="sxs-lookup"><span data-stu-id="5a7f4-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="5a7f4-255">A`Static`本機變數已宣告它的程序較長的生命週期。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="5a7f4-256">變數的存留期的範圍取決於宣告程序的位置，以及它是否`Shared`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="5a7f4-257">程序宣告</span><span class="sxs-lookup"><span data-stu-id="5a7f4-257">Procedure declaration</span></span>|<span data-ttu-id="5a7f4-258">初始化變數</span><span class="sxs-lookup"><span data-stu-id="5a7f4-258">Variable initialized</span></span>|<span data-ttu-id="5a7f4-259">變數會停止現有的</span><span class="sxs-lookup"><span data-stu-id="5a7f4-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="5a7f4-260">在模組中</span><span class="sxs-lookup"><span data-stu-id="5a7f4-260">In a module</span></span>|<span data-ttu-id="5a7f4-261">第一次呼叫程序</span><span class="sxs-lookup"><span data-stu-id="5a7f4-261">The first time the procedure is called</span></span>|<span data-ttu-id="5a7f4-262">當您的程式停止執行</span><span class="sxs-lookup"><span data-stu-id="5a7f4-262">When your program stops execution</span></span>|  
|<span data-ttu-id="5a7f4-263">程序是在類別或結構中，`Shared`</span><span class="sxs-lookup"><span data-stu-id="5a7f4-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="5a7f4-264">第一次呼叫程序的特定執行個體或類別或結構本身</span><span class="sxs-lookup"><span data-stu-id="5a7f4-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="5a7f4-265">當您的程式停止執行</span><span class="sxs-lookup"><span data-stu-id="5a7f4-265">When your program stops execution</span></span>|  
|<span data-ttu-id="5a7f4-266">在類別或結構中，程序並不會`Shared`</span><span class="sxs-lookup"><span data-stu-id="5a7f4-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="5a7f4-267">第一次在特定的執行個體呼叫程序</span><span class="sxs-lookup"><span data-stu-id="5a7f4-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="5a7f4-268">釋放執行個體進行記憶體回收 (GC)</span><span class="sxs-lookup"><span data-stu-id="5a7f4-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="5a7f4-269">屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="5a7f4-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="5a7f4-270">您可以套用屬性，只以成員變數，而非區域變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="5a7f4-271">屬性會提供資訊給組件的中繼資料，不是有意義的暫存儲存體，例如本機變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="5a7f4-272">在模組層級，您不能使用`Static`修飾詞宣告成員變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="5a7f4-273">在程序層級，您不能使用`Shared`， `Shadows`， `ReadOnly`， `WithEvents`，或以任何方式存取修飾詞來宣告區域變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="5a7f4-274">您可以指定哪些程式碼可以存取的變數，藉由提供`accessmodifier`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="5a7f4-275">類別和模組成員變數 （外部的任何程序） 預設為私人存取，而結構成員變數預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="5a7f4-276">您可以調整存取層級的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="5a7f4-277">您不能使用本機變數 （在程序） 的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="5a7f4-278">您可以指定`WithEvents`只對成員變數，而非程序內的區域變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="5a7f4-279">如果您指定`WithEvents`，變數的資料型別不可以是特定類別類型時， `Object`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="5a7f4-280">您無法宣告陣列`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="5a7f4-281">如需事件的詳細資訊，請參閱[事件](../../../visual-basic/programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a7f4-282">程式碼類別之外，結構或模組必須限定成員變數的名稱，該類別、 結構或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="5a7f4-283">程序或區塊不能參考該程序或區塊內任何區域變數的外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="5a7f4-284">釋放 Managed 的資源</span><span class="sxs-lookup"><span data-stu-id="5a7f4-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="5a7f4-285">.NET Framework 記憶體回收行程會處置 managed 資源而不需要您採取任何額外程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="5a7f4-286">不過，您可以強制受管理的資源，而不是等待記憶體回收行程的處置。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="5a7f4-287">如果類別是由特別有用，且很少資源 （例如資料庫連接或檔案控制代碼） 所佔用，您可能不想等到下一個記憶體回收清除不再使用的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="5a7f4-288">類別可以實作<xref:System.IDisposable>介面，以提供方法來釋放記憶體回收之前的資源。</xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="5a7f4-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="5a7f4-289">實作該介面的類別會公開`Dispose`強制立即釋出寶貴的資源，可以呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="5a7f4-290">`Using`陳述式會自動取得資源、 執行一組陳述式，然後處置資源的程序。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="5a7f4-291">不過，資源必須實作<xref:System.IDisposable>介面。</xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="5a7f4-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="5a7f4-292">如需詳細資訊，請參閱[Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a7f4-293">範例</span><span class="sxs-lookup"><span data-stu-id="5a7f4-293">Example</span></span>  
 <span data-ttu-id="5a7f4-294">下列範例會使用宣告變數`Dim`陳述式搭配各種選項。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 <span data-ttu-id="5a7f4-295">[!code-vb[VbVbalrStatements #&141; 毫秒](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a7f4-295">[!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a7f4-296">範例</span><span class="sxs-lookup"><span data-stu-id="5a7f4-296">Example</span></span>  
 <span data-ttu-id="5a7f4-297">下列範例會列出介於 1 到 30 之間的質數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-297">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="5a7f4-298">本機變數的範圍是程式碼註解中所述。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-298">The scope of local variables is described in code comments.</span></span>  
  
 <span data-ttu-id="5a7f4-299">[!code-vb[VbVbalrStatements #&142;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a7f4-299">[!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a7f4-300">範例</span><span class="sxs-lookup"><span data-stu-id="5a7f4-300">Example</span></span>  
 <span data-ttu-id="5a7f4-301">在下列範例中，`speedValue`在類別層級中宣告變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="5a7f4-302">`Private`關鍵字用來宣告變數。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="5a7f4-303">中的任何程序可以存取這個變數`Car`類別。</span><span class="sxs-lookup"><span data-stu-id="5a7f4-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 <span data-ttu-id="5a7f4-304">[!code-vb[VbVbalrStatements #&144;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a7f4-304">[!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="5a7f4-305">[!code-vb[VbVbalrStatements #&145;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a7f4-305">[!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a7f4-306">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a7f4-306">See Also</span></span>  
 <span data-ttu-id="5a7f4-307">[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-307">[Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="5a7f4-308"> [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-308"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="5a7f4-309"> [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-309"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="5a7f4-310"> [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-310"> [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="5a7f4-311"> [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-311"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="5a7f4-312"> [專案設計工具、編譯頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-312"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="5a7f4-313"> [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-313"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="5a7f4-314"> [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-314"> [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="5a7f4-315"> [物件初始設定式︰ 具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-315"> [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="5a7f4-316"> [匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-316"> [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="5a7f4-317"> [物件初始設定式︰ 具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-317"> [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="5a7f4-318"> [如何︰ 使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) </span><span class="sxs-lookup"><span data-stu-id="5a7f4-318"> [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) </span></span>  
<span data-ttu-id="5a7f4-319"> [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="5a7f4-319"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>

