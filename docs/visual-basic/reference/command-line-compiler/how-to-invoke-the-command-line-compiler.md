---
title: "如何：叫用命令列編譯器 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c69860ede5620272e67bde435e6e6fa08cc81bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="1dd8f-102">如何：叫用命令列編譯器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dd8f-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="1dd8f-103">您可以在命令列中，也稱為 MS-DOS 命令提示字元中輸入可執行檔的名稱來叫用命令列編譯器。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="1dd8f-104">如果您從預設 Windows 命令提示字元進行編譯，您必須輸入的可執行檔的完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="1dd8f-105">若要覆寫此預設行為，您可以使用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]命令提示字元，或修改的 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-105">To override this default behavior, you can either use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt, or modify the PATH environment variable.</span></span> <span data-ttu-id="1dd8f-106">兩者都可讓您只要輸入編譯器名稱從任何目錄進行編譯。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a><span data-ttu-id="1dd8f-107">要叫用編譯器使用 Visual Studio 命令提示字元</span><span class="sxs-lookup"><span data-stu-id="1dd8f-107">To invoke the compiler using the Visual Studio Command Prompt</span></span>  
  
1.  <span data-ttu-id="1dd8f-108">開啟 Microsoft Visual Studio 程式群組中的 Visual Studio Tools 程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="1dd8f-109">您可以使用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]編譯器存取從您的電腦上的任何目錄，如果在安裝 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-109">You can use the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="1dd8f-110">叫用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-110">Invoke the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
4.  <span data-ttu-id="1dd8f-111">在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="1dd8f-112">例如，如果您呼叫的目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元，然後輸入`cd SourceFiles`變更到該目錄。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="1dd8f-113">如果目錄包含原始程式檔名為`Source.vb`，您無法編譯，則輸入`vbc.exe Source.vb`。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="1dd8f-114">編譯器的 Windows 命令提示字元中設定的 PATH 環境變數</span><span class="sxs-lookup"><span data-stu-id="1dd8f-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="1dd8f-115">使用 「 Windows 搜尋 」 功能來尋找 Vbc.exe 本機磁碟上。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="1dd8f-116">編譯器所在的目錄完整名稱取決於 Windows 目錄的位置和 <.NET Framework > 安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="1dd8f-117">如果您有多個版本的 <.NET Framework > 安裝，您必須決定要使用 （通常是最新版本） 的版本。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="1dd8f-118">從您**啟動**功能表上，以滑鼠右鍵按一下**我的電腦**，然後按一下 **屬性**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="1dd8f-119">按一下**進階**索引標籤，然後再按一下**環境變數**。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="1dd8f-120">在**系統**變數窗格中，選取**路徑**從清單按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="1dd8f-121">在**編輯系統**變數對話方塊中，將插入點移至在字串結尾**變數值**欄位並輸入分號 （;） 後面的步驟 1 中的完整目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="1dd8f-122">按一下**確定**確認您的編輯，並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="1dd8f-123">變更 PATH 環境變數之後，您可以執行[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器在 Windows 命令提示字元，從任何電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-123">After you change the PATH environment variable, you can run the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="1dd8f-124">要叫用編譯器使用 Windows 命令提示字元</span><span class="sxs-lookup"><span data-stu-id="1dd8f-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="1dd8f-125">從**啟動**功能表，然後按一下**附屬應用程式**資料夾，然後再開啟**Windows 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="1dd8f-126">在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="1dd8f-127">例如，如果您呼叫的目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元，然後輸入`cd SourceFiles`變更到該目錄。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="1dd8f-128">如果目錄包含原始程式檔名為`Source.vb`，您無法編譯，則輸入`vbc.exe Source.vb`。</span><span class="sxs-lookup"><span data-stu-id="1dd8f-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd8f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd8f-129">See Also</span></span>  
 [<span data-ttu-id="1dd8f-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="1dd8f-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1dd8f-131">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="1dd8f-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
