---
title: 快取應用程式資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: b7d999f94e2f2ae410a16e537d51c0f890def4e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728067"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="1f4e7-102">逐步解說：在 WPF 應用程式中快取應用程式資料</span><span class="sxs-lookup"><span data-stu-id="1f4e7-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="1f4e7-103">快取可讓您將資料儲存在記憶體中，以進行快速存取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="1f4e7-104">重新存取資料時，應用程式可以從快取中取得資料，而不是從原始來源進行擷取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="1f4e7-105">這可以改善效能和延展性。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-105">This can improve performance and scalability.</span></span> <span data-ttu-id="1f4e7-106">此外，暫時無法使用資料來源時，快取可讓資料可用。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="1f4e7-107">.NET Framework 提供的類別可讓您在 .NET Framework 應用程式中使用快取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-107">The .NET Framework provides classes that enable you to use caching in .NET Framework applications.</span></span> <span data-ttu-id="1f4e7-108">這些類別位於 <xref:System.Runtime.Caching> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="1f4e7-109"><xref:System.Runtime.Caching> 命名空間在 .NET Framework 4 中是新的。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-109">The <xref:System.Runtime.Caching> namespace is new in the .NET Framework 4.</span></span> <span data-ttu-id="1f4e7-110">這個命名空間可讓所有 .NET Framework 應用程式使用快取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-110">This namespace makes caching is available to all .NET Framework applications.</span></span> <span data-ttu-id="1f4e7-111">在舊版的 .NET Framework 中，快取僅適用于 <xref:System.Web> 命名空間，因此需要 ASP.NET 類別的相依性。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-111">In previous versions of the .NET Framework, caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="1f4e7-112">本逐步解說將示範如何使用 .NET Framework 中提供的快取功能，做為 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-112">This walkthrough shows you how to use the caching functionality that is available in the .NET Framework as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="1f4e7-113">在此逐步解說中，您會快取文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="1f4e7-114">本逐步解說所述的工作包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-114">Tasks illustrated in this walkthrough include the following:</span></span>

- <span data-ttu-id="1f4e7-115">建立 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-115">Creating a WPF application project.</span></span>

- <span data-ttu-id="1f4e7-116">將參考加入至 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-116">Adding a reference to the .NET Framework 4.</span></span>

- <span data-ttu-id="1f4e7-117">初始化快取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-117">Initializing a cache.</span></span>

- <span data-ttu-id="1f4e7-118">加入包含文字檔內容的快取專案。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-118">Adding a cache entry that contains the contents of a text file.</span></span>

- <span data-ttu-id="1f4e7-119">提供快取專案的收回原則。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-119">Providing an eviction policy for the cache entry.</span></span>

- <span data-ttu-id="1f4e7-120">監視快取檔案的路徑，並通知快取實例有關受監視專案的變更。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f4e7-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="1f4e7-121">Prerequisites</span></span>
 <span data-ttu-id="1f4e7-122">為了完成這個逐步解說，您需要：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-122">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="1f4e7-123">Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-123">Visual Studio 2010.</span></span>

- <span data-ttu-id="1f4e7-124">包含少量文字的文字檔。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="1f4e7-125">（您會在訊息方塊中顯示文字檔的內容）。本逐步解說中說明的程式碼假設您正在使用下列檔案：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="1f4e7-126">不過，您可以使用任何文字檔，並對此逐步解說中的程式碼進行較小的變更。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="1f4e7-127">建立 WPF 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="1f4e7-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="1f4e7-128">您將從建立 WPF 應用程式專案開始。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="1f4e7-129">建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="1f4e7-129">To create a WPF application</span></span>

