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
ms.openlocfilehash: 719ca45403ea56a655f06dbfea7c0fb7e32b34f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046434"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="3839c-102">從命令列建置 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3839c-102">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="3839c-103">Visual Basic 專案是由一或多個不同的原始檔所組成。</span><span class="sxs-lookup"><span data-stu-id="3839c-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="3839c-104">在稱為編譯的程式期間, 這些檔案會結合成一個套件, 也就是可當做應用程式執行的單一可執行檔。</span><span class="sxs-lookup"><span data-stu-id="3839c-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="3839c-105">Visual Basic 提供命令列編譯器, 做為從 Visual Studio 整合式開發環境 (IDE) 中編譯器的替代方法。</span><span class="sxs-lookup"><span data-stu-id="3839c-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="3839c-106">命令列編譯器是針對您不需要 IDE 中完整功能集的情況所設計, 例如, 當您針對系統記憶體或儲存空間有限的電腦使用或寫入時。</span><span class="sxs-lookup"><span data-stu-id="3839c-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="3839c-107">若要從 Visual Studio IDE 內編譯來源檔案, 請從 [**組建**] 功能表選擇 [**組建**] 命令。</span><span class="sxs-lookup"><span data-stu-id="3839c-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="3839c-108">當您使用 Visual Studio IDE 來建立專案檔時, 可以在 [輸出] 視窗中顯示相關聯的**vbc**命令及其參數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3839c-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="3839c-109">若要顯示這項資訊, 請開啟 [[選項] 對話方塊、[專案和方案]、[建立並執行]](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), 然後將 [ **MSBuild 專案組建輸出詳細**資訊] 設定為 [**一般**] 或更高層級的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3839c-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="3839c-110">如需詳細資訊，請參閱[如何：查看、儲存和設定組建記錄](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)檔。</span><span class="sxs-lookup"><span data-stu-id="3839c-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="3839c-111">您可以在命令提示字元中使用 MSBuild 來編譯專案 (. vbproj) 檔案。</span><span class="sxs-lookup"><span data-stu-id="3839c-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="3839c-112">如需詳細資訊, 請參閱[命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)和[逐步解說:使用 MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild)。</span><span class="sxs-lookup"><span data-stu-id="3839c-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3839c-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="3839c-113">In This Section</span></span>

<span data-ttu-id="3839c-114">[如何：叫用命令列編譯器](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="3839c-114">[How to: Invoke the Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="3839c-115">描述如何在 MS-DOS 提示字元或從特定子目錄叫用命令列編譯器。</span><span class="sxs-lookup"><span data-stu-id="3839c-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="3839c-116">[範例編譯命令列](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="3839c-116">[Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="3839c-117">提供範例命令列清單, 您可以針對自己的用途加以修改。</span><span class="sxs-lookup"><span data-stu-id="3839c-117">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="3839c-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="3839c-118">Related Sections</span></span>

<span data-ttu-id="3839c-119">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="3839c-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>\
<span data-ttu-id="3839c-120">提供編譯器選項清單, 以字母順序或依目的組織。</span><span class="sxs-lookup"><span data-stu-id="3839c-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="3839c-121">[條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="3839c-121">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="3839c-122">描述如何編譯器代碼的特定區段。</span><span class="sxs-lookup"><span data-stu-id="3839c-122">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="3839c-123">[在 Visual Studio 中建置和清除專案與方案](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="3839c-123">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span></span>\
<span data-ttu-id="3839c-124">描述如何組織將包含在不同組建中的內容、選擇專案屬性, 並確保專案以正確的順序建立。</span><span class="sxs-lookup"><span data-stu-id="3839c-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
