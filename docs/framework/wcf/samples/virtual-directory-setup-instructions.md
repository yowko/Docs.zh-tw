---
title: 虛擬目錄安裝指示
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: fdff88026a49989870ee5c47f9a38a65ecad3c80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325341"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="65c03-102">虛擬目錄安裝指示</span><span class="sxs-lookup"><span data-stu-id="65c03-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="65c03-103">Windows Communication Foundation (WCF) 範例的目的是共用一個通用的虛擬目錄，名為 servicemodelsamples 的會對應到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 資料夾。</span><span class="sxs-lookup"><span data-stu-id="65c03-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65c03-104">%SystemDrive% 通常是 C: 或 D:，這視安裝 Internet Information Services (IIS) 的磁碟機位置而定。</span><span class="sxs-lookup"><span data-stu-id="65c03-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="65c03-105">您可以執行 Setupvroot.bat 和 Cleanupvroot.bat 檔案，從[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)建立虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="65c03-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="65c03-106">如果您偏好手動建立虛擬目錄，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="65c03-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="65c03-107">程序</span><span class="sxs-lookup"><span data-stu-id="65c03-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="65c03-108">若要建立虛擬目錄在 IIS 7.0 或 7.5</span><span class="sxs-lookup"><span data-stu-id="65c03-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="65c03-109">從**開始**功能表上，按一下**執行**，然後輸入**inetmgr**以開啟 Internet Information Services (IIS) MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="65c03-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="65c03-110">在左窗格中，展開電腦名稱的節點，然後展開**站台**節點。</span><span class="sxs-lookup"><span data-stu-id="65c03-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="65c03-111">以滑鼠右鍵按一下**Default Web Site**，然後選取**新增應用程式**以開啟**新增應用程式視窗**。</span><span class="sxs-lookup"><span data-stu-id="65c03-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="65c03-112">在視窗中，輸入`servicemodelsamples`做為您所建立的虛擬目錄的別名。</span><span class="sxs-lookup"><span data-stu-id="65c03-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="65c03-113">建立下列目錄：%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="65c03-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="65c03-114">設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的實體路徑。</span><span class="sxs-lookup"><span data-stu-id="65c03-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="65c03-115">建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。</span><span class="sxs-lookup"><span data-stu-id="65c03-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="65c03-116">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="65c03-116">Click **OK**.</span></span> <span data-ttu-id="65c03-117">隨即為 WCF 範例建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="65c03-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65c03-118">這項工作必須執行一次，因為所有的 WCF 範例都使用相同的 servicemodelsamples Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="65c03-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65c03-119">就此文件的用途而言，`virtual directory`一詞是 `Web application`的同義詞。</span><span class="sxs-lookup"><span data-stu-id="65c03-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="65c03-120">除了建立虛擬目錄，您也必須設定其屬性，以啟用要執行的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="65c03-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="65c03-121">如需詳細資訊，請參閱下方。</span><span class="sxs-lookup"><span data-stu-id="65c03-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="65c03-122">在 IIS 5.1 或 6.0 中建立虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="65c03-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="65c03-123">開啟命令提示字元] 視窗並輸入`start inetmgr`以開啟 [Internet Information Services (IIS) MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="65c03-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="65c03-124">在左窗格中，展開電腦名稱的節點，然後展開**網站**節點。</span><span class="sxs-lookup"><span data-stu-id="65c03-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="65c03-125">以滑鼠右鍵按一下**Default Web Site** ，然後選取**新的虛擬目錄**以開啟 虛擬目錄建立精靈。</span><span class="sxs-lookup"><span data-stu-id="65c03-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="65c03-126">在精靈中，輸入`servicemodelsamples`做為您所建立的虛擬目錄的別名。</span><span class="sxs-lookup"><span data-stu-id="65c03-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="65c03-127">設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的路徑。</span><span class="sxs-lookup"><span data-stu-id="65c03-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="65c03-128">建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。</span><span class="sxs-lookup"><span data-stu-id="65c03-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="65c03-129">按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="65c03-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="65c03-130">預設會選取下列核取方塊：</span><span class="sxs-lookup"><span data-stu-id="65c03-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="65c03-131">**Read**</span><span class="sxs-lookup"><span data-stu-id="65c03-131">**Read**</span></span>  
  
    -   <span data-ttu-id="65c03-132">**執行指令碼 （例如 ASP)**</span><span class="sxs-lookup"><span data-stu-id="65c03-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="65c03-133">按一下 **下一步**，然後按一下**完成**以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="65c03-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65c03-134">此工作必須一次執行，因為所有的 WCF 範例都使用相同的 servicemodelsamples 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="65c03-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="65c03-135">若要設定額外的虛擬目錄屬性，在 IIS 7.0 或 7.5</span><span class="sxs-lookup"><span data-stu-id="65c03-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="65c03-136">按一下 servicemodelsamples 節點。</span><span class="sxs-lookup"><span data-stu-id="65c03-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="65c03-137">視窗的底部會有兩個檢視。</span><span class="sxs-lookup"><span data-stu-id="65c03-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="65c03-138">選取 **功能檢視**如果已選取。</span><span class="sxs-lookup"><span data-stu-id="65c03-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="65c03-139">按兩下項目**瀏覽目錄**。</span><span class="sxs-lookup"><span data-stu-id="65c03-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="65c03-140">在 [動作] 窗格中，選取**啟用**選項。</span><span class="sxs-lookup"><span data-stu-id="65c03-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="65c03-141">這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="65c03-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="65c03-142">最後，您必須設定 servicemodelsamples 資料夾的安全性屬性，讓其他使用者能夠存取此資料夾。</span><span class="sxs-lookup"><span data-stu-id="65c03-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="65c03-143">如需詳細資訊，請參閱下方。</span><span class="sxs-lookup"><span data-stu-id="65c03-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="65c03-144">若要在 IIS 5.1 或 6.0 中設定額外的虛擬目錄屬性</span><span class="sxs-lookup"><span data-stu-id="65c03-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="65c03-145">以滑鼠右鍵按一下 servicemodelsamples 節點，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="65c03-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="65c03-146">預設會選取下列核取方塊：</span><span class="sxs-lookup"><span data-stu-id="65c03-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="65c03-147">**Read**</span><span class="sxs-lookup"><span data-stu-id="65c03-147">**Read**</span></span>  
  
    -   <span data-ttu-id="65c03-148">**記錄查閱**</span><span class="sxs-lookup"><span data-stu-id="65c03-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="65c03-149">**此資源編製索引**</span><span class="sxs-lookup"><span data-stu-id="65c03-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="65c03-150">選取 **瀏覽目錄**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="65c03-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="65c03-151">這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="65c03-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="65c03-152">若要在 IIS 7.0 或 7.5 中設定資料夾的安全性屬性</span><span class="sxs-lookup"><span data-stu-id="65c03-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="65c03-153">巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。</span><span class="sxs-lookup"><span data-stu-id="65c03-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="65c03-154">以滑鼠右鍵按一下 servicemodelsamples 資料夾，然後按一下 **共用**或是**共用對象**。</span><span class="sxs-lookup"><span data-stu-id="65c03-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="65c03-155">按一下左邊的向下箭號**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="65c03-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="65c03-156">選取 **尋找**項目。</span><span class="sxs-lookup"><span data-stu-id="65c03-156">Select the **Find** entry.</span></span> <span data-ttu-id="65c03-157">**選取使用者或群組**視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="65c03-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="65c03-158">按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="65c03-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="65c03-159">按一下 **位置**。</span><span class="sxs-lookup"><span data-stu-id="65c03-159">Click **Locations**.</span></span> <span data-ttu-id="65c03-160">**位置** 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="65c03-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="65c03-161">選取使用的電腦項目。</span><span class="sxs-lookup"><span data-stu-id="65c03-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="65c03-162">請務必選取本機電腦，而非列出的任何網域或網路項目。</span><span class="sxs-lookup"><span data-stu-id="65c03-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="65c03-163">您已選取的電腦之後，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="65c03-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="65c03-164">按一下 **立即尋找**。</span><span class="sxs-lookup"><span data-stu-id="65c03-164">Click **Find Now**.</span></span> <span data-ttu-id="65c03-165">這會將與本機電腦相關聯的物件填入到搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="65c03-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="65c03-166">尋找**IIS_IUSRS**中的項目**名稱 （相對分辨名稱）** 資料行。</span><span class="sxs-lookup"><span data-stu-id="65c03-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="65c03-167">選取該項目，然後按一下**確定**以關閉搜尋結果視窗。</span><span class="sxs-lookup"><span data-stu-id="65c03-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="65c03-168">按一下  **確定**以關閉**選取使用者或群組**視窗。</span><span class="sxs-lookup"><span data-stu-id="65c03-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="65c03-169">按一下 **共用**來保存變更。</span><span class="sxs-lookup"><span data-stu-id="65c03-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="65c03-170">若要啟用共用的變更都完成之後，請按一下**完成**以關閉**檔案共用**視窗。</span><span class="sxs-lookup"><span data-stu-id="65c03-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="65c03-171">設定 IIS 5.1 或 6.0 中資料夾的安全性屬性</span><span class="sxs-lookup"><span data-stu-id="65c03-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="65c03-172">巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。</span><span class="sxs-lookup"><span data-stu-id="65c03-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="65c03-173">以滑鼠右鍵按一下**servicemodelsamples**資料夾，然後按一下**共用和安全性。**</span><span class="sxs-lookup"><span data-stu-id="65c03-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="65c03-174">按一下 [ **安全性** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="65c03-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="65c03-175">如果您在使用 IIS 6.0**群組或使用者名稱**方塊中，檢查是否**Internet Guest 帳戶**列。</span><span class="sxs-lookup"><span data-stu-id="65c03-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="65c03-176">如果未列出：</span><span class="sxs-lookup"><span data-stu-id="65c03-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="65c03-177">按一下 [開始]，然後按一下 [控制台]。</span><span class="sxs-lookup"><span data-stu-id="65c03-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="65c03-178">如果您看不見**使用者帳戶**圖示，按一下**切換至 類別檢視**。</span><span class="sxs-lookup"><span data-stu-id="65c03-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="65c03-179">按一下 **使用者帳戶**圖示。</span><span class="sxs-lookup"><span data-stu-id="65c03-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="65c03-180">在 或選取 控制台 圖示，「 按一下**使用者帳戶**。</span><span class="sxs-lookup"><span data-stu-id="65c03-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="65c03-181">在 **使用者帳戶** 對話方塊中，按一下**進階** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="65c03-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="65c03-182">按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="65c03-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="65c03-183">在 [**本機使用者和群組**] 對話方塊中，按一下以展開**使用者**資料夾。</span><span class="sxs-lookup"><span data-stu-id="65c03-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="65c03-184">在右窗格中，按兩下**Internet Guest 帳戶**。</span><span class="sxs-lookup"><span data-stu-id="65c03-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="65c03-185">在 [**屬性**] 對話方塊中，複製 Internet guest 帳戶為使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="65c03-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="65c03-186">根據預設，該名稱開頭為 "USR_"，後面會加上電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="65c03-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="65c03-187">關閉 [內容]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="65c03-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="65c03-188">關閉**本機使用者和群組** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="65c03-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="65c03-189">關閉**使用者帳戶** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="65c03-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="65c03-190">關閉其他**使用者帳戶** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="65c03-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="65c03-191">在  **servicemodelsamples 屬性**對話方塊的 **安全性**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="65c03-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="65c03-192">輸入一個反斜線，後面接著電腦名稱，然後貼上網際網路使用者帳戶，例如 myMachineName 名稱\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="65c03-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="65c03-193">按一下 **檢查名稱**驗證新增。</span><span class="sxs-lookup"><span data-stu-id="65c03-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="65c03-194">如果有效，該名稱會是全部大寫字母並加上底線。</span><span class="sxs-lookup"><span data-stu-id="65c03-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="65c03-195">IIS 6.0，也請檢查網路服務會列在**群組或使用者名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="65c03-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="65c03-196">如果未列示 NETWORK SERVICE：</span><span class="sxs-lookup"><span data-stu-id="65c03-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="65c03-197">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="65c03-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="65c03-198">在 [**選取使用者或群組**] 對話方塊中，輸入電腦名稱後面接著反斜線。</span><span class="sxs-lookup"><span data-stu-id="65c03-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="65c03-199">型別**服務**反斜線 （不含空格） 後面。</span><span class="sxs-lookup"><span data-stu-id="65c03-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="65c03-200">按一下 **檢查名稱**。</span><span class="sxs-lookup"><span data-stu-id="65c03-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="65c03-201">如果找到多個名稱，選取**NETWORK SERVICE**然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="65c03-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="65c03-202">按一下 [ **[確定]** 以關閉**選取使用者或群組**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="65c03-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="65c03-203">如果您使用 Windows XP SP2 搭配 IIS 5.1，請檢查，會將 Internet Guest 帳戶和 ASPNET 都列在**群組或使用者名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="65c03-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="65c03-204">請注意，ASPNET 使用者可能是內建的成員**使用者**安全性群組。</span><span class="sxs-lookup"><span data-stu-id="65c03-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="65c03-205">如果是的話，則**使用者**群組列於對話方塊中，您不需要將它做為個別的項目新增至允許的使用者清單。</span><span class="sxs-lookup"><span data-stu-id="65c03-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="65c03-206">若要檢查 ASPNET 是否屬於**使用者**安全性群組：</span><span class="sxs-lookup"><span data-stu-id="65c03-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="65c03-207">在 [**開始**] 功能表中，按一下**控制台**。</span><span class="sxs-lookup"><span data-stu-id="65c03-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="65c03-208">按一下 **使用者帳戶**圖示。</span><span class="sxs-lookup"><span data-stu-id="65c03-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="65c03-209">在 **群組**資料行中，確認的值**ASPNET**是 「 使用者 」。</span><span class="sxs-lookup"><span data-stu-id="65c03-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c03-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65c03-210">See also</span></span>

- [<span data-ttu-id="65c03-211">Internet Information Service 裝載指示</span><span class="sxs-lookup"><span data-stu-id="65c03-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
