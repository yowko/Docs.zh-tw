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
# <a name="-optionexplicit"></a><span data-ttu-id="6444a-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="6444a-102">-optionexplicit</span></span>
<span data-ttu-id="6444a-103">如果變數在使用之前未宣告，則會導致編譯器報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="6444a-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6444a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6444a-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6444a-105">引數</span><span class="sxs-lookup"><span data-stu-id="6444a-105">Arguments</span></span>  
 <span data-ttu-id="6444a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="6444a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="6444a-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6444a-107">Optional.</span></span> <span data-ttu-id="6444a-108">指定`-optionexplicit+` ，以要求明確宣告變數。</span><span class="sxs-lookup"><span data-stu-id="6444a-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="6444a-109">`-optionexplicit+`選項是預設值，而且與相同`-optionexplicit`。</span><span class="sxs-lookup"><span data-stu-id="6444a-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="6444a-110">`-optionexplicit-`選項會啟用變數的隱含宣告。</span><span class="sxs-lookup"><span data-stu-id="6444a-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6444a-111">備註</span><span class="sxs-lookup"><span data-stu-id="6444a-111">Remarks</span></span>  
 <span data-ttu-id="6444a-112">如果原始程式碼檔案包含[Option Explicit 語句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，則語句會覆寫`-optionexplicit`命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="6444a-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="6444a-113">若要在 Visual Studio IDE 中設定-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="6444a-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="6444a-114">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="6444a-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6444a-115">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6444a-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="6444a-116">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6444a-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="6444a-117">修改 [選項] [**明確**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="6444a-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6444a-118">範例</span><span class="sxs-lookup"><span data-stu-id="6444a-118">Example</span></span>  
 <span data-ttu-id="6444a-119">使用時`-optionexplicit-` ，下列程式碼會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="6444a-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6444a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6444a-120">See also</span></span>

- [<span data-ttu-id="6444a-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="6444a-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6444a-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="6444a-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="6444a-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="6444a-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="6444a-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="6444a-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="6444a-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="6444a-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="6444a-126">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="6444a-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="6444a-127">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="6444a-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
