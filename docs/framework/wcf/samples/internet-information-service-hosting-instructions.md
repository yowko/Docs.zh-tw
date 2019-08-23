---
title: Internet Information Service 裝載指示
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929116"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="2ef42-102">Internet Information Service 裝載指示</span><span class="sxs-lookup"><span data-stu-id="2ef42-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="2ef42-103">若要執行由網際網路資訊服務 (IIS) 裝載的範例，您必須確定 IIS 已正確安裝並正在執行中。</span><span class="sxs-lookup"><span data-stu-id="2ef42-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="2ef42-104">若要在 Windows Server 2008 R2 上安裝 IIS 7.5</span><span class="sxs-lookup"><span data-stu-id="2ef42-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="2ef42-105">從**伺服器管理員**選取 [**角色]。**</span><span class="sxs-lookup"><span data-stu-id="2ef42-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="2ef42-106">在 [**角色摘要**] 底下, 按一下 [**新增角色**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2ef42-107">按 **[下一步**] 以顯示 [**選取伺服器角色**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2ef42-108">從 [**角色**] 清單中選取 [**應用程式伺服器**], 然後按兩次 **[下一步]** , 顯示應用程式伺服器角色的 [**選取角色服務**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2ef42-109">選取 [**網頁伺服器 (IIS)** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2ef42-110">如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的功能**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2ef42-111">按兩次 [**下一步**], 顯示網頁伺服器 (IIS) 角色的 [**選取角色服務**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2ef42-112">展開 [**管理工具**], 然後展開 [ **IIS 6 管理相容性**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2ef42-113">選取 [ **IIS 6 腳本工具**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2ef42-114">如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的角色服務**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2ef42-115">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2ef42-116">如果選取專案的摘要正確, 請按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2ef42-117">當安裝完成時, 按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="2ef42-118">若要在 Windows 7 上安裝 IIS 7.5 版</span><span class="sxs-lookup"><span data-stu-id="2ef42-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="2ef42-119">按一下 [**開始**], 然後按一下 [**控制台**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="2ef42-120">開啟 [**程式**] 群組。</span><span class="sxs-lookup"><span data-stu-id="2ef42-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2ef42-121">在 [**程式和功能**] 底下, 按一下 [**開啟或關閉 Windows 功能**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2ef42-122">[**使用者帳戶控制**] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="2ef42-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2ef42-123">按一下 [ **繼續**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2ef42-124">[ **Windows 功能**] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="2ef42-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2ef42-125">展開標示為 [ **Internet Information Services**] 的專案。</span><span class="sxs-lookup"><span data-stu-id="2ef42-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2ef42-126">展開標示為 [ **World Wide Web 服務**] 的專案。</span><span class="sxs-lookup"><span data-stu-id="2ef42-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2ef42-127">展開標記為 [**應用程式開發功能**] 的專案。</span><span class="sxs-lookup"><span data-stu-id="2ef42-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2ef42-128">請確定已選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="2ef42-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="2ef42-129">**.NET 擴充性**</span><span class="sxs-lookup"><span data-stu-id="2ef42-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="2ef42-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="2ef42-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="2ef42-131">**ISAPI 擴充程式**</span><span class="sxs-lookup"><span data-stu-id="2ef42-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="2ef42-132">**ISAPI 篩選器**</span><span class="sxs-lookup"><span data-stu-id="2ef42-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="2ef42-133">在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**一般 Http 功能**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="2ef42-134">請確定已選取 [**靜態內容**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="2ef42-135">在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**安全性**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="2ef42-136">請確定已選取 [ **Windows 驗證**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="2ef42-137">在 [ **Internet Information Services** ] 目錄底下, 展開標示為 [ **Web 管理工具**] 的專案, 然後選取 [ **IIS 管理主控台**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="2ef42-138">展開標記為 [ **iis 6 管理相容性**] 的專案, 然後選取 [ **Iis 6 腳本工具**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2ef42-139">在 [ **Internet Information Services** ] 目錄底下, 展開標記為 [ **Microsoft .NET Framework 3.5.1**] 的專案, 然後選取 [ **Windows Communication Foundation Http 啟用**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2ef42-140">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="2ef42-141">在 Windows Server 2008 上安裝 IIS 7.0 版</span><span class="sxs-lookup"><span data-stu-id="2ef42-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="2ef42-142">從**伺服器管理員**選取 [**角色**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="2ef42-143">在 [**角色摘要**] 底下, 按一下 [**新增角色**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2ef42-144">按 **[下一步**] 以顯示 [**選取伺服器角色**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2ef42-145">從 [**角色**] 清單中選取 [**應用程式伺服器**], 然後按兩次 **[下一步]** , 顯示應用程式伺服器角色的 [**選取角色服務**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2ef42-146">選取 **[網頁伺服器 (IIS)** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2ef42-147">如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的功能**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2ef42-148">按兩次 [**下一步**], 顯示網頁伺服器 (IIS) 角色的 [**選取角色服務**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ef42-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2ef42-149">展開 [**管理工具**], 然後展開 [ **IIS 6 管理相容性**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2ef42-150">選取 [ **IIS 6 腳本工具**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2ef42-151">如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的角色服務**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2ef42-152">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2ef42-153">如果選取專案的摘要正確, 請按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2ef42-154">當安裝完成時, 按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="2ef42-155">在 Windows Vista 上安裝 IIS 7.0 版</span><span class="sxs-lookup"><span data-stu-id="2ef42-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="2ef42-156">按一下 [開始]，然後按一下 [控制台]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="2ef42-157">選取 [**程式**] 群組。</span><span class="sxs-lookup"><span data-stu-id="2ef42-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2ef42-158">在 [**程式和功能**] 底下, 按一下 [**開啟或關閉 Windows 功能**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2ef42-159">[**使用者帳戶控制**] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="2ef42-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2ef42-160">按一下 [ **繼續**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2ef42-161">[ **Windows 功能**] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="2ef42-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2ef42-162">展開標示為 [ **Internet Information Services**] 的專案。</span><span class="sxs-lookup"><span data-stu-id="2ef42-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2ef42-163">展開標示為 [ **World Wide Web 服務**] 的專案。</span><span class="sxs-lookup"><span data-stu-id="2ef42-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2ef42-164">展開標記為 [**應用程式開發功能**] 的專案。</span><span class="sxs-lookup"><span data-stu-id="2ef42-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2ef42-165">請確定已選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="2ef42-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="2ef42-166">**.NET 擴充性**</span><span class="sxs-lookup"><span data-stu-id="2ef42-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="2ef42-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="2ef42-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="2ef42-168">**ISAPI 擴充程式**</span><span class="sxs-lookup"><span data-stu-id="2ef42-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="2ef42-169">**ISAPI 篩選器**</span><span class="sxs-lookup"><span data-stu-id="2ef42-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="2ef42-170">展開標記為 [ **Web 管理工具**] 的專案, 然後選取 [ **IIS 管理主控台**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="2ef42-171">在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**一般 Http 功能**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="2ef42-172">請確定已選取 [**靜態內容**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="2ef42-173">在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**安全性**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="2ef42-174">請確定已選取 [ **Windows 驗證**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="2ef42-175">展開標記為 [ **iis 6 管理相容性**] 的專案, 然後選取 [ **Iis 6 腳本工具**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2ef42-176">展開標記為 [ **Microsoft .NET Framework 3.0**] 的專案, 然後選取 [ **Windows Communication Foundation Http 啟用**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2ef42-177">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="2ef42-178">在 Windows Server 2003 上安裝 IIS 6.0 版</span><span class="sxs-lookup"><span data-stu-id="2ef42-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="2ef42-179">從 [**管理您的伺服器**], 按一下 [**新增或移除角色**], 然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef42-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="2ef42-180">從 [**伺服器角色**] 清單中選取 [**應用程式伺服器 (IIS, ASP.NET)** ], 然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef42-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="2ef42-181">選取 [**啟用 ASP.NET** ] 核取方塊, 然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef42-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2ef42-182">如果選項的摘要正確，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="2ef42-183">若要在已安裝 Service Pack 2 和 Service Pack 3 的 Windows XP 上安裝 IIS 5.1 版</span><span class="sxs-lookup"><span data-stu-id="2ef42-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="2ef42-184">在 [控制台] 中, 按一下 [**新增或移除程式**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="2ef42-185">在 [**新增或移除程式**] 對話方塊中, 按一下 [**新增/移除 Windows 元件**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="2ef42-186">在 [ **Windows 元件]** 中, 選取 [ **Internet Information Services (IIS)** ] 核取方塊, 然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef42-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2ef42-187">如果顯示 [**需要**檔案] 對話方塊, 請插入作業系統安裝光碟, 流覽至 [i386] 資料夾, 然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef42-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="2ef42-188">當安裝完成時, 按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="2ef42-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="2ef42-189">關閉 [**新增或移除程式**] 對話方塊, 然後關閉 [**控制台**]。</span><span class="sxs-lookup"><span data-stu-id="2ef42-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="2ef42-190">確認 IIS 和 ASP.NET 安裝</span><span class="sxs-lookup"><span data-stu-id="2ef42-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="2ef42-191">將本主題結尾處的 HTML 檔儲存在根 \InetPub\wwwroot 目錄，並重新命名為 Default.aspx。</span><span class="sxs-lookup"><span data-stu-id="2ef42-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="2ef42-192">開啟瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="2ef42-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="2ef42-193">在`http://localhost/Default.aspx` [位址] 方塊中輸入, 然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="2ef42-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="2ef42-194">這時應該會出現包含文字 "Hello World" 的網頁。</span><span class="sxs-lookup"><span data-stu-id="2ef42-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ef42-195">每次您安裝新版的 .NET Framework 時, 都必須重新註冊 aspnet_isapi 做為 IIS 的 Web 服務延伸模組。</span><span class="sxs-lookup"><span data-stu-id="2ef42-195">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="2ef42-196">若要這樣做，請發出 `aspnet_regiis –I –enable` 命令。</span><span class="sxs-lookup"><span data-stu-id="2ef42-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="2ef42-197">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="2ef42-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
