---
title: Visual Studio 的開發人員命令提示字元
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc88106a54a00b4b12e5043da7961791a98102c0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344360"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="61acf-102">Visual Studio 的開發人員命令提示字元</span><span class="sxs-lookup"><span data-stu-id="61acf-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="61acf-103">Visual Studio 的開發人員命令提示字元可讓您更輕鬆地使用 .NET Framework 工具。</span><span class="sxs-lookup"><span data-stu-id="61acf-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="61acf-104">它是命令提示字元，可自動設定特定的環境變數。</span><span class="sxs-lookup"><span data-stu-id="61acf-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
> [<span data-ttu-id="61acf-105">下載 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="61acf-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="61acf-106">搜尋您電腦上的命令提示字元</span><span class="sxs-lookup"><span data-stu-id="61acf-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="61acf-107">根據您已安裝的 Visual Studio 及任何其他 SDK 版本，您可能會有多個命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="61acf-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="61acf-108">例如，Visual Studio 64 位元版本提供 32 位元和 64 位元的命令提示字元 </span><span class="sxs-lookup"><span data-stu-id="61acf-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="61acf-109">(大多數工具的 32 位元和 64 位元版本完全相同；然而，少數工具會分別變更 32 位元和 64 位元的環境)。如果下列步驟沒有作用，您可以嘗試[以手動方式尋找您電腦上的檔案](#manually-locate-the-files-on-your-machine)或[從 Visual Studio 內部執行命令提示字元](#run-the-command-prompt-from-inside-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="61acf-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="61acf-110">在 Windows 10</span><span class="sxs-lookup"><span data-stu-id="61acf-110">In Windows 10</span></span>

1. <span data-ttu-id="61acf-111">在工作列的搜尋方塊中開始鍵入工具名稱，例如 `dev` 或 `developer command prompt`。</span><span class="sxs-lookup"><span data-stu-id="61acf-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="61acf-112">這會顯示符合搜尋模式的已安裝應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="61acf-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="61acf-113">如果您要尋找不同的命令提示字元，請嘗試輸入不同的搜尋字詞，例如 `prompt`。</span><span class="sxs-lookup"><span data-stu-id="61acf-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="61acf-114">選擇 [Visual Studio 開發人員命令提示字元] (或您想要使用的命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="61acf-114">Choose the **Developer Command Prompt for Visual Studio** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="61acf-115">在 Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="61acf-115">In Windows 8.1</span></span>

1. <span data-ttu-id="61acf-116">移至 [開始] 畫面，例如藉由按下鍵盤上的 Windows 標誌鍵 ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。</span><span class="sxs-lookup"><span data-stu-id="61acf-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="61acf-117">在 [開始] 畫面上，按 **Ctrl** + **Tab** 以開啟 [應用程式] 清單，然後輸入 `V`。</span><span class="sxs-lookup"><span data-stu-id="61acf-117">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="61acf-118">這會顯示包含所有已安裝 Visual Studio 命令提示字元的清單。</span><span class="sxs-lookup"><span data-stu-id="61acf-118">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="61acf-119">選擇 [開發人員命令提示字元] (或您想要使用的命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="61acf-119">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="61acf-120">在 Windows 8</span><span class="sxs-lookup"><span data-stu-id="61acf-120">In Windows 8</span></span>

1. <span data-ttu-id="61acf-121">移至 [開始] 畫面，例如藉由按下鍵盤上的 Windows 標誌鍵 ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。</span><span class="sxs-lookup"><span data-stu-id="61acf-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="61acf-122">在 [開始] 畫面上，按下 Windows 標誌鍵 ![Windows 標誌](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`。</span><span class="sxs-lookup"><span data-stu-id="61acf-122">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="61acf-123">選擇畫面底部的 [應用程式檢視] 圖示，然後輸入 `V`。</span><span class="sxs-lookup"><span data-stu-id="61acf-123">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="61acf-124">這會顯示包含所有已安裝 Visual Studio 命令提示字元的清單。</span><span class="sxs-lookup"><span data-stu-id="61acf-124">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="61acf-125">選擇 [開發人員命令提示字元] (或您想要使用的命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="61acf-125">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="61acf-126">在 Windows 7</span><span class="sxs-lookup"><span data-stu-id="61acf-126">In Windows 7</span></span>

1. <span data-ttu-id="61acf-127">選擇 [開始]，展開 [所有程式]，然後展開 [Microsoft Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="61acf-127">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="61acf-128">根據您已安裝的 Visual Studio 版本，請選擇 [Visual Studio Tools]、[Visual Studio 命令提示字元] 或您想要使用的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="61acf-128">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="61acf-129">如果已安裝 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 或[舊版](https://developer.microsoft.com/windows/downloads/sdk-archive)之類的其他 SDK，您可能會看到 ARM、x86 或 x64 架構的其他命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="61acf-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="61acf-130">查看個別工具的文件以判斷要使用哪個版本的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="61acf-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="61acf-131">以手動方式尋找您電腦上的檔案</span><span class="sxs-lookup"><span data-stu-id="61acf-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="61acf-132">您已安裝之命令提示字元的捷徑通常會位於 Visual Studio 的 [開始功能表] 資料夾中，例如 C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools 中。</span><span class="sxs-lookup"><span data-stu-id="61acf-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="61acf-133">但如果基於某些原因，搜尋命令提示字元未產生預期的結果，您可以嘗試以手動方式尋找電腦上的捷徑。</span><span class="sxs-lookup"><span data-stu-id="61acf-133">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="61acf-134">嘗試搜尋 *VsDevCmd.bat* 等命令提示字元檔案名稱，或移至 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools 之類的 Tools 資料夾 (根據您的 Visual Studio 版本和安裝位置，這個路徑會變更)。</span><span class="sxs-lookup"><span data-stu-id="61acf-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="61acf-135">從 Visual Studio 內部執行命令提示字元</span><span class="sxs-lookup"><span data-stu-id="61acf-135">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="61acf-136">為方便存取，您可以將 Visual Studio 開發人員命令提示字元或任何其他命令提示字元新增至 Visual Studio 的 [工具] 功能表。</span><span class="sxs-lookup"><span data-stu-id="61acf-136">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="61acf-137">若要讓工具可供使用，請將它新增至外部工具清單。</span><span class="sxs-lookup"><span data-stu-id="61acf-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="61acf-138">其步驟如下：</span><span class="sxs-lookup"><span data-stu-id="61acf-138">Here are the steps:</span></span>

1. <span data-ttu-id="61acf-139">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="61acf-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="61acf-140">選取 [工具] 功能表，然後選擇 [外部工具]。</span><span class="sxs-lookup"><span data-stu-id="61acf-140">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="61acf-141">在 [外部工具] 對話方塊中，選擇 [加入] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="61acf-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="61acf-142">新項目隨即出現。</span><span class="sxs-lookup"><span data-stu-id="61acf-142">A new entry appears.</span></span>

4. <span data-ttu-id="61acf-143">輸入新功能表項目的 [標題]，例如 `Command Prompt`。</span><span class="sxs-lookup"><span data-stu-id="61acf-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="61acf-144">在 [命令] 欄位中，指定您要啟動的檔案，例如 `%comspec%` 或 `C:\Windows\System32\cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="61acf-144">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="61acf-145">在 [引數] 欄位中，指定尋找所要使用之特定命令提示字元的位置，例如 `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (此命令會啟動隨 Visual Studio 2017 Enterprise 一起安裝的開發人員命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="61acf-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="61acf-146">根據您的 Visual Studio 版本和安裝位置變更這個值。</span><span class="sxs-lookup"><span data-stu-id="61acf-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="61acf-147">選擇 [初始目錄] 欄位的值，例如 [專案目錄]。</span><span class="sxs-lookup"><span data-stu-id="61acf-147">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="61acf-148">選擇 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="61acf-148">Choose the **OK** button.</span></span>

   <span data-ttu-id="61acf-149">這會新增功能表項目，而且您可以從 [工具] 功能表存取命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="61acf-149">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Visual Studio 中的命令提示字元功能表項目](media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="61acf-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61acf-151">See also</span></span>

- [<span data-ttu-id="61acf-152">工具</span><span class="sxs-lookup"><span data-stu-id="61acf-152">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="61acf-153">管理外部工具</span><span class="sxs-lookup"><span data-stu-id="61acf-153">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
