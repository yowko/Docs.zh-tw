---
title: Option Explicit 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 44bf8205ec071710ee3660968ab3c3e9af33f74d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874941"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="bd992-102">Option Explicit 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd992-102">Option Explicit Statement (Visual Basic)</span></span>

<span data-ttu-id="bd992-103">強制明確宣告檔案中的所有變數，或允許變數的隱含宣告。</span><span class="sxs-lookup"><span data-stu-id="bd992-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd992-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bd992-104">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="bd992-105">組件</span><span class="sxs-lookup"><span data-stu-id="bd992-105">Parts</span></span>  

 `On`  
 <span data-ttu-id="bd992-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd992-106">Optional.</span></span> <span data-ttu-id="bd992-107">啟用 `Option Explicit` 檢查。</span><span class="sxs-lookup"><span data-stu-id="bd992-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="bd992-108">如果 `On` `Off` 未指定或，則預設值為 `On` 。</span><span class="sxs-lookup"><span data-stu-id="bd992-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="bd992-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd992-109">Optional.</span></span> <span data-ttu-id="bd992-110">停用 `Option Explicit` 檢查。</span><span class="sxs-lookup"><span data-stu-id="bd992-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd992-111">備註</span><span class="sxs-lookup"><span data-stu-id="bd992-111">Remarks</span></span>  

 <span data-ttu-id="bd992-112">當 `Option Explicit On` 或 `Option Explicit` 出現在檔案中時，您必須使用或語句來明確宣告所有變數 `Dim` `ReDim` 。</span><span class="sxs-lookup"><span data-stu-id="bd992-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="bd992-113">如果您嘗試使用未宣告的變數名稱，則會在編譯時期發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bd992-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="bd992-114">`Option Explicit Off`語句允許變數的隱含宣告。</span><span class="sxs-lookup"><span data-stu-id="bd992-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="bd992-115">如果使用的話， `Option Explicit` 語句必須出現在檔案中的任何其他原始程式碼語句之前。</span><span class="sxs-lookup"><span data-stu-id="bd992-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd992-116">將設定 `Option Explicit` 為 `Off` 通常不是理想的作法。</span><span class="sxs-lookup"><span data-stu-id="bd992-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="bd992-117">一或多個位置中的變數名稱可能有拼字錯誤，這會在程式執行時造成非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="bd992-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="bd992-118">當選項明確語句不存在時</span><span class="sxs-lookup"><span data-stu-id="bd992-118">When an Option Explicit Statement Is Not Present</span></span>  

 <span data-ttu-id="bd992-119">如果原始程式碼不包含 `Option Explicit` 語句，則會使用 [編譯] 頁面上的 [ **明確** 設定] [、[專案設計工具] (Visual Basic) ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 。</span><span class="sxs-lookup"><span data-stu-id="bd992-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="bd992-120">如果使用命令列編譯器，則會使用 [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="bd992-120">If the command-line compiler is used, the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="bd992-121">在 IDE 中設定 Explicit 選項</span><span class="sxs-lookup"><span data-stu-id="bd992-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="bd992-122">在 **方案總管**中，選取專案。</span><span class="sxs-lookup"><span data-stu-id="bd992-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="bd992-123">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="bd992-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="bd992-124">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bd992-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="bd992-125">在 [ **選項明確** ] 方塊中設定值。</span><span class="sxs-lookup"><span data-stu-id="bd992-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="bd992-126">當您建立新專案時，[**編譯**] 索引標籤上的**選項明確**設定會設定為 [ **VB 預設值**] 對話方塊中的 [明確設定]**選項**。</span><span class="sxs-lookup"><span data-stu-id="bd992-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="bd992-127">若要存取 [ **VB 預設值** ] 對話方塊，請按一下 [ **工具** ] 功能表上的 [ **選項**]。</span><span class="sxs-lookup"><span data-stu-id="bd992-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="bd992-128">在 [選項]\*\*\*\* 對話方塊中，展開 [專案和方案]\*\*\*\*，然後按一下 [VB 預設值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd992-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="bd992-129">**VB**的初始預設設定為 `On` 。</span><span class="sxs-lookup"><span data-stu-id="bd992-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="bd992-130">若要在命令列上設定 Explicit 選項</span><span class="sxs-lookup"><span data-stu-id="bd992-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="bd992-131">在**vbc**命令中包含[-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="bd992-131">Include the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd992-132">範例</span><span class="sxs-lookup"><span data-stu-id="bd992-132">Example</span></span>  

 <span data-ttu-id="bd992-133">下列範例會使用 `Option Explicit` 語句來強制明確宣告所有變數。</span><span class="sxs-lookup"><span data-stu-id="bd992-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="bd992-134">嘗試使用未宣告的變數會導致編譯時期發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bd992-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="bd992-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd992-135">See also</span></span>

- [<span data-ttu-id="bd992-136">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="bd992-136">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="bd992-137">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="bd992-137">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="bd992-138">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="bd992-138">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="bd992-139">Long</span><span class="sxs-lookup"><span data-stu-id="bd992-139">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="bd992-140">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="bd992-140">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="bd992-141">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="bd992-141">-optionexplicit</span></span>](../../reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="bd992-142">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="bd992-142">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="bd992-143">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="bd992-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
