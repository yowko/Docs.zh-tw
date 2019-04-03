---
title: 區域類型推斷 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826817"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="aaab6-102">區域類型推斷 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aaab6-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="aaab6-103">Visual Basic 編譯器會使用*型別推斷*來判斷資料類型的未宣告的區域變數`As`子句。</span><span class="sxs-lookup"><span data-stu-id="aaab6-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="aaab6-104">編譯器會推斷變數的初始化運算式的類型的類型。</span><span class="sxs-lookup"><span data-stu-id="aaab6-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="aaab6-105">這可讓您宣告變數而不用明確陳述的型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aaab6-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="aaab6-106">宣告，因為兩者`num1`和`num2`強型別為整數。</span><span class="sxs-lookup"><span data-stu-id="aaab6-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  <span data-ttu-id="aaab6-107">如果您不想`num2`在上述範例中做為型別`Integer`，您可以使用如下的宣告，以便指定另一個型別`Dim num3 As Object = 3`或`Dim num4 As Double = 3`。</span><span class="sxs-lookup"><span data-stu-id="aaab6-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="aaab6-108">型別推斷僅用於非靜態區域變數;它不能用來判斷類別欄位、 屬性或函式的型別。</span><span class="sxs-lookup"><span data-stu-id="aaab6-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="aaab6-109">區域類型推斷會套用在程序層級。</span><span class="sxs-lookup"><span data-stu-id="aaab6-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="aaab6-110">它不能用來宣告變數，在模組層級 （在類別、 結構、 模組或介面，但不是在程序或區塊）。</span><span class="sxs-lookup"><span data-stu-id="aaab6-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="aaab6-111">如果`num2`在上述範例中的類別，而不是程序中的本機變數的欄位，宣告會導致發生錯誤`Option Strict`，並會分類`num2`作為`Object`與`Option Strict`關閉。</span><span class="sxs-lookup"><span data-stu-id="aaab6-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="aaab6-112">同樣地，區域類型推斷並不適用於程序層級變數宣告為`Static`。</span><span class="sxs-lookup"><span data-stu-id="aaab6-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="aaab6-113">類型推斷 vs。晚期繫結</span><span class="sxs-lookup"><span data-stu-id="aaab6-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="aaab6-114">使用型別推斷的程式碼類似於依賴晚期繫結的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aaab6-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="aaab6-115">不過，類型推斷強型別，而非保留做為變數`Object`。</span><span class="sxs-lookup"><span data-stu-id="aaab6-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="aaab6-116">編譯器會使用變數的初始設定式，以判斷在編譯時期產生早期繫結的程式碼的變數的類型。</span><span class="sxs-lookup"><span data-stu-id="aaab6-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="aaab6-117">在上述範例中， `num2`，例如`num1`，輸入為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="aaab6-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="aaab6-118">早期繫結變數的行為不同於晚期繫結變數，這只能在執行階段已知的型別。</span><span class="sxs-lookup"><span data-stu-id="aaab6-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="aaab6-119">早知道的型別，可讓編譯器執行之前識別問題、 精確地說，配置記憶體，並執行其他最佳化。</span><span class="sxs-lookup"><span data-stu-id="aaab6-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="aaab6-120">早期繫結也可讓 Visual Basic 的整合式的開發環境 (IDE) 的相關物件的成員提供 IntelliSense 協助。</span><span class="sxs-lookup"><span data-stu-id="aaab6-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="aaab6-121">早期繫結也十分適用於效能。</span><span class="sxs-lookup"><span data-stu-id="aaab6-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="aaab6-122">這是因為晚期繫結變數中儲存的所有資料必須為型別都包裝`Object`，並在執行階段存取類型的成員，會讓程式變慢。</span><span class="sxs-lookup"><span data-stu-id="aaab6-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="aaab6-123">範例</span><span class="sxs-lookup"><span data-stu-id="aaab6-123">Examples</span></span>  
 <span data-ttu-id="aaab6-124">而不宣告的區域變數時發生類型推斷`As`子句和初始化。</span><span class="sxs-lookup"><span data-stu-id="aaab6-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="aaab6-125">編譯器會使用指派的起始值的型別，做為變數的類型。</span><span class="sxs-lookup"><span data-stu-id="aaab6-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="aaab6-126">例如，下列程式碼行的每個宣告類型的變數`String`。</span><span class="sxs-lookup"><span data-stu-id="aaab6-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="aaab6-127">下列程式碼示範兩個對等的方式，來建立整數的陣列。</span><span class="sxs-lookup"><span data-stu-id="aaab6-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="aaab6-128">它是方便使用類型推斷來判斷迴圈控制變數的型別。</span><span class="sxs-lookup"><span data-stu-id="aaab6-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="aaab6-129">下列程式碼中，編譯器會推斷所`number`是`Integer`因為`someNumbers2`前一個範例是一個整數的陣列。</span><span class="sxs-lookup"><span data-stu-id="aaab6-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="aaab6-130">區域類型推斷可用於`Using`陳述式來建立的資源名稱，型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aaab6-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="aaab6-131">變數的型別也從函式的傳回值推斷，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aaab6-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="aaab6-132">兩者`pList1`並`pList2`是處理程序的陣列，因為`Process.GetProcesses`傳回處理程序的陣列。</span><span class="sxs-lookup"><span data-stu-id="aaab6-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="aaab6-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="aaab6-133">Option Infer</span></span>  
 <span data-ttu-id="aaab6-134">`Option Infer` 可讓您指定特定的檔案中是否允許區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="aaab6-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="aaab6-135">若要啟用或封鎖選項，請輸入下列陳述式的其中一個，在檔案開頭。</span><span class="sxs-lookup"><span data-stu-id="aaab6-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="aaab6-136">如果您未指定的值`Option Infer`在您的程式碼中，編譯器預設值是`Option Infer On`。</span><span class="sxs-lookup"><span data-stu-id="aaab6-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="aaab6-137">針對從升級的專案[!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)]或更早版本，編譯器預設值是`Option Infer Off`。</span><span class="sxs-lookup"><span data-stu-id="aaab6-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="aaab6-138">如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。</span><span class="sxs-lookup"><span data-stu-id="aaab6-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="aaab6-139">如需詳細資訊，請參閱 < [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)並[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="aaab6-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaab6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaab6-140">See also</span></span>

- [<span data-ttu-id="aaab6-141">匿名類型</span><span class="sxs-lookup"><span data-stu-id="aaab6-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="aaab6-142">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="aaab6-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="aaab6-143">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="aaab6-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="aaab6-144">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="aaab6-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="aaab6-145">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="aaab6-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="aaab6-146">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="aaab6-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="aaab6-147">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="aaab6-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
