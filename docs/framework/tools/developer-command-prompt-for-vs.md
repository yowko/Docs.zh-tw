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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715876"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="72496-102">Visual Studio 的開發人員命令提示字元</span><span class="sxs-lookup"><span data-stu-id="72496-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="72496-103">Visual Studio 的開發人員命令提示字元可讓您更輕鬆地使用 .NET Framework 工具。</span><span class="sxs-lookup"><span data-stu-id="72496-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="72496-104">它是自動設定特定環境變數的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="72496-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="72496-105">開啟開發人員命令提示字元之後，您可以輸入[.NET Framework 工具](index.md)的命令，例如 `ildasm` 或 `clrver`。</span><span class="sxs-lookup"><span data-stu-id="72496-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72496-106">必要條件：</span><span class="sxs-lookup"><span data-stu-id="72496-106">Prerequisites</span></span>

- [<span data-ttu-id="72496-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="72496-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="72496-108">搜尋您電腦上的命令提示字元</span><span class="sxs-lookup"><span data-stu-id="72496-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="72496-109">您可能會有多個命令提示字元，視 Visual Studio 版本以及您已安裝的任何其他 Sdk 和工作負載而定。</span><span class="sxs-lookup"><span data-stu-id="72496-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="72496-110">如果下列步驟沒有作用，您可以嘗試以[手動方式尋找您電腦上的](#manually-locate-the-files-on-your-machine)檔案，或[從 Visual Studio 內啟動命令提示](#start-the-command-prompt-from-inside-visual-studio)字元。</span><span class="sxs-lookup"><span data-stu-id="72496-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="72496-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="72496-111">Windows 10</span></span>

1. <span data-ttu-id="72496-112">選取鍵盤上的 [**啟動**![Windows 標誌鍵]。](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="72496-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="72496-113">並滾動到字母**V**。</span><span class="sxs-lookup"><span data-stu-id="72496-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="72496-114">展開 [ **Visual Studio 2019** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="72496-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="72496-115">選擇 [**適用于 VS 2019 的開發人員命令提示字元**] （或您想要使用的命令提示字元）。</span><span class="sxs-lookup"><span data-stu-id="72496-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="72496-116">或者，您可以在工作列的 [搜尋] 方塊中，開始輸入命令提示字元的名稱，然後選擇您想要的結果，因為結果清單會開始顯示搜尋相符專案。</span><span class="sxs-lookup"><span data-stu-id="72496-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![顯示 Windows 10 搜尋行為的動畫 gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="72496-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="72496-118">Windows 8.1</span></span>

1. <span data-ttu-id="72496-119">按下 Windows 標誌鍵 ![鍵盤上的 Windows 標誌鍵](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 前往 [開始] 畫面。</span><span class="sxs-lookup"><span data-stu-id="72496-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="72496-120">位於您的鍵盤上，作為範例。</span><span class="sxs-lookup"><span data-stu-id="72496-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="72496-121">在 **開始** 畫面上，按**Ctrl**+ 索引標籤以開啟 **應用程式**清單，然後按**V**。這會顯示一份清單，其中包含所有已安裝的 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="72496-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="72496-122">選擇 [**適用于 VS 2019 的開發人員命令提示字元**] （或您想要使用的命令提示字元）。</span><span class="sxs-lookup"><span data-stu-id="72496-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="72496-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="72496-123">Windows 7</span></span>

1. <span data-ttu-id="72496-124">選擇 [**開始**]，然後展開 [**所有程式**]。</span><span class="sxs-lookup"><span data-stu-id="72496-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="72496-125">**針對 VS 2019**選擇**Visual Studio 2019** > **Visual Studio Tools** > 開發人員命令提示字元或您想要使用的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="72496-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![已反白顯示命令提示字元的 Windows 7 [開始] 功能表](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="72496-127">如果您已安裝其他 Sdk （例如[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)或[舊版](https://developer.microsoft.com/windows/downloads/sdk-archive)），您可能會看到其他的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="72496-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="72496-128">查看個別工具的文件以判斷要使用哪個版本的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="72496-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="72496-129">以手動方式尋找您電腦上的檔案</span><span class="sxs-lookup"><span data-stu-id="72496-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="72496-130">您已安裝之命令提示字元的快捷方式通常會放在 Visual Studio 的 [**開始功能表**] 資料夾中，例如 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*。</span><span class="sxs-lookup"><span data-stu-id="72496-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="72496-131">但如果基於某些原因，搜尋命令提示字元並不會產生預期的結果，您可以嘗試在您的電腦上手動找出快捷方式。</span><span class="sxs-lookup"><span data-stu-id="72496-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="72496-132">請嘗試搜尋命令提示字元檔案的名稱（例如*vsdevcmd.bat*），或移至 [工具] 資料夾，例如 *% ProgramFiles （x86）% \ Microsoft Visual Studio\2019\Community\Common7\Tools* （根據您的 Visual Studio 版本、版本和安裝位置的路徑變更）。</span><span class="sxs-lookup"><span data-stu-id="72496-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="72496-133">從內部啟動命令提示字元 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72496-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="72496-134">為方便存取，您可以將開發人員命令提示字元或任何其他命令提示字元新增至 Visual Studio 中的 [工具] 功能表。</span><span class="sxs-lookup"><span data-stu-id="72496-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="72496-135">若要讓工具可供使用，請將它新增至外部工具清單。</span><span class="sxs-lookup"><span data-stu-id="72496-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="72496-136">其步驟如下：</span><span class="sxs-lookup"><span data-stu-id="72496-136">Here are the steps:</span></span>

1. <span data-ttu-id="72496-137">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="72496-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="72496-138">在 [開始] 視窗中，選擇 [不使用程式碼繼續]。</span><span class="sxs-lookup"><span data-stu-id="72496-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="72496-139">在功能表列上，選擇 [**工具**] > [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="72496-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="72496-140">在 [外部工具] 對話方塊中，選擇 [加入] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="72496-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="72496-141">新項目隨即出現。</span><span class="sxs-lookup"><span data-stu-id="72496-141">A new entry appears.</span></span>

1. <span data-ttu-id="72496-142">輸入新功能表項目的 [標題]，例如 `Command Prompt`。</span><span class="sxs-lookup"><span data-stu-id="72496-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="72496-143">在 [命令] 欄位中，指定您要啟動的檔案，例如 `%comspec%` 或 `C:\Windows\System32\cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="72496-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="72496-144">在 [**引數**] 欄位中，指定要在哪裡尋找您要使用的特定命令提示字元，例如 `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`。</span><span class="sxs-lookup"><span data-stu-id="72496-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="72496-145">此命令會啟動隨 Visual Studio 2019 的社區安裝的開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="72496-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="72496-146">根據您的 Visual Studio 版本和安裝位置變更這個值。</span><span class="sxs-lookup"><span data-stu-id="72496-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="72496-147">在 [**初始目錄**] 欄位中，指定要在其中啟動命令提示字元的目錄。</span><span class="sxs-lookup"><span data-stu-id="72496-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="72496-148">選取欄位旁的箭號，以選擇 [**專案目錄**] 之類的值。</span><span class="sxs-lookup"><span data-stu-id="72496-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="72496-149">選擇 [ **確定** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="72496-149">Choose the **OK** button.</span></span>

   ![填入域值的 [外部工具] 對話方塊。](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="72496-151">[新增] 功能表項目隨即加入，而且您可以從 [工具] 功能表存取命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="72496-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Visual Studio 中的命令提示字元功能表項目](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="72496-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="72496-153">See also</span></span>

- [<span data-ttu-id="72496-154">.NET Framework 工具</span><span class="sxs-lookup"><span data-stu-id="72496-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="72496-155">管理外部工具</span><span class="sxs-lookup"><span data-stu-id="72496-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="72496-156">從命令列C++使用 Microsoft 工具組</span><span class="sxs-lookup"><span data-stu-id="72496-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
