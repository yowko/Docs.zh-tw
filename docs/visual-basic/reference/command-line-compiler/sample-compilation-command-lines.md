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
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824296"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="7e62a-102">編譯命令列範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e62a-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="7e62a-103">為編譯 Visual Basic 程式從 Visual Studio 內的替代方法，您可以編譯從命令列來產生可執行檔 (.exe) 檔案或動態連結程式庫 (.dll) 檔案。</span><span class="sxs-lookup"><span data-stu-id="7e62a-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="7e62a-104">Visual Basic 命令列編譯器支援一組完整的選項來控制輸入和輸出檔案、 組件，以及偵錯和前置處理器選項。</span><span class="sxs-lookup"><span data-stu-id="7e62a-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="7e62a-105">每個選項是可互換的兩種形式：`-option`和`/option`。</span><span class="sxs-lookup"><span data-stu-id="7e62a-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="7e62a-106">此文件只說明`-option`表單。</span><span class="sxs-lookup"><span data-stu-id="7e62a-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="7e62a-107">下表列出一些您可以修改供自己使用的範例命令列。</span><span class="sxs-lookup"><span data-stu-id="7e62a-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="7e62a-108">以</span><span class="sxs-lookup"><span data-stu-id="7e62a-108">To</span></span>|<span data-ttu-id="7e62a-109">使用</span><span class="sxs-lookup"><span data-stu-id="7e62a-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="7e62a-110">編譯 File.vb 並建立 File.exe</span><span class="sxs-lookup"><span data-stu-id="7e62a-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="7e62a-111">編譯 File.vb 並建立 file.dll 的 File.cs</span><span class="sxs-lookup"><span data-stu-id="7e62a-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="7e62a-112">編譯 File.vb 並建立 My.exe</span><span class="sxs-lookup"><span data-stu-id="7e62a-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="7e62a-113">編譯 File.vb 和建立文件庫和名為 file.dll 的 File.cs 參考組件</span><span class="sxs-lookup"><span data-stu-id="7e62a-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="7e62a-114">在編譯所有的 Visual Basic 檔案，在目前目錄中，以最佳化和`DEBUG`符號定義，產生 File2.exe</span><span class="sxs-lookup"><span data-stu-id="7e62a-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="7e62a-115">編譯產生 File2.dll 偵錯版本，而不會顯示標誌或警告的目前目錄中的所有 Visual Basic 檔案</span><span class="sxs-lookup"><span data-stu-id="7e62a-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="7e62a-116">編譯 Something.dll 目前的目錄中的所有 Visual Basic 檔案</span><span class="sxs-lookup"><span data-stu-id="7e62a-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="7e62a-117">當您使用 Visual Studio IDE 建置專案時，您可以顯示相關聯的相關資訊**vbc**命令搭配其編譯器選項，在 [輸出] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="7e62a-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="7e62a-118">若要顯示這項資訊，請開啟[選項對話方塊、 專案和解決方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後將**MSBuild 專案建置輸出詳細等級**來**一般**或較高層級的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7e62a-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="7e62a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e62a-119">See also</span></span>

- [<span data-ttu-id="7e62a-120">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="7e62a-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7e62a-121">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="7e62a-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
