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
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005313"
---
# <a name="-optionexplicit"></a><span data-ttu-id="5a145-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5a145-102">-optionexplicit</span></span>
<span data-ttu-id="5a145-103">如果變數在使用之前未宣告，則會導致編譯器報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a145-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a145-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a145-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5a145-105">引數</span><span class="sxs-lookup"><span data-stu-id="5a145-105">Arguments</span></span>  
 <span data-ttu-id="5a145-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5a145-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="5a145-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5a145-107">Optional.</span></span> <span data-ttu-id="5a145-108">指定 `-optionexplicit+` 則需要明確宣告變數。</span><span class="sxs-lookup"><span data-stu-id="5a145-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="5a145-109">@No__t-0 選項是預設值，而且與 `-optionexplicit` 相同。</span><span class="sxs-lookup"><span data-stu-id="5a145-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="5a145-110">@No__t-0 選項可啟用變數的隱含宣告。</span><span class="sxs-lookup"><span data-stu-id="5a145-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a145-111">備註</span><span class="sxs-lookup"><span data-stu-id="5a145-111">Remarks</span></span>  
 <span data-ttu-id="5a145-112">如果原始程式碼檔包含[Option Explicit 語句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，則語句會覆寫 `-optionexplicit` 命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="5a145-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="5a145-113">若要在 Visual Studio IDE 中設定-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5a145-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="5a145-114">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="5a145-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5a145-115">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="5a145-115">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="5a145-116">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5a145-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="5a145-117">修改 [選項] [**明確**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="5a145-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a145-118">範例</span><span class="sxs-lookup"><span data-stu-id="5a145-118">Example</span></span>  
 <span data-ttu-id="5a145-119">當使用 `-optionexplicit-` 時，下列程式碼會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="5a145-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5a145-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a145-120">See also</span></span>

- [<span data-ttu-id="5a145-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="5a145-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5a145-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="5a145-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="5a145-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="5a145-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="5a145-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="5a145-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="5a145-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="5a145-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="5a145-126">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="5a145-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="5a145-127">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="5a145-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
