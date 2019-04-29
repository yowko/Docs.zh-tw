---
title: Dim 陳述式 (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: cab1cc07d23a44e57bdb0962a323b014308cb1e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638210"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="3d3e6-102">Dim 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d3e6-102">Dim Statement (Visual Basic)</span></span>

<span data-ttu-id="3d3e6-103">宣告，並針對一或多個變數配置儲存空間。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-103">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d3e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d3e6-104">Syntax</span></span>

```
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="3d3e6-105">組件</span><span class="sxs-lookup"><span data-stu-id="3d3e6-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="3d3e6-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-106">Optional.</span></span> <span data-ttu-id="3d3e6-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="3d3e6-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-108">Optional.</span></span> <span data-ttu-id="3d3e6-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3d3e6-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="3d3e6-110">Public</span><span class="sxs-lookup"><span data-stu-id="3d3e6-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="3d3e6-111">Protected</span><span class="sxs-lookup"><span data-stu-id="3d3e6-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="3d3e6-112">Friend</span><span class="sxs-lookup"><span data-stu-id="3d3e6-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="3d3e6-113">Private</span><span class="sxs-lookup"><span data-stu-id="3d3e6-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="3d3e6-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="3d3e6-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="3d3e6-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="3d3e6-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="3d3e6-116">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="3d3e6-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-117">Optional.</span></span> <span data-ttu-id="3d3e6-118">請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="3d3e6-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-119">Optional.</span></span> <span data-ttu-id="3d3e6-120">請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="3d3e6-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-121">Optional.</span></span> <span data-ttu-id="3d3e6-122">請參閱[靜態](../../../visual-basic/language-reference/modifiers/static.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="3d3e6-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-123">Optional.</span></span> <span data-ttu-id="3d3e6-124">請參閱[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>

- `WithEvents`

<span data-ttu-id="3d3e6-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-125">Optional.</span></span> <span data-ttu-id="3d3e6-126">指定這些是可以引發事件的類別執行個體參考的物件變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="3d3e6-127">請參閱[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="3d3e6-128">必要項。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-128">Required.</span></span> <span data-ttu-id="3d3e6-129">此陳述式所宣告的變數清單。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-129">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="3d3e6-130">每個 `variable` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="3d3e6-130">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="3d3e6-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="3d3e6-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="3d3e6-132">組件</span><span class="sxs-lookup"><span data-stu-id="3d3e6-132">Part</span></span>|<span data-ttu-id="3d3e6-133">描述</span><span class="sxs-lookup"><span data-stu-id="3d3e6-133">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="3d3e6-134">必要項。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-134">Required.</span></span> <span data-ttu-id="3d3e6-135">變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-135">Name of the variable.</span></span> <span data-ttu-id="3d3e6-136">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="3d3e6-137">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-137">Optional.</span></span> <span data-ttu-id="3d3e6-138">每個維度的陣列變數的範圍的清單。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-138">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="3d3e6-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-139">Optional.</span></span> <span data-ttu-id="3d3e6-140">建立類別的新執行個體時`Dim`陳述式執行。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="3d3e6-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-141">Optional.</span></span> <span data-ttu-id="3d3e6-142">變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-142">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="3d3e6-143">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-143">Optional.</span></span> <span data-ttu-id="3d3e6-144">導入了物件初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-144">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="3d3e6-145">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-145">Optional.</span></span> <span data-ttu-id="3d3e6-146">在類別中屬性的名稱，您要進行執行的個體。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-146">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="3d3e6-147">後需要`propertyname`=。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-147">Required after `propertyname` =.</span></span> <span data-ttu-id="3d3e6-148">運算式評估，以及指派給屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-148">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="3d3e6-149">選擇性如果`New`未指定。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="3d3e6-150">運算式評估，以及建立時指派給變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d3e6-151">備註</span><span class="sxs-lookup"><span data-stu-id="3d3e6-151">Remarks</span></span>

<span data-ttu-id="3d3e6-152">Visual Basic 編譯器使用`Dim`陳述式來判斷變數的資料類型和其他資訊，例如哪些程式碼可以存取的變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="3d3e6-153">下列範例會宣告變數，以保留`Integer`值。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-153">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="3d3e6-154">您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="3d3e6-155">對於參考型別，您使用`New`關鍵字來建立類別的新執行個體，或結構，指定資料型別。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="3d3e6-156">如果您使用`New`，您不使用初始設定式運算式。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="3d3e6-157">相反地，您提供引數，如有必要，建立變數類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="3d3e6-158">您可以宣告程序、 區塊、 類別、 結構或模組中的變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="3d3e6-159">您無法宣告的原始程式檔、 命名空間或介面中的變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="3d3e6-160">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="3d3e6-161">在模組層級，任何程序中，外部宣告的變數是*成員變數*或是*欄位*。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="3d3e6-162">成員變數會在其類別、 結構或模組的範圍中。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="3d3e6-163">程序層級宣告的變數是*區域變數*。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="3d3e6-164">本機變數是在範圍內，只在他們的程序或區塊內。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-164">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="3d3e6-165">下列存取修飾詞用來宣告變數的程序之外： `Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="3d3e6-166">如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="3d3e6-167">`Dim`關鍵字是選擇性，而且通常省略 如果您指定任何下列修飾詞： `Public`， `Protected`， `Friend`， `Protected Friend`， `Private`， `Shared`， `Shadows`， `Static`，`ReadOnly`，或`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="3d3e6-168">如果`Option Explicit`是 on （預設值），編譯器會需要的宣告的每個您所使用的變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="3d3e6-169">如需詳細資訊，請參閱 < [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="3d3e6-170">指定的初始值</span><span class="sxs-lookup"><span data-stu-id="3d3e6-170">Specifying an Initial Value</span></span>

<span data-ttu-id="3d3e6-171">建立時，您可以指派值給變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="3d3e6-172">在您使用實值類型，如*初始設定式*提供要指派給變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="3d3e6-173">運算式必須評估為常數，可以在編譯時期計算。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="3d3e6-174">如果已指定初始設定式，而且中未指定資料型別`As`子句*型別推斷*用來推斷資料型別，從初始設定式。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="3d3e6-175">在下列範例中，同時`num1`和`num2`強型別為整數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="3d3e6-176">在第二個宣告中，型別推斷會推斷值 3 的類型。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-176">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="3d3e6-177">型別推斷會套用在程序層級。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="3d3e6-178">它不適用於外部類別、 結構、 模組或介面中的程序。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="3d3e6-179">如需型別推斷的詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)並[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="3d3e6-180">如未指定資料型別或初始設定式時，會發生什麼情況的相關資訊，請參閱 <<c0> [ 預設資料類型和值](../../../visual-basic/language-reference/statements/dim-statement.md#default)本主題稍後的。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="3d3e6-181">您可以使用*物件初始設定式*宣告具名和匿名型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="3d3e6-182">下列程式碼建立的執行個體`Student`類別，並使用物件初始設定式初始化的屬性。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="3d3e6-183">如需物件初始設定式的詳細資訊，請參閱[How to:使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)，[物件初始設定式：具名和匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)，並[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="3d3e6-184">宣告多個變數</span><span class="sxs-lookup"><span data-stu-id="3d3e6-184">Declaring Multiple Variables</span></span>

<span data-ttu-id="3d3e6-185">您可以宣告一個宣告陳述式中的數個變數使用括號指定針對每個與下列每個陣列名稱的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="3d3e6-186">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-186">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="3d3e6-187">如果您宣告多個變數具有一個`As`子句中，您無法提供該變數群組的初始設定式。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="3d3e6-188">您可以指定不同的變數的不同資料類型使用個別`As`子句宣告每個變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="3d3e6-189">每個變數會在第一個指定的資料類型`As`子句後發生其`variablename`組件。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="3d3e6-190">陣列</span><span class="sxs-lookup"><span data-stu-id="3d3e6-190">Arrays</span></span>

<span data-ttu-id="3d3e6-191">您可以宣告的變數來保存*陣列*，其中可包含多個值。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="3d3e6-192">若要指定變數會保留一個陣列，請遵循其`variablename`立即使用括號。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="3d3e6-193">如需陣列的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="3d3e6-194">您可以指定的下限與上限的每個維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="3d3e6-195">若要這樣做，請包含`boundslist`在括號內。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="3d3e6-196">每個維度，`boundslist`指定上限以及選擇性的下限。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="3d3e6-197">下限一律為零，是否您不指定。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="3d3e6-198">每個索引從 0 到上限值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-198">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="3d3e6-199">下列兩個陳述式是相等的。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-199">The following two statements are equivalent.</span></span> <span data-ttu-id="3d3e6-200">每個陳述式會宣告陣列的 21`Integer`項目。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="3d3e6-201">當您存取陣列時，索引有所不同從 0 到 20。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-201">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="3d3e6-202">下列陳述式會宣告類型的二維陣列`Double`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="3d3e6-203">陣列中有 4 個資料列 (3 + 1) 的 6 個資料行 (5 + 1) 每個。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="3d3e6-204">請注意上限，代表索引，而不是維度的長度最大的可能值。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="3d3e6-205">維度的長度是上限加 1。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-205">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="3d3e6-206">陣列可以有 1 到 32 個維度。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-206">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="3d3e6-207">您可以將所有範圍都保留為空白陣列宣告中。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="3d3e6-208">如果您這麼做時，陣列中有指定，維度的數目，但它未初始化。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="3d3e6-209">它的值為`Nothing`直到您至少初始化其項目部分。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="3d3e6-210">`Dim`陳述式必須指定所有的維度或的任何維度的界限。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="3d3e6-211">如果陣列中有多個維度，您必須包含括號來表示的維度數目之間的逗號。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="3d3e6-212">您可以宣告*長度零的陣列*藉由宣告一個陣列的維度，以便是-1。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="3d3e6-213">此變數會保存的長度為零的陣列沒有值`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="3d3e6-214">特定的 common language runtime 函數所需長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="3d3e6-215">如果您嘗試存取這類陣列時，就會發生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="3d3e6-216">如需詳細資訊，請參閱 <<c0> [ 陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="3d3e6-217">您可以使用陣列常值來初始化陣列的值。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="3d3e6-218">若要這樣做，括住的初始設定值，以大括弧 (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-218">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="3d3e6-219">對於多維度陣列，初始化的每個個別的維度會包含在外部維度中的大括號。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="3d3e6-220">項目是以列為主要順序指定。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-220">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="3d3e6-221">如需有關陣列常值的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default"></a> <span data-ttu-id="3d3e6-222">預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="3d3e6-222">Default Data Types and Values</span></span>

<span data-ttu-id="3d3e6-223">下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="3d3e6-224">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="3d3e6-224">Data type specified?</span></span>|<span data-ttu-id="3d3e6-225">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="3d3e6-225">Initializer specified?</span></span>|<span data-ttu-id="3d3e6-226">範例</span><span class="sxs-lookup"><span data-stu-id="3d3e6-226">Example</span></span>|<span data-ttu-id="3d3e6-227">結果</span><span class="sxs-lookup"><span data-stu-id="3d3e6-227">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="3d3e6-228">否</span><span class="sxs-lookup"><span data-stu-id="3d3e6-228">No</span></span>|<span data-ttu-id="3d3e6-229">否</span><span class="sxs-lookup"><span data-stu-id="3d3e6-229">No</span></span>|`Dim qty`|<span data-ttu-id="3d3e6-230">如果[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)會將變數設為 off （預設值）， `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="3d3e6-231">如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="3d3e6-232">否</span><span class="sxs-lookup"><span data-stu-id="3d3e6-232">No</span></span>|<span data-ttu-id="3d3e6-233">是</span><span class="sxs-lookup"><span data-stu-id="3d3e6-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="3d3e6-234">如果[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)是 on （預設值），此變數會採用資料類型的初始設定式。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="3d3e6-235">請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="3d3e6-236">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="3d3e6-237">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="3d3e6-238">是</span><span class="sxs-lookup"><span data-stu-id="3d3e6-238">Yes</span></span>|<span data-ttu-id="3d3e6-239">否</span><span class="sxs-lookup"><span data-stu-id="3d3e6-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="3d3e6-240">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="3d3e6-241">請參閱本節稍後的表格。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-241">See the table later in this section.</span></span>|
|<span data-ttu-id="3d3e6-242">是</span><span class="sxs-lookup"><span data-stu-id="3d3e6-242">Yes</span></span>|<span data-ttu-id="3d3e6-243">是</span><span class="sxs-lookup"><span data-stu-id="3d3e6-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="3d3e6-244">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="3d3e6-245">如果您指定的資料類型，但未指定初始設定式，Visual Basic 變數初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="3d3e6-246">下表顯示的預設初始化值。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-246">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="3d3e6-247">資料類型</span><span class="sxs-lookup"><span data-stu-id="3d3e6-247">Data type</span></span>|<span data-ttu-id="3d3e6-248">預設值</span><span class="sxs-lookup"><span data-stu-id="3d3e6-248">Default value</span></span>|
|---|---|
|<span data-ttu-id="3d3e6-249">所有數字類型 (包括`Byte`和`SByte`)</span><span class="sxs-lookup"><span data-stu-id="3d3e6-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="3d3e6-250">0</span><span class="sxs-lookup"><span data-stu-id="3d3e6-250">0</span></span>|
|`Char`|<span data-ttu-id="3d3e6-251">二進位的 0</span><span class="sxs-lookup"><span data-stu-id="3d3e6-251">Binary 0</span></span>|
|<span data-ttu-id="3d3e6-252">所有參考型別 (包括`Object`， `String`，和所有陣列)</span><span class="sxs-lookup"><span data-stu-id="3d3e6-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="3d3e6-253">1 年 1 月 12:00 AM (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="3d3e6-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="3d3e6-254">結構的每個項目都會被視為個別的變數它初始化。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="3d3e6-255">如果您宣告陣列的長度，但未初始化其項目，如同個別的變數，會初始化每個項目。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="3d3e6-256">靜態的本機變數存留期</span><span class="sxs-lookup"><span data-stu-id="3d3e6-256">Static Local Variable Lifetime</span></span>

<span data-ttu-id="3d3e6-257">A`Static`區域變數有較長的存留期比宣告它的程序。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="3d3e6-258">變數的存留期的範圍取決於宣告程序的位置，以及它是否`Shared`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="3d3e6-259">程序宣告</span><span class="sxs-lookup"><span data-stu-id="3d3e6-259">Procedure declaration</span></span>|<span data-ttu-id="3d3e6-260">初始化變數</span><span class="sxs-lookup"><span data-stu-id="3d3e6-260">Variable initialized</span></span>|<span data-ttu-id="3d3e6-261">變數會停止現有的</span><span class="sxs-lookup"><span data-stu-id="3d3e6-261">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="3d3e6-262">在模組中</span><span class="sxs-lookup"><span data-stu-id="3d3e6-262">In a module</span></span>|<span data-ttu-id="3d3e6-263">第一次呼叫程序</span><span class="sxs-lookup"><span data-stu-id="3d3e6-263">The first time the procedure is called</span></span>|<span data-ttu-id="3d3e6-264">當您的程式停止執行</span><span class="sxs-lookup"><span data-stu-id="3d3e6-264">When your program stops execution</span></span>|
|<span data-ttu-id="3d3e6-265">程序是在類別或結構中， `Shared`</span><span class="sxs-lookup"><span data-stu-id="3d3e6-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="3d3e6-266">第一次呼叫程序的特定執行個體或類別或結構本身</span><span class="sxs-lookup"><span data-stu-id="3d3e6-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="3d3e6-267">當您的程式停止執行</span><span class="sxs-lookup"><span data-stu-id="3d3e6-267">When your program stops execution</span></span>|
|<span data-ttu-id="3d3e6-268">在類別或結構中，程序不是 `Shared`</span><span class="sxs-lookup"><span data-stu-id="3d3e6-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="3d3e6-269">第一次在特定的執行個體上呼叫程序</span><span class="sxs-lookup"><span data-stu-id="3d3e6-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="3d3e6-270">執行個體進行記憶體回收 (GC) 的發行時</span><span class="sxs-lookup"><span data-stu-id="3d3e6-270">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="3d3e6-271">屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="3d3e6-271">Attributes and Modifiers</span></span>

<span data-ttu-id="3d3e6-272">您可以套用屬性，只以成員變數，而非區域變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="3d3e6-273">屬性會提供資訊給組件的中繼資料，不是暫時的儲存體，例如本機變數才有意義。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="3d3e6-274">在模組層級，您無法使用`Static`修飾詞來宣告成員變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="3d3e6-275">在程序層級，您無法使用`Shared`， `Shadows`， `ReadOnly`， `WithEvents`，或任何存取修飾詞來宣告本機變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="3d3e6-276">您可以指定哪些程式碼可以存取的變數，藉由提供`accessmodifier`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="3d3e6-277">類別和模組成員 （以外的任何程序） 的變數預設為私用存取，而結構成員變數預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="3d3e6-278">您可以調整它們的存取層級，使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="3d3e6-279">您無法使用存取修飾詞 （在程序） 的本機變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="3d3e6-280">您可以指定`WithEvents`只對成員變數，而不是在程序內的本機變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="3d3e6-281">如果您指定`WithEvents`，變數的資料類型必須是特定類別類型時，不`Object`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="3d3e6-282">您無法宣告陣列`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="3d3e6-283">如需有關事件的詳細資訊，請參閱[事件](../../../visual-basic/programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3d3e6-284">程式碼類別之外，結構或模組必須限定成員變數的名稱，該類別、 結構或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="3d3e6-285">程序或區塊不能參考該程序或區塊內任何區域變數的外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="3d3e6-286">釋放 Managed 的資源</span><span class="sxs-lookup"><span data-stu-id="3d3e6-286">Releasing Managed Resources</span></span>

<span data-ttu-id="3d3e6-287">.NET Framework 記憶體回收行程會處置 managed 資源而不需要任何額外的程式碼，就在您的組件。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="3d3e6-288">不過，您可以強制受管理的資源，而不是等待記憶體回收行程的處置。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="3d3e6-289">如果類別是由特別重要，且很少資源 （例如資料庫連接或檔案控制代碼） 所佔用，您可能不想等到下一個記憶體回收以清除不再使用中的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="3d3e6-290">類別可以實作<xref:System.IDisposable>介面，以提供方法來釋放資源之前進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="3d3e6-291">類別若實作該介面會公開`Dispose`可以強制寶貴的資源可立即釋放呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="3d3e6-292">`Using`陳述式自動化程序取得資源、 執行一組陳述式，和然後處置的資源。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="3d3e6-293">不過，資源必須實作<xref:System.IDisposable>介面。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="3d3e6-294">如需詳細資訊，請參閱 [Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="3d3e6-295">範例</span><span class="sxs-lookup"><span data-stu-id="3d3e6-295">Example</span></span>

<span data-ttu-id="3d3e6-296">下列範例會藉由宣告變數`Dim`搭配各種選項的陳述式。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-296">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="3d3e6-297">範例</span><span class="sxs-lookup"><span data-stu-id="3d3e6-297">Example</span></span>

<span data-ttu-id="3d3e6-298">下列範例會列出介於 1 到 30 之間的質數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="3d3e6-299">程式碼註解說明本機變數的範圍。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-299">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="3d3e6-300">範例</span><span class="sxs-lookup"><span data-stu-id="3d3e6-300">Example</span></span>

<span data-ttu-id="3d3e6-301">在下列範例中，`speedValue`在類別層級中宣告變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="3d3e6-302">`Private`關鍵字用來宣告變數。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="3d3e6-303">中的任何程序可以存取該變數`Car`類別。</span><span class="sxs-lookup"><span data-stu-id="3d3e6-303">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="3d3e6-304">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d3e6-304">See also</span></span>

- [<span data-ttu-id="3d3e6-305">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d3e6-305">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="3d3e6-306">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d3e6-306">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="3d3e6-307">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d3e6-307">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="3d3e6-308">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d3e6-308">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="3d3e6-309">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d3e6-309">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="3d3e6-310">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d3e6-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="3d3e6-311">變數宣告</span><span class="sxs-lookup"><span data-stu-id="3d3e6-311">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="3d3e6-312">陣列</span><span class="sxs-lookup"><span data-stu-id="3d3e6-312">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="3d3e6-313">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="3d3e6-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="3d3e6-314">匿名類型</span><span class="sxs-lookup"><span data-stu-id="3d3e6-314">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="3d3e6-315">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="3d3e6-315">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="3d3e6-316">如何：使用物件初始設定式宣告物件</span><span class="sxs-lookup"><span data-stu-id="3d3e6-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="3d3e6-317">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="3d3e6-317">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
