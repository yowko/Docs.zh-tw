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
ms.openlocfilehash: 4aca6e9c20dbce7aa8a94067c96fcf44329a6fe4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814870"
---
# <a name="-optionexplicit"></a><span data-ttu-id="b3d46-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="b3d46-102">-optionexplicit</span></span>
<span data-ttu-id="b3d46-103">如果變數未宣告在使用前，會導致編譯器報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3d46-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d46-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3d46-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3d46-105">引數</span><span class="sxs-lookup"><span data-stu-id="b3d46-105">Arguments</span></span>  
 <span data-ttu-id="b3d46-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b3d46-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="b3d46-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b3d46-107">Optional.</span></span> <span data-ttu-id="b3d46-108">指定`-optionexplicit+`表示需要明確宣告變數。</span><span class="sxs-lookup"><span data-stu-id="b3d46-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="b3d46-109">`-optionexplicit+`選項是預設值，並與相同`-optionexplicit`。</span><span class="sxs-lookup"><span data-stu-id="b3d46-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="b3d46-110">`-optionexplicit-`選項可讓隱含宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="b3d46-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3d46-111">備註</span><span class="sxs-lookup"><span data-stu-id="b3d46-111">Remarks</span></span>  
 <span data-ttu-id="b3d46-112">如果原始程式碼檔中包含[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，此陳述式會覆寫`-optionexplicit`命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="b3d46-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="b3d46-113">若要在 Visual Studio IDE 中設定-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="b3d46-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="b3d46-114">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="b3d46-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b3d46-115">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b3d46-115">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="b3d46-116">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b3d46-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="b3d46-117">修改中的值**Option Explicit**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="b3d46-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3d46-118">範例</span><span class="sxs-lookup"><span data-stu-id="b3d46-118">Example</span></span>  
 <span data-ttu-id="b3d46-119">下列程式碼會編譯時`-optionexplicit-`用。</span><span class="sxs-lookup"><span data-stu-id="b3d46-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b3d46-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3d46-120">See also</span></span>

- [<span data-ttu-id="b3d46-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="b3d46-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b3d46-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="b3d46-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="b3d46-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="b3d46-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="b3d46-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="b3d46-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="b3d46-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="b3d46-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="b3d46-126">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="b3d46-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="b3d46-127">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="b3d46-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
