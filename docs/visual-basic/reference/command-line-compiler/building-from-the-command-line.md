---
title: 從命令列建置 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 89bcd6e0e7c1cc867bf853dc9bbe96628942ace2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542267"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="64b5b-102">從命令列建置 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64b5b-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="64b5b-103">Visual Basic 專案組成的一或多個不同的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="64b5b-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="64b5b-104">在稱為編譯過程中，這些檔案會結合成一個套件，可以為應用程式執行單一可執行檔。</span><span class="sxs-lookup"><span data-stu-id="64b5b-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="64b5b-105">Visual Basic 提供的命令列編譯器作為從 Visual Studio 整合式的開發環境 (IDE) 內編譯程式的替代方案。</span><span class="sxs-lookup"><span data-stu-id="64b5b-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="64b5b-106">命令列編譯器專為您在不需要完整的 IDE 功能的情況下 — 比方說，當您使用或撰寫具有有限的系統記憶體或儲存體空間的電腦。</span><span class="sxs-lookup"><span data-stu-id="64b5b-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="64b5b-107">若要編譯原始程式檔從 Visual Studio IDE 中的，選擇**建置**命令**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="64b5b-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="64b5b-108">當您使用 Visual Studio IDE 建置專案檔時，您可以顯示相關聯的相關資訊**vbc**命令和其參數，在 [輸出] 視窗中的。</span><span class="sxs-lookup"><span data-stu-id="64b5b-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="64b5b-109">若要顯示這項資訊，請開啟[選項對話方塊、 專案和解決方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後將**MSBuild 專案建置輸出詳細等級**來**一般**或較高層級的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="64b5b-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="64b5b-110">如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](https://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)。</span><span class="sxs-lookup"><span data-stu-id="64b5b-110">For more information, see [How to: View, Save, and Configure Build Log Files](https://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="64b5b-111">您可以使用 MSBuild 編譯專案 (.vbproj) 檔，在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="64b5b-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="64b5b-112">如需詳細資訊，請參閱 <<c0> [ 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)並[逐步解說： 使用 MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild)。</span><span class="sxs-lookup"><span data-stu-id="64b5b-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64b5b-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="64b5b-113">In This Section</span></span>  
 [<span data-ttu-id="64b5b-114">操作說明：叫用命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="64b5b-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="64b5b-115">描述如何叫用命令列編譯器在 MS-DOS 命令提示字元，或從特定的子目錄。</span><span class="sxs-lookup"><span data-stu-id="64b5b-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="64b5b-116">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="64b5b-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="64b5b-117">提供一份您可以修改供自己使用的範例命令列。</span><span class="sxs-lookup"><span data-stu-id="64b5b-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="64b5b-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="64b5b-118">Related Sections</span></span>  
 [<span data-ttu-id="64b5b-119">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="64b5b-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="64b5b-120">提供編譯器選項，依字母順序或依用途組織的清單。</span><span class="sxs-lookup"><span data-stu-id="64b5b-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="64b5b-121">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="64b5b-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="64b5b-122">說明如何編譯的程式碼的特定區段。</span><span class="sxs-lookup"><span data-stu-id="64b5b-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="64b5b-123">在 Visual Studio 中建置和清除專案與方案</span><span class="sxs-lookup"><span data-stu-id="64b5b-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="64b5b-124">描述如何組織功能將會包含在不同的組建，選擇 專案屬性，並且確認專案建置正確的順序。</span><span class="sxs-lookup"><span data-stu-id="64b5b-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
