---
title: 逐步解說：在 WPF 應用程式中快取應用程式資料
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8d3fe2dbfe0b4b5fb9081d71cec080dfa54add8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="3131b-102">逐步解說：在 WPF 應用程式中快取應用程式資料</span><span class="sxs-lookup"><span data-stu-id="3131b-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="3131b-103">快取可讓您將資料儲存在記憶體中，以進行快速存取。</span><span class="sxs-lookup"><span data-stu-id="3131b-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="3131b-104">一次存取資料時，應用程式可以從快取，而要擷取的原始來源取得資料。</span><span class="sxs-lookup"><span data-stu-id="3131b-104">When the data is accessed again, applications can get the data from the cache instead retrieving it from the original source.</span></span> <span data-ttu-id="3131b-105">這可以改善效能和延展性。</span><span class="sxs-lookup"><span data-stu-id="3131b-105">This can improve performance and scalability.</span></span> <span data-ttu-id="3131b-106">此外，暫時無法使用資料來源時，快取可讓資料可用。</span><span class="sxs-lookup"><span data-stu-id="3131b-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>  
  
 <span data-ttu-id="3131b-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供類別，可讓您使用中的快取[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="3131b-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides classes that enable you to use caching in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="3131b-108">這些類別位於<xref:System.Runtime.Caching>命名空間。</span><span class="sxs-lookup"><span data-stu-id="3131b-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3131b-109"><xref:System.Runtime.Caching>命名空間的新[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3131b-109">The <xref:System.Runtime.Caching> namespace is new in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="3131b-110">此命名空間可讓快取可供所有[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="3131b-110">This namespace makes caching is available to all [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="3131b-111">在舊版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中，快取只能用於 <xref:System.Web> 命名空間中，因此需要與 ASP.NET 類別的相依性。</span><span class="sxs-lookup"><span data-stu-id="3131b-111">In previous versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>  
  
 <span data-ttu-id="3131b-112">本逐步解說會示範如何使用所提供的快取功能[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]一部分[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="3131b-112">This walkthrough shows you how to use the caching functionality that is available in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="3131b-113">逐步解說中，您快取之文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="3131b-113">In the walkthrough, you cache the contents of a text file.</span></span>  
  
 <span data-ttu-id="3131b-114">本逐步解說所述的工作包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="3131b-114">Tasks illustrated in this walkthrough include the following:</span></span>  
  
-   <span data-ttu-id="3131b-115">建立 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="3131b-115">Creating a WPF application project.</span></span>  
  
-   <span data-ttu-id="3131b-116">將參考加入至[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3131b-116">Adding a reference to the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="3131b-117">正在初始化快取。</span><span class="sxs-lookup"><span data-stu-id="3131b-117">Initializing a cache.</span></span>  
  
-   <span data-ttu-id="3131b-118">加入快取項目包含文字檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="3131b-118">Adding a cache entry that contains the contents of a text file.</span></span>  
  
-   <span data-ttu-id="3131b-119">快取項目的提供的收回原則。</span><span class="sxs-lookup"><span data-stu-id="3131b-119">Providing an eviction policy for the cache entry.</span></span>  
  
-   <span data-ttu-id="3131b-120">監視快取檔案的路徑與通知有關的快取執行個體變更受監視的項目。</span><span class="sxs-lookup"><span data-stu-id="3131b-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3131b-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="3131b-121">Prerequisites</span></span>  
 <span data-ttu-id="3131b-122">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="3131b-122">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="3131b-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3131b-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="3131b-124">包含少量文字的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="3131b-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="3131b-125">（您會在訊息方塊中顯示文字檔案的內容）。逐步解說中所述的程式碼會假設您使用下列檔案：</span><span class="sxs-lookup"><span data-stu-id="3131b-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>  
  
     `c:\cache\cacheText.txt`  
  
     <span data-ttu-id="3131b-126">不過，您可以使用任何文字檔案，並在本逐步解說的程式碼中進行小量變更。</span><span class="sxs-lookup"><span data-stu-id="3131b-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>  
  
## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="3131b-127">建立 WPF 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="3131b-127">Creating a WPF Application Project</span></span>  
 <span data-ttu-id="3131b-128">您將開始建立 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="3131b-128">You will start by creating a WPF application project.</span></span>  
  
#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="3131b-129">建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="3131b-129">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="3131b-130">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3131b-130">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3131b-131">在**檔案**功能表上，按一下 **新增**，然後按一下 **新專案**。</span><span class="sxs-lookup"><span data-stu-id="3131b-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>  
  
     <span data-ttu-id="3131b-132">[新增專案] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3131b-132">The **New Project** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="3131b-133">在下**已安裝的範本**，選取您想要使用的程式設計語言 (**Visual Basic**或**Visual C#**)。</span><span class="sxs-lookup"><span data-stu-id="3131b-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>  
  
4.  <span data-ttu-id="3131b-134">在**新專案**對話方塊中，選取**WPF 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="3131b-134">In the **New Project** dialog box, select **WPF Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3131b-135">如果您沒有看到**WPF 應用程式**範本，請確定您的目標版本[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]支援 WPF。</span><span class="sxs-lookup"><span data-stu-id="3131b-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] that supports WPF.</span></span> <span data-ttu-id="3131b-136">在**新專案**對話方塊中，選取[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]從清單中。</span><span class="sxs-lookup"><span data-stu-id="3131b-136">In the **New Project** dialog box, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] from the list.</span></span>  
  
5.  <span data-ttu-id="3131b-137">在**名稱**文字方塊中，輸入您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="3131b-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="3131b-138">例如，您可以輸入**WPFCaching**。</span><span class="sxs-lookup"><span data-stu-id="3131b-138">For example, you can enter **WPFCaching**.</span></span>  
  
6.  <span data-ttu-id="3131b-139">選取**為方案建立目錄**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3131b-139">Select the **Create directory for solution** check box.</span></span>  
  
7.  <span data-ttu-id="3131b-140">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="3131b-140">Click **OK**.</span></span>  
  
     <span data-ttu-id="3131b-141">WPF 設計工具會在中開啟**設計**檢視，並顯示 MainWindow.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="3131b-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="3131b-142">Visual Studio 會建立**我的專案**資料夾、 Application.xaml 檔案和 MainWindow.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="3131b-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="3131b-143">以.NET Framework 為目標，並加入快取的組件的參考</span><span class="sxs-lookup"><span data-stu-id="3131b-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>  
 <span data-ttu-id="3131b-144">根據預設，WPF 應用程式目標[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3131b-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="3131b-145">若要使用<xref:System.Runtime.Caching>WPF 應用程式中的命名空間，應用程式必須為目標[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (不[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)])，而且必須包含命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="3131b-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>  
  
 <span data-ttu-id="3131b-146">因此下, 一個步驟為變更.NET Framework 目標，並將參考加入<xref:System.Runtime.Caching>命名空間。</span><span class="sxs-lookup"><span data-stu-id="3131b-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3131b-147">變更.NET Framework 目標的程序是不同的 Visual C# 專案和 Visual Basic 專案中。</span><span class="sxs-lookup"><span data-stu-id="3131b-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="3131b-148">若要變更的目標.NET Framework 在 Visual Basic 中</span><span class="sxs-lookup"><span data-stu-id="3131b-148">To change the target .NET Framework in Visual Basic</span></span>  
  
1.  <span data-ttu-id="3131b-149">在**方案總管 中**，以滑鼠右鍵按一下專案名稱，然後按**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3131b-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="3131b-150">應用程式的 [屬性] 視窗會顯示。</span><span class="sxs-lookup"><span data-stu-id="3131b-150">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="3131b-151">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3131b-151">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="3131b-152">在視窗底部，按一下 **進階編譯選項...**.</span><span class="sxs-lookup"><span data-stu-id="3131b-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>  
  
     <span data-ttu-id="3131b-153">**進階編譯器設定**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3131b-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="3131b-154">在**目標 framework （所有組態）**清單中，選取[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3131b-154">In the **Target framework (all configurations)** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="3131b-155">(請勿選取[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]。)</span><span class="sxs-lookup"><span data-stu-id="3131b-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>  
  
5.  <span data-ttu-id="3131b-156">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="3131b-156">Click **OK**.</span></span>  
  
     <span data-ttu-id="3131b-157">**目標 Framework 變更**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3131b-157">The **Target Framework Change** dialog box is displayed.</span></span>  
  
6.  <span data-ttu-id="3131b-158">在**目標 Framework 變更**對話方塊中，按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="3131b-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>  
  
     <span data-ttu-id="3131b-159">專案已關閉，並再重新開啟。</span><span class="sxs-lookup"><span data-stu-id="3131b-159">The project is closed and is then reopened.</span></span>  
  
7.  <span data-ttu-id="3131b-160">新增快取的組件的參考，依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3131b-160">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="3131b-161">在**方案總管 中**，以滑鼠右鍵按一下專案名稱，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="3131b-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="3131b-162">選取 **.NET**索引標籤上，選取`System.Runtime.Caching`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3131b-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="3131b-163">若要變更 Visual C# 專案中的目標.NET Framework</span><span class="sxs-lookup"><span data-stu-id="3131b-163">To change the target .NET Framework in a Visual C# project</span></span>  
  
1.  <span data-ttu-id="3131b-164">在**方案總管 中**，以滑鼠右鍵按一下專案名稱，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3131b-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>  
  
     <span data-ttu-id="3131b-165">應用程式的 [屬性] 視窗會顯示。</span><span class="sxs-lookup"><span data-stu-id="3131b-165">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="3131b-166">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3131b-166">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="3131b-167">在**目標 framework**清單中，選取[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3131b-167">In the **Target framework** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="3131b-168">(請勿選取 **.NET Framework 4 Client Profile**。)</span><span class="sxs-lookup"><span data-stu-id="3131b-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>  
  
4.  <span data-ttu-id="3131b-169">新增快取的組件的參考，依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3131b-169">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="3131b-170">以滑鼠右鍵按一下**參考**資料夾，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="3131b-170">Right-click the **References** folder and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="3131b-171">選取 **.NET**索引標籤上，選取`System.Runtime.Caching`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3131b-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="3131b-172">將按鈕加入至 WPF 視窗</span><span class="sxs-lookup"><span data-stu-id="3131b-172">Adding a Button to the WPF Window</span></span>  
 <span data-ttu-id="3131b-173">接下來，您會在 加入按鈕控制項，以及建立的按鈕的事件處理常式`Click`事件。</span><span class="sxs-lookup"><span data-stu-id="3131b-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="3131b-174">稍後您將加入程式碼，因此當您按一下按鈕時，會快取文字檔案的內容，並顯示。</span><span class="sxs-lookup"><span data-stu-id="3131b-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>  
  
#### <a name="to-add-a-button-control"></a><span data-ttu-id="3131b-175">若要將按鈕控制項</span><span class="sxs-lookup"><span data-stu-id="3131b-175">To add a button control</span></span>  
  
1.  <span data-ttu-id="3131b-176">在**方案總管 中**，按兩下 MainWindow.xaml 檔案，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="3131b-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>  
  
2.  <span data-ttu-id="3131b-177">從**工具箱**下**一般 WPF 控制項**，拖曳`Button`控制權傳輸至`MainWindow`視窗。</span><span class="sxs-lookup"><span data-stu-id="3131b-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>  
  
3.  <span data-ttu-id="3131b-178">在**屬性**視窗中，將`Content`屬性`Button`控制權傳輸至**取得快取**。</span><span class="sxs-lookup"><span data-stu-id="3131b-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="3131b-179">初始化快取和快取項目</span><span class="sxs-lookup"><span data-stu-id="3131b-179">Initializing the Cache and Caching an Entry</span></span>  
 <span data-ttu-id="3131b-180">接下來，您將加入程式碼執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3131b-180">Next, you will add the code to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="3131b-181">建立快取類別的執行個體 — 也就是您會具現化新<xref:System.Runtime.Caching.MemoryCache>物件。</span><span class="sxs-lookup"><span data-stu-id="3131b-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>  
  
-   <span data-ttu-id="3131b-182">指定快取佔用<xref:System.Runtime.Caching.HostFileChangeMonitor>物件來監視在文字檔案中的變更。</span><span class="sxs-lookup"><span data-stu-id="3131b-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>  
  
-   <span data-ttu-id="3131b-183">讀取文字檔並快取其內容為快取項目。</span><span class="sxs-lookup"><span data-stu-id="3131b-183">Read the text file and cache its contents as a cache entry.</span></span>  
  
-   <span data-ttu-id="3131b-184">顯示快取的文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="3131b-184">Display the contents of the cached text file.</span></span>  
  
#### <a name="to-create-the-cache-object"></a><span data-ttu-id="3131b-185">建立快取物件</span><span class="sxs-lookup"><span data-stu-id="3131b-185">To create the cache object</span></span>  
  
1.  <span data-ttu-id="3131b-186">按兩下您剛才加入才能 MainWindow.xaml.cs 或 MainWindow.Xaml.vb 檔案中建立事件處理常式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="3131b-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>  
  
2.  <span data-ttu-id="3131b-187">（之前在類別宣告中） 的檔案頂端新增下列`Imports`(Visual Basic) 或`using`(C#) 陳述式：</span><span class="sxs-lookup"><span data-stu-id="3131b-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  <span data-ttu-id="3131b-188">在此事件處理常式，加入下列程式碼來具現化的快取物件：</span><span class="sxs-lookup"><span data-stu-id="3131b-188">In the event handler, add the following code to instantiate the cache object:</span></span>  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <span data-ttu-id="3131b-189"><xref:System.Runtime.Caching.ObjectCache>類別是內建的類別，提供記憶體中物件快取。</span><span class="sxs-lookup"><span data-stu-id="3131b-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>  
  
4.  <span data-ttu-id="3131b-190">加入下列程式碼會讀取名為快取項目的內容`filecontents`:</span><span class="sxs-lookup"><span data-stu-id="3131b-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  <span data-ttu-id="3131b-191">加入下列程式碼，檢查是否快取項目名稱`filecontents`存在：</span><span class="sxs-lookup"><span data-stu-id="3131b-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     <span data-ttu-id="3131b-192">如果指定的快取項目不存在，您必須閱讀文字檔案，並將它當做快取項目加入至快取。</span><span class="sxs-lookup"><span data-stu-id="3131b-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>  
  
6.  <span data-ttu-id="3131b-193">在`if/then`封鎖，加入下列程式碼來建立新的<xref:System.Runtime.Caching.CacheItemPolicy>物件，指定快取項目，在 10 秒後到期。</span><span class="sxs-lookup"><span data-stu-id="3131b-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     <span data-ttu-id="3131b-194">如果未不提供任何收回或到期資訊，則預設值是<xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>，這表示快取項目永遠不過期根據只在絕對時間。</span><span class="sxs-lookup"><span data-stu-id="3131b-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="3131b-195">相反地，快取項目過期時，才有記憶體不足的壓力。</span><span class="sxs-lookup"><span data-stu-id="3131b-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="3131b-196">最佳做法，您應該一律明確地提供絕對或板到期。</span><span class="sxs-lookup"><span data-stu-id="3131b-196">As a best practice, you should always explicitly provide either an absolute or a siding expiration.</span></span>  
  
7.  <span data-ttu-id="3131b-197">內部`if/then`區塊並遵循您在上一個步驟中加入的程式碼，加入下列程式碼來建立您想要監視，並將文字檔的路徑新增至集合的檔案路徑的集合：</span><span class="sxs-lookup"><span data-stu-id="3131b-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3131b-198">如果您想要使用的文字檔不`c:\cache\cacheText.txt`，指定文字檔案是您想要使用的路徑。</span><span class="sxs-lookup"><span data-stu-id="3131b-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>  
  
8.  <span data-ttu-id="3131b-199">遵循您在上一個步驟中，加入的程式碼加入下列程式碼，將新<xref:System.Runtime.Caching.HostFileChangeMonitor>的變更集合的物件會監視快取項目：</span><span class="sxs-lookup"><span data-stu-id="3131b-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <span data-ttu-id="3131b-200"><xref:System.Runtime.Caching.HostFileChangeMonitor>物件監控文字檔案的路徑，以及通知的快取，如果發生變更。</span><span class="sxs-lookup"><span data-stu-id="3131b-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="3131b-201">在此範例中，如果檔案的內容變更時，將到期快取項目。</span><span class="sxs-lookup"><span data-stu-id="3131b-201">In this example, the cache entry will expire if the content of the file changes.</span></span>  
  
9. <span data-ttu-id="3131b-202">您在上一個步驟中加入的程式碼之後, 加入下列程式碼讀取文字檔的內容：</span><span class="sxs-lookup"><span data-stu-id="3131b-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     <span data-ttu-id="3131b-203">讓您將能夠看到快取項目過期時，會加入日期和時間戳記。</span><span class="sxs-lookup"><span data-stu-id="3131b-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>  
  
10. <span data-ttu-id="3131b-204">遵循您在上一個步驟中，加入的程式碼加入下列程式碼，將檔案的內容插入至快取物件，做為<xref:System.Runtime.Caching.CacheItem>執行個體：</span><span class="sxs-lookup"><span data-stu-id="3131b-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     <span data-ttu-id="3131b-205">指定有關如何收回快取項目藉由傳遞資訊<xref:System.Runtime.Caching.CacheItemPolicy>您稍早建立做為參數的物件。</span><span class="sxs-lookup"><span data-stu-id="3131b-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>  
  
11. <span data-ttu-id="3131b-206">之後`if/then`封鎖，加入下列程式碼顯示在訊息方塊中的快取的檔案內容：</span><span class="sxs-lookup"><span data-stu-id="3131b-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. <span data-ttu-id="3131b-207">在**建置**功能表上，按一下 **建置 WPFCaching**建置專案。</span><span class="sxs-lookup"><span data-stu-id="3131b-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>  
  
## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="3131b-208">測試 WPF 應用程式中的快取</span><span class="sxs-lookup"><span data-stu-id="3131b-208">Testing Caching in the WPF Application</span></span>  
 <span data-ttu-id="3131b-209">您現在可以測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="3131b-209">You can now test the application.</span></span>  
  
#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="3131b-210">若要測試的 WPF 應用程式中的快取</span><span class="sxs-lookup"><span data-stu-id="3131b-210">To test caching in the WPF application</span></span>  
  
1.  <span data-ttu-id="3131b-211">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="3131b-211">Press CTRL+F5 to run the application.</span></span>  
  
     <span data-ttu-id="3131b-212">`MainWindow`  視窗隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="3131b-212">The `MainWindow` window is displayed.</span></span>  
  
2.  <span data-ttu-id="3131b-213">按一下**取得快取**。</span><span class="sxs-lookup"><span data-stu-id="3131b-213">Click **Get Cache**.</span></span>  
  
     <span data-ttu-id="3131b-214">從文字檔案快取的內容會顯示在訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="3131b-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="3131b-215">請注意，在檔案上的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="3131b-215">Notice the timestamp on the file.</span></span>  
  
3.  <span data-ttu-id="3131b-216">關閉訊息方塊，然後按一下 **取得快取**再次**。**</span><span class="sxs-lookup"><span data-stu-id="3131b-216">Close the message box and then click **Get Cache** again **.**</span></span>  
  
     <span data-ttu-id="3131b-217">時間戳記不變。</span><span class="sxs-lookup"><span data-stu-id="3131b-217">The timestamp is unchanged.</span></span> <span data-ttu-id="3131b-218">這表示會顯示快取的內容。</span><span class="sxs-lookup"><span data-stu-id="3131b-218">This indicates the cached content is displayed.</span></span>  
  
4.  <span data-ttu-id="3131b-219">等候 10 秒或更久，然後按**取得快取**一次。</span><span class="sxs-lookup"><span data-stu-id="3131b-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="3131b-220">此時會顯示新的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="3131b-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="3131b-221">這表示此原則可讓過期的快取項目，而且會顯示新的快取的內容。</span><span class="sxs-lookup"><span data-stu-id="3131b-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>  
  
5.  <span data-ttu-id="3131b-222">在文字編輯器中，開啟您所建立的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="3131b-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="3131b-223">還不要進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="3131b-223">Do not make any changes yet.</span></span>  
  
6.  <span data-ttu-id="3131b-224">關閉訊息方塊，然後按一下 **取得快取**再次**。**</span><span class="sxs-lookup"><span data-stu-id="3131b-224">Close the message box and then click **Get Cache** again **.**</span></span>  
  
     <span data-ttu-id="3131b-225">再次注意時間戳記。</span><span class="sxs-lookup"><span data-stu-id="3131b-225">Notice the timestamp again.</span></span>  
  
7.  <span data-ttu-id="3131b-226">變更文字檔案，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="3131b-226">Make a change to the text file and then save the file.</span></span>  
  
8.  <span data-ttu-id="3131b-227">關閉訊息方塊，然後按一下 **取得快取**一次。</span><span class="sxs-lookup"><span data-stu-id="3131b-227">Close the message box and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="3131b-228">此訊息方塊包含的文字檔案與新時間戳記更新的內容。</span><span class="sxs-lookup"><span data-stu-id="3131b-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="3131b-229">這表示，主機檔案變更監視器收回快取項目立即當您變更該檔案，即使絕對逾時期間已過期。</span><span class="sxs-lookup"><span data-stu-id="3131b-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3131b-230">您可以增加到 20 秒或更久允許更多的時間，讓您在檔案中變更的收回時間。</span><span class="sxs-lookup"><span data-stu-id="3131b-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="3131b-231">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="3131b-231">Code Example</span></span>  
 <span data-ttu-id="3131b-232">您已經完成此逐步解說之後，您所建立的專案的程式碼將類似下列範例。</span><span class="sxs-lookup"><span data-stu-id="3131b-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3131b-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3131b-233">See Also</span></span>  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [<span data-ttu-id="3131b-234">.NET Framework 應用程式中的快取</span><span class="sxs-lookup"><span data-stu-id="3131b-234">Caching in .NET Framework Applications</span></span>](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
