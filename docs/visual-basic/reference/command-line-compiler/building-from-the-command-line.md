---
title: "從命令列 (Visual Basic) 建置 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e7550a4a54637ea5ef425a1cb7ae02abd07808a8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="7e594-102">從命令列建置 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e594-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="7e594-103">A[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案由一或多個不同的原始程式檔所組成。</span><span class="sxs-lookup"><span data-stu-id="7e594-103">A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project is made up of one or more separate source files.</span></span> <span data-ttu-id="7e594-104">在稱為編譯過程中，這些檔案組成成一個套件，可以為應用程式執行單一可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7e594-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="7e594-105">提供命令列編譯器編譯程式從替代[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="7e594-105"> provides a command-line compiler as an alternative to compiling programs from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] integrated development environment (IDE).</span></span> <span data-ttu-id="7e594-106">命令列編譯器設計成供您在不需要完整的 IDE 功能 — 例如，當您要使用還是寫入電腦具有有限的系統記憶體或儲存體空間。</span><span class="sxs-lookup"><span data-stu-id="7e594-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
 <span data-ttu-id="7e594-107">當從命令列進行編譯，您必須明確參考 Microsoft[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]透過執行階段程式庫`/reference`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="7e594-107">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
 <span data-ttu-id="7e594-108">若要編譯原始程式檔內[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]IDE 中，選擇 **建置**命令**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="7e594-108">To compile source files from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="7e594-109">當您使用 Visual Studio IDE 建置專案檔時，您可以顯示相關聯的相關資訊**vbc**命令，並在 [輸出] 視窗中的，其參數。</span><span class="sxs-lookup"><span data-stu-id="7e594-109">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="7e594-110">若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案建置輸出詳細程度**至**正常**或更高的層級的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7e594-110">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="7e594-111">如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)。</span><span class="sxs-lookup"><span data-stu-id="7e594-111">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="7e594-112">您可以使用 MSBuild 編譯專案 (.vbproj) 檔案，在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7e594-112">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="7e594-113">如需詳細資訊，請參閱[命令列參考](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)和[逐步解說︰ 使用 MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310)。</span><span class="sxs-lookup"><span data-stu-id="7e594-113">For more information, see [Command-Line Reference](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e594-114">本章節內容</span><span class="sxs-lookup"><span data-stu-id="7e594-114">In This Section</span></span>  
 [<span data-ttu-id="7e594-115">如何：叫用命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="7e594-115">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="7e594-116">說明如何叫用命令列編譯器在 MS-DOS 命令提示字元，或從特定的子目錄。</span><span class="sxs-lookup"><span data-stu-id="7e594-116">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="7e594-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="7e594-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="7e594-118">提供命令列範例，您可以修改供自己使用的清單。</span><span class="sxs-lookup"><span data-stu-id="7e594-118">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7e594-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="7e594-119">Related Sections</span></span>  
 [<span data-ttu-id="7e594-120">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="7e594-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="7e594-121">提供依字母順序或依用途的編譯器選項的清單。</span><span class="sxs-lookup"><span data-stu-id="7e594-121">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="7e594-122">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="7e594-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="7e594-123">描述如何編譯程式碼的特定區段。</span><span class="sxs-lookup"><span data-stu-id="7e594-123">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="7e594-124">在 Visual Studio 中建置和清除專案與方案</span><span class="sxs-lookup"><span data-stu-id="7e594-124">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="7e594-125">描述如何組織將會包含在不同的組建，選擇 專案屬性，以及確保以正確的順序建置專案。</span><span class="sxs-lookup"><span data-stu-id="7e594-125">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
