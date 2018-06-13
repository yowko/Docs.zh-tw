---
title: Visual Studio 的開發人員命令提示字元
ms.date: 03/30/2017
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
ms.openlocfilehash: d3ff897e37e3fa2f7202a54c05c8093ba05282c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402024"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="f6de8-102">Visual Studio 的開發人員命令提示字元</span><span class="sxs-lookup"><span data-stu-id="f6de8-102">Developer Command Prompt for Visual Studio</span></span>
<span data-ttu-id="f6de8-103">「Visual Studio 開發人員命令提示字元」會自動設定環境變數，讓您能夠輕鬆使用 .NET Framework 工具。</span><span class="sxs-lookup"><span data-stu-id="f6de8-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="f6de8-104">開發人員命令提示字元會隨 Visual Studio 的完整版本或 Community Edition 一起安裝，</span><span class="sxs-lookup"><span data-stu-id="f6de8-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="f6de8-105">但無法隨 Visual Studio 的 Express 版本一起安裝。</span><span class="sxs-lookup"><span data-stu-id="f6de8-105">It is not installed with the Express versions of Visual Studio.</span></span>  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="f6de8-106">搜尋您電腦上的命令提示字元</span><span class="sxs-lookup"><span data-stu-id="f6de8-106">Searching for the Command Prompt on your machine</span></span>  
 <span data-ttu-id="f6de8-107">您可以根據所安裝的 Visual Studio 和其他 SDK 版本，查看多個命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f6de8-107">You may see multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="f6de8-108">例如，Visual Studio 64 位元版本提供 32 位元和 64 位元的命令提示字元 </span><span class="sxs-lookup"><span data-stu-id="f6de8-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="f6de8-109">(大多數工具的 32 位元和 64 位元版本完全相同；然而，少數工具會分別變更 32 位元和 64 位元的環境)。如果下面的步驟沒有作用，您可以嘗試[以手動方式尋找您電腦上的檔案](#alternative)或[從 Visual Studio 內部執行命令提示字元](#visualstudio)。</span><span class="sxs-lookup"><span data-stu-id="f6de8-109">(The 32-bit and 64-bit versions of most tools are identical; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the steps below don't work, you can try [Manually locating the files on your machine](#alternative) or [Running command prompt from inside Visual Studio](#visualstudio).</span></span>  
  
 <span data-ttu-id="f6de8-110">**在 Windows 10**</span><span class="sxs-lookup"><span data-stu-id="f6de8-110">**In Windows 10**</span></span>  
  
1.  <span data-ttu-id="f6de8-111">開啟 [開始] 功能表，例如藉由按下鍵盤上的 Windows 標誌鍵 ![Windows 標誌](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。</span><span class="sxs-lookup"><span data-stu-id="f6de8-111">Open the **Start** menu, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="f6de8-112">在 [開始] 功能表上，輸入 `dev`。</span><span class="sxs-lookup"><span data-stu-id="f6de8-112">On the **Start** menu, enter `dev`.</span></span> <span data-ttu-id="f6de8-113">這會顯示符合搜尋模式的已安裝應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="f6de8-113">This will bring a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="f6de8-114">如果您要尋找不同的命令提示字元，請嘗試輸入不同的搜尋字詞，例如 `prompt`。</span><span class="sxs-lookup"><span data-stu-id="f6de8-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>  
  
3.  <span data-ttu-id="f6de8-115">選擇 [開發人員命令提示字元] (或您想要使用的命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="f6de8-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="f6de8-116">**在 Windows 8.1**</span><span class="sxs-lookup"><span data-stu-id="f6de8-116">**In Windows 8.1**</span></span>  
  
1.  <span data-ttu-id="f6de8-117">移至 [開始] 畫面，例如藉由按下鍵盤上的 Windows 標誌鍵 ![Windows 標誌](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。</span><span class="sxs-lookup"><span data-stu-id="f6de8-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="f6de8-118">在 [開始] 畫面上，按 `CTRL + TAB` 以開啟 [應用程式] 清單，然後輸入 `V`。</span><span class="sxs-lookup"><span data-stu-id="f6de8-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="f6de8-119">這會顯示包含所有已安裝之 Visual Studio 命令提示字元的清單。</span><span class="sxs-lookup"><span data-stu-id="f6de8-119">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
3.  <span data-ttu-id="f6de8-120">選擇 [開發人員命令提示字元] (或您想要使用的命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="f6de8-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="f6de8-121">**在 Windows 8**</span><span class="sxs-lookup"><span data-stu-id="f6de8-121">**In Windows 8**</span></span>  
  
1.  <span data-ttu-id="f6de8-122">移至 [開始] 畫面，例如藉由按下鍵盤上的 Windows 標誌鍵 ![Windows 標誌](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")。</span><span class="sxs-lookup"><span data-stu-id="f6de8-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="f6de8-123">在 [開始] 畫面上，按下 Windows 標誌鍵 ![Windows 標誌](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`。</span><span class="sxs-lookup"><span data-stu-id="f6de8-123">On the **Start** screen, press the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>  
  
3.  <span data-ttu-id="f6de8-124">選擇畫面底部的 [應用程式檢視] 圖示，然後輸入 `V`。</span><span class="sxs-lookup"><span data-stu-id="f6de8-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="f6de8-125">這會顯示包含所有已安裝之 Visual Studio 命令提示字元的清單。</span><span class="sxs-lookup"><span data-stu-id="f6de8-125">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
4.  <span data-ttu-id="f6de8-126">選擇 [開發人員命令提示字元] (或您想要使用的命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="f6de8-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="f6de8-127">**在 Windows 7**</span><span class="sxs-lookup"><span data-stu-id="f6de8-127">**In Windows 7**</span></span>  
  
1.  <span data-ttu-id="f6de8-128">選擇 [開始]，展開 [所有程式]，然後展開 [Microsoft Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="f6de8-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="f6de8-129">根據您已安裝的 Visual Studio 版本，請選擇 [Visual Studio Tools]、[Visual Studio 命令提示字元] 或您想要使用的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f6de8-129">Depending on the version of Visual Studio you have installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>  
  
 <span data-ttu-id="f6de8-130">如果已安裝 [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) 或 [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk)，您可能會看到 ARM、x86 或 x64 架構的其他命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f6de8-130">If you have the [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) or [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="f6de8-131">查看個別工具的文件以判斷要使用哪個版本的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f6de8-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="f6de8-132">以手動方式尋找您電腦上的檔案</span><span class="sxs-lookup"><span data-stu-id="f6de8-132">Manually locating the files on your machine</span></span>  
  <span data-ttu-id="f6de8-133">您已安裝之命令提示字元的捷徑通常會置於 Visual Studio 的 [開始功能表] 資料夾中，例如 C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools 中。</span><span class="sxs-lookup"><span data-stu-id="f6de8-133">Usually, the shortcuts for the command prompts you have installed will be placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span></span>    <span data-ttu-id="f6de8-134">但如果基於某些原因，搜尋命令提示字元未產生預期的結果，您可以嘗試以手動方式尋找電腦上的捷徑來加以使用。</span><span class="sxs-lookup"><span data-stu-id="f6de8-134">But if for some reason, searching for the command prompt doesn't yield the expected results, you can try to manually locate the shortcut on your machine in order to use it.</span></span>   <span data-ttu-id="f6de8-135">嘗試搜尋 VsDevCmd.bat 等命令提示字元檔案名稱，或移至 C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools 之類的 Tools 資料夾 (根據您的 Visual Studio 版本和安裝位置，這個路徑會變更)。</span><span class="sxs-lookup"><span data-stu-id="f6de8-135">Try searching for the name of the command prompt file such as VsDevCmd.bat or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (path will change according to your Visual Studio version and installation location).</span></span>  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="f6de8-136">從 Visual Studio 內部執行命令提示字元</span><span class="sxs-lookup"><span data-stu-id="f6de8-136">Running command prompt from inside Visual Studio</span></span>  
 <span data-ttu-id="f6de8-137">為方便存取，您可以將 Visual Studio 開發人員命令提示字元或其他任何命令提示字元加入 Visual Studio 的 [工具] 功能表，方法是將其加入外部工具清單。</span><span class="sxs-lookup"><span data-stu-id="f6de8-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="f6de8-138">以下說明如何完成這項作業：</span><span class="sxs-lookup"><span data-stu-id="f6de8-138">This is how you can accomplish that:</span></span>  
  
1.  <span data-ttu-id="f6de8-139">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f6de8-139">Open Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f6de8-140">選取 [工具] 功能表並選擇 [外部工具...]。</span><span class="sxs-lookup"><span data-stu-id="f6de8-140">Select the **Tools** menu and choose **External Tools...**.</span></span>  
  
3.  <span data-ttu-id="f6de8-141">在 [外部工具] 對話方塊中，選擇 [加入] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f6de8-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="f6de8-142">新項目隨即出現</span><span class="sxs-lookup"><span data-stu-id="f6de8-142">A new entry appears</span></span>  
  
4.  <span data-ttu-id="f6de8-143">輸入新功能表項目的 [標題]，例如 `Command Prompt`。</span><span class="sxs-lookup"><span data-stu-id="f6de8-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>  
  
5.  <span data-ttu-id="f6de8-144">在 [命令] 欄位中，指定您要啟動的檔案，例如 `%comspec%` 或 `C:\Windows\System32\cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="f6de8-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe` .</span></span>  
  
6.  <span data-ttu-id="f6de8-145">在 [引數] 欄位中，指定尋找所要使用之特定命令提示字元的位置，例如 `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (這會啟動隨 [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)] 一起安裝的開發人員命令提示字元)。</span><span class="sxs-lookup"><span data-stu-id="f6de8-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (this will launch the Developer Command Prompt installed with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span></span> <span data-ttu-id="f6de8-146">根據您的 Visual Studio 版本和安裝位置，必須變更這個值。</span><span class="sxs-lookup"><span data-stu-id="f6de8-146">This value needs to be changed according to your Visual Studio version and installation location.</span></span>  
  
7.  <span data-ttu-id="f6de8-147">選擇 [初始目錄] 欄位的值，例如 [專案目錄]。</span><span class="sxs-lookup"><span data-stu-id="f6de8-147">Choose a value for the **Initial directory** field such as **Project Directory** .</span></span>  
  
8.  <span data-ttu-id="f6de8-148">選擇 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="f6de8-148">Choose the **OK** button.</span></span>  
  
 <span data-ttu-id="f6de8-149">在這之後會加入新的功能表項目，而且您可以從 [工具] 功能表存取命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f6de8-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6de8-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6de8-150">See Also</span></span>  
 [<span data-ttu-id="f6de8-151">工具</span><span class="sxs-lookup"><span data-stu-id="f6de8-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="f6de8-152">管理外部工具</span><span class="sxs-lookup"><span data-stu-id="f6de8-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
