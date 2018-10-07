---
title: 停用 Visual Studio 中的 DPI 感知
description: 討論在 HDPI 監視器上的 Windows Form 設計工具，以及如何執行 Visual Studio 做為 DPI 感知的處理序的限制。
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 3b290b67ca97065dfc408c09850cf0b5720d65ae
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847573"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="fbd8f-103">停用 Visual Studio 中的 DPI 感知</span><span class="sxs-lookup"><span data-stu-id="fbd8f-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="fbd8f-104">Visual Studio 是為 dots per inch (DPI) 感知應用程式，這表示顯示標尺自動。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="fbd8f-105">如果應用程式指出不 DPI 感知，作業系統會調整為點陣圖的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="fbd8f-106">此行為也稱為 DPI 虛擬化。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="fbd8f-107">應用程式仍然會認為它正在執行 100%縮放比例，或 96 dpi。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="fbd8f-108">在 HDPI 監視器上的 Windows Form 設計工具</span><span class="sxs-lookup"><span data-stu-id="fbd8f-108">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="fbd8f-109">**Windows Form 設計工具**Visual Studio 中沒有縮放支援。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-109">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="fbd8f-110">這會導致顯示問題，當您開啟中的某些表單**Windows Form 設計工具**在 hdpi () 監視的高 dpi。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-110">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="fbd8f-111">如需範例，控制項可能會出現重疊，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="fbd8f-111">For examples, controls can appear to overlap as shown in the following image:</span></span>

