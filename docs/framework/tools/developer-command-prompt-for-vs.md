---
title: Visual Studio 的開發人員命令提示字元
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715876"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="a5935-102">Visual Studio 的開發人員命令提示字元</span><span class="sxs-lookup"><span data-stu-id="a5935-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="a5935-103">Visual Studio 的開發人員命令提示允許您更輕鬆地使用 .NET 框架工具。</span><span class="sxs-lookup"><span data-stu-id="a5935-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="a5935-104">它是自動設置特定環境變數的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a5935-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="a5935-105">打開開發人員命令提示符後，可以輸入[.NET 框架工具](index.md)的命令，如`ildasm``clrver`或 。</span><span class="sxs-lookup"><span data-stu-id="a5935-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5935-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="a5935-106">Prerequisites</span></span>

- [<span data-ttu-id="a5935-107">視覺工作室 2019</span><span class="sxs-lookup"><span data-stu-id="a5935-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="a5935-108">搜尋您電腦上的命令提示字元</span><span class="sxs-lookup"><span data-stu-id="a5935-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="a5935-109">您可能有多個命令提示，具體取決於 Visual Studio 的版本以及已安裝的任何其他 SDK 和工作負載。</span><span class="sxs-lookup"><span data-stu-id="a5935-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="a5935-110">如果以下步驟不起作用，您可以嘗試[手動查找電腦上的檔](#manually-locate-the-files-on-your-machine)，或[從 Visual Studio 內部啟動命令提示](#start-the-command-prompt-from-inside-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="a5935-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="a5935-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a5935-111">Windows 10</span></span>

1. <span data-ttu-id="a5935-112">選擇鍵盤上的 **"開始**![視窗"徽標鍵。](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="a5935-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="a5935-113">並滾動到字母**V**。</span><span class="sxs-lookup"><span data-stu-id="a5935-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="a5935-114">展開**視覺化工作室 2019**資料夾。</span><span class="sxs-lookup"><span data-stu-id="a5935-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="a5935-115">為**VS 2019 選擇開發人員命令提示**（或要使用的命令提示）。</span><span class="sxs-lookup"><span data-stu-id="a5935-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="a5935-116">或者，您可以在工作列上的搜索框中開始鍵入命令提示符的名稱，並在結果清單開始顯示搜索匹配項時選擇所需的結果。</span><span class="sxs-lookup"><span data-stu-id="a5935-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![顯示 Windows 10 上的搜索行為的動畫 gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="a5935-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a5935-118">Windows 8.1</span></span>

1. <span data-ttu-id="a5935-119">按下 Windows 標誌鍵 ![鍵盤上的 Windows 標誌鍵](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 前往 [開始]\*\*\*\* 畫面。</span><span class="sxs-lookup"><span data-stu-id="a5935-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="a5935-120">位於您的鍵盤上，作為範例。</span><span class="sxs-lookup"><span data-stu-id="a5935-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="a5935-121">在 **"開始"** 螢幕上，**按"Ctrl"**+**選項卡**打開 **"應用"** 清單，然後按**V**。這將顯示一個清單，其中包含所有已安裝的 Visual Studio 命令提示。</span><span class="sxs-lookup"><span data-stu-id="a5935-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="a5935-122">為**VS 2019 選擇開發人員命令提示**（或要使用的命令提示）。</span><span class="sxs-lookup"><span data-stu-id="a5935-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="a5935-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a5935-123">Windows 7</span></span>

1. <span data-ttu-id="a5935-124">選擇 **"開始"，** 然後展開**所有程式**。</span><span class="sxs-lookup"><span data-stu-id="a5935-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="a5935-125">選擇**Visual Studio 2019** > **視覺化工作室工具** > **開發人員命令提示符 VS 2019**，或要使用的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a5935-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Windows 7 啟動功能表，命令提示符突出顯示](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="a5935-127">如果安裝了其他 SDK，如[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)或[以前的版本](https://developer.microsoft.com/windows/downloads/sdk-archive)，您可能會看到其他命令提示。</span><span class="sxs-lookup"><span data-stu-id="a5935-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="a5935-128">查看個別工具的文件以判斷要使用哪個版本的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a5935-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="a5935-129">以手動方式尋找您電腦上的檔案</span><span class="sxs-lookup"><span data-stu-id="a5935-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="a5935-130">通常，已安裝的命令提示的快捷方式將放置在 Visual Studio 的 **"開始功能表"** 資料夾中，例如*在 %程式資料%*Microsoft_Windows_開始功能表\程式\Visual Studio 2019_Visual Studio 工具\*中。</span><span class="sxs-lookup"><span data-stu-id="a5935-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="a5935-131">但是，如果由於某種原因搜索命令提示未產生預期結果，則可以嘗試手動查找電腦上的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="a5935-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="a5935-132">嘗試搜索命令提示檔的名稱，如*VsDevCmd.bat*， 或轉到"工具"資料夾，例如 *%程式檔 （x86）%_Microsoft Visual Studio_2019_社區\通用7\工具*（路徑會根據您的 Visual Studio 版本、版本和安裝位置更改）。</span><span class="sxs-lookup"><span data-stu-id="a5935-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="a5935-133">從視覺化工作室內部啟動命令提示</span><span class="sxs-lookup"><span data-stu-id="a5935-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="a5935-134">為了便於訪問，您可以將開發人員命令提示符或任何其他命令提示符添加到 Visual Studio 中的"工具"功能表中。</span><span class="sxs-lookup"><span data-stu-id="a5935-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="a5935-135">若要讓工具可供使用，請將它新增至外部工具清單。</span><span class="sxs-lookup"><span data-stu-id="a5935-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="a5935-136">以下為其步驟：</span><span class="sxs-lookup"><span data-stu-id="a5935-136">Here are the steps:</span></span>

1. <span data-ttu-id="a5935-137">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a5935-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="a5935-138">在 [開始] 視窗中，選擇 [不使用程式碼繼續]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a5935-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="a5935-139">在功能表列上，選擇 **"工具** > **外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="a5935-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="a5935-140">在 [外部工具]\*\*\*\* 對話方塊中，選擇 [加入]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a5935-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="a5935-141">新項目隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a5935-141">A new entry appears.</span></span>

1. <span data-ttu-id="a5935-142">輸入新功能表項目的 [標題]\*\*\*\*，例如 `Command Prompt`。</span><span class="sxs-lookup"><span data-stu-id="a5935-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="a5935-143">在 **"命令"** 欄位中，指定要啟動的檔，如`%comspec%`或`C:\Windows\System32\cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="a5935-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="a5935-144">在 **"參數"** 欄位中，指定要使用的特定命令提示的位置，例如`/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`。</span><span class="sxs-lookup"><span data-stu-id="a5935-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="a5935-145">此命令啟動與 Visual Studio 2019 社區一起安裝的開發人員命令提示。</span><span class="sxs-lookup"><span data-stu-id="a5935-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="a5935-146">根據您的 Visual Studio 版本和安裝位置變更這個值。</span><span class="sxs-lookup"><span data-stu-id="a5935-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="a5935-147">在 **"初始目錄"** 欄位中，指定命令提示符將在其中啟動的目錄。</span><span class="sxs-lookup"><span data-stu-id="a5935-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="a5935-148">通過選擇欄位旁邊的箭頭來選擇專案**目錄**等值。</span><span class="sxs-lookup"><span data-stu-id="a5935-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="a5935-149">選擇 [確定] \*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a5935-149">Choose the **OK** button.</span></span>

   ![外部工具對話方塊，欄位值已填寫。](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="a5935-151">這會新增功能表項目，而且您可以從 [工具] 功能表存取命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a5935-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Visual Studio 中的命令提示字元功能表項目](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="a5935-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5935-153">See also</span></span>

- [<span data-ttu-id="a5935-154">.NET Framework 工具</span><span class="sxs-lookup"><span data-stu-id="a5935-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="a5935-155">管理外部工具</span><span class="sxs-lookup"><span data-stu-id="a5935-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="a5935-156">使用命令列中的 Microsoft C++工具集</span><span class="sxs-lookup"><span data-stu-id="a5935-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
