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
ms.openlocfilehash: a52900f36ee20e827518598a97c7b7f867bd0d43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586822"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="a7a1d-102">Option Explicit 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7a1d-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="a7a1d-103">會強制明確宣告在檔案中，所有變數，或允許隱含宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7a1d-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="a7a1d-105">組件</span><span class="sxs-lookup"><span data-stu-id="a7a1d-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="a7a1d-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-106">Optional.</span></span> <span data-ttu-id="a7a1d-107">可讓`Option Explicit`檢查。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="a7a1d-108">如果`On`或是`Off`未指定，預設值是`On`。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="a7a1d-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-109">Optional.</span></span> <span data-ttu-id="a7a1d-110">停用`Option Explicit`檢查。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7a1d-111">備註</span><span class="sxs-lookup"><span data-stu-id="a7a1d-111">Remarks</span></span>  
 <span data-ttu-id="a7a1d-112">當`Option Explicit On`或是`Option Explicit`會出現在檔案中，您必須使用，以明確地宣告所有變數`Dim`或`ReDim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="a7a1d-113">如果您嘗試使用了未宣告的變數名稱，則會在編譯時期發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="a7a1d-114">`Option Explicit Off`陳述式可讓隱含宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="a7a1d-115">如果使用，`Option Explicit`陳述式必須出現在任何其他來源的程式碼陳述式之前的檔案。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7a1d-116">設定`Option Explicit`至`Off`通常這項操作並不是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="a7a1d-117">一或多個位置中的變數名稱可能有拼字錯誤，這會在程式執行時造成非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="a7a1d-118">當 Option Explicit 陳述式不存在</span><span class="sxs-lookup"><span data-stu-id="a7a1d-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="a7a1d-119">如果原始程式碼不包含`Option Explicit`陳述式中， **Option Explicit**上設定[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="a7a1d-120">如果使用命令列編譯器，則[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)編譯器選項使用。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="a7a1d-121">若要設定在 IDE 中的 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="a7a1d-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="a7a1d-122">在方案總管中選取專案。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="a7a1d-123">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-123">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a7a1d-124">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-124">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="a7a1d-125">在設定的值**Option Explicit**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="a7a1d-126">當您建立新的專案中， **Option Explicit**上設定**編譯**索引標籤設定為**Option Explicit**中設定**VB 預設值** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="a7a1d-127">若要存取**VB 預設值**對話方塊的 **工具**功能表上，按一下 **選項**。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="a7a1d-128">在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="a7a1d-129">中的初始預設設定**VB 預設值**是`On`。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="a7a1d-130">若要設定 命令列上的 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="a7a1d-130">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="a7a1d-131">包含[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)中的編譯器選項**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7a1d-132">範例</span><span class="sxs-lookup"><span data-stu-id="a7a1d-132">Example</span></span>  
 <span data-ttu-id="a7a1d-133">下列範例會使用`Option Explicit`強制明確宣告所有變數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="a7a1d-134">嘗試使用未宣告的變數在編譯時期產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7a1d-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a7a1d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7a1d-135">See also</span></span>
- [<span data-ttu-id="a7a1d-136">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="a7a1d-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="a7a1d-137">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="a7a1d-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="a7a1d-138">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="a7a1d-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="a7a1d-139">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="a7a1d-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="a7a1d-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="a7a1d-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="a7a1d-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="a7a1d-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="a7a1d-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="a7a1d-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="a7a1d-143">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="a7a1d-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
