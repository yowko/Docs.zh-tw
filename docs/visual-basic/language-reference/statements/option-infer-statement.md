---
title: Option Infer 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: f5c824df43997282d50c9c2a458fb1d854cc160a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672581"
---
# <a name="option-infer-statement"></a><span data-ttu-id="f3ae9-102">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="f3ae9-102">Option Infer Statement</span></span>
<span data-ttu-id="f3ae9-103">可讓您在宣告變數時使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ae9-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3ae9-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="f3ae9-105">組件</span><span class="sxs-lookup"><span data-stu-id="f3ae9-105">Parts</span></span>  
  
|<span data-ttu-id="f3ae9-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f3ae9-106">Term</span></span>|<span data-ttu-id="f3ae9-107">定義</span><span class="sxs-lookup"><span data-stu-id="f3ae9-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="f3ae9-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-108">Optional.</span></span> <span data-ttu-id="f3ae9-109">啟用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="f3ae9-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-110">Optional.</span></span> <span data-ttu-id="f3ae9-111">停用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3ae9-112">備註</span><span class="sxs-lookup"><span data-stu-id="f3ae9-112">Remarks</span></span>  
 <span data-ttu-id="f3ae9-113">若要在檔案中設定 `Option Infer`，請在檔案頂端的任何其他原始程式碼之前輸入 `Option Infer On` 或 `Option Infer Off`。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="f3ae9-114">如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="f3ae9-115">當您將 `Option Infer` 設定為 `On` 時，可以宣告區域變數而不用明確陳述資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="f3ae9-116">編譯器會從其初始化運算式的類型推斷變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="f3ae9-117">在下圖中，`Option Infer` 已開啟。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="f3ae9-118">宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為整數。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="f3ae9-119">![宣告的 IntelliSense 檢視。](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="f3ae9-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="f3ae9-120">Option Infer 開啟時的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f3ae9-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="f3ae9-121">在下圖中，`Option Infer` 已關閉。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="f3ae9-122">宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="f3ae9-123">在此範例中， **Option Strict**設定設為**Off**上[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="f3ae9-124">![宣告的 IntelliSense 檢視。](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="f3ae9-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="f3ae9-125">Option Infer 關閉時的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f3ae9-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3ae9-126">當變數被宣告為 `Object` 時，執行階段類型可以在程式執行時變更。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="f3ae9-127">Visual Basic 執行呼叫的作業*boxing*並*unboxing*之間進行轉換`Object`和實值類型，可讓執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="f3ae9-128">如需 boxing 和 unboxing 的詳細資訊，請參閱[Visual Basic 語言規格](../../../visual-basic/reference/language-specification/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="f3ae9-129">類型推斷會套用在程序層級，不會套用在類別、結構、模組或介面中的程序之外。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="f3ae9-130">如需詳細資訊，請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="f3ae9-131">Option Infer 陳述式不存在時</span><span class="sxs-lookup"><span data-stu-id="f3ae9-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="f3ae9-132">如果原始程式碼不包含`Option Infer`陳述式中， **Option Infer**上設定[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="f3ae9-133">如果使用命令列編譯器，則[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)編譯器選項使用。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="f3ae9-134">在 IDE 中設定 Option Infer</span><span class="sxs-lookup"><span data-stu-id="f3ae9-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="f3ae9-135">在方案總管中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="f3ae9-136">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-136">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f3ae9-137">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-137">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="f3ae9-138">在設定的值**Option infer**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="f3ae9-139">當您建立新的專案中， **Option Infer**上設定**編譯**索引標籤設定為**Option Infer**中設定**VB 預設值** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="f3ae9-140">若要存取**VB 預設值**對話方塊的 **工具**功能表上，按一下 **選項**。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="f3ae9-141">在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="f3ae9-142">中的初始預設設定**VB 預設值**是`On`。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="f3ae9-143">在命令列上設定 Option Infer</span><span class="sxs-lookup"><span data-stu-id="f3ae9-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="f3ae9-144">包含[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)中的編譯器選項**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="f3ae9-145">預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="f3ae9-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="f3ae9-146">下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="f3ae9-147">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="f3ae9-147">Data type specified?</span></span>|<span data-ttu-id="f3ae9-148">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="f3ae9-148">Initializer specified?</span></span>|<span data-ttu-id="f3ae9-149">範例</span><span class="sxs-lookup"><span data-stu-id="f3ae9-149">Example</span></span>|<span data-ttu-id="f3ae9-150">結果</span><span class="sxs-lookup"><span data-stu-id="f3ae9-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="f3ae9-151">否</span><span class="sxs-lookup"><span data-stu-id="f3ae9-151">No</span></span>|<span data-ttu-id="f3ae9-152">否</span><span class="sxs-lookup"><span data-stu-id="f3ae9-152">No</span></span>|`Dim qty`|<span data-ttu-id="f3ae9-153">如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="f3ae9-154">如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="f3ae9-155">否</span><span class="sxs-lookup"><span data-stu-id="f3ae9-155">No</span></span>|<span data-ttu-id="f3ae9-156">是</span><span class="sxs-lookup"><span data-stu-id="f3ae9-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="f3ae9-157">如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="f3ae9-158">請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="f3ae9-159">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="f3ae9-160">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="f3ae9-161">是</span><span class="sxs-lookup"><span data-stu-id="f3ae9-161">Yes</span></span>|<span data-ttu-id="f3ae9-162">否</span><span class="sxs-lookup"><span data-stu-id="f3ae9-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="f3ae9-163">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="f3ae9-164">如需詳細資訊，請參閱 < [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="f3ae9-165">是</span><span class="sxs-lookup"><span data-stu-id="f3ae9-165">Yes</span></span>|<span data-ttu-id="f3ae9-166">是</span><span class="sxs-lookup"><span data-stu-id="f3ae9-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="f3ae9-167">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3ae9-168">範例</span><span class="sxs-lookup"><span data-stu-id="f3ae9-168">Example</span></span>  
 <span data-ttu-id="f3ae9-169">下列範例示範 `Option Infer` 陳述式如何啟用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="f3ae9-170">範例</span><span class="sxs-lookup"><span data-stu-id="f3ae9-170">Example</span></span>  
 <span data-ttu-id="f3ae9-171">下列範例示範當變數被視為 `Object` 時，執行階段類型可能會不同。</span><span class="sxs-lookup"><span data-stu-id="f3ae9-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f3ae9-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3ae9-172">See Also</span></span>  
 [<span data-ttu-id="f3ae9-173">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="f3ae9-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="f3ae9-174">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="f3ae9-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="f3ae9-175">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="f3ae9-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="f3ae9-176">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="f3ae9-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="f3ae9-177">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="f3ae9-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="f3ae9-178">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="f3ae9-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="f3ae9-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="f3ae9-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="f3ae9-180">Boxing 和 Unboxing</span><span class="sxs-lookup"><span data-stu-id="f3ae9-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
