---
title: HOW TO：叫用命令列編譯器 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 78bf5b1f19db3a4f39e263cfd71283f0f7718631
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817177"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="cda37-102">HOW TO：叫用命令列編譯器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda37-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="cda37-103">您可以叫用命令列編譯器，命令列中，也稱為 MS-DOS 命令提示字元中輸入的可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="cda37-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="cda37-104">如果您從預設的 Windows 命令提示字元進行編譯，您必須輸入可執行檔的完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="cda37-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="cda37-105">若要覆寫此預設行為，您可以使用 Visual Studio 中，開發人員命令提示字元，或修改 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="cda37-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="cda37-106">兩者都可讓您只要鍵入編譯器名稱從任何目錄進行編譯。</span><span class="sxs-lookup"><span data-stu-id="cda37-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="cda37-107">若要叫用編譯器使用 for Visual Studio 的開發人員命令提示字元</span><span class="sxs-lookup"><span data-stu-id="cda37-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>  
  
1.  <span data-ttu-id="cda37-108">開啟 Microsoft Visual Studio 程式群組中的 Visual Studio Tools 程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="cda37-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="cda37-109">如果已安裝 Visual Studio，您可以使用 Visual Studio 開發人員命令提示字元存取編譯器從任何目錄，您的電腦。</span><span class="sxs-lookup"><span data-stu-id="cda37-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="cda37-110">叫用 Visual studio 的開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="cda37-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>  
  
4.  <span data-ttu-id="cda37-111">在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="cda37-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="cda37-112">例如，如果您在名為目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元並輸入`cd SourceFiles`變更至該目錄。</span><span class="sxs-lookup"><span data-stu-id="cda37-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="cda37-113">如果目錄包含名為原始程式檔`Source.vb`，您可以輸入來編譯`vbc.exe Source.vb`。</span><span class="sxs-lookup"><span data-stu-id="cda37-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="cda37-114">若要設定 PATH 環境變數，編譯器的 Windows 命令提示字元</span><span class="sxs-lookup"><span data-stu-id="cda37-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="cda37-115">使用 「 Windows Search 」 功能來尋找 Vbc.exe 本機磁碟上。</span><span class="sxs-lookup"><span data-stu-id="cda37-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="cda37-116">編譯器所在的目錄完整名稱是根據 Windows 目錄的位置和 [.NET Framework] 安裝的版本而定。</span><span class="sxs-lookup"><span data-stu-id="cda37-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="cda37-117">如果您有多個版本的 「 安裝的.NET Framework"，您必須決定要使用 （通常是最新版本） 的版本。</span><span class="sxs-lookup"><span data-stu-id="cda37-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="cda37-118">從您**開始** 功能表中，以滑鼠右鍵按一下**我的電腦**，然後按一下**屬性**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="cda37-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="cda37-119">按一下 **進階**索引標籤，然後再按一下**環境變數**。</span><span class="sxs-lookup"><span data-stu-id="cda37-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="cda37-120">在 **系統**變數窗格中，選取**路徑**從清單，然後按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="cda37-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="cda37-121">在 **編輯系統**變數對話方塊中，將插入點移至 在字串結尾**變數值**欄位並輸入分號 （;） 後面接著在步驟 1 中找到完整的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="cda37-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="cda37-122">按一下 **確定**，確認您的編輯，並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cda37-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="cda37-123">變更 PATH 環境變數之後，您可以執行 Visual Basic 編譯器在 Windows 命令提示字元從任何目錄電腦上。</span><span class="sxs-lookup"><span data-stu-id="cda37-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="cda37-124">若要叫用編譯器使用 Windows 命令提示字元</span><span class="sxs-lookup"><span data-stu-id="cda37-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="cda37-125">從**開始**功能表，然後按一下**附屬應用程式**資料夾，然後再開啟**Windows 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="cda37-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="cda37-126">在命令列中，輸入`vbc.exe` *sourceFileName*然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="cda37-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="cda37-127">例如，如果您在名為目錄中儲存您的原始程式碼`SourceFiles`，您會開啟命令提示字元並輸入`cd SourceFiles`變更至該目錄。</span><span class="sxs-lookup"><span data-stu-id="cda37-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="cda37-128">如果目錄包含名為原始程式檔`Source.vb`，您可以輸入來編譯`vbc.exe Source.vb`。</span><span class="sxs-lookup"><span data-stu-id="cda37-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda37-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cda37-129">See also</span></span>

- [<span data-ttu-id="cda37-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="cda37-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cda37-131">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="cda37-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
