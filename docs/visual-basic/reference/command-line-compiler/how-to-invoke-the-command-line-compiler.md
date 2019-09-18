---
title: 作法：叫用命令列編譯器（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: a81d5b4f4eae76b0306e2d27475cb8527bda0ff2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054223"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="dd22c-102">作法：叫用命令列編譯器（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="dd22c-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="dd22c-103">您可以叫用命令列編譯器，方法是在命令列中輸入其可執行檔的名稱，也就是 MS-DOS 提示字元。</span><span class="sxs-lookup"><span data-stu-id="dd22c-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="dd22c-104">如果您從預設的 Windows 命令提示字元進行編譯，則必須輸入可執行檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="dd22c-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="dd22c-105">若要覆寫此預設行為，您可以使用 Visual Studio 的開發人員命令提示字元，或修改 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="dd22c-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="dd22c-106">這兩種方法都可讓您直接輸入編譯器名稱，從任何目錄進行編譯。</span><span class="sxs-lookup"><span data-stu-id="dd22c-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="dd22c-107">若要使用適用于 Visual Studio 的開發人員命令提示字元叫用編譯器</span><span class="sxs-lookup"><span data-stu-id="dd22c-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="dd22c-108">開啟 Microsoft Visual Studio 程式群組內的 [Visual Studio Tools 程式] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd22c-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="dd22c-109">如果安裝 Visual Studio，您可以使用 Visual Studio 的開發人員命令提示字元，從電腦上的任何目錄存取編譯器。</span><span class="sxs-lookup"><span data-stu-id="dd22c-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="dd22c-110">叫用 Visual Studio 的開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dd22c-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="dd22c-111">在命令列中輸入`vbc.exe` *sourceFileName* ，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="dd22c-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="dd22c-112">例如，如果您將原始程式碼儲存在名`SourceFiles`為的目錄中，您會開啟命令提示字元，然後輸入`cd SourceFiles`以變更至該目錄。</span><span class="sxs-lookup"><span data-stu-id="dd22c-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="dd22c-113">如果目錄包含名為`Source.vb`的原始程式檔，您可以輸入`vbc.exe Source.vb`來編譯它。</span><span class="sxs-lookup"><span data-stu-id="dd22c-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="dd22c-114">若要將 PATH 環境變數設定為 Windows 命令提示字元的編譯器</span><span class="sxs-lookup"><span data-stu-id="dd22c-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="dd22c-115">使用 Windows 搜尋功能，在您的本機磁片上尋找 Vbc。</span><span class="sxs-lookup"><span data-stu-id="dd22c-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="dd22c-116">編譯器所在目錄的確切名稱，取決於 Windows 目錄的位置和安裝的「.NET Framework」版本。</span><span class="sxs-lookup"><span data-stu-id="dd22c-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="dd22c-117">如果您已安裝多個版本的「.NET Framework」，您必須決定要使用哪個版本（通常是最新版本）。</span><span class="sxs-lookup"><span data-stu-id="dd22c-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="dd22c-118">在 **開始** 功能表中，以滑鼠右鍵按一下 **我的電腦**，然後從快捷方式功能表按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="dd22c-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="dd22c-119">按一下 [ **Advanced** ] 索引標籤，然後按一下 [**環境變數**]。</span><span class="sxs-lookup"><span data-stu-id="dd22c-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="dd22c-120">在 [**系統**變數] 窗格中，從清單中選取 [**路徑**]，然後按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="dd22c-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="dd22c-121">在 [**編輯系統**變數] 對話方塊中，將插入點移至 [**變數值**] 欄位中的字串結尾，然後輸入分號（;)後面接著在步驟1中找到的完整目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="dd22c-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="dd22c-122">按一下 **[確定]** 以確認您的編輯，並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="dd22c-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="dd22c-123">變更 PATH 環境變數之後，您可以從電腦上的任何目錄，在 Windows 命令提示字元中執行 Visual Basic 編譯器。</span><span class="sxs-lookup"><span data-stu-id="dd22c-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="dd22c-124">使用 Windows 命令提示字元叫用編譯器</span><span class="sxs-lookup"><span data-stu-id="dd22c-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="dd22c-125">在 [**開始**] 功能表中，按一下 [**附屬**應用程式] 資料夾，然後開啟**Windows 命令提示**字元。</span><span class="sxs-lookup"><span data-stu-id="dd22c-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="dd22c-126">在命令列中輸入`vbc.exe` *sourceFileName* ，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="dd22c-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="dd22c-127">例如，如果您將原始程式碼儲存在名`SourceFiles`為的目錄中，您會開啟命令提示字元，然後輸入`cd SourceFiles`以變更至該目錄。</span><span class="sxs-lookup"><span data-stu-id="dd22c-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="dd22c-128">如果目錄包含名為`Source.vb`的原始程式檔，您可以輸入`vbc.exe Source.vb`來編譯它。</span><span class="sxs-lookup"><span data-stu-id="dd22c-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd22c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd22c-129">See also</span></span>

- [<span data-ttu-id="dd22c-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="dd22c-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="dd22c-131">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="dd22c-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
