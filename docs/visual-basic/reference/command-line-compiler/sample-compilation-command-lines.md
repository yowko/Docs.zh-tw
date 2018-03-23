---
title: 編譯命令列範例 (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7c3fac318e05c5e3d6fb9dd7117cac70ead03dc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="72edd-102">編譯命令列範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72edd-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="72edd-103">做為編譯替代[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式從[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]，您可以從命令列，以產生可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案進行編譯。</span><span class="sxs-lookup"><span data-stu-id="72edd-103">As an alternative to compiling [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs from within [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="72edd-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]命令列編譯器支援一組完整的選項來控制輸入和輸出檔案、 組件，以及偵錯和前置處理器選項。</span><span class="sxs-lookup"><span data-stu-id="72edd-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="72edd-105">每個選項可互換的兩種形式：`-option`和`/option`。</span><span class="sxs-lookup"><span data-stu-id="72edd-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="72edd-106">這份文件只會顯示`-option`表單。</span><span class="sxs-lookup"><span data-stu-id="72edd-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="72edd-107">下表列出您可以修改您自己使用的一些範例命令列。</span><span class="sxs-lookup"><span data-stu-id="72edd-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="72edd-108">以</span><span class="sxs-lookup"><span data-stu-id="72edd-108">To</span></span>|<span data-ttu-id="72edd-109">使用</span><span class="sxs-lookup"><span data-stu-id="72edd-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="72edd-110">編譯不能包含 File.vb 並建立 File.exe</span><span class="sxs-lookup"><span data-stu-id="72edd-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="72edd-111">編譯不能包含 File.vb 並建立 File.dll</span><span class="sxs-lookup"><span data-stu-id="72edd-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="72edd-112">編譯不能包含 File.vb 並建立 My.exe</span><span class="sxs-lookup"><span data-stu-id="72edd-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="72edd-113">所有編譯[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]檔案在目前目錄中，以最佳化和`DEBUG`產生 File2.exe 定義，符號</span><span class="sxs-lookup"><span data-stu-id="72edd-113">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="72edd-114">所有編譯[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]在目前目錄中，而不會顯示標誌或警告產生 File2.dll 的偵錯版本的檔案</span><span class="sxs-lookup"><span data-stu-id="72edd-114">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="72edd-115">所有編譯[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Something.dll 目前的目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="72edd-115">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
 <span data-ttu-id="72edd-116">當從命令列編譯時，您必須明確參考 Microsoft[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]透過執行階段程式庫`-reference`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="72edd-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] run-time library through the `-reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="72edd-117">當您使用 Visual Studio IDE 建置專案時，您可以顯示相關聯的相關資訊**vbc**命令與輸出 視窗中其編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="72edd-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="72edd-118">若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案組建輸出詳細等級**至**一般**或更高的層級的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="72edd-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="72edd-119">如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)。</span><span class="sxs-lookup"><span data-stu-id="72edd-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72edd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72edd-120">See Also</span></span>  
 [<span data-ttu-id="72edd-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="72edd-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="72edd-122">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="72edd-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
