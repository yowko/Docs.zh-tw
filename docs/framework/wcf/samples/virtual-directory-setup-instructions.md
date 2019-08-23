---
title: 虛擬目錄安裝指示
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: f755fadf6bef2bdd58fd31f3460a143b8f52eddf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966732"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="0084d-102">虛擬目錄安裝指示</span><span class="sxs-lookup"><span data-stu-id="0084d-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="0084d-103">Windows Communication Foundation (WCF) 範例的目的是共用名稱為 servicemodelsamples 的通用虛擬目錄, 其對應至%SystemDrive%\inetpub\wwwroot\servicemodelsamples 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0084d-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0084d-104">%SystemDrive% 通常是 C: 或 D:，這視安裝 Internet Information Services (IIS) 的磁碟機位置而定。</span><span class="sxs-lookup"><span data-stu-id="0084d-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="0084d-105">您可以從[Windows Communication Foundation 範例的一次性安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)執行 Setupvroot.bat 和 cleanupvroot.bat 檔案, 以建立虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0084d-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="0084d-106">如果您偏好手動建立虛擬目錄，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="0084d-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0084d-107">程序</span><span class="sxs-lookup"><span data-stu-id="0084d-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="0084d-108">若要在 IIS 7.0 或7.5 中建立虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="0084d-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="0084d-109">在 [**開始**] 功能表中, 按一下 [**執行**], 然後輸入**inetmgr**以開啟 [Internet Information Services (IIS) mmc 嵌入式管理單元]。</span><span class="sxs-lookup"><span data-stu-id="0084d-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="0084d-110">在左窗格中, 展開具有電腦名稱稱的節點, 然後展開 [**網站**] 節點。</span><span class="sxs-lookup"><span data-stu-id="0084d-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="0084d-111">以滑鼠右鍵按一下 [**預設的網站**], 然後選取 [**新增應用程式**] 以開啟 [**新增應用程式] 視窗**。</span><span class="sxs-lookup"><span data-stu-id="0084d-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="0084d-112">在視窗中, 輸入`servicemodelsamples`做為您所建立虛擬目錄的別名。</span><span class="sxs-lookup"><span data-stu-id="0084d-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="0084d-113">建立下列目錄：%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="0084d-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="0084d-114">設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的實體路徑。</span><span class="sxs-lookup"><span data-stu-id="0084d-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="0084d-115">建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。</span><span class="sxs-lookup"><span data-stu-id="0084d-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="0084d-116">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-116">Click **OK**.</span></span> <span data-ttu-id="0084d-117">隨即為 WCF 範例建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0084d-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0084d-118">這項工作只需執行一次, 因為所有 WCF 範例都使用相同的 servicemodelsamples Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0084d-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0084d-119">就此文件的用途而言，`virtual directory`一詞是 `Web application`的同義詞。</span><span class="sxs-lookup"><span data-stu-id="0084d-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="0084d-120">除了建立虛擬目錄以外, 您還必須設定其屬性, 讓 WCF 服務得以執行。</span><span class="sxs-lookup"><span data-stu-id="0084d-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="0084d-121">如需詳細資訊，請參閱下方。</span><span class="sxs-lookup"><span data-stu-id="0084d-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="0084d-122">在 IIS 5.1 或 6.0 中建立虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="0084d-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="0084d-123">開啟 [命令提示字元] 視窗`start inetmgr` , 然後輸入以開啟 Internet Information Services (IIS) MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="0084d-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="0084d-124">在左窗格中, 展開具有電腦名稱稱的節點, 然後展開 [**網站**] 節點。</span><span class="sxs-lookup"><span data-stu-id="0084d-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="0084d-125">以滑鼠右鍵按一下 [**預設的網站**], 然後選取 [新增] **、[虛擬目錄**] 以開啟 [虛擬目錄建立嚮導]。</span><span class="sxs-lookup"><span data-stu-id="0084d-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="0084d-126">在嚮導中, 輸入`servicemodelsamples`做為您所建立虛擬目錄的別名。</span><span class="sxs-lookup"><span data-stu-id="0084d-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="0084d-127">設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的路徑。</span><span class="sxs-lookup"><span data-stu-id="0084d-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="0084d-128">建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。</span><span class="sxs-lookup"><span data-stu-id="0084d-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="0084d-129">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0084d-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="0084d-130">預設會選取下列核取方塊：</span><span class="sxs-lookup"><span data-stu-id="0084d-130">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="0084d-131">**Read**</span><span class="sxs-lookup"><span data-stu-id="0084d-131">**Read**</span></span>  
  
    - <span data-ttu-id="0084d-132">**執行腳本 (例如 ASP)**</span><span class="sxs-lookup"><span data-stu-id="0084d-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="0084d-133">按 **[下一步**], 然後按一下 **[完成**] 以完成嚮導。</span><span class="sxs-lookup"><span data-stu-id="0084d-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0084d-134">這項工作只需執行一次, 因為所有 WCF 範例都使用相同的 servicemodelsamples 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="0084d-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="0084d-135">若要在 IIS 7.0 或7.5 中設定其他虛擬目錄屬性</span><span class="sxs-lookup"><span data-stu-id="0084d-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="0084d-136">按一下 servicemodelsamples 節點。</span><span class="sxs-lookup"><span data-stu-id="0084d-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="0084d-137">視窗的底部會有兩個檢視。</span><span class="sxs-lookup"><span data-stu-id="0084d-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="0084d-138">選取 [功能] [**視圖**] (如果尚未選取)。</span><span class="sxs-lookup"><span data-stu-id="0084d-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="0084d-139">按兩下專案以**流覽目錄**。</span><span class="sxs-lookup"><span data-stu-id="0084d-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="0084d-140">在 [動作] 窗格中, 選取 [**啟用**] 選項。</span><span class="sxs-lookup"><span data-stu-id="0084d-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="0084d-141">這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="0084d-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="0084d-142">最後，您必須設定 servicemodelsamples 資料夾的安全性屬性，讓其他使用者能夠存取此資料夾。</span><span class="sxs-lookup"><span data-stu-id="0084d-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="0084d-143">如需詳細資訊，請參閱下方。</span><span class="sxs-lookup"><span data-stu-id="0084d-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="0084d-144">若要在 IIS 5.1 或 6.0 中設定額外的虛擬目錄屬性</span><span class="sxs-lookup"><span data-stu-id="0084d-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="0084d-145">以滑鼠右鍵按一下 [servicemodelsamples] 節點, 然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="0084d-146">預設會選取下列核取方塊：</span><span class="sxs-lookup"><span data-stu-id="0084d-146">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="0084d-147">**Read**</span><span class="sxs-lookup"><span data-stu-id="0084d-147">**Read**</span></span>  
  
    - <span data-ttu-id="0084d-148">**記錄造訪**</span><span class="sxs-lookup"><span data-stu-id="0084d-148">**Log visits**</span></span>  
  
    - <span data-ttu-id="0084d-149">**為此資源編制索引**</span><span class="sxs-lookup"><span data-stu-id="0084d-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="0084d-150">選取 [**流覽目錄**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0084d-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="0084d-151">這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="0084d-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="0084d-152">若要在 IIS 7.0 或7.5 中設定資料夾的安全性屬性</span><span class="sxs-lookup"><span data-stu-id="0084d-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="0084d-153">巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。</span><span class="sxs-lookup"><span data-stu-id="0084d-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="0084d-154">以滑鼠右鍵按一下 [servicemodelsamples] 資料夾, 然後按一下 [**共用**] 或 [**共用于**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="0084d-155">按一下 [**新增**] 按鈕左邊的向下箭號。</span><span class="sxs-lookup"><span data-stu-id="0084d-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="0084d-156">選取 [**尋找**] 專案。</span><span class="sxs-lookup"><span data-stu-id="0084d-156">Select the **Find** entry.</span></span> <span data-ttu-id="0084d-157">[**選取使用者或群組**] 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0084d-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="0084d-158">按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="0084d-159">按一下 [**位置**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-159">Click **Locations**.</span></span> <span data-ttu-id="0084d-160">[**位置**] 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0084d-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="0084d-161">選取使用的電腦項目。</span><span class="sxs-lookup"><span data-stu-id="0084d-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="0084d-162">請務必選取本機電腦，而非列出的任何網域或網路項目。</span><span class="sxs-lookup"><span data-stu-id="0084d-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="0084d-163">選取電腦後, 按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0084d-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="0084d-164">按一下 [**立即尋找**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-164">Click **Find Now**.</span></span> <span data-ttu-id="0084d-165">這會將與本機電腦相關聯的物件填入到搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="0084d-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="0084d-166">在 [**名稱 (相對辨別名稱)** ] 資料行中尋找**IIS_IUSRS**專案。</span><span class="sxs-lookup"><span data-stu-id="0084d-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="0084d-167">選取該專案, 然後按一下 **[確定**] 以關閉搜尋結果視窗。</span><span class="sxs-lookup"><span data-stu-id="0084d-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="0084d-168">按一下 **[確定]** 以關閉 [**選取使用者或群組**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0084d-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="0084d-169">按一下 [**共用**] 保存變更。</span><span class="sxs-lookup"><span data-stu-id="0084d-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="0084d-170">啟用共用的變更完成後, 請按一下 [**完成**] 以關閉 [檔案**共用**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0084d-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="0084d-171">設定 IIS 5.1 或 6.0 中資料夾的安全性屬性</span><span class="sxs-lookup"><span data-stu-id="0084d-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="0084d-172">巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。</span><span class="sxs-lookup"><span data-stu-id="0084d-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="0084d-173">以滑鼠右鍵按一下 [ **servicemodelsamples** ] 資料夾, 然後按一下 [**共用和安全性]。**</span><span class="sxs-lookup"><span data-stu-id="0084d-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="0084d-174">按一下 [ **安全性** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0084d-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="0084d-175">如果您使用 IIS 6.0, 請在 [**群組或使用者名稱**] 方塊中, 檢查是否列出 [ **Internet Guest 帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="0084d-176">如果未列出：</span><span class="sxs-lookup"><span data-stu-id="0084d-176">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="0084d-177">按一下 [開始]，然後按一下 [控制台]。</span><span class="sxs-lookup"><span data-stu-id="0084d-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="0084d-178">如果您看不到 [**使用者帳戶**] 圖示, 請按一下 [**切換到類別目錄檢視**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="0084d-179">按一下 [**使用者帳戶**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="0084d-179">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="0084d-180">在 [或選擇控制台圖示] 底下, 按一下 [**使用者帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="0084d-181">在 [**使用者帳戶**] 對話方塊中, 按一下 [ **Advanced** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0084d-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="0084d-182">按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-182">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="0084d-183">在 [**本機使用者和群組**] 對話方塊中, 按一下以展開 [**使用者**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0084d-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="0084d-184">在右窗格中, 按兩下 [**網際網路來賓帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="0084d-185">在 [內容] 對話方塊中, 複製用來做為網際網路來賓帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="0084d-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="0084d-186">根據預設，該名稱開頭為 "USR_"，後面會加上電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="0084d-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="0084d-187">關閉 [內容] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0084d-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="0084d-188">關閉 [**本機使用者和群組**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0084d-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="0084d-189">關閉 [**使用者帳戶**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0084d-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="0084d-190">關閉 [其他**使用者帳戶**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0084d-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="0084d-191">在 [ **Servicemodelsamples 屬性**] 對話方塊的 [**安全性**] 索引標籤上, 按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="0084d-192">輸入電腦名稱稱, 後面加上反斜線, 然後貼上網際網路使用者帳戶的名稱, 例如 myMachineName\\% InternetGuestAccountName%</span><span class="sxs-lookup"><span data-stu-id="0084d-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="0084d-193">按一下 [**檢查名稱**] 以確認新增。</span><span class="sxs-lookup"><span data-stu-id="0084d-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="0084d-194">如果有效，該名稱會是全部大寫字母並加上底線。</span><span class="sxs-lookup"><span data-stu-id="0084d-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="0084d-195">針對 IIS 6.0, 也請檢查 [**群組或使用者名稱**] 方塊中是否列出 [網路服務]。</span><span class="sxs-lookup"><span data-stu-id="0084d-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="0084d-196">如果未列示 NETWORK SERVICE：</span><span class="sxs-lookup"><span data-stu-id="0084d-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="0084d-197">按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="0084d-197">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="0084d-198">在 [**選取使用者或群組**] 對話方塊中, 輸入電腦名稱稱, 後面加上反斜線。</span><span class="sxs-lookup"><span data-stu-id="0084d-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="0084d-199">在反斜線後面輸入**服務**(沒有空格)。</span><span class="sxs-lookup"><span data-stu-id="0084d-199">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="0084d-200">按一下 [**檢查名稱**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-200">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="0084d-201">如果找到多個名稱, 請選取 [**網路服務**], 然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0084d-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="0084d-202">按一下 **[確定]** 以關閉 [**選取使用者或群組**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0084d-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="0084d-203">如果您使用 Windows XP SP2 搭配 IIS 5.1, 請檢查 [**群組或使用者名稱**] 方塊中是否列出 [網際網路來賓帳戶] 和 [ASPNET]。</span><span class="sxs-lookup"><span data-stu-id="0084d-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="0084d-204">請注意, ASPNET 使用者可能是內建 [**使用者**] 安全性群組的成員。</span><span class="sxs-lookup"><span data-stu-id="0084d-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="0084d-205">若是如此, 則如果 [**使用者**] 群組列在對話方塊中, 您就不需要將它當做個別專案新增至允許的使用者清單。</span><span class="sxs-lookup"><span data-stu-id="0084d-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="0084d-206">若要檢查 ASPNET 是否為**Users**安全性群組的一部分:</span><span class="sxs-lookup"><span data-stu-id="0084d-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="0084d-207">在 [**開始**] 功能表上, 按一下 [**控制台**]。</span><span class="sxs-lookup"><span data-stu-id="0084d-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="0084d-208">按一下 [**使用者帳戶**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="0084d-208">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="0084d-209">在 [**群組**] 資料行中, 檢查**ASPNET**的值是否為「使用者」。</span><span class="sxs-lookup"><span data-stu-id="0084d-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0084d-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0084d-210">See also</span></span>

- [<span data-ttu-id="0084d-211">Internet Information Service 裝載指示</span><span class="sxs-lookup"><span data-stu-id="0084d-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
