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
ms.openlocfilehash: b7879c23bc64269c793c21b61b84d6f0fd4bdc24
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046285"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="80825-102">範例編譯命令列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80825-102">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="80825-103">除了從 Visual Studio 內編譯 Visual Basic 程式以外, 您還可以從命令列進行編譯, 以產生可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案。</span><span class="sxs-lookup"><span data-stu-id="80825-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="80825-104">Visual Basic 命令列編譯器支援一組完整的選項, 可控制輸入和輸出檔案、元件和 debug 和預處理器選項。</span><span class="sxs-lookup"><span data-stu-id="80825-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="80825-105">每個選項都有兩種可交換`-option`的`/option`形式: 和。</span><span class="sxs-lookup"><span data-stu-id="80825-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="80825-106">本檔只`-option`會顯示表單。</span><span class="sxs-lookup"><span data-stu-id="80825-106">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="80825-107">下表列出您可以修改以供自己使用的一些範例命令列。</span><span class="sxs-lookup"><span data-stu-id="80825-107">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="80825-108">以</span><span class="sxs-lookup"><span data-stu-id="80825-108">To</span></span>|<span data-ttu-id="80825-109">使用</span><span class="sxs-lookup"><span data-stu-id="80825-109">Use</span></span>|
|--------|---------|
|<span data-ttu-id="80825-110">編譯 .vb 和 create File .exe</span><span class="sxs-lookup"><span data-stu-id="80825-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="80825-111">編譯 .vb 和 create File .dll</span><span class="sxs-lookup"><span data-stu-id="80825-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="80825-112">編譯 .vb 並建立 My .exe</span><span class="sxs-lookup"><span data-stu-id="80825-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="80825-113">編譯 .vb 並建立名為 File .dll 的程式庫和參考元件</span><span class="sxs-lookup"><span data-stu-id="80825-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="80825-114">編譯目前目錄中的所有 Visual Basic 檔案, 並在其上進行`DEBUG`優化和定義的符號, 產生 File2 .exe</span><span class="sxs-lookup"><span data-stu-id="80825-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="80825-115">編譯目前目錄中的所有 Visual Basic 檔案, 產生 File2 的 debug 版本, 而不顯示標誌或警告</span><span class="sxs-lookup"><span data-stu-id="80825-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="80825-116">將目前目錄中的所有 Visual Basic 檔案編譯為 .dll</span><span class="sxs-lookup"><span data-stu-id="80825-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="80825-117">當您使用 Visual Studio IDE 來建立專案時, 您可以在 [輸出] 視窗中, 使用編譯器選項來顯示相關聯的**vbc**命令資訊。</span><span class="sxs-lookup"><span data-stu-id="80825-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="80825-118">若要顯示這項資訊, 請開啟 [[選項] 對話方塊、[專案和方案]、[建立並執行]](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), 然後將 [ **MSBuild 專案組建輸出詳細**資訊] 設定為 [**一般**] 或更高層級的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="80825-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="80825-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80825-119">See also</span></span>

- [<span data-ttu-id="80825-120">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="80825-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="80825-121">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="80825-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