1. <span data-ttu-id="1f4e7-130">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="1f4e7-131">**在 [檔案**] 功能表中，按一下 [**新增**]，然後按一下 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="1f4e7-132">[**新增專案**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="1f4e7-133">在 [**已安裝的範本**] 底下，選取您想要使用的程式設計語言（**Visual Basic**或**視覺效果C#** ）。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="1f4e7-134">在 [**新增專案**] 對話方塊中，選取 [ **WPF 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f4e7-135">如果您看不到 [ **Wpf 應用程式**] 範本，請確定您的目標是支援 WPF 的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the .NET Framework that supports WPF.</span></span> <span data-ttu-id="1f4e7-136">在 [**新增專案**] 對話方塊中，從清單中選取 [.NET Framework 4]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-136">In the **New Project** dialog box, select .NET Framework 4 from the list.</span></span>

5. <span data-ttu-id="1f4e7-137">在 [**名稱**] 文字方塊中，輸入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="1f4e7-138">例如，您可以輸入**WPFCaching**。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="1f4e7-139">選取 [為解決方案建立目錄] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="1f4e7-140">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-140">Click **OK**.</span></span>

     <span data-ttu-id="1f4e7-141">WPF 設計工具會在**設計**視圖中開啟，並顯示 mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="1f4e7-142">Visual Studio 會建立 [**我的專案**] 資料夾、應用程式 .xaml 檔案和 mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="1f4e7-143">以 .NET Framework 為目標並加入快取元件的參考</span><span class="sxs-lookup"><span data-stu-id="1f4e7-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="1f4e7-144">根據預設，WPF 應用程式會以 .NET Framework 4 用戶端設定檔為目標。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-144">By default, WPF applications target the .NET Framework 4 Client Profile.</span></span> <span data-ttu-id="1f4e7-145">若要在 WPF 應用程式中使用 <xref:System.Runtime.Caching> 命名空間，應用程式必須將目標設為 .NET Framework 4 （而不是 .NET Framework 4 用戶端設定檔），而且必須包含命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the .NET Framework 4 (not the .NET Framework 4 Client Profile) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="1f4e7-146">因此，下一個步驟是變更 .NET Framework 目標，並加入 <xref:System.Runtime.Caching> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="1f4e7-147">在 Visual Basic 專案和 Visual C#專案中，變更 .NET Framework 目標的程式會有所不同。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="1f4e7-148">若要在 Visual Basic 中變更目標 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1f4e7-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="1f4e7-149">在 [**方案瀏覽器**] 中，以滑鼠右鍵按一下專案名稱，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="1f4e7-150">應用程式的 [屬性] 視窗隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="1f4e7-151">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="1f4e7-152">在視窗底部，按一下 [**高級編譯選項 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="1f4e7-153">[ **Advanced 編譯器設定**] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="1f4e7-154">在 [**目標 framework （所有設定）** ] 清單中，選取 [.NET Framework 4]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-154">In the **Target framework (all configurations)** list, select .NET Framework 4.</span></span> <span data-ttu-id="1f4e7-155">（請勿選取 [.NET Framework 4 用戶端設定檔]）。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-155">(Do not select .NET Framework 4 Client Profile.)</span></span>

5. <span data-ttu-id="1f4e7-156">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-156">Click **OK**.</span></span>

     <span data-ttu-id="1f4e7-157">[目標 Framework 變更] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="1f4e7-158">在 [**目標 Framework 變更**] 對話方塊中，按一下 **[是**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="1f4e7-159">專案已關閉，然後重新開啟。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="1f4e7-160">依照下列步驟，新增對快取元件的參考：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-160">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="1f4e7-161">在**方案總管**中，以滑鼠右鍵按一下專案的名稱，然後按一下 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="1f4e7-162">選取 [ **.net** ] 索引標籤，選取 [`System.Runtime.Caching`]，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="1f4e7-163">變更視覺效果C#專案中的目標 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1f4e7-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="1f4e7-164">在**方案總管**中，以滑鼠右鍵按一下專案名稱，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="1f4e7-165">應用程式的 [屬性] 視窗隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="1f4e7-166">按一下 [應用程式] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="1f4e7-167">在 [**目標 framework** ] 清單中，選取 [.NET Framework 4]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-167">In the **Target framework** list, select .NET Framework 4.</span></span> <span data-ttu-id="1f4e7-168">（請勿選取 [ **.NET Framework 4 用戶端設定檔**]）。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="1f4e7-169">依照下列步驟，新增對快取元件的參考：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-169">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="1f4e7-170">以滑鼠右鍵按一下 [**參考**] 資料夾，然後按一下 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="1f4e7-171">選取 [ **.net** ] 索引標籤，選取 [`System.Runtime.Caching`]，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="1f4e7-172">將按鈕加入至 WPF 視窗</span><span class="sxs-lookup"><span data-stu-id="1f4e7-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="1f4e7-173">接下來，您將加入按鈕控制項，並為按鈕的 `Click` 事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="1f4e7-174">稍後您會將程式碼加入至，當您按一下按鈕時，就會快取並顯示文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="1f4e7-175">若要加入按鈕控制項</span><span class="sxs-lookup"><span data-stu-id="1f4e7-175">To add a button control</span></span>

1. <span data-ttu-id="1f4e7-176">在**方案總管**中，按兩下 [mainwindow.xaml] 檔案以開啟它。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="1f4e7-177">從 [**工具箱**] 的 [**通用 WPF 控制項**] 底下，將 [`Button`] 控制項拖曳至 [`MainWindow`] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="1f4e7-178">在 [**屬性**] 視窗中，將 `Button` 控制項的 [`Content`] 屬性設定為 [**取得快取**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="1f4e7-179">初始化快取並快取專案</span><span class="sxs-lookup"><span data-stu-id="1f4e7-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="1f4e7-180">接下來，您將新增程式碼來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-180">Next, you will add the code to perform the following tasks:</span></span>

- <span data-ttu-id="1f4e7-181">建立快取類別的實例，也就是您將具現化新的 <xref:System.Runtime.Caching.MemoryCache> 物件。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

- <span data-ttu-id="1f4e7-182">指定快取使用 <xref:System.Runtime.Caching.HostFileChangeMonitor> 物件來監視文字檔中的變更。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

- <span data-ttu-id="1f4e7-183">讀取文字檔，並將其內容快取為快取專案。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-183">Read the text file and cache its contents as a cache entry.</span></span>

- <span data-ttu-id="1f4e7-184">顯示快取文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="1f4e7-185">若要建立快取物件</span><span class="sxs-lookup"><span data-stu-id="1f4e7-185">To create the cache object</span></span>

1. <span data-ttu-id="1f4e7-186">按兩下您剛才加入的按鈕，以便在 MainWindow.xaml.cs 或 Mainwindow.xaml 中建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="1f4e7-187">在檔案的頂端（在類別宣告之前），加入下列 `Imports` （Visual Basic）或 `using` （C#）語句：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="1f4e7-188">在事件處理常式中，新增下列程式碼以具現化 cache 物件：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="1f4e7-189"><xref:System.Runtime.Caching.ObjectCache> 類別是內建類別，可提供記憶體中的物件快取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="1f4e7-190">新增下列程式碼，以讀取名為 `filecontents`之快取專案的內容：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="1f4e7-191">新增下列程式碼，以檢查名為 `filecontents` 的快取專案是否存在：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="1f4e7-192">如果指定的快取專案不存在，您必須讀取文字檔，並將它當做快取專案新增至快取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="1f4e7-193">在 [`if/then`] 區塊中，新增下列程式碼以建立新的 <xref:System.Runtime.Caching.CacheItemPolicy> 物件，指定快取專案在10秒後到期。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="1f4e7-194">如果未提供收回或到期資訊，預設值會是 <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>，這表示快取專案永遠不會根據絕對時間過期。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="1f4e7-195">相反地，只有在發生記憶體壓力時，快取專案才會過期。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="1f4e7-196">最佳做法是一律明確地提供絕對或滑動期限。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="1f4e7-197">在 `if/then` 區塊內，並遵循您在上一個步驟中新增的程式碼，新增下列程式碼以建立您想要監視之檔案路徑的集合，並將文字檔的路徑新增至集合：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > <span data-ttu-id="1f4e7-198">如果您要使用的文字檔不是 `c:\cache\cacheText.txt`，請指定您要使用之文字檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="1f4e7-199">遵循您在上一個步驟中新增的程式碼，新增下列程式碼，將新的 <xref:System.Runtime.Caching.HostFileChangeMonitor> 物件新增至快取專案的變更監視集合：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="1f4e7-200"><xref:System.Runtime.Caching.HostFileChangeMonitor> 物件會監視文字檔的路徑，並在發生變更時通知快取。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="1f4e7-201">在此範例中，如果檔案的內容變更，快取專案就會過期。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="1f4e7-202">遵循您在上一個步驟中新增的程式碼，新增下列程式碼來讀取文字檔的內容：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="1f4e7-203">新增日期和時間時間戳記，讓您能夠查看快取專案何時到期。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="1f4e7-204">在您于上一個步驟中新增的程式碼之後，新增下列程式碼，以將檔案的內容插入快取物件中做為 <xref:System.Runtime.Caching.CacheItem> 實例：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="1f4e7-205">您可以藉由傳遞您稍早建立的 <xref:System.Runtime.Caching.CacheItemPolicy> 物件做為參數，指定快取專案應如何收回的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="1f4e7-206">在 `if/then` 區塊之後，新增下列程式碼，以在訊息方塊中顯示快取檔案內容：</span><span class="sxs-lookup"><span data-stu-id="1f4e7-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="1f4e7-207">在 [**建立**] 功能表中，按一下 [**建立 WPFCaching** ] 來建立您的專案。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="1f4e7-208">在 WPF 應用程式中測試快取</span><span class="sxs-lookup"><span data-stu-id="1f4e7-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="1f4e7-209">：您現在可以測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="1f4e7-210">若要在 WPF 應用程式中測試快取</span><span class="sxs-lookup"><span data-stu-id="1f4e7-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="1f4e7-211">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="1f4e7-212">[`MainWindow`] 視窗隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="1f4e7-213">按一下 [**取得快取**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="1f4e7-214">文字檔中的快取內容會顯示在訊息方塊中。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="1f4e7-215">請注意檔案上的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="1f4e7-216">關閉訊息方塊，然後按一下 [**取得快取**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="1f4e7-217">時間戳記不變。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-217">The timestamp is unchanged.</span></span> <span data-ttu-id="1f4e7-218">這表示會顯示快取的內容。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="1f4e7-219">等待10秒或以上，然後再按一下 [**取得快取**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="1f4e7-220">這次會顯示新的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="1f4e7-221">這表示原則讓快取專案到期，並顯示新的快取內容。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="1f4e7-222">在文字編輯器中，開啟您所建立的文字檔。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="1f4e7-223">尚未進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="1f4e7-224">關閉訊息方塊，然後按一下 [**取得快取**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="1f4e7-225">請再次注意時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="1f4e7-226">對文字檔進行變更，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="1f4e7-227">關閉訊息方塊，然後按一下 [**取得快取**]。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="1f4e7-228">此訊息方塊包含來自文字檔的更新內容和新的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="1f4e7-229">這表示當您變更檔案時，主機檔案變更監視器會立即收回快取專案，即使絕對的超時時間尚未過期也一樣。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f4e7-230">您可以將收回時間增加為20秒以上，讓您有更多時間在檔案中進行變更。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="1f4e7-231">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="1f4e7-231">Code Example</span></span>
 <span data-ttu-id="1f4e7-232">完成本逐步解說之後，您所建立之專案的程式碼會如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1f4e7-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="1f4e7-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f4e7-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="1f4e7-234">.NET Framework 應用程式中的快取</span><span class="sxs-lookup"><span data-stu-id="1f4e7-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
