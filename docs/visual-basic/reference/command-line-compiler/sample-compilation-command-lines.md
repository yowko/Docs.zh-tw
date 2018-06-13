---
title: 編譯命令列範例 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0f1fc1d269801efdbf2e89d10679dc8159851f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653659"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="2d649-102">編譯命令列範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d649-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="2d649-103">Visual Basic 中編譯程式從 Visual Studio 或者，您可以編譯從命令列，以產生可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d649-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="2d649-104">Visual Basic 命令列編譯器支援一組完整的選項來控制輸入和輸出檔案、 組件，以及偵錯和前置處理器選項。</span><span class="sxs-lookup"><span data-stu-id="2d649-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="2d649-105">每個選項可互換的兩種形式：`-option`和`/option`。</span><span class="sxs-lookup"><span data-stu-id="2d649-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="2d649-106">這份文件只會顯示`-option`表單。</span><span class="sxs-lookup"><span data-stu-id="2d649-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="2d649-107">下表列出您可以修改您自己使用的一些範例命令列。</span><span class="sxs-lookup"><span data-stu-id="2d649-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="2d649-108">以</span><span class="sxs-lookup"><span data-stu-id="2d649-108">To</span></span>|<span data-ttu-id="2d649-109">使用</span><span class="sxs-lookup"><span data-stu-id="2d649-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="2d649-110">編譯不能包含 File.vb 並建立 File.exe</span><span class="sxs-lookup"><span data-stu-id="2d649-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="2d649-111">編譯不能包含 File.vb 並建立 File.dll</span><span class="sxs-lookup"><span data-stu-id="2d649-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="2d649-112">編譯不能包含 File.vb 並建立 My.exe</span><span class="sxs-lookup"><span data-stu-id="2d649-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="2d649-113">編譯不能包含 File.vb 並建立名為 File.dll 的參考組件和文件庫</span><span class="sxs-lookup"><span data-stu-id="2d649-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="2d649-114">在編譯所有的 Visual Basic 檔案，在目前目錄中，以最佳化和`DEBUG`產生 File2.exe 定義，符號</span><span class="sxs-lookup"><span data-stu-id="2d649-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="2d649-115">編譯所有在目前目錄中，而不會顯示標誌或警告產生 File2.dll 的偵錯版本的 Visual Basic 檔案</span><span class="sxs-lookup"><span data-stu-id="2d649-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="2d649-116">編譯 Something.dll 目前的目錄中的所有 Visual Basic 檔案</span><span class="sxs-lookup"><span data-stu-id="2d649-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="2d649-117">當您使用 Visual Studio IDE 建置專案時，您可以顯示相關聯的相關資訊**vbc**命令與輸出 視窗中其編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="2d649-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="2d649-118">若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案組建輸出詳細等級**至**一般**或更高的層級的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2d649-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="2d649-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d649-119">See Also</span></span>  
 [<span data-ttu-id="2d649-120">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="2d649-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2d649-121">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="2d649-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
