---
title: "Option 明確陳述式 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
dev_langs:
- VB
helpviewer_keywords:
- declaring variables, explicit
- forced variable declaration in Option Explicit statement
- Explicit keyword
- explicit variable declaration
- Option Explicit statement
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
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
ms.openlocfilehash: 4283599d9ed2ad9075ab0b2f404f1a12a31437ec
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="afe14-102">Option Explicit 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afe14-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="afe14-103">會強制明確宣告所有變數在檔案中，或允許隱含宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="afe14-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe14-104">語法</span><span class="sxs-lookup"><span data-stu-id="afe14-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="afe14-105">組件</span><span class="sxs-lookup"><span data-stu-id="afe14-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="afe14-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="afe14-106">Optional.</span></span> <span data-ttu-id="afe14-107">可讓`Option Explicit`檢查。</span><span class="sxs-lookup"><span data-stu-id="afe14-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="afe14-108">如果`On`或`Off`未指定，預設值是`On`。</span><span class="sxs-lookup"><span data-stu-id="afe14-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="afe14-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="afe14-109">Optional.</span></span> <span data-ttu-id="afe14-110">停用`Option Explicit`檢查。</span><span class="sxs-lookup"><span data-stu-id="afe14-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afe14-111">備註</span><span class="sxs-lookup"><span data-stu-id="afe14-111">Remarks</span></span>  
 <span data-ttu-id="afe14-112">當`Option Explicit On`或`Option Explicit`會出現在檔案中，您必須使用明確宣告所有變數`Dim`或`ReDim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="afe14-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="afe14-113">如果您嘗試使用未宣告的變數名稱，則會在編譯時期發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="afe14-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="afe14-114">`Option Explicit Off`陳述式允許隱含宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="afe14-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="afe14-115">如果使用`Option Explicit`陳述式必須出現在任何其他來源的程式碼陳述式之前的檔案。</span><span class="sxs-lookup"><span data-stu-id="afe14-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afe14-116">設定`Option Explicit`至`Off`通常不是比較好的作法。</span><span class="sxs-lookup"><span data-stu-id="afe14-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="afe14-117">您可能拼錯的變數名稱在一個或多個位置，程式執行時，會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="afe14-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="afe14-118">當 Option Explicit 陳述式不存在</span><span class="sxs-lookup"><span data-stu-id="afe14-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="afe14-119">如果原始程式碼不包含`Option Explicit`陳述式， **Option Explicit**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="afe14-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="afe14-120">使用命令列編譯器時，如果[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)編譯器選項使用。</span><span class="sxs-lookup"><span data-stu-id="afe14-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="afe14-121">若要在 IDE 中設定 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="afe14-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="afe14-122">在**方案總管 中**，選取專案。</span><span class="sxs-lookup"><span data-stu-id="afe14-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="afe14-123">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="afe14-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="afe14-124">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="afe14-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="afe14-125">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="afe14-125">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="afe14-126">在設定的值**Option Explicit**方塊。</span><span class="sxs-lookup"><span data-stu-id="afe14-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="afe14-127">當您建立新的專案， **Option Explicit**上設定**編譯** 索引標籤設為**Option Explicit**中設定**VB 預設值**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="afe14-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="afe14-128">若要存取**VB 預設值**對話方塊的 **工具** 功能表上，按一下 **選項**。</span><span class="sxs-lookup"><span data-stu-id="afe14-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="afe14-129">在**選項**對話方塊方塊中，展開**專案和方案**，然後按一下  **VB 預設值**。</span><span class="sxs-lookup"><span data-stu-id="afe14-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="afe14-130">中的初始預設設定**VB 預設值**是`On`。</span><span class="sxs-lookup"><span data-stu-id="afe14-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="afe14-131">若要命令列上設定 Option Explicit</span><span class="sxs-lookup"><span data-stu-id="afe14-131">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="afe14-132">包含[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)編譯器選項，在**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="afe14-132">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afe14-133">範例</span><span class="sxs-lookup"><span data-stu-id="afe14-133">Example</span></span>  
 <span data-ttu-id="afe14-134">下列範例會使用`Option Explicit`強制明確宣告所有變數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="afe14-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="afe14-135">嘗試使用未宣告的變數在編譯時期會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="afe14-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 <span data-ttu-id="afe14-136">[!code-vb[VbVbalrStatements #&47;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="afe14-136">[!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="afe14-137">[!code-vb[VbVbalrStatements #&48;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="afe14-137">[!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe14-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afe14-138">See Also</span></span>  
 <span data-ttu-id="afe14-139">[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="afe14-139">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="afe14-140"> [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="afe14-140"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="afe14-141"> [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="afe14-141"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="afe14-142"> [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="afe14-142"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="afe14-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="afe14-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="afe14-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="afe14-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="afe14-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="afe14-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="afe14-146"> [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="afe14-146"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
