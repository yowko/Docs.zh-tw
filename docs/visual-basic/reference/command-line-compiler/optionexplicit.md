---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a><span data-ttu-id="0dc3b-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0dc3b-102">/optionexplicit</span></span>
<span data-ttu-id="0dc3b-103">如果變數不宣告在使用前，會導致編譯器錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc3b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0dc3b-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0dc3b-105">引數</span><span class="sxs-lookup"><span data-stu-id="0dc3b-105">Arguments</span></span>  
 <span data-ttu-id="0dc3b-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0dc3b-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="0dc3b-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-107">Optional.</span></span> <span data-ttu-id="0dc3b-108">指定`/optionexplicit+`表示需要明確宣告變數。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="0dc3b-109">`/optionexplicit+`選項是預設值，並與相同`/optionexplicit`。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="0dc3b-110">`/optionexplicit-`選項可讓隱含宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dc3b-111">備註</span><span class="sxs-lookup"><span data-stu-id="0dc3b-111">Remarks</span></span>  
 <span data-ttu-id="0dc3b-112">如果原始程式碼檔內含[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，陳述式會覆寫`/optionexplicit`命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="0dc3b-113">在 Visual Studio IDE 中設定 /optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0dc3b-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="0dc3b-114">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0dc3b-115">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="0dc3b-116">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="0dc3b-117">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="0dc3b-118">修改中的值**Option Explicit**方塊。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dc3b-119">範例</span><span class="sxs-lookup"><span data-stu-id="0dc3b-119">Example</span></span>  
 <span data-ttu-id="0dc3b-120">下列程式碼會編譯時`/optionexplicit-`用。</span><span class="sxs-lookup"><span data-stu-id="0dc3b-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0dc3b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc3b-121">See Also</span></span>  
 [<span data-ttu-id="0dc3b-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0dc3b-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0dc3b-123">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="0dc3b-123">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="0dc3b-124">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="0dc3b-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="0dc3b-125">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="0dc3b-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="0dc3b-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="0dc3b-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0dc3b-127">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="0dc3b-127">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="0dc3b-128">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="0dc3b-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
