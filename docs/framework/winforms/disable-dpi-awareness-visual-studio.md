---
title: 停用 Visual Studio 中的 DPI 感知
description: 討論 Windows Form 設計工具的 HDPI 監視器上的限制，以及如何執行 Visual Studio 做為 DPI 感知的處理序。
ms.date: 04/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.custom: seoapril2019
ms.openlocfilehash: e52debea382033417afe0bd47f899af1666192bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181374"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="b9119-103">停用 Visual Studio 中的 DPI 感知</span><span class="sxs-lookup"><span data-stu-id="b9119-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="b9119-104">Visual Studio 是為 dots per inch (DPI) 感知應用程式，這表示顯示標尺自動。</span><span class="sxs-lookup"><span data-stu-id="b9119-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="b9119-105">如果應用程式指出不 DPI 感知，作業系統會調整為點陣圖的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9119-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="b9119-106">此行為也稱為 DPI 虛擬化。</span><span class="sxs-lookup"><span data-stu-id="b9119-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="b9119-107">應用程式仍然會認為它正在執行 100%縮放比例，或 96 dpi。</span><span class="sxs-lookup"><span data-stu-id="b9119-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

<span data-ttu-id="b9119-108">這篇文章討論 Windows Form 設計工具的 HDPI 監視器上的限制，以及如何執行 Visual Studio 做為 DPI 感知的處理序。</span><span class="sxs-lookup"><span data-stu-id="b9119-108">This article discusses the limitations of Windows Forms Designer on HDPI monitors and how to run Visual Studio as a DPI-unaware process.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="b9119-109">在 HDPI 監視器上的 Windows Form 設計工具</span><span class="sxs-lookup"><span data-stu-id="b9119-109">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="b9119-110">**Windows Form 設計工具**Visual Studio 中沒有縮放支援。</span><span class="sxs-lookup"><span data-stu-id="b9119-110">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="b9119-111">這會導致顯示問題，當您開啟中的某些表單**Windows Form 設計工具**在 hdpi () 監視的高 dpi。</span><span class="sxs-lookup"><span data-stu-id="b9119-111">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="b9119-112">如需範例，控制項可能會出現重疊，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="b9119-112">For examples, controls can appear to overlap as shown in the following image:</span></span>

