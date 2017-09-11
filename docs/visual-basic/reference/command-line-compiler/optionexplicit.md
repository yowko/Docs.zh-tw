---
title: "/optionexplicit |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
dev_langs:
- VB
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
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
ms.openlocfilehash: 3d2622c08b863233c8e1088bad252b37b3b38b04
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="optionexplicit"></a><span data-ttu-id="0bdb6-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0bdb6-102">/optionexplicit</span></span>
<span data-ttu-id="0bdb6-103">如果變數不在使用前宣告，請讓編譯器將報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bdb6-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bdb6-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0bdb6-105">引數</span><span class="sxs-lookup"><span data-stu-id="0bdb6-105">Arguments</span></span>  
 <span data-ttu-id="0bdb6-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0bdb6-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="0bdb6-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-107">Optional.</span></span> <span data-ttu-id="0bdb6-108">指定`/optionexplicit+`需要明確宣告變數。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="0bdb6-109">`/optionexplicit+`選項的預設值，而且相同`/optionexplicit`。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="0bdb6-110">`/optionexplicit-`選項可讓隱含宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bdb6-111">備註</span><span class="sxs-lookup"><span data-stu-id="0bdb6-111">Remarks</span></span>  
 <span data-ttu-id="0bdb6-112">如果原始程式碼檔案包含[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，陳述式會覆寫`/optionexplicit`命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="0bdb6-113">在 Visual Studio IDE 中設定 /optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0bdb6-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="0bdb6-114">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0bdb6-115">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="0bdb6-116">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="0bdb6-117">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="0bdb6-118">修改中的值**Option Explicit**方塊。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bdb6-119">範例</span><span class="sxs-lookup"><span data-stu-id="0bdb6-119">Example</span></span>  
 <span data-ttu-id="0bdb6-120">下列程式碼編譯時`/optionexplicit-`用。</span><span class="sxs-lookup"><span data-stu-id="0bdb6-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 <span data-ttu-id="0bdb6-121">[!code-vb[VbVbalrCompiler #&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0bdb6-121">[!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bdb6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bdb6-122">See Also</span></span>  
 <span data-ttu-id="0bdb6-123">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb6-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0bdb6-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb6-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="0bdb6-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb6-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="0bdb6-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb6-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="0bdb6-127"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb6-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="0bdb6-128"> [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0bdb6-128"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="0bdb6-129"> [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="0bdb6-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
