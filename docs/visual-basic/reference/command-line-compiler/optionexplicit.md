---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266725"
---
# <a name="-optionexplicit"></a><span data-ttu-id="88b46-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="88b46-102">-optionexplicit</span></span>
<span data-ttu-id="88b46-103">如果變數在使用之前未聲明，則使編譯器報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="88b46-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88b46-104">語法</span><span class="sxs-lookup"><span data-stu-id="88b46-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="88b46-105">引數</span><span class="sxs-lookup"><span data-stu-id="88b46-105">Arguments</span></span>  
 <span data-ttu-id="88b46-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="88b46-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="88b46-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="88b46-107">Optional.</span></span> <span data-ttu-id="88b46-108">指定`-optionexplicit+`以需要顯式聲明變數。</span><span class="sxs-lookup"><span data-stu-id="88b46-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="88b46-109">該`-optionexplicit+`選項為預設值，與`-optionexplicit`相同。</span><span class="sxs-lookup"><span data-stu-id="88b46-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="88b46-110">該`-optionexplicit-`選項支援變數的隱式聲明。</span><span class="sxs-lookup"><span data-stu-id="88b46-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88b46-111">備註</span><span class="sxs-lookup"><span data-stu-id="88b46-111">Remarks</span></span>  
 <span data-ttu-id="88b46-112">如果原始程式碼檔包含[Option 顯式語句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，則語句將覆蓋`-optionexplicit`命令列編譯器設置。</span><span class="sxs-lookup"><span data-stu-id="88b46-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="88b46-113">在視覺化工作室 IDE 中設置 -選項顯式</span><span class="sxs-lookup"><span data-stu-id="88b46-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="88b46-114">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="88b46-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="88b46-115">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88b46-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="88b46-116">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="88b46-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="88b46-117">修改 **"選項顯式"** 框中的值。</span><span class="sxs-lookup"><span data-stu-id="88b46-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b46-118">範例</span><span class="sxs-lookup"><span data-stu-id="88b46-118">Example</span></span>  
 <span data-ttu-id="88b46-119">使用時`-optionexplicit-`編譯以下代碼。</span><span class="sxs-lookup"><span data-stu-id="88b46-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="88b46-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88b46-120">See also</span></span>

- [<span data-ttu-id="88b46-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="88b46-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="88b46-122">-選項比較</span><span class="sxs-lookup"><span data-stu-id="88b46-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="88b46-123">-選項嚴格</span><span class="sxs-lookup"><span data-stu-id="88b46-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="88b46-124">-選項</span><span class="sxs-lookup"><span data-stu-id="88b46-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="88b46-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="88b46-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="88b46-126">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="88b46-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="88b46-127">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="88b46-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