![HDPI 監視器上的 Windows Form 設計工具](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="b9119-114">當您開啟中的表單**Windows Form 設計工具**在 HDPI 監視器上的 Visual Studio 中 Visual Studio 會顯示黃色列的參考設計工具的頂端：</span><span class="sxs-lookup"><span data-stu-id="b9119-114">When you open a form in the **Windows Forms Designer** in Visual Studio on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![在以 DPI 感知的模式重新啟動 Visual Studio 中的資訊列](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="b9119-116">訊息讀取**主顯示器上的縮放比例設為 200%(192 dpi)。設計師視窗中，這可能造成轉譯問題。**</span><span class="sxs-lookup"><span data-stu-id="b9119-116">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

> [!NOTE]
> <span data-ttu-id="b9119-117">此資訊列是在 Visual Studio 2017 版本 15.8 引進。</span><span class="sxs-lookup"><span data-stu-id="b9119-117">This informational bar was introduced in Visual Studio 2017 version 15.8.</span></span>

<span data-ttu-id="b9119-118">如果您不使用設計工具中，而且不需要調整表單的配置，您可以略過的資訊列，並繼續運作，在程式碼編輯器，或在其他類型的設計工具。</span><span class="sxs-lookup"><span data-stu-id="b9119-118">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="b9119-119">(您也可以[停用通知](#disable-notifications)這樣的資訊列不會持續顯示。)只有**Windows Form 設計工具**會受到影響。</span><span class="sxs-lookup"><span data-stu-id="b9119-119">(You can also [disable notifications](#disable-notifications) so that the informational bar doesn't continue to appear.) Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="b9119-120">如果您需要在中運作**Windows Form 設計工具**下, 一節可協助您[解決此問題](#to-resolve-the-display-problem)。</span><span class="sxs-lookup"><span data-stu-id="b9119-120">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-display-problem).</span></span>

## <a name="to-resolve-the-display-problem"></a><span data-ttu-id="b9119-121">若要解決顯示問題</span><span class="sxs-lookup"><span data-stu-id="b9119-121">To resolve the display problem</span></span>

<span data-ttu-id="b9119-122">有三個選項可以解決顯示問題：</span><span class="sxs-lookup"><span data-stu-id="b9119-122">There are three options to resolve the display problem:</span></span>

1. [<span data-ttu-id="b9119-123">重新啟動 Visual Studio 做為 DPI 感知的處理序</span><span class="sxs-lookup"><span data-stu-id="b9119-123">Restart Visual Studio as a DPI-unaware process</span></span>](#restart-visual-studio-as-a-dpi-unaware-process)
2. [<span data-ttu-id="b9119-124">新增登錄項目</span><span class="sxs-lookup"><span data-stu-id="b9119-124">Add a registry entry</span></span>](#add-a-registry-entry)
3. [<span data-ttu-id="b9119-125">設定您的顯示縮放比例為 100%的設定</span><span class="sxs-lookup"><span data-stu-id="b9119-125">Set your display scaling setting to 100%</span></span>](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="b9119-126">重新啟動 Visual Studio 做為 DPI 感知的處理序</span><span class="sxs-lookup"><span data-stu-id="b9119-126">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="b9119-127">您可以選取黃色的資訊列上的選項重新啟動 Visual Studio 做為 DPI 感知的處理序。</span><span class="sxs-lookup"><span data-stu-id="b9119-127">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="b9119-128">這是最好的解決問題。</span><span class="sxs-lookup"><span data-stu-id="b9119-128">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="b9119-129">Visual Studio 執行時做為 DPI 感知的處理序，設計工具的版面配置問題解決，但是字型可能會模糊。</span><span class="sxs-lookup"><span data-stu-id="b9119-129">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="b9119-130">Visual Studio 會顯示不同的黃色參考用訊息，指出 DPI 感知處理程序的形式執行時**Visual Studio 正在執行做為 DPI 感知的處理序。WPF 與 XAML 設計工具可能無法正確顯示。**</span><span class="sxs-lookup"><span data-stu-id="b9119-130">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="b9119-131">資訊列也會提供選項，以**做為 DPI 感知的處理序重新啟動 Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="b9119-131">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="b9119-132">如果您有浮動工具視窗，在 Visual Studio 中的，當您選取要做為 DPI 感知的處理序重新啟動選項，這些工具視窗的位置可能會變更。</span><span class="sxs-lookup"><span data-stu-id="b9119-132">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="b9119-133">如果您使用預設的 Visual Basic 設定檔，或如果您有**儲存新專案建立時**中的選項取消選取**工具** > **選項** > **專案和方案**，Visual Studio 無法重新開啟專案，做為 DPI 感知的處理序重新啟動時。</span><span class="sxs-lookup"><span data-stu-id="b9119-133">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="b9119-134">不過，您可以開啟專案，選取它底下**檔案** > **最新的專案和方案**。</span><span class="sxs-lookup"><span data-stu-id="b9119-134">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="b9119-135">請務必重新啟動 Visual Studio 做為 DPI 感知的處理序，當您完成在工作時**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="b9119-135">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="b9119-136">當它做為 DPI 感知的處理序執行時，字型可以看得很吃力，和您可能會看到其他設計工具中的問題，例如**XAML 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="b9119-136">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="b9119-137">如果您關閉並重新開啟 Visual Studio，它 DPI 感知的模式中執行時，它會變成 DPI 感知一次。</span><span class="sxs-lookup"><span data-stu-id="b9119-137">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="b9119-138">您也可以按一下**做為 DPI 感知的處理序重新啟動 Visual Studio**資訊列中的選項。</span><span class="sxs-lookup"><span data-stu-id="b9119-138">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="b9119-139">新增登錄項目</span><span class="sxs-lookup"><span data-stu-id="b9119-139">Add a registry entry</span></span>

<span data-ttu-id="b9119-140">您可以藉由修改登錄，以將 Visual Studio 標記為 DPI 感知。</span><span class="sxs-lookup"><span data-stu-id="b9119-140">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="b9119-141">開啟**登錄編輯程式** ，並新增一個項目**您可以 NT\CurrentVersion\AppCompatFlags\Layers**子機碼：</span><span class="sxs-lookup"><span data-stu-id="b9119-141">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="b9119-142">**項目**:根據您使用 Visual Studio 2017 或 2019年，使用下列值之一：</span><span class="sxs-lookup"><span data-stu-id="b9119-142">**Entry**: Depending on whether you're using Visual Studio 2017 or 2019, use one of these values:</span></span>

- <span data-ttu-id="b9119-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="b9119-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>
- <span data-ttu-id="b9119-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="b9119-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span></span>

> [!NOTE]
> <span data-ttu-id="b9119-145">如果您使用 Visual Studio Professional 或 Enterprise 版本，取代**社群**與**Professional**或是**Enterprise**項目中。</span><span class="sxs-lookup"><span data-stu-id="b9119-145">If you're using the Professional or Enterprise edition of Visual Studio, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span> <span data-ttu-id="b9119-146">也取代為所需的磁碟機代號。</span><span class="sxs-lookup"><span data-stu-id="b9119-146">Also replace the drive letter as necessary.</span></span>

<span data-ttu-id="b9119-147">**型別**:REG_SZ</span><span class="sxs-lookup"><span data-stu-id="b9119-147">**Type**: REG_SZ</span></span>

<span data-ttu-id="b9119-148">**值**：DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="b9119-148">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="b9119-149">Visual Studio 會保留在 DPI 感知的模式，直到您移除登錄項目。</span><span class="sxs-lookup"><span data-stu-id="b9119-149">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="b9119-150">設定您的顯示縮放比例為 100%的設定</span><span class="sxs-lookup"><span data-stu-id="b9119-150">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="b9119-151">若要設定您 Windows 10 中的縮放比例設定為 100%的顯示，請輸入**顯示設定**在 [搜尋] 方塊中，然後選取工作列**變更顯示設定**。</span><span class="sxs-lookup"><span data-stu-id="b9119-151">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="b9119-152">在 **設定**視窗中，將**變更的文字、 應用程式和其他項目大小**來**100%**。</span><span class="sxs-lookup"><span data-stu-id="b9119-152">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="b9119-153">設定您的顯示器設為 100%縮放比例可能不想要因為它可以讓使用者介面太小而無法使用。</span><span class="sxs-lookup"><span data-stu-id="b9119-153">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="disable-notifications"></a><span data-ttu-id="b9119-154">停用通知</span><span class="sxs-lookup"><span data-stu-id="b9119-154">Disable notifications</span></span>

<span data-ttu-id="b9119-155">您可以選擇不會收到通知的 DPI 縮放問題，在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b9119-155">You can choose not to be notified of DPI scaling issues in Visual Studio.</span></span> <span data-ttu-id="b9119-156">您可能想要停用通知，如果您不在設計師中，例如。</span><span class="sxs-lookup"><span data-stu-id="b9119-156">You might want to disable notifications if you aren't working in the designer, for example.</span></span>

<span data-ttu-id="b9119-157">若要停用通知，請選擇**工具** > **選項**以開啟**選項**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b9119-157">To disable notifications, choose **Tools** > **Options** to open the **Options** dialog.</span></span> <span data-ttu-id="b9119-158">然後選擇  **Windows Form 設計工具** > **一般**，並將**DPI 縮放比例通知**至**False**。</span><span class="sxs-lookup"><span data-stu-id="b9119-158">Then, choose **Windows Forms Designer** > **General**, and set **DPI Scaling Notifications** to **False**.</span></span>

![DPI 縮放比例通知選項，在 Visual Studio 中](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

<span data-ttu-id="b9119-160">如果您想要稍後重新啟用調整的通知，將屬性設定為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="b9119-160">If you want to later reenable scaling notifications, set the property to **True**.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="b9119-161">疑難排解</span><span class="sxs-lookup"><span data-stu-id="b9119-161">Troubleshoot</span></span>

<span data-ttu-id="b9119-162">如果 DPI 感知轉換運作不如預期在 Visual Studio 中，請檢查以查看是否有`dpiAwareness`中的值**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image 檔案執行 Options\devenv.exe**子機碼在登錄編輯程式。</span><span class="sxs-lookup"><span data-stu-id="b9119-162">If the DPI-awareness transition isn't working as expected in Visual Studio, check to see if you have the `dpiAwareness` value in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** subkey in Registry Editor.</span></span> <span data-ttu-id="b9119-163">如果有的話，請刪除值。</span><span class="sxs-lookup"><span data-stu-id="b9119-163">Delete the value if it's present.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9119-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9119-164">See also</span></span>

- [<span data-ttu-id="b9119-165">自動縮放 Windows Form</span><span class="sxs-lookup"><span data-stu-id="b9119-165">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
