---
title: "Option Infer 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement
- Infer keyword
- declaring variables, inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 56c2813f0fcfc23c4eb4039ffbbb1d9deeccb72c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="option-infer-statement"></a><span data-ttu-id="415ff-102">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="415ff-102">Option Infer Statement</span></span>
<span data-ttu-id="415ff-103">可讓您在宣告變數時使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="415ff-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="415ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="415ff-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="415ff-105">組件</span><span class="sxs-lookup"><span data-stu-id="415ff-105">Parts</span></span>  
  
|<span data-ttu-id="415ff-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="415ff-106">Term</span></span>|<span data-ttu-id="415ff-107">定義</span><span class="sxs-lookup"><span data-stu-id="415ff-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="415ff-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="415ff-108">Optional.</span></span> <span data-ttu-id="415ff-109">啟用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="415ff-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="415ff-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="415ff-110">Optional.</span></span> <span data-ttu-id="415ff-111">停用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="415ff-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="415ff-112">備註</span><span class="sxs-lookup"><span data-stu-id="415ff-112">Remarks</span></span>  
 <span data-ttu-id="415ff-113">若要在檔案中設定 `Option Infer`，請在檔案頂端的任何其他原始程式碼之前輸入 `Option Infer On` 或 `Option Infer Off`。</span><span class="sxs-lookup"><span data-stu-id="415ff-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="415ff-114">如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。</span><span class="sxs-lookup"><span data-stu-id="415ff-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="415ff-115">當您將 `Option Infer` 設定為 `On` 時，可以宣告區域變數而不用明確陳述資料類型。</span><span class="sxs-lookup"><span data-stu-id="415ff-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="415ff-116">編譯器會從其初始化運算式的類型推斷變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="415ff-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="415ff-117">在下圖中，`Option Infer` 已開啟。</span><span class="sxs-lookup"><span data-stu-id="415ff-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="415ff-118">宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為整數。</span><span class="sxs-lookup"><span data-stu-id="415ff-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="415ff-119">![宣告的 IntelliSense 檢視。](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="415ff-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="415ff-120">Option Infer 開啟時的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="415ff-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="415ff-121">在下圖中，`Option Infer` 已關閉。</span><span class="sxs-lookup"><span data-stu-id="415ff-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="415ff-122">宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="415ff-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="415ff-123">在此範例中， **Option Strict**設定設為**關閉**上[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="415ff-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="415ff-124">![宣告的 IntelliSense 檢視。](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="415ff-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="415ff-125">Option Infer 關閉時的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="415ff-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="415ff-126">當變數被宣告為 `Object` 時，執行階段類型可以在程式執行時變更。</span><span class="sxs-lookup"><span data-stu-id="415ff-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="415ff-127">執行作業呼叫*boxing*和*unboxing*之間進行轉換`Object`和數值型別，使得執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="415ff-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="415ff-128">Boxing 和 unboxing 的相關資訊，請參閱[Visual Basic 語言規格](../../../visual-basic/reference/language-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="415ff-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).</span></span>  
  
 <span data-ttu-id="415ff-129">類型推斷會套用在程序層級，不會套用在類別、結構、模組或介面中的程序之外。</span><span class="sxs-lookup"><span data-stu-id="415ff-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="415ff-130">如需詳細資訊，請參閱[本機的型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="415ff-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="415ff-131">Option Infer 陳述式不存在時</span><span class="sxs-lookup"><span data-stu-id="415ff-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="415ff-132">如果原始程式碼不包含`Option Infer`陳述式， **Option Infer**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="415ff-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="415ff-133">使用命令列編譯器時，如果[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)編譯器選項使用。</span><span class="sxs-lookup"><span data-stu-id="415ff-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="415ff-134">在 IDE 中設定 Option Infer</span><span class="sxs-lookup"><span data-stu-id="415ff-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="415ff-135">在**方案總管 中**，選取專案。</span><span class="sxs-lookup"><span data-stu-id="415ff-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="415ff-136">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="415ff-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="415ff-137">如需詳細資訊，請參閱[NIB︰ 使用專案設計工具管理專案屬性](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)。</span><span class="sxs-lookup"><span data-stu-id="415ff-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="415ff-138">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="415ff-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="415ff-139">在設定的值**Option infer**方塊。</span><span class="sxs-lookup"><span data-stu-id="415ff-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="415ff-140">當您建立新的專案， **Option Infer**上設定**編譯** 索引標籤設為**Option Infer**中設定**VB 預設值**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="415ff-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="415ff-141">若要存取**VB 預設值**對話方塊的 **工具** 功能表上，按一下 **選項**。</span><span class="sxs-lookup"><span data-stu-id="415ff-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="415ff-142">在**選項**對話方塊方塊中，展開**專案和方案**，然後按一下  **VB 預設值**。</span><span class="sxs-lookup"><span data-stu-id="415ff-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="415ff-143">中的初始預設設定**VB 預設值**是`On`。</span><span class="sxs-lookup"><span data-stu-id="415ff-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="415ff-144">在命令列上設定 Option Infer</span><span class="sxs-lookup"><span data-stu-id="415ff-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="415ff-145">包含[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)編譯器選項，在**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="415ff-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="415ff-146">預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="415ff-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="415ff-147">下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。</span><span class="sxs-lookup"><span data-stu-id="415ff-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="415ff-148">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="415ff-148">Data type specified?</span></span>|<span data-ttu-id="415ff-149">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="415ff-149">Initializer specified?</span></span>|<span data-ttu-id="415ff-150">範例</span><span class="sxs-lookup"><span data-stu-id="415ff-150">Example</span></span>|<span data-ttu-id="415ff-151">結果</span><span class="sxs-lookup"><span data-stu-id="415ff-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="415ff-152">否</span><span class="sxs-lookup"><span data-stu-id="415ff-152">No</span></span>|<span data-ttu-id="415ff-153">否</span><span class="sxs-lookup"><span data-stu-id="415ff-153">No</span></span>|`Dim qty`|<span data-ttu-id="415ff-154">如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="415ff-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="415ff-155">如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="415ff-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="415ff-156">否</span><span class="sxs-lookup"><span data-stu-id="415ff-156">No</span></span>|<span data-ttu-id="415ff-157">是</span><span class="sxs-lookup"><span data-stu-id="415ff-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="415ff-158">如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="415ff-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="415ff-159">請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="415ff-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="415ff-160">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="415ff-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="415ff-161">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="415ff-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="415ff-162">是</span><span class="sxs-lookup"><span data-stu-id="415ff-162">Yes</span></span>|<span data-ttu-id="415ff-163">否</span><span class="sxs-lookup"><span data-stu-id="415ff-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="415ff-164">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="415ff-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="415ff-165">如需詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="415ff-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="415ff-166">是</span><span class="sxs-lookup"><span data-stu-id="415ff-166">Yes</span></span>|<span data-ttu-id="415ff-167">是</span><span class="sxs-lookup"><span data-stu-id="415ff-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="415ff-168">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="415ff-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="415ff-169">範例</span><span class="sxs-lookup"><span data-stu-id="415ff-169">Example</span></span>  
 <span data-ttu-id="415ff-170">下列範例示範 `Option Infer` 陳述式如何啟用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="415ff-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 <span data-ttu-id="415ff-171">[!code-vb[VbVbalrTypeInference #&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="415ff-171">[!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="415ff-172">範例</span><span class="sxs-lookup"><span data-stu-id="415ff-172">Example</span></span>  
 <span data-ttu-id="415ff-173">下列範例示範當變數被視為 `Object` 時，執行階段類型可能會不同。</span><span class="sxs-lookup"><span data-stu-id="415ff-173">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 <span data-ttu-id="415ff-174">[!code-vb[VbVbalrTypeInference #&11;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="415ff-174">[!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415ff-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="415ff-175">See Also</span></span>  
 <span data-ttu-id="415ff-176">[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="415ff-176">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="415ff-177"> [區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="415ff-177"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="415ff-178"> [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="415ff-178"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="415ff-179"> [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="415ff-179"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="415ff-180"> [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="415ff-180"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="415ff-181"> [Visual Basic 預設值，專案選項對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span><span class="sxs-lookup"><span data-stu-id="415ff-181"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span></span>  
<span data-ttu-id="415ff-182"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="415ff-182"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="415ff-183"> [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)</span><span class="sxs-lookup"><span data-stu-id="415ff-183"> [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)</span></span>