![HDPI 監視器上的 Windows Form 設計工具](media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="fbd8f-113">在 Visual Studio 2017 版本 15.8 和更新版本，當您開啟中的表單**Windows Form 設計工具**在 HDPI 監視器中，Visual Studio 會顯示黃色列的參考設計工具的頂端：</span><span class="sxs-lookup"><span data-stu-id="fbd8f-113">In Visual Studio 2017 version 15.8 and later, when you open a form in the **Windows Forms Designer** on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![在以 DPI 感知的模式重新啟動 Visual Studio 中的資訊列](media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="fbd8f-115">訊息讀取**主顯示器上的縮放比例設為 200%(192 dpi)。設計師視窗中，這可能造成轉譯問題。**</span><span class="sxs-lookup"><span data-stu-id="fbd8f-115">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

<span data-ttu-id="fbd8f-116">如果您不使用設計工具中，而且不需要調整表單的配置，您可以略過的資訊列，並繼續運作，在程式碼編輯器，或在其他類型的設計工具。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-116">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="fbd8f-117">只有**Windows Form 設計工具**會受到影響。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-117">Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="fbd8f-118">如果您需要在中運作**Windows Form 設計工具**下, 一節可協助您[解決此問題](#to-resolve-the-problem)。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-118">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-problem).</span></span>

## <a name="to-resolve-the-problem"></a><span data-ttu-id="fbd8f-119">若要解決此問題</span><span class="sxs-lookup"><span data-stu-id="fbd8f-119">To resolve the problem</span></span>

<span data-ttu-id="fbd8f-120">有三個選項可以解決顯示問題。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-120">There are three options to resolve the display problem.</span></span>

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="fbd8f-121">重新啟動 Visual Studio 做為 DPI 感知的處理序</span><span class="sxs-lookup"><span data-stu-id="fbd8f-121">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="fbd8f-122">您可以選取黃色的資訊列上的選項重新啟動 Visual Studio 做為 DPI 感知的處理序。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-122">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="fbd8f-123">這是最好的解決問題。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-123">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="fbd8f-124">Visual Studio 執行時做為 DPI 感知的處理序，設計工具的版面配置問題解決，但是字型可能會模糊。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-124">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="fbd8f-125">Visual Studio 會顯示不同的黃色參考用訊息，指出 DPI 感知處理程序的形式執行時**Visual Studio 正在執行做為 DPI 感知的處理序。WPF 與 XAML 設計工具可能無法正確顯示。**</span><span class="sxs-lookup"><span data-stu-id="fbd8f-125">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="fbd8f-126">資訊列也會提供選項，以**做為 DPI 感知的處理序重新啟動 Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-126">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="fbd8f-127">如果您有浮動工具視窗，在 Visual Studio 中的，當您選取要做為 DPI 感知的處理序重新啟動選項，這些工具視窗的位置可能會變更。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-127">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="fbd8f-128">如果您使用預設的 Visual Basic 設定檔，或如果您有**儲存新專案建立時**中的選項取消選取**工具** > **選項** > **專案和方案**，Visual Studio 無法重新開啟專案，做為 DPI 感知的處理序重新啟動時。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-128">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="fbd8f-129">不過，您可以開啟專案，選取它底下**檔案** > **最新的專案和方案**。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-129">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="fbd8f-130">請務必重新啟動 Visual Studio 做為 DPI 感知的處理序，當您完成在工作時**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-130">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="fbd8f-131">當它做為 DPI 感知的處理序執行時，字型可以看得很吃力，和您可能會看到其他設計工具中的問題，例如**XAML 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-131">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="fbd8f-132">如果您關閉並重新開啟 Visual Studio，它 DPI 感知的模式中執行時，它會變成 DPI 感知一次。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-132">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="fbd8f-133">您也可以按一下**做為 DPI 感知的處理序重新啟動 Visual Studio**資訊列中的選項。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-133">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="fbd8f-134">新增登錄項目</span><span class="sxs-lookup"><span data-stu-id="fbd8f-134">Add a registry entry</span></span>

<span data-ttu-id="fbd8f-135">您可以藉由修改登錄，以將 Visual Studio 標記為 DPI 感知。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-135">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="fbd8f-136">開啟**登錄編輯程式** ，並新增一個項目**您可以 NT\CurrentVersion\AppCompatFlags\Layers**子機碼：</span><span class="sxs-lookup"><span data-stu-id="fbd8f-136">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="fbd8f-137">**項目**: %programfiles (x86) %\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="fbd8f-137">**Entry**: %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>

   > [!NOTE]
   > <span data-ttu-id="fbd8f-138">如果您使用 Visual Studio 2017 Professional 或 Enterprise edition，將**社群**使用**Professional**或是**Enterprise**項目中。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-138">If you're using the Professional or Enterprise edition of Visual Studio 2017, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span>

<span data-ttu-id="fbd8f-139">**型別**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="fbd8f-139">**Type**: REG_SZ</span></span>

<span data-ttu-id="fbd8f-140">**值**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="fbd8f-140">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="fbd8f-141">Visual Studio 會保留在 DPI 感知的模式，直到您移除登錄項目。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-141">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="fbd8f-142">設定您的顯示縮放比例為 100%的設定</span><span class="sxs-lookup"><span data-stu-id="fbd8f-142">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="fbd8f-143">若要設定您 Windows 10 中的縮放比例設定為 100%的顯示，請輸入**顯示設定**在 [搜尋] 方塊中，然後選取工作列**變更顯示設定**。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-143">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="fbd8f-144">在 **設定**視窗中，將**變更的文字、 應用程式和其他項目大小**來**100%**。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-144">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="fbd8f-145">設定您的顯示器設為 100%縮放比例可能不想要因為它可以讓使用者介面太小而無法使用。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-145">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="fbd8f-146">疑難排解</span><span class="sxs-lookup"><span data-stu-id="fbd8f-146">Troubleshoot</span></span>

<span data-ttu-id="fbd8f-147">如果 DPI 感知轉換運作不如預期在 Visual Studio 中，請檢查以查看是否有`dpiAwareness`中的值**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image 檔案執行 Options\devenv.exe**子機碼在登錄編輯程式。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-147">If the DPI-awareness transition isn't working as expected in Visual Studio, check to see if you have the `dpiAwareness` value in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** subkey in Registry Editor.</span></span> <span data-ttu-id="fbd8f-148">如果有的話，請刪除值。</span><span class="sxs-lookup"><span data-stu-id="fbd8f-148">Delete the value if it's present.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbd8f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbd8f-149">See also</span></span>

- [<span data-ttu-id="fbd8f-150">自動縮放 Windows Form</span><span class="sxs-lookup"><span data-stu-id="fbd8f-150">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)