---
title: "區域型別推斷 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- local type inference
- vb.TypeInfer
dev_langs:
- VB
helpviewer_keywords:
- Option Infer statement
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: af8de63eb00db917771600f0fca8f200ec451afe
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="efb7a-102">區域類型推斷 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efb7a-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="efb7a-103">Visual Basic 編譯器會使用*型別推斷*來判斷資料類型的未宣告的區域變數`As`子句。</span><span class="sxs-lookup"><span data-stu-id="efb7a-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="efb7a-104">編譯器會推斷變數的初始化運算式的型別類型。</span><span class="sxs-lookup"><span data-stu-id="efb7a-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="efb7a-105">這可讓您宣告變數而不用明確陳述的型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="efb7a-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="efb7a-106">由於宣告，兩者`num1`和`num2`強型別為整數。</span><span class="sxs-lookup"><span data-stu-id="efb7a-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 <span data-ttu-id="efb7a-107">[!code-vb[VbVbalrTypeInference #&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="efb7a-107">[!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efb7a-108">如果您不想`num2`型別為前一個範例中`Integer`，您可以使用如下的宣告，以指定另一個型別`Dim num3 As Object = 3`或`Dim num4 As Double = 3`。</span><span class="sxs-lookup"><span data-stu-id="efb7a-108">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  
  
 <span data-ttu-id="efb7a-109">區域型別推斷會套用在程序層級。</span><span class="sxs-lookup"><span data-stu-id="efb7a-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="efb7a-110">它不能用來宣告在模組層級 （類別、 結構、 模組或介面中，但不是在程序或區塊內） 變數。</span><span class="sxs-lookup"><span data-stu-id="efb7a-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="efb7a-111">如果`num2`前一個範例中的類別，而非區域變數的程序中的欄位，宣告會導致發生錯誤`Option Strict`，並會分類`num2`為`Object`與`Option Strict`關閉。</span><span class="sxs-lookup"><span data-stu-id="efb7a-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="efb7a-112">同樣地，區域型別推斷並不適用於程序層級變數宣告為`Static`。</span><span class="sxs-lookup"><span data-stu-id="efb7a-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="efb7a-113">類型推斷 vs。晚期繫結</span><span class="sxs-lookup"><span data-stu-id="efb7a-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="efb7a-114">使用型別推斷的程式碼類似於仰賴晚期繫結的程式碼。</span><span class="sxs-lookup"><span data-stu-id="efb7a-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="efb7a-115">不過，型別推斷強型別，而非保留做為變數`Object`。</span><span class="sxs-lookup"><span data-stu-id="efb7a-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="efb7a-116">編譯器會使用變數的初始設定式，判斷變數的型別在編譯時期產生早期繫結的程式碼。</span><span class="sxs-lookup"><span data-stu-id="efb7a-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="efb7a-117">在上述範例中，`num2`一樣`num1`，型別為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="efb7a-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="efb7a-118">早期繫結變數的行為與不同的晚期繫結變數，只能在執行階段的已知型別。</span><span class="sxs-lookup"><span data-stu-id="efb7a-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="efb7a-119">早知道的型別，可讓編譯器在執行之前識別問題、 準確配置記憶體，並執行其他最佳化。</span><span class="sxs-lookup"><span data-stu-id="efb7a-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="efb7a-120">早期繫結也可讓 Visual Basic 的整合式的開發環境 (IDE) 提供 IntelliSense 協助提供物件的成員。</span><span class="sxs-lookup"><span data-stu-id="efb7a-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="efb7a-121">早期繫結也是慣用的效能。</span><span class="sxs-lookup"><span data-stu-id="efb7a-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="efb7a-122">這是因為必須包裝晚期繫結變數中儲存的所有資料類型為`Object`，並在執行階段存取型別的成員，會讓程式變慢。</span><span class="sxs-lookup"><span data-stu-id="efb7a-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="efb7a-123">範例</span><span class="sxs-lookup"><span data-stu-id="efb7a-123">Examples</span></span>  
 <span data-ttu-id="efb7a-124">本機變數宣告沒有時，就會發生型別推斷`As`子句和初始化。</span><span class="sxs-lookup"><span data-stu-id="efb7a-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="efb7a-125">編譯器會使用指派的起始值的型別做為變數的類型。</span><span class="sxs-lookup"><span data-stu-id="efb7a-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="efb7a-126">例如，下列程式碼行中每個宣告型別的變數`String`。</span><span class="sxs-lookup"><span data-stu-id="efb7a-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 <span data-ttu-id="efb7a-127">[!code-vb[VbVbalrTypeInference #&2;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="efb7a-127">[!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]</span></span>  
  
 <span data-ttu-id="efb7a-128">下列程式碼示範兩個對等的方式建立整數的陣列。</span><span class="sxs-lookup"><span data-stu-id="efb7a-128">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 <span data-ttu-id="efb7a-129">[!code-vb[VbVbalrTypeInference #&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="efb7a-129">[!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]</span></span>  
  
 <span data-ttu-id="efb7a-130">很方便地使用型別推斷來判斷迴圈控制變數的型別。</span><span class="sxs-lookup"><span data-stu-id="efb7a-130">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="efb7a-131">下列程式碼中，編譯器會推斷，`number`是`Integer`因為`someNumbers2`前一個範例是整數的陣列。</span><span class="sxs-lookup"><span data-stu-id="efb7a-131">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 <span data-ttu-id="efb7a-132">[!code-vb[VbVbalrTypeInference #&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="efb7a-132">[!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]</span></span>  
  
 <span data-ttu-id="efb7a-133">區域型別推斷可以用於`Using`陳述式來建立資源名稱的型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="efb7a-133">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 <span data-ttu-id="efb7a-134">[!code-vb[VbVbalrTypeInference #&7;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="efb7a-134">[!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]</span></span>  
  
 <span data-ttu-id="efb7a-135">變數的型別也從函式的傳回值推斷，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="efb7a-135">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="efb7a-136">同時`pList1`和`pList2`是處理程序的陣列，因為`Process.GetProcesses`傳回處理程序的陣列。</span><span class="sxs-lookup"><span data-stu-id="efb7a-136">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 <span data-ttu-id="efb7a-137">[!code-vb[VbVbalrTypeInference #&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="efb7a-137">[!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]</span></span>  
  
## <a name="option-infer"></a><span data-ttu-id="efb7a-138">Option Infer</span><span class="sxs-lookup"><span data-stu-id="efb7a-138">Option Infer</span></span>  
 <span data-ttu-id="efb7a-139">`Option Infer`可讓您指定特定的檔案中是否允許區域型別推斷。</span><span class="sxs-lookup"><span data-stu-id="efb7a-139">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="efb7a-140">若要啟用或封鎖選項，請輸入下列陳述式的其中一個檔案的開頭。</span><span class="sxs-lookup"><span data-stu-id="efb7a-140">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="efb7a-141">如果您未指定的值`Option Infer`在您的程式碼的編譯器預設值是`Option Infer On`。</span><span class="sxs-lookup"><span data-stu-id="efb7a-141">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="efb7a-142">從專案升級為[!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)]或更早版本，編譯器預設值是`Option Infer Off`。</span><span class="sxs-lookup"><span data-stu-id="efb7a-142">For projects upgraded from [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="efb7a-143">如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。</span><span class="sxs-lookup"><span data-stu-id="efb7a-143">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="efb7a-144">如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="efb7a-144">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="efb7a-145">限制</span><span class="sxs-lookup"><span data-stu-id="efb7a-145">Restrictions</span></span>  
 <span data-ttu-id="efb7a-146">型別推斷只能用於非靜態區域變數。它不能用來判斷類別欄位、 屬性或函式的型別。</span><span class="sxs-lookup"><span data-stu-id="efb7a-146">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb7a-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efb7a-147">See Also</span></span>  
 <span data-ttu-id="efb7a-148">[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="efb7a-148">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="efb7a-149"> [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span><span class="sxs-lookup"><span data-stu-id="efb7a-149"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span></span>  
<span data-ttu-id="efb7a-150"> [每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="efb7a-150"> [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="efb7a-151"> [For...下一個陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="efb7a-151"> [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="efb7a-152"> [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="efb7a-152"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="efb7a-153"> [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="efb7a-153"> [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="efb7a-154"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="efb7a-154"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
