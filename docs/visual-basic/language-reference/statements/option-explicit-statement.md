---
title: Option Explicit 陳述式 (Visual Basic)
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
ms.openlocfilehash: c027964d185d7f69c0a56a4386bedc2d8f9d2eac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912341"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="3d9ac-102">Option Explicit 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d9ac-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="3d9ac-103">強制明確宣告檔案中的所有變數, 或允許變數的隱含宣告。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d9ac-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="3d9ac-105">組件</span><span class="sxs-lookup"><span data-stu-id="3d9ac-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="3d9ac-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-106">Optional.</span></span> <span data-ttu-id="3d9ac-107">啟用`Option Explicit`檢查。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="3d9ac-108">如果`On`未`Off`指定或, 則預設值為`On`。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="3d9ac-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-109">Optional.</span></span> <span data-ttu-id="3d9ac-110">停`Option Explicit`用檢查。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d9ac-111">備註</span><span class="sxs-lookup"><span data-stu-id="3d9ac-111">Remarks</span></span>  
 <span data-ttu-id="3d9ac-112">當`Option Explicit On`或`Option Explicit`出現在檔案中時, 您必須使用`Dim`或`ReDim`語句來明確宣告所有變數。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="3d9ac-113">如果您嘗試使用未宣告的變數名稱, 則會在編譯時期發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="3d9ac-114">`Option Explicit Off`語句允許隱含宣告變數。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="3d9ac-115">如果使用的話, `Option Explicit`語句必須出現在檔案中的任何其他原始程式碼語句之前。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d9ac-116">將`Option Explicit`設定`Off`為通常不是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="3d9ac-117">一或多個位置中的變數名稱可能有拼字錯誤，這會在程式執行時造成非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="3d9ac-118">當 Option Explicit 語句不存在時</span><span class="sxs-lookup"><span data-stu-id="3d9ac-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="3d9ac-119">如果原始程式碼不包含`Option Explicit`語句, 則會使用 [編譯] 頁面上的 [ **Option Explicit** ] 設定 ([專案設計工具] [(Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="3d9ac-120">如果使用命令列編譯器, 則會使用[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="3d9ac-121">若要在 IDE 中設定 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="3d9ac-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="3d9ac-122">在方案總管中選取專案。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="3d9ac-123">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="3d9ac-124">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="3d9ac-125">在 [**選項明確**] 方塊中設定值。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="3d9ac-126">當您建立新的專案時, [**編譯**] 索引標籤上的 [ **option explicit** ] 設定會設定為 [ **VB 預設值**] 對話方塊中的 [ **option explicit** ] 設定。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="3d9ac-127">若要存取 [ **VB 預設值**] 對話方塊, 請在 [**工具**] 功能表上按一下 [**選項**]。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="3d9ac-128">在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="3d9ac-129">**VB 預設值**中的初始預設設定`On`為。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="3d9ac-130">若要在命令列上設定 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="3d9ac-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="3d9ac-131">在**vbc**命令中包含[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d9ac-132">範例</span><span class="sxs-lookup"><span data-stu-id="3d9ac-132">Example</span></span>  
 <span data-ttu-id="3d9ac-133">下列範例會使用`Option Explicit`語句來強制執行所有變數的明確宣告。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="3d9ac-134">嘗試使用未宣告的變數會在編譯時期導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d9ac-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="3d9ac-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d9ac-135">See also</span></span>

- [<span data-ttu-id="3d9ac-136">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d9ac-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="3d9ac-137">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d9ac-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="3d9ac-138">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d9ac-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="3d9ac-139">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d9ac-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="3d9ac-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="3d9ac-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="3d9ac-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="3d9ac-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="3d9ac-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="3d9ac-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="3d9ac-143">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="3d9ac-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
