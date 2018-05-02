---
title: 逐步解說：使用用戶端應用程式服務
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe0e446a0005ffcbf296c2728fd93056c3e38f2a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-client-application-services"></a><span data-ttu-id="da152-102">逐步解說：使用用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="da152-102">Walkthrough: Using Client Application Services</span></span>
<span data-ttu-id="da152-103">本主題說明如何建立使用用戶端應用程式服務驗證使用者，以及擷取使用者角色和設定的 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-103">This topic describes how to create a Windows application that uses client application services to authenticate users and retrieve user roles and settings.</span></span>  
  
 <span data-ttu-id="da152-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="da152-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="da152-105">建立 Windows Form 應用程式，並使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案設計工具啟用及設定用戶端應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="da152-105">Create a Windows Forms application and use the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project designer to enable and configure client application services.</span></span>  
  
-   <span data-ttu-id="da152-106">建立簡單的 ASP.NET Web 服務應用程式，以裝載應用程式服務並測試用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="da152-106">Create a simple ASP.NET Web Service application to host the application services and test your client configuration.</span></span>  
  
-   <span data-ttu-id="da152-107">將表單驗證加入應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-107">Add forms authentication to your application.</span></span> <span data-ttu-id="da152-108">一開始會使用硬式編碼的使用者名稱和密碼測試服務。</span><span class="sxs-lookup"><span data-stu-id="da152-108">You will start by using a hard-coded user name and password to test the service.</span></span> <span data-ttu-id="da152-109">然後將登入表單指定為應用程式組態中的認證提供者予以加入。</span><span class="sxs-lookup"><span data-stu-id="da152-109">You will then add a login form by specifying it as a credentials provider in your application configuration.</span></span>  
  
-   <span data-ttu-id="da152-110">加入以角色為基礎的功能，並且只針對 "manager" 角色的使用者啟用和顯示按鈕。</span><span class="sxs-lookup"><span data-stu-id="da152-110">Add role-based functionality, enabling and displaying a button only for users in the "manager" role.</span></span>  
  
-   <span data-ttu-id="da152-111">存取 Web 設定。</span><span class="sxs-lookup"><span data-stu-id="da152-111">Access Web settings.</span></span> <span data-ttu-id="da152-112">一開始會在專案設計工具的 [設定]  頁面上載入已驗證 (測試) 使用者的 Web 設定。</span><span class="sxs-lookup"><span data-stu-id="da152-112">You will start by loading Web settings for an authenticated (test) user on the **Settings** page of the project designer.</span></span> <span data-ttu-id="da152-113">然後使用 Windows Form 設計工具將文字方塊繫結至 Web 設定。</span><span class="sxs-lookup"><span data-stu-id="da152-113">You will then use the Windows Forms Designer to bind a text box to a Web setting.</span></span> <span data-ttu-id="da152-114">最後再將已修改的值儲存回伺服器。</span><span class="sxs-lookup"><span data-stu-id="da152-114">Finally, you will save the modified value back to the server.</span></span>  
  
-   <span data-ttu-id="da152-115">實作登出。</span><span class="sxs-lookup"><span data-stu-id="da152-115">Implement logout.</span></span> <span data-ttu-id="da152-116">您會將登出選項加入表單，然後呼叫登出方法。</span><span class="sxs-lookup"><span data-stu-id="da152-116">You will add a logout option to the form and call a logout method.</span></span>  
  
-   <span data-ttu-id="da152-117">啟用離線模式。</span><span class="sxs-lookup"><span data-stu-id="da152-117">Enable offline mode.</span></span> <span data-ttu-id="da152-118">您會提供核取方塊，讓使用者指定其連接狀態。</span><span class="sxs-lookup"><span data-stu-id="da152-118">You will provide a check box so that users can specify their connection status.</span></span> <span data-ttu-id="da152-119">然後使用這個值指定用戶端應用程式服務提供者，是否使用本機快取資料而不是存取其 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="da152-119">You will then use this value to specify whether the client application service providers will use locally cached data instead of accessing their Web services.</span></span> <span data-ttu-id="da152-120">最後當應用程式返回線上模式時，再重新驗證目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="da152-120">Finally, you will re-authenticate the current user when the application returns to online mode.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="da152-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="da152-121">Prerequisites</span></span>  
 <span data-ttu-id="da152-122">您需要下列元件才能完成這個逐步解說：</span><span class="sxs-lookup"><span data-stu-id="da152-122">You need the following component to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="da152-123">.</span><span class="sxs-lookup"><span data-stu-id="da152-123">.</span></span>  
  
## <a name="creating-the-client-application"></a><span data-ttu-id="da152-124">建立用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="da152-124">Creating the Client Application</span></span>  
 <span data-ttu-id="da152-125">首先您必須建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="da152-125">The first thing that you will do is create a Windows Forms project.</span></span> <span data-ttu-id="da152-126">本逐步解說使用 Windows Form，因為很多人已熟悉這項功能，而且其程序類似 Windows Presentation Foundation (WPF) 專案。</span><span class="sxs-lookup"><span data-stu-id="da152-126">This walkthrough uses Windows Forms because more people are familiar with it, but the process is similar for Windows Presentation Foundation (WPF) projects.</span></span>  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a><span data-ttu-id="da152-127">建立用戶端應用程式並啟用用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="da152-127">To create a client application and enable client application services</span></span>  
  
1.  <span data-ttu-id="da152-128">在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中，選取 [檔案 &#124; 新增 &#124; 專案] 功能表選項。</span><span class="sxs-lookup"><span data-stu-id="da152-128">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], select the **File &#124; New &#124; Project** menu option.</span></span>  
  
2.  <span data-ttu-id="da152-129">在 [新增專案] 對話方塊中，展開 [專案類型] 窗格中的 [Visual Basic] 或 [Visual C#] 節點，然後選取 [Windows] 專案類型。</span><span class="sxs-lookup"><span data-stu-id="da152-129">In the **New Project** dialog box, in the **Project types** pane, expand the **Visual Basic** or **Visual C#** node and select the **Windows** project type.</span></span>  
  
3.  <span data-ttu-id="da152-130">確定已選取 [.NET Framework 3.5]  ，然後選取 [Windows Form 應用程式]  範本。</span><span class="sxs-lookup"><span data-stu-id="da152-130">Make sure that **.NET Framework 3.5** is selected, and then select the **Windows Forms Application** template.</span></span>  
  
4.  <span data-ttu-id="da152-131">將專案的 [名稱]  變更為 `ClientAppServicesDemo`，然後按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="da152-131">Change the project **Name** to `ClientAppServicesDemo`, and then click **OK**.</span></span>  
  
     <span data-ttu-id="da152-132">在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]中隨即開啟新的 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="da152-132">A new Windows Forms project is opened in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
5.  <span data-ttu-id="da152-133">在 [專案]  功能表上，選取 [ClientAppServicesDemo 屬性] 。</span><span class="sxs-lookup"><span data-stu-id="da152-133">On the **Project** menu, select **ClientAppServicesDemo Properties**.</span></span>  
  
     <span data-ttu-id="da152-134">[專案設計工具] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-134">The project designer appears.</span></span>  
  
6.  <span data-ttu-id="da152-135">在 [服務]  索引標籤上，選取 [啟用用戶端應用程式服務] 。</span><span class="sxs-lookup"><span data-stu-id="da152-135">On the **Services** tab, select **Enable client application services**.</span></span>  
  
7.  <span data-ttu-id="da152-136">確定選取了 [使用表單驗證]  ，然後將 [驗證服務位置] 、[角色服務位置] 及 [Web 設定服務位置]  設定為 `http://localhost:55555/AppServices`。</span><span class="sxs-lookup"><span data-stu-id="da152-136">Make sure that **Use Forms authentication** is selected, and then set **Authentication service location**, **Roles service location**, and **Web settings service location** to `http://localhost:55555/AppServices`.</span></span>  
  
8.  <span data-ttu-id="da152-137">在 Visual Basic 的 [應用程式] 索引標籤上，將 [驗證模式] 設定為 [由應用程式定義]。</span><span class="sxs-lookup"><span data-stu-id="da152-137">For Visual Basic, on the **Application** tab, set **Authentication mode** to **Application-defined**.</span></span>  
  
 <span data-ttu-id="da152-138">設計工具會將指定的設定儲存在應用程式的 app.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="da152-138">The designer stores the specified settings in the application's app.config file.</span></span>  
  
 <span data-ttu-id="da152-139">此時，應用程式會設定為從相同的主機存取這三種服務。</span><span class="sxs-lookup"><span data-stu-id="da152-139">At this point, the application is configured to access all three services from the same host.</span></span> <span data-ttu-id="da152-140">在下一節中，您將建立以簡單 Web 服務應用程式呈現的主機，以便您測試用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="da152-140">In the next section, you will create the host as a simple Web service application, enabling you to test your client configuration.</span></span>  
  
## <a name="creating-the-application-services-host"></a><span data-ttu-id="da152-141">建立應用程式服務主機</span><span class="sxs-lookup"><span data-stu-id="da152-141">Creating the Application Services Host</span></span>  
 <span data-ttu-id="da152-142">在本節中，您將建立簡單的 Web 服務應用程式，以便從本機 SQL Server Compact 資料庫檔案存取使用者資料。</span><span class="sxs-lookup"><span data-stu-id="da152-142">In this section, you will create a simple Web service application that accesses user data from a local SQL Server Compact database file.</span></span> <span data-ttu-id="da152-143">接下來，您將會使用 [ASP.NET Web Site Administration Tool](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)植入資料庫。</span><span class="sxs-lookup"><span data-stu-id="da152-143">Then, you will populate the database using the [ASP.NET Web Site Administration Tool](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec).</span></span> <span data-ttu-id="da152-144">這個簡單的組態可讓您快速地測試用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-144">This simple configuration enables you to quickly test your client application.</span></span> <span data-ttu-id="da152-145">除此之外，您還可以設定 Web 服務主機，以便從完整的 SQL Server 資料庫存取使用者資料，或透過自訂 <xref:System.Web.Security.MembershipProvider> 和 <xref:System.Web.Security.RoleProvider> 類別來存取使用者資料。</span><span class="sxs-lookup"><span data-stu-id="da152-145">As an alternative, you can configure the Web service host to access user data from a full SQL Server database or through custom <xref:System.Web.Security.MembershipProvider> and <xref:System.Web.Security.RoleProvider> classes.</span></span> <span data-ttu-id="da152-146">如需詳細資訊，請參閱 [Creating and Configuring the Application Services Database for SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)。</span><span class="sxs-lookup"><span data-stu-id="da152-146">For more information, see [Creating and Configuring the Application Services Database for SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).</span></span>  
  
 <span data-ttu-id="da152-147">在下列程序中，您將建立並設定 AppServices Web 服務。</span><span class="sxs-lookup"><span data-stu-id="da152-147">In the following procedure, you create and configure the AppServices Web service.</span></span>  
  
#### <a name="to-create-and-configure-the-application-services-host"></a><span data-ttu-id="da152-148">建立並設定應用程式服務主機</span><span class="sxs-lookup"><span data-stu-id="da152-148">To create and configure the application services host</span></span>  
  
1.  <span data-ttu-id="da152-149">在 [方案總管] 中，選取 ClientAppServicesDemo 解決方案，然後在 [檔案] 功能表上，選取 [新增 &#124; 新增專案]。</span><span class="sxs-lookup"><span data-stu-id="da152-149">In **Solution Explorer**, select the ClientAppServicesDemo solution, and then on the **File** menu, select **Add &#124; New Project**.</span></span>  
  
2.  <span data-ttu-id="da152-150">在 [加入新的專案] 對話方塊中，展開 [專案類型] 窗格中的 [Visual Basic] 或 [Visual C#] 節點，然後選取 [Web] 專案類型。</span><span class="sxs-lookup"><span data-stu-id="da152-150">In the **Add New Project** dialog box, in the **Project types** pane, expand the **Visual Basic** or **Visual C#** node and select the **Web** project type.</span></span>  
  
3.  <span data-ttu-id="da152-151">確定已選取 [.NET Framework 3.5]  ，然後選取 [ASP.NET Web 服務應用程式]  範本。</span><span class="sxs-lookup"><span data-stu-id="da152-151">Make sure that **.NET Framework 3.5** is selected, and then select the **ASP.NET Web Service Application** template.</span></span>  
  
4.  <span data-ttu-id="da152-152">將專案的 [名稱]  變更為 `AppServices` ，然後按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="da152-152">Change the project **Name** to `AppServices` and then click **OK**.</span></span>  
  
     <span data-ttu-id="da152-153">新的 ASP.NET Web 服務應用程式專案隨即加入方案，並在編輯器中顯示 Service1.asmx.vb 或 Service1.asmx.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="da152-153">A new ASP.NET Web service application project is added to the solution, and the Service1.asmx.vb or Service1.asmx.cs file appears in the editor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da152-154">這個範例中不會使用 Service1.asmx.vb 或 Service1.asmx.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="da152-154">The Service1.asmx.vb or Service1.asmx.cs file is not used in this example.</span></span> <span data-ttu-id="da152-155">如果您想要保持工作環境的整齊，可以將其關閉，並將其從 [方案總管] 中刪除。</span><span class="sxs-lookup"><span data-stu-id="da152-155">If you want to keep your work environment uncluttered, you can close it and delete it from **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="da152-156">在 [方案總管] 中，選取 AppServices 專案，然後在 [專案]  功能表上，選取 [AppServices 屬性] 。</span><span class="sxs-lookup"><span data-stu-id="da152-156">In **Solution Explorer**, select the AppServices project, and then on the **Project** menu, select **AppServices Properties**.</span></span>  
  
     <span data-ttu-id="da152-157">[專案設計工具] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-157">The project designer appears.</span></span>  
  
6.  <span data-ttu-id="da152-158">在 [Web]  索引標籤上，確定已選取 [使用 Visual Studio 程式開發伺服器]  。</span><span class="sxs-lookup"><span data-stu-id="da152-158">On the **Web** tab, make sure that **Use Visual Studio Development Server** is selected.</span></span>  
  
7.  <span data-ttu-id="da152-159">選取 [指定通訊埠] ，再將值指定為 `55555`，然後將 [虛擬路徑]  設定為 `/AppServices`。</span><span class="sxs-lookup"><span data-stu-id="da152-159">Select **Specific port**, specify a value of `55555`, and then set **Virtual path** to `/AppServices`.</span></span>  
  
8.  <span data-ttu-id="da152-160">儲存所有檔案。</span><span class="sxs-lookup"><span data-stu-id="da152-160">Save all files.</span></span>  
  
9. <span data-ttu-id="da152-161">在 [方案總管] 中，開啟 Web.config，然後尋找 `<system.web>` 開頭標記。</span><span class="sxs-lookup"><span data-stu-id="da152-161">In **Solution Explorer**, open Web.config and find the `<system.web>` opening tag.</span></span>  
  
10. <span data-ttu-id="da152-162">在 `<system.web>` 標記 (Tag) 之前加入下列標記 (Markup)。</span><span class="sxs-lookup"><span data-stu-id="da152-162">Add the following markup before the `<system.web>` tag.</span></span>  
  
     <span data-ttu-id="da152-163">在這個標記中的 `authenticationService`、 `profileService`和 `roleService` 項目會啟用及設定應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="da152-163">The `authenticationService`, `profileService`, and `roleService` elements in this markup enable and configure the application services.</span></span> <span data-ttu-id="da152-164">基於測試目的， `requireSSL` 項目的 `authenticationService` 屬性會設定為 "false"。</span><span class="sxs-lookup"><span data-stu-id="da152-164">For testing purposes, the `requireSSL` attribute of the `authenticationService` element is set to "false".</span></span> <span data-ttu-id="da152-165">`readAccessProperties` 項目的 `writeAccessProperties` 和 `profileService` 屬性 (Attribute) 表示 `WebSettingsTestText` 屬性 (Property) 是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="da152-165">The `readAccessProperties` and `writeAccessProperties` attributes of the `profileService` element indicate that the `WebSettingsTestText` property is read/write.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da152-166">在實際執行的程式碼中，一定要透過 Secure Sockets Layer (SSL，使用 HTTPS 通訊協定) 存取驗證服務。</span><span class="sxs-lookup"><span data-stu-id="da152-166">In production code, you should always access the authentication service over the secure sockets layer (SSL, by using the HTTPS protocol).</span></span> <span data-ttu-id="da152-167">如需如何設定 SSL 的資訊，請參閱 [Configuring Secure Sockets Layer (IIS 6.0 Operations Guide)](http://go.microsoft.com/fwlink/?LinkId=91844)(設定安全通訊端層 (IIS 6.0 操作指南))。</span><span class="sxs-lookup"><span data-stu-id="da152-167">For information about how to set up SSL, see [Configuring Secure Sockets Layer (IIS 6.0 Operations Guide)](http://go.microsoft.com/fwlink/?LinkId=91844).</span></span>  
  
    ```xml  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. <span data-ttu-id="da152-168">在 `<system.web>` 開頭標記 (Tag) 之後加入下列標記 (Markup)，將其包含在 `<system.web>` 項目中。</span><span class="sxs-lookup"><span data-stu-id="da152-168">Add the following markup after the `<system.web>` opening tag so that it is within the `<system.web>` element.</span></span>  
  
     <span data-ttu-id="da152-169">`profile` 項目會設定名為 `WebSettingsTestText`的單一 Web 設定。</span><span class="sxs-lookup"><span data-stu-id="da152-169">The `profile` element configures a single Web setting named `WebSettingsTestText`.</span></span>  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 <span data-ttu-id="da152-170">在下列程序中，您將使用 [ASP.NET 網站管理工具] 來完成服務組態，並填入本機資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="da152-170">In the following procedure, you use the ASP.NET Web Site Administration tool to complete the service configuration and populate the local database file.</span></span> <span data-ttu-id="da152-171">您將加入兩位使用者，並將其命名為 `employee` 及 `manager` 。兩者會分屬兩個同名的角色。</span><span class="sxs-lookup"><span data-stu-id="da152-171">You will add two users named `employee` and `manager` belonging to two roles with the same names.</span></span> <span data-ttu-id="da152-172">使用者密碼各為 `employee!` 及 `manager!` 。</span><span class="sxs-lookup"><span data-stu-id="da152-172">The user passwords are `employee!` and `manager!` respectively.</span></span>  
  
#### <a name="to-configure-membership-and-roles"></a><span data-ttu-id="da152-173">設定成員資格和角色</span><span class="sxs-lookup"><span data-stu-id="da152-173">To configure membership and roles</span></span>  
  
1.  <span data-ttu-id="da152-174">在 [方案總管] 中，選取 AppServices 專案，然後在 [專案]  功能表上，選取 [ASP.NET 組態] 。</span><span class="sxs-lookup"><span data-stu-id="da152-174">In **Solution Explorer**, select the AppServices project, and then on the **Project** menu, select **ASP.NET Configuration**.</span></span>  
  
     <span data-ttu-id="da152-175">[ASP.NET 網站管理工具]  隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-175">The **ASP.NET Web Site Administration Tool** appears.</span></span>  
  
2.  <span data-ttu-id="da152-176">在 [安全性]  索引標籤上，按一下 [使用安全性設定精靈，逐步設定安全性] 。</span><span class="sxs-lookup"><span data-stu-id="da152-176">On the **Security** tab, click **Use the security Setup Wizard to configure security step by step**.</span></span>  
  
     <span data-ttu-id="da152-177">[安全性設定精靈]  隨即出現，並顯示 [歡迎使用]  步驟。</span><span class="sxs-lookup"><span data-stu-id="da152-177">The **Security Setup Wizard** appears and displays the **Welcome** step.</span></span>  
  
3.  <span data-ttu-id="da152-178">按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="da152-178">Click **Next**.</span></span>  
  
     <span data-ttu-id="da152-179">[選取存取方法]  步驟隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-179">The **Select Access Method** step appears.</span></span>  
  
4.  <span data-ttu-id="da152-180">選取 [從網際網路] 。</span><span class="sxs-lookup"><span data-stu-id="da152-180">Select **From the internet**.</span></span> <span data-ttu-id="da152-181">這會將服務設定為使用表單驗證，而不是 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="da152-181">This configures the service to use Forms authentication instead of Windows authentication.</span></span>  
  
5.  <span data-ttu-id="da152-182">按 [ **下一步** ] 兩次。</span><span class="sxs-lookup"><span data-stu-id="da152-182">Click **Next** twice.</span></span>  
  
     <span data-ttu-id="da152-183">[定義角色]  步驟隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-183">The **Define Roles** step appears.</span></span>  
  
6.  <span data-ttu-id="da152-184">選取 [啟用這個網站的角色] 。</span><span class="sxs-lookup"><span data-stu-id="da152-184">Select **Enable roles for this Web site**.</span></span>  
  
7.  <span data-ttu-id="da152-185">按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="da152-185">Click **Next**.</span></span> <span data-ttu-id="da152-186">[建立新角色]  表單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-186">The **Create New Role** form appears.</span></span>  
  
8.  <span data-ttu-id="da152-187">在 [新角色名稱]  文字方塊中輸入 `manager` ，然後按一下 [加入角色] 。</span><span class="sxs-lookup"><span data-stu-id="da152-187">In the **New Role Name** text box, type `manager` and then click **Add Role**.</span></span>  
  
     <span data-ttu-id="da152-188">具有指定值的 [現有角色]  資料表隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-188">The **Existing Roles** table appears with the specified value.</span></span>  
  
9. <span data-ttu-id="da152-189">將 [新角色名稱]  文字方塊中的 `manager` 置換成 `employee` ，然後按一下 [加入角色] 。</span><span class="sxs-lookup"><span data-stu-id="da152-189">In the **New Role Name** text box, replace `manager` with `employee` and then click **Add Role**.</span></span>  
  
     <span data-ttu-id="da152-190">[現有角色]  資料表中隨即出現新的值。</span><span class="sxs-lookup"><span data-stu-id="da152-190">The new value appears in the **Existing Roles** table.</span></span>  
  
10. <span data-ttu-id="da152-191">按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="da152-191">Click **Next**.</span></span>  
  
     <span data-ttu-id="da152-192">[加入新的使用者]  步驟隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-192">The **Add New Users** step appears.</span></span>  
  
11. <span data-ttu-id="da152-193">在 [建立使用者]  表單中，指定下列值。</span><span class="sxs-lookup"><span data-stu-id="da152-193">In the **Create User** form, specify the following values.</span></span>  
  
  	|||  
  	|-|-|  
  	|<span data-ttu-id="da152-194">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="da152-194">**User Name**</span></span>|`manager`|  
  	|<span data-ttu-id="da152-195">**密碼**</span><span class="sxs-lookup"><span data-stu-id="da152-195">**Password**</span></span>|`manager!`|  
  	|<span data-ttu-id="da152-196">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="da152-196">**Confirm Password**</span></span>|`manager!`|  
  	|<span data-ttu-id="da152-197">**電子郵件**</span><span class="sxs-lookup"><span data-stu-id="da152-197">**Email**</span></span>|`manager@contoso.com`|  
  	|<span data-ttu-id="da152-198">**安全性問題**</span><span class="sxs-lookup"><span data-stu-id="da152-198">**Security Question**</span></span>|`manager`|  
  	|<span data-ttu-id="da152-199">**安全性解答**</span><span class="sxs-lookup"><span data-stu-id="da152-199">**Security Answer**</span></span>|`manager`|  
  
12. <span data-ttu-id="da152-200">按一下 [建立使用者] 。</span><span class="sxs-lookup"><span data-stu-id="da152-200">Click **Create User**.</span></span>  
  
     <span data-ttu-id="da152-201">成功訊息隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-201">A success message appears.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da152-202">[電子郵件]、[安全性問題] 及 [安全性解答] 是表單的必要值，但這個範例中並未使用。</span><span class="sxs-lookup"><span data-stu-id="da152-202">The **Email**, **Security Question**, and **Security Answer** values are required by the form, but are not used in this example.</span></span>  
  
13. <span data-ttu-id="da152-203">按一下 [ **繼續**]。</span><span class="sxs-lookup"><span data-stu-id="da152-203">Click **Continue**.</span></span>  
  
     <span data-ttu-id="da152-204">[建立使用者]  表單隨即再度出現。</span><span class="sxs-lookup"><span data-stu-id="da152-204">The **Create User** form reappears.</span></span>  
  
14. <span data-ttu-id="da152-205">在 [建立使用者]  表單中，指定下列值。</span><span class="sxs-lookup"><span data-stu-id="da152-205">In the **Create User** form, specify the following values.</span></span>  
  
  	|||  
  	|-|-|  
  	|<span data-ttu-id="da152-206">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="da152-206">**User Name**</span></span>|`employee`|  
  	|<span data-ttu-id="da152-207">**密碼**</span><span class="sxs-lookup"><span data-stu-id="da152-207">**Password**</span></span>|`employee!`|  
  	|<span data-ttu-id="da152-208">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="da152-208">**Confirm Password**</span></span>|`employee!`|  
  	|<span data-ttu-id="da152-209">**電子郵件**</span><span class="sxs-lookup"><span data-stu-id="da152-209">**Email**</span></span>|`employee@contoso.com`|  
  	|<span data-ttu-id="da152-210">**安全性問題**</span><span class="sxs-lookup"><span data-stu-id="da152-210">**Security Question**</span></span>|`Employee`|  
  	|<span data-ttu-id="da152-211">**安全性解答**</span><span class="sxs-lookup"><span data-stu-id="da152-211">**Security Answer**</span></span>|`employee`|  
  
15. <span data-ttu-id="da152-212">按一下 [建立使用者] 。</span><span class="sxs-lookup"><span data-stu-id="da152-212">Click **Create User**.</span></span>  
  
     <span data-ttu-id="da152-213">成功訊息隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-213">A success message appears.</span></span>  
  
16. <span data-ttu-id="da152-214">按一下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="da152-214">Click **Finish**.</span></span>  
  
     <span data-ttu-id="da152-215">[網站管理工具]  隨即再度出現。</span><span class="sxs-lookup"><span data-stu-id="da152-215">The **Web Site Administration Tool** reappears.</span></span>  
  
17. <span data-ttu-id="da152-216">按一下 [Manager 使用者] 。</span><span class="sxs-lookup"><span data-stu-id="da152-216">Click **Manager users**.</span></span>  
  
     <span data-ttu-id="da152-217">使用者清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-217">The list of users appears.</span></span>  
  
18. <span data-ttu-id="da152-218">針對 [employee]  使用者按一下 [編輯角色]  ，然後選取 [employee]  角色。</span><span class="sxs-lookup"><span data-stu-id="da152-218">Click **Edit roles** for the **employee** user, and then select the **employee** role.</span></span>  
  
19. <span data-ttu-id="da152-219">針對 [manager]  使用者按一下 [編輯角色]  ，然後選取 [manager]  角色。</span><span class="sxs-lookup"><span data-stu-id="da152-219">Click **Edit roles** for the **manager** user, and then select the **manager** role.</span></span>  
  
20. <span data-ttu-id="da152-220">關閉裝載 [網站管理工具] 的瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="da152-220">Close the browser window that hosts the **Web Site Administration Tool**.</span></span>  
  
21. <span data-ttu-id="da152-221">如果出現訊息方塊，詢問您是否要重新載入已修改的 Web.config 檔案，按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="da152-221">If a message box appears asking if you want to reload the modified Web.config file, click **Yes**.</span></span>  
  
 <span data-ttu-id="da152-222">如此即完成 Web 服務設定。</span><span class="sxs-lookup"><span data-stu-id="da152-222">This completes the Web service setup.</span></span> <span data-ttu-id="da152-223">此時，您可以按 F5 鍵執行用戶端應用程式，[ASP.NET 程式開發伺服器]  將會自動與用戶端應用程式一起啟動。</span><span class="sxs-lookup"><span data-stu-id="da152-223">At this point, you can press F5 to run the client application, and the **ASP.NET Development Server** will start automatically along with your client application.</span></span> <span data-ttu-id="da152-224">在您結束應用程式之後，伺服器會繼續執行，但是會在重新啟動應用程式時重新啟動。</span><span class="sxs-lookup"><span data-stu-id="da152-224">The server will continue to run after you exit the application, but will restart when you restart the application.</span></span> <span data-ttu-id="da152-225">如此可讓它偵測對 Web.config 所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="da152-225">This allows it to detect any changes you have made to Web.config.</span></span>  
  
 <span data-ttu-id="da152-226">若要手動停止伺服器，請以滑鼠右鍵按一下工作列上通知區域中的 ASP.NET 程式開發伺服器圖示，然後按一下 [停止] 。</span><span class="sxs-lookup"><span data-stu-id="da152-226">To stop the server manually, right-click the ASP.NET Development Server icon in the notification area of the taskbar and then click **Stop**.</span></span> <span data-ttu-id="da152-227">有時候在確定是否完全重新啟動時會很有用。</span><span class="sxs-lookup"><span data-stu-id="da152-227">This is useful occasionally to make sure that a clean restart occurs.</span></span>  
  
## <a name="adding-forms-authentication"></a><span data-ttu-id="da152-228">加入表單驗證</span><span class="sxs-lookup"><span data-stu-id="da152-228">Adding Forms Authentication</span></span>  
 <span data-ttu-id="da152-229">在下列程序中，您會將程式碼加入主要表單，以嘗試驗證使用者，並在使用者提供無效的認證時拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="da152-229">In the following procedure, you add code to the main form that attempts to validate the user, and denies access when the user supplies invalid credentials.</span></span> <span data-ttu-id="da152-230">您會使用硬式編碼的使用者名稱和密碼測試服務。</span><span class="sxs-lookup"><span data-stu-id="da152-230">You use a hard-coded user name and password to test the service.</span></span>  
  
#### <a name="to-validate-the-user-in-your-application-code"></a><span data-ttu-id="da152-231">在應用程式程式碼中驗證使用者</span><span class="sxs-lookup"><span data-stu-id="da152-231">To validate the user in your application code</span></span>  
  
1.  <span data-ttu-id="da152-232">在 [方案總管] 中，於 ClientAppServicesDemo 專案中加入 System.Web 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="da152-232">In **Solution Explorer**, in the ClientAppServicesDemo project, add a reference to the System.Web assembly.</span></span>  
  
2.  <span data-ttu-id="da152-233">選取 Form1 檔案，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 [檢視 &#124; 程式碼]。</span><span class="sxs-lookup"><span data-stu-id="da152-233">Select the Form1 file and then select **View &#124; Code** from the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] main menu.</span></span>  
  
3.  <span data-ttu-id="da152-234">在程式碼編輯器中，將下列陳述式加入 Form1 檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="da152-234">In the code editor, add the following statements to the top of the Form1 file.</span></span>  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  <span data-ttu-id="da152-235">在 [方案總管] 中，按兩下 Form1 以顯示設計工具。</span><span class="sxs-lookup"><span data-stu-id="da152-235">In **Solution Explorer**, double-click Form1 to display the designer.</span></span>  
  
5.  <span data-ttu-id="da152-236">在設計工具中，按兩下表單介面以產生名為 <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> 的 `Form1_Load`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="da152-236">In the designer, double-click the form surface to generate a <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler named `Form1_Load`.</span></span>  
  
     <span data-ttu-id="da152-237">程式碼編輯器隨即出現，並將游標置於 `Form1_Load` 方法中。</span><span class="sxs-lookup"><span data-stu-id="da152-237">The code editor appears with the cursor in the `Form1_Load` method.</span></span>  
  
6.  <span data-ttu-id="da152-238">將下列程式碼加入至 `Form1_Load` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-238">Add the following code to the `Form1_Load` method.</span></span>  
  
     <span data-ttu-id="da152-239">這段程式碼會以結束應用程式的方式，來拒絕未經驗證之使用者的存取。</span><span class="sxs-lookup"><span data-stu-id="da152-239">This code denies access to unauthenticated users by exiting the application.</span></span> <span data-ttu-id="da152-240">或者，您可以允許未經驗證的使用者存取表單，但拒絕其存取特定功能。</span><span class="sxs-lookup"><span data-stu-id="da152-240">Alternatively, you could allow unauthenticated users access to the form, but deny access to specific functionality.</span></span> <span data-ttu-id="da152-241">您通常不會以這種方式硬式編碼使用者名稱和密碼，但是基於測試目的就很有用。</span><span class="sxs-lookup"><span data-stu-id="da152-241">Normally, you will not hard-code the user name and password like this, but it is useful for testing purposes.</span></span> <span data-ttu-id="da152-242">在下一節中，您將會使用更強固的程式碼來取代這段程式碼，以顯示 [登入] 對話方塊並包含例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="da152-242">In the next section, you will replace this code with more robust code that displays a login dialog box and includes exception handling.</span></span>  
  
     <span data-ttu-id="da152-243">請注意， `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法是在 [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="da152-243">Note that the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method is in the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="da152-244">這個方法會將其工作委派給已設定的驗證提供者，然後在驗證成功時傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="da152-244">This method delegates its work to the configured authentication provider, and returns `true` if authentication is successful.</span></span> <span data-ttu-id="da152-245">您的應用程式不需要直接參考用戶端驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="da152-245">Your application does not require a direct reference to the client authentication provider.</span></span>  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 <span data-ttu-id="da152-246">您現在可以按 F5 鍵執行應用程式，由於提供了正確的使用者名稱和密碼，您將會看到表單。</span><span class="sxs-lookup"><span data-stu-id="da152-246">You can now press F5 to run the application, and because you provide a correct user name and password, you will see the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da152-247">如果您無法執行應用程式，請嘗試停止 ASP.NET 程式開發伺服器。</span><span class="sxs-lookup"><span data-stu-id="da152-247">If you are unable to run the application, try stopping the ASP.NET Development Server.</span></span> <span data-ttu-id="da152-248">當伺服器重新啟動時，請確認通訊埠設定為 55555。</span><span class="sxs-lookup"><span data-stu-id="da152-248">When the server restarts, verify that the port is set to 55555.</span></span>  
  
 <span data-ttu-id="da152-249">若要改為查看錯誤訊息，請變更 <xref:System.Web.Security.Membership.ValidateUser%2A> 參數。</span><span class="sxs-lookup"><span data-stu-id="da152-249">To see the error message instead, change the <xref:System.Web.Security.Membership.ValidateUser%2A> parameters.</span></span> <span data-ttu-id="da152-250">例如，以不正確的密碼 (像是 `"manager!"` ) 取代第二個 `"MANAGER"`參數。</span><span class="sxs-lookup"><span data-stu-id="da152-250">For example, replace the second `"manager!"` parameter with an incorrect password like `"MANAGER"`.</span></span>  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a><span data-ttu-id="da152-251">加入登入表單當做認證提供者</span><span class="sxs-lookup"><span data-stu-id="da152-251">Adding a Login Form as a Credentials Provider</span></span>  
 <span data-ttu-id="da152-252">您可以在應用程式程式碼中取得使用者認證，並將其傳遞給 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-252">You can acquire the user credentials in your application code and pass them to the <xref:System.Web.Security.Membership.ValidateUser%2A> method.</span></span> <span data-ttu-id="da152-253">不過，如果您稍後想要進行變更，將取得認證的程式碼與應用程式程式碼分開通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="da152-253">However, it is often useful to keep your credentials-acquiring code separate from your application code, in case you want to change it later.</span></span>  
  
 <span data-ttu-id="da152-254">在下列程序中，您會將應用程式設定為使用認證提供者，然後變更您的 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法呼叫，同時針對兩個參數傳遞 <xref:System.String.Empty> 。</span><span class="sxs-lookup"><span data-stu-id="da152-254">In the following procedure, you configure your application to use a credentials provider, and then change your <xref:System.Web.Security.Membership.ValidateUser%2A> method call to pass <xref:System.String.Empty> for both parameters.</span></span> <span data-ttu-id="da152-255">空字串會對 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法發出訊號，使其呼叫已設定之認證提供者的 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-255">The empty strings signal the <xref:System.Web.Security.Membership.ValidateUser%2A> method to call the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> method of the configured credentials provider.</span></span>  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a><span data-ttu-id="da152-256">將應用程式設定為使用認證提供者</span><span class="sxs-lookup"><span data-stu-id="da152-256">To configure your application to use a credentials provider</span></span>  
  
1.  <span data-ttu-id="da152-257">在 [方案總管] 中，選取 ClientAppServicesDemo 專案，然後在 [專案]  功能表上，選取 [ClientAppServicesDemo 屬性] 。</span><span class="sxs-lookup"><span data-stu-id="da152-257">In **Solution Explorer**, select the ClientAppServicesDemo project, and then on the **Project** menu, select **ClientAppServicesDemo Properties**.</span></span>  
  
     <span data-ttu-id="da152-258">[專案設計工具] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-258">The project designer appears.</span></span>  
  
2.  <span data-ttu-id="da152-259">在 [服務]  索引標籤上，將 [選擇性：認證提供者]  設定為下列值。</span><span class="sxs-lookup"><span data-stu-id="da152-259">On the **Services** tab, set **Optional: Credential provider** to the following value.</span></span> <span data-ttu-id="da152-260">這個值表示組件限定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="da152-260">This value indicates the assembly-qualified type name.</span></span>  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  <span data-ttu-id="da152-261">在 Form1 程式碼檔案中，將 `Form1_Load` 方法中的程式碼以下列程式碼取代。</span><span class="sxs-lookup"><span data-stu-id="da152-261">In the Form1 code file, replace the code in the `Form1_Load` method with the following code.</span></span>  
  
     <span data-ttu-id="da152-262">這段程式碼會顯示歡迎訊息，然後呼叫在下一個步驟中加入的 `ValidateUsingCredentialsProvider` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-262">This code displays a welcome message and then calls the `ValidateUsingCredentialsProvider` method that you will add in the next step.</span></span> <span data-ttu-id="da152-263">如果使用者未經過驗證， `ValidateUsingCredentialsProvider` 方法會傳回 `false` ，且 `Form1_Load` 方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="da152-263">If the user is not authenticated, the `ValidateUsingCredentialsProvider` method returns `false` and the `Form1_Load` method returns.</span></span> <span data-ttu-id="da152-264">這可以避免在應用程式結束之前執行任何其他的程式碼。</span><span class="sxs-lookup"><span data-stu-id="da152-264">This prevents any additional code from running before the application exits.</span></span> <span data-ttu-id="da152-265">歡迎訊息可以清楚表示應用程式重新啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="da152-265">The welcome message is useful to make it clear when the application restarts.</span></span> <span data-ttu-id="da152-266">當您在本逐步解說稍後實作登出時，將會加入程式碼以重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-266">You will add code to restart the application when you implement logout later in this walkthrough.</span></span>  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  <span data-ttu-id="da152-267">將下列方法加入 `Form1_Load` 方法之後。</span><span class="sxs-lookup"><span data-stu-id="da152-267">Add the following method after the `Form1_Load` method.</span></span>  
  
     <span data-ttu-id="da152-268">這個方法會將空字串傳遞給 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法，而出現 [登入] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="da152-268">This method passes empty strings to the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method, which causes the Login dialog box to appear.</span></span> <span data-ttu-id="da152-269">如果驗證服務無法使用， <xref:System.Web.Security.Membership.ValidateUser%2A> 方法會擲回 <xref:System.Net.WebException>。</span><span class="sxs-lookup"><span data-stu-id="da152-269">If the authentication service is unavailable, the <xref:System.Web.Security.Membership.ValidateUser%2A> method will throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="da152-270">在這種情況下， `ValidateUsingCredentialsProvider` 方法會顯示警告訊息，並詢問使用者是否要在離線模式中再試一次。</span><span class="sxs-lookup"><span data-stu-id="da152-270">In this case, the `ValidateUsingCredentialsProvider` method displays a warning message and asks if the user wants to try again in offline mode.</span></span> <span data-ttu-id="da152-271">此功能需要 **將密碼雜湊儲存在本機，以便能使用離線登入功能** ，如 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)所述。</span><span class="sxs-lookup"><span data-stu-id="da152-271">This functionality requires the **Save password hash locally to enable offline login** feature described in [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).</span></span> <span data-ttu-id="da152-272">新專案預設會啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="da152-272">This feature is enabled by default for new projects.</span></span>  
  
     <span data-ttu-id="da152-273">如果使用者未經過驗證， `ValidateUsingCredentialsProvider` 方法會顯示錯誤訊息並結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-273">If the user is not validated, the `ValidateUsingCredentialsProvider` method displays an error message and exits the application.</span></span> <span data-ttu-id="da152-274">最後，這個方法會傳回驗證嘗試的結果。</span><span class="sxs-lookup"><span data-stu-id="da152-274">Finally, this method returns the result of the authentication attempt.</span></span>  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a><span data-ttu-id="da152-275">建立登入表單</span><span class="sxs-lookup"><span data-stu-id="da152-275">Creating a Login Form</span></span>  
 <span data-ttu-id="da152-276">認證提供者是實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="da152-276">A credentials provider is a class that implements the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interface.</span></span> <span data-ttu-id="da152-277">這個介面具有名為 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 的單一方法，可傳回 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> 物件。</span><span class="sxs-lookup"><span data-stu-id="da152-277">This interface has a single method named <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> that returns a <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> object.</span></span> <span data-ttu-id="da152-278">下列程序說明如何建立實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 的 [登入] 對話方塊，以顯示本身並傳回使用者指定的認證。</span><span class="sxs-lookup"><span data-stu-id="da152-278">The following procedures describe how to create a login dialog box that implements <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> to display itself and return the user-specified credentials.</span></span>  
  
 <span data-ttu-id="da152-279">針對 Visual Basic 和 C# 所提供的程序不同，因為 Visual Basic 提供 [登入表單] 範本。</span><span class="sxs-lookup"><span data-stu-id="da152-279">Separate procedures are provided for Visual Basic and C# because Visual Basic provides a **Login Form** template.</span></span> <span data-ttu-id="da152-280">這可以節省一些時間和撰寫程式碼的工作。</span><span class="sxs-lookup"><span data-stu-id="da152-280">This saves some time and coding effort.</span></span>  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a><span data-ttu-id="da152-281">建立 [登入] 對話方塊當做 Visual Basic 中的認證提供者</span><span class="sxs-lookup"><span data-stu-id="da152-281">To create a login dialog box as a credentials provider in Visual Basic</span></span>  
  
1.  <span data-ttu-id="da152-282">在 [方案總管] 中，選取 ClientAppServicesDemo 專案，然後在 [專案]  功能表上，選取 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="da152-282">In **Solution Explorer**, select the ClientAppServicesDemo project, and then on the **Project** menu, select **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="da152-283">在 [加入新項目]  對話方塊中，選取 [登入表單]  範本，再將項目的 [名稱]  變更為 `Login.vb`，然後按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="da152-283">In the **Add New Item** dialog box, select the **Login Form** template, change the item **Name** to `Login.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="da152-284">[登入] 對話方塊隨即在 [Windows Form 設計工具] 中出現。</span><span class="sxs-lookup"><span data-stu-id="da152-284">The login dialog box appears in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="da152-285">在設計工具中，選取 [確定]  按鈕，然後在 [屬性]  視窗中，將 `DialogResult` 設定為 `OK`。</span><span class="sxs-lookup"><span data-stu-id="da152-285">In the designer, select the **OK** button and then, in the **Properties** window, set `DialogResult` to `OK`.</span></span>  
  
4.  <span data-ttu-id="da152-286">在設計工具中，將 `CheckBox` 控制項加入 [密碼]  文字方塊下的表單中。</span><span class="sxs-lookup"><span data-stu-id="da152-286">In the designer, add a `CheckBox` control to the form under the **Password** text box.</span></span>  
  
5.  <span data-ttu-id="da152-287">在 [屬性] 視窗中，將 [(名稱)] 值指定為 `rememberMeCheckBox`，並將 [文字] 值指定為 `&Remember me`。</span><span class="sxs-lookup"><span data-stu-id="da152-287">In the **Properties** window, specify a **(Name)** value of `rememberMeCheckBox` and a **Text** value of `&Remember me`.</span></span>  
  
6.  <span data-ttu-id="da152-288">從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 [檢視 &#124; 程式碼]。</span><span class="sxs-lookup"><span data-stu-id="da152-288">Select **View &#124; Code** from the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] main menu.</span></span>  
  
7.  <span data-ttu-id="da152-289">在程式碼編輯器中，將下列程式碼加入檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="da152-289">In the code editor, add the following code to the top of the file.</span></span>  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  <span data-ttu-id="da152-290">修改類別簽章，使類別實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面。</span><span class="sxs-lookup"><span data-stu-id="da152-290">Modify the class signature so that the class implements the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interface.</span></span>  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. <span data-ttu-id="da152-291">確定游標在 `IClientformsAuthenticationCredentialsProvider` 之後，然後按 Enter 鍵產生 `GetCredentials` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-291">Make sure that the cursor is after `IClientformsAuthenticationCredentialsProvider`, and then press ENTER to generate the `GetCredentials` method.</span></span>  
  
10. <span data-ttu-id="da152-292">找出 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 實作，然後以下列程式碼取代。</span><span class="sxs-lookup"><span data-stu-id="da152-292">Locate the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementation and then replace it with the following code.</span></span>  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 <span data-ttu-id="da152-293">下列 C# 程序提供簡單 [登入] 對話方塊的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="da152-293">The following C# procedure provides the entire code listing for a simple login dialog box.</span></span> <span data-ttu-id="da152-294">這個對話方塊的配置有一點粗糙，但是重點是 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 實作。</span><span class="sxs-lookup"><span data-stu-id="da152-294">The layout for this dialog box is a bit crude, but the important part is the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementation.</span></span>  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a><span data-ttu-id="da152-295">建立 [登入] 對話方塊當做 C# 中的認證提供者</span><span class="sxs-lookup"><span data-stu-id="da152-295">To create a login dialog box as a credentials provider in C#</span></span>  
  
1.  <span data-ttu-id="da152-296">在 [方案總管] 中，選取 ClientAppServicesDemo 專案，然後在 [專案]  功能表上，選取 [加入類別] 。</span><span class="sxs-lookup"><span data-stu-id="da152-296">In **Solution Explorer**, select the ClientAppServicesDemo project, and then on the **Project** menu, select **Add Class**.</span></span>  
  
2.  <span data-ttu-id="da152-297">在 [加入新項目]  對話方塊中，將 [名稱]  變更為 `Login.cs`，然後按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="da152-297">In the **Add New Item** dialog box, change the **Name** to `Login.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="da152-298">Login.cs 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="da152-298">The Login.cs file opens in the code editor.</span></span>  
  
3.  <span data-ttu-id="da152-299">使用下列程式碼取代預設程式碼。</span><span class="sxs-lookup"><span data-stu-id="da152-299">Replace the default code with the following code.</span></span>  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 <span data-ttu-id="da152-300">您現在可以執行應用程式，然後會看到 [登入] 對話方塊出現。</span><span class="sxs-lookup"><span data-stu-id="da152-300">You can now run the application and see the login dialog box appear.</span></span> <span data-ttu-id="da152-301">若要測試這段程式碼，請同時嘗試有效和無效的不同認證，然後確認您只能夠以有效認證存取表單。</span><span class="sxs-lookup"><span data-stu-id="da152-301">To test this code, try different credentials, both valid and invalid, and confirm that you can access the form only with valid credentials.</span></span> <span data-ttu-id="da152-302">有效的使用者名稱為 `employee` 及 `manager` ； 密碼則分別為 `employee!` 及 `manager!` 。</span><span class="sxs-lookup"><span data-stu-id="da152-302">Valid user names are `employee` and `manager` with passwords `employee!` and `manager!` respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da152-303">請勿在此時選取 [記住我]  ，否則在本逐步解說稍後實作登出之前，您都無法以其他使用者身分登入。</span><span class="sxs-lookup"><span data-stu-id="da152-303">Do not select **Remember me** at this point or you will not be able to login as another user until you implement logout later in this walkthrough.</span></span>  
  
## <a name="adding-role-based-functionality"></a><span data-ttu-id="da152-304">加入以角色為基礎的功能</span><span class="sxs-lookup"><span data-stu-id="da152-304">Adding Role-Based Functionality</span></span>  
 <span data-ttu-id="da152-305">在下列程序中，您會加入一個按鈕到表單，並只針對 manager 角色的使用者顯示該按鈕。</span><span class="sxs-lookup"><span data-stu-id="da152-305">In the following procedure, you add a button to the form and display it only for users in the manager role.</span></span>  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a><span data-ttu-id="da152-306">根據使用者角色變更使用者介面</span><span class="sxs-lookup"><span data-stu-id="da152-306">To change the user interface based on user role</span></span>  
  
1.  <span data-ttu-id="da152-307">在 [方案總管] 中，選取 ClientAppServicesDemo 專案中的 Form1，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 [檢視 &#124; 設計工具]。</span><span class="sxs-lookup"><span data-stu-id="da152-307">In **Solution Explorer**, in the ClientAppServicesDemo project, select Form1 and then select **View &#124; Designer** from the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] main menu.</span></span>  
  
2.  <span data-ttu-id="da152-308">在設計工具中，從 [工具箱] 將 <xref:System.Windows.Forms.Button> 控制項新增表單。</span><span class="sxs-lookup"><span data-stu-id="da152-308">In the designer, add a <xref:System.Windows.Forms.Button> control to the form from the **ToolBox**.</span></span>  
  
3.  <span data-ttu-id="da152-309">在 [屬性]  視窗中，設定按鈕的下列屬性。</span><span class="sxs-lookup"><span data-stu-id="da152-309">In the **Properties** window, set the following properties for the button.</span></span>  
  
  	|<span data-ttu-id="da152-310">屬性</span><span class="sxs-lookup"><span data-stu-id="da152-310">Property</span></span>|<span data-ttu-id="da152-311">值</span><span class="sxs-lookup"><span data-stu-id="da152-311">Value</span></span>|  
  	|--------------|-----------|  
  	|<span data-ttu-id="da152-312">**(名稱)**</span><span class="sxs-lookup"><span data-stu-id="da152-312">**(Name)**</span></span>|<span data-ttu-id="da152-313">managerOnlyButton</span><span class="sxs-lookup"><span data-stu-id="da152-313">managerOnlyButton</span></span>|  
  	|<span data-ttu-id="da152-314">**Text**</span><span class="sxs-lookup"><span data-stu-id="da152-314">**Text**</span></span>|<span data-ttu-id="da152-315">&Manager task</span><span class="sxs-lookup"><span data-stu-id="da152-315">&Manager task</span></span>|  
  	|<span data-ttu-id="da152-316">**可見**</span><span class="sxs-lookup"><span data-stu-id="da152-316">**Visible**</span></span>|`False`|  
  
4.  <span data-ttu-id="da152-317">在 Form1 的程式碼編輯器中，將下列程式碼加入 `Form1_Load` 方法的結尾。</span><span class="sxs-lookup"><span data-stu-id="da152-317">In the code editor for Form1, add the following code to the end of the `Form1_Load` method.</span></span>  
  
     <span data-ttu-id="da152-318">這段程式碼會呼叫在下一個步驟中加入的 `DisplayButtonForManagerRole` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-318">This code calls the `DisplayButtonForManagerRole` method that you will add in the next step.</span></span>  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  <span data-ttu-id="da152-319">將下列方法加入 Form1 類別的結尾。</span><span class="sxs-lookup"><span data-stu-id="da152-319">Add the following method to the end of the Form1 class.</span></span>  
  
     <span data-ttu-id="da152-320">這個方法會呼叫 `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性所傳回之 <xref:System.Security.Principal.IPrincipal> 的 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-320">This method calls the <xref:System.Security.Principal.IPrincipal.IsInRole%2A> method of the <xref:System.Security.Principal.IPrincipal> returned by the `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="da152-321">針對設定為使用用戶端應用程式服務的應用程式，這個屬性會傳回 <xref:System.Web.ClientServices.ClientRolePrincipal>。</span><span class="sxs-lookup"><span data-stu-id="da152-321">For applications configured to use client application services, this property returns a <xref:System.Web.ClientServices.ClientRolePrincipal>.</span></span> <span data-ttu-id="da152-322">因為這個類別會實作 <xref:System.Security.Principal.IPrincipal> 介面，所以您不需要明確地參考它。</span><span class="sxs-lookup"><span data-stu-id="da152-322">Because this class implements the <xref:System.Security.Principal.IPrincipal> interface, you do not need to reference it explicitly.</span></span>  
  
     <span data-ttu-id="da152-323">如果使用者的角色為 "manager"， `DisplayButtonForManagerRole` 方法會將 <xref:System.Windows.Forms.Control.Visible%2A> 的 `managerOnlyButton` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="da152-323">If the user is in the "manager" role, the `DisplayButtonForManagerRole` method sets the <xref:System.Windows.Forms.Control.Visible%2A> property of the `managerOnlyButton` to `true`.</span></span> <span data-ttu-id="da152-324">如果擲回 <xref:System.Net.WebException> 表示角色服務無法使用，這個方法也會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="da152-324">This method also displays an error message if a <xref:System.Net.WebException> is thrown, which indicates that the roles service is unavailable.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da152-325">如果使用者登入已過期， <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> 方法一律會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="da152-325">The <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> method will always return `false` if the user login has expired.</span></span> <span data-ttu-id="da152-326">如果應用程式在驗證後很短的時間內呼叫一次 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法 (如本逐步解說的範例程式碼所示)，則不會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="da152-326">This will not occur if your application calls the <xref:System.Security.Principal.IPrincipal.IsInRole%2A> method one time shortly after authentication, as shown in the example code for this walkthrough.</span></span> <span data-ttu-id="da152-327">如果應用程式必須在其他時間點擷取使用者角色，您可能會想要加入程式碼，以重新驗證登入已過期的使用者。</span><span class="sxs-lookup"><span data-stu-id="da152-327">If your application must retrieve user roles at other times, you might want to add code to revalidate users whose login has expired.</span></span> <span data-ttu-id="da152-328">如果所有有效的使用者都獲派角色，您可以呼叫 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> 方法以判斷登入是否過期。</span><span class="sxs-lookup"><span data-stu-id="da152-328">If all valid users are assigned to roles, you can determine whether the login has expired by calling the <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="da152-329">如果沒有角色傳回，則表示登入已過期。</span><span class="sxs-lookup"><span data-stu-id="da152-329">If no roles are returned, the login has expired.</span></span> <span data-ttu-id="da152-330">如需這項功能的範例，請參閱 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-330">For an example of this functionality, see the <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> method.</span></span> <span data-ttu-id="da152-331">只有在應用程式組態中已選取 [要求使用者在伺服器 Cookie 過期時必須再次登入]  時，才需要這項功能。</span><span class="sxs-lookup"><span data-stu-id="da152-331">This functionality is only necessary if you have selected **Require users to log on again whenever the server cookie expires** in your application configuration.</span></span> <span data-ttu-id="da152-332">如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。</span><span class="sxs-lookup"><span data-stu-id="da152-332">For more information, see [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).</span></span>  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 <span data-ttu-id="da152-333">如果驗證成功，用戶端驗證提供者會將 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Web.ClientServices.ClientRolePrincipal> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="da152-333">If authentication is successful, the client authentication provider sets the <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Web.ClientServices.ClientRolePrincipal> class.</span></span> <span data-ttu-id="da152-334">這個類別會實作 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法，以便將工作委派給已設定的角色提供者。</span><span class="sxs-lookup"><span data-stu-id="da152-334">This class implements the <xref:System.Security.Principal.IPrincipal.IsInRole%2A> method so that the work is delegated to the configured role provider.</span></span> <span data-ttu-id="da152-335">如前所述，應用程式程式碼不需要直接參考服務提供者。</span><span class="sxs-lookup"><span data-stu-id="da152-335">As before, your application code does not require a direct reference to the service provider.</span></span>  
  
 <span data-ttu-id="da152-336">您現在可以執行應用程式並以 employee 身分登入，您會發現按鈕並未顯示；然後再以 manager 身分登入，則會看到按鈕。</span><span class="sxs-lookup"><span data-stu-id="da152-336">You can now run the application and log in as employee to see that the button does not appear, and then log in as manager to see the button.</span></span>  
  
## <a name="accessing-web-settings"></a><span data-ttu-id="da152-337">存取 Web 設定</span><span class="sxs-lookup"><span data-stu-id="da152-337">Accessing Web Settings</span></span>  
 <span data-ttu-id="da152-338">在下列程序中，您會將文字方塊加入表單並繫結至 Web 設定。</span><span class="sxs-lookup"><span data-stu-id="da152-338">In the following procedure, you add a text box to the form and bind it to a Web setting.</span></span> <span data-ttu-id="da152-339">如同先前使用驗證和角色的程式碼，您的設定程式碼不會直接存取設定提供者，</span><span class="sxs-lookup"><span data-stu-id="da152-339">Like the previous code that uses authentication and roles, your settings code does not access the settings provider directly.</span></span> <span data-ttu-id="da152-340">而是會使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 針對專案所產生的強型別 `Settings` 類別 (在 C# 中是當作 `Properties.Settings.Default` 存取，而在 Visual Basic 中則是當作 `My.Settings` 存取)。</span><span class="sxs-lookup"><span data-stu-id="da152-340">Instead, it uses the strongly-typed `Settings` class (accessed as `Properties.Settings.Default` in C# and `My.Settings` in Visual Basic) generated for your project by [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a><span data-ttu-id="da152-341">在使用者介面中使用 Web 設定</span><span class="sxs-lookup"><span data-stu-id="da152-341">To use Web settings in your user interface</span></span>  
  
1.  <span data-ttu-id="da152-342">檢查工作列的通知區域，確定 [ASP.NET Web 程式開發伺服器]  仍在執行中。</span><span class="sxs-lookup"><span data-stu-id="da152-342">Make sure that the **ASP.NET Web Development Server** is still running by checking the notification area of the taskbar.</span></span> <span data-ttu-id="da152-343">如果您已停止伺服器，請重新啟動應用程式 (這會自動啟動伺服器)，然後關閉 [登入] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="da152-343">If you have stopped the server, restart the application (which starts the server automatically) then close the login dialog box.</span></span>  
  
2.  <span data-ttu-id="da152-344">在 [方案總管] 中，選取 ClientAppServicesDemo 專案，然後在 [專案]  功能表上，選取 [ClientAppServicesDemo 屬性] 。</span><span class="sxs-lookup"><span data-stu-id="da152-344">In **Solution Explorer**, select the ClientAppServicesDemo project, and then on the **Project** menu, select **ClientAppServicesDemo Properties**.</span></span>  
  
     <span data-ttu-id="da152-345">[專案設計工具] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-345">The project designer appears.</span></span>  
  
3.  <span data-ttu-id="da152-346">在 [設定]  索引標籤上，按一下 [載入 Web 設定] 。</span><span class="sxs-lookup"><span data-stu-id="da152-346">On the **Settings** tab, click **Load Web Settings**.</span></span>  
  
     <span data-ttu-id="da152-347">[登入]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da152-347">A **Login** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="da152-348">輸入 employee 或 manager 的認證，然後按一下 [登入] 。</span><span class="sxs-lookup"><span data-stu-id="da152-348">Enter credentials for employee or manager and click **Log In**.</span></span> <span data-ttu-id="da152-349">您將使用的 Web 設定已設定為只有經過驗證的使用者才能存取，因此按一下 [略過登入]  將不會載入任何設定。</span><span class="sxs-lookup"><span data-stu-id="da152-349">The Web setting you will use is configured for access by authenticated users only, so clicking **Skip Login** will not load any settings.</span></span>  
  
     <span data-ttu-id="da152-350">`WebSettingsTestText` 設定會以 `DefaultText`的預設值出現在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="da152-350">The `WebSettingsTestText` setting appears in the designer with the default value of `DefaultText`.</span></span> <span data-ttu-id="da152-351">此外，也會為專案產生包含 `WebSettingsTestText` 屬性的 `Settings` 類別。</span><span class="sxs-lookup"><span data-stu-id="da152-351">Additionally, a `Settings` class that contains a `WebSettingsTestText` property is generated for your project.</span></span>  
  
5.  <span data-ttu-id="da152-352">在 [方案總管] 中，選取 ClientAppServicesDemo 專案中的 Form1，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 [檢視 &#124; 設計工具]。</span><span class="sxs-lookup"><span data-stu-id="da152-352">In **Solution Explorer**, in the ClientAppServicesDemo project, select Form1 and then select **View &#124; Designer** from the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] main menu.</span></span>  
  
6.  <span data-ttu-id="da152-353">在設計工具中，將 <xref:System.Windows.Forms.TextBox> 控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="da152-353">In the designer, add a <xref:System.Windows.Forms.TextBox> control to the form.</span></span>  
  
7.  <span data-ttu-id="da152-354">在 [屬性]  視窗中，指定 **的 [(名稱)]**`webSettingsTestTextBox`值 。</span><span class="sxs-lookup"><span data-stu-id="da152-354">In the **Properties** window, specify a **(Name)** value of `webSettingsTestTextBox`.</span></span>  
  
8.  <span data-ttu-id="da152-355">在程式碼編輯器中，將下列程式碼加入 `Form1_Load` 方法的結尾。</span><span class="sxs-lookup"><span data-stu-id="da152-355">In the code editor, add the following code to the end of the `Form1_Load` method.</span></span>  
  
     <span data-ttu-id="da152-356">這段程式碼會呼叫在下一個步驟中加入的 `BindWebSettingsTestTextBox` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-356">This code calls the `BindWebSettingsTestTextBox` method that you will add in the next step.</span></span>  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. <span data-ttu-id="da152-357">將下列方法加入 Form1 類別的結尾。</span><span class="sxs-lookup"><span data-stu-id="da152-357">Add the following method to the end of the Form1 class.</span></span>  
  
     <span data-ttu-id="da152-358">這個方法會將 <xref:System.Windows.Forms.TextBox.Text%2A> 的 `webSettingsTestTextBox` 屬性，繫結至本程序稍早所產生之 `WebSettingsTestText` 類別的 `Settings` 屬性。</span><span class="sxs-lookup"><span data-stu-id="da152-358">This method binds the <xref:System.Windows.Forms.TextBox.Text%2A> property of the `webSettingsTestTextBox` to the `WebSettingsTestText` property of the `Settings` class generated earlier in this procedure.</span></span> <span data-ttu-id="da152-359">如果擲回 <xref:System.Net.WebException> 表示 Web 設定無法使用，這個方法也會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="da152-359">This method also displays an error message if a <xref:System.Net.WebException> is thrown, which indicates that the Web settings service is unavailable.</span></span>  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  <span data-ttu-id="da152-360">您通常會使用資料繫結啟用控制項與 Web 設定之間的自動雙向通訊。</span><span class="sxs-lookup"><span data-stu-id="da152-360">You will typically use data binding to enable automatic two-way communication between a control and a Web setting.</span></span> <span data-ttu-id="da152-361">不過，您也可以直接存取 Web 設定，如同下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="da152-361">However, you can also access Web settings directly as shown in the following example:</span></span>  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. <span data-ttu-id="da152-362">在設計工具中選取表單，然後在 [屬性] 視窗中按一下 [事件] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="da152-362">In the designer, select the form, and then, in the **Properties** window, click the **Events** button.</span></span>  
  
11. <span data-ttu-id="da152-363">選取 <xref:System.Windows.Forms.Form.FormClosing> 事件，然後按 ENTER 鍵產生事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="da152-363">Select the <xref:System.Windows.Forms.Form.FormClosing> event and then press ENTER to generate an event handler.</span></span>  
  
12. <span data-ttu-id="da152-364">以下列程式碼取代所產生的方法。</span><span class="sxs-lookup"><span data-stu-id="da152-364">Replace the generated method with the following code.</span></span>  
  
     <span data-ttu-id="da152-365"><xref:System.Windows.Forms.Form.FormClosing> 事件處理常式會呼叫 `SaveSettings` 方法，下一節將加入的登出功能也會使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="da152-365">The <xref:System.Windows.Forms.Form.FormClosing> event handler calls the `SaveSettings` method, which is also used by the logout functionality that you will add in the next section.</span></span> <span data-ttu-id="da152-366">`SaveSettings` 方法會先確認使用者尚未登出，作法是檢查目前主體所傳回之 <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> 的 <xref:System.Security.Principal.IIdentity> 屬性。</span><span class="sxs-lookup"><span data-stu-id="da152-366">The `SaveSettings` method first confirms that the user has not logged out. It does this by checking the <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> property of the <xref:System.Security.Principal.IIdentity> returned by the current principal.</span></span> <span data-ttu-id="da152-367">目前的主體是透過 `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> 屬性所擷取。</span><span class="sxs-lookup"><span data-stu-id="da152-367">The current principal is retrieved through the `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="da152-368">如果使用者已經過驗證可使用用戶端應用程式服務，驗證類型將會是 "ClientForms"。</span><span class="sxs-lookup"><span data-stu-id="da152-368">If the user has been authenticated for client application services, the authentication type will be "ClientForms".</span></span> <span data-ttu-id="da152-369">`SaveSettings` 方法不能只檢查 <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> 屬性，因為使用者在登出後可能仍擁有有效的 Windows 識別。</span><span class="sxs-lookup"><span data-stu-id="da152-369">The `SaveSettings` method cannot just check the <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> property because the user might have a valid Windows identity after logout.</span></span>  
  
     <span data-ttu-id="da152-370">如果使用者尚未登出， `SaveSettings` 方法會呼叫在這個程序稍早所產生之 <xref:System.Configuration.ApplicationSettingsBase.Save%2A> 類別的 `Settings` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-370">If the user has not logged out, the `SaveSettings` method calls the <xref:System.Configuration.ApplicationSettingsBase.Save%2A> method of the `Settings` class generated earlier in this procedure.</span></span> <span data-ttu-id="da152-371">如果驗證 Cookie 已過期，這個方法會擲回 <xref:System.Net.WebException> 。</span><span class="sxs-lookup"><span data-stu-id="da152-371">This method can throw a <xref:System.Net.WebException> if the authentication cookie has expired.</span></span> <span data-ttu-id="da152-372">只有在應用程式組態中已選取 [要求使用者在伺服器 Cookie 過期時必須再次登入]  時，才會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="da152-372">This occurs only if you have selected **Require users to log on again whenever the server cookie expires** in your application configuration.</span></span> <span data-ttu-id="da152-373">如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。</span><span class="sxs-lookup"><span data-stu-id="da152-373">For more information, see [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).</span></span> <span data-ttu-id="da152-374">`SaveSettings` 方法會透過呼叫 <xref:System.Web.Security.Membership.ValidateUser%2A> 顯示 [登入] 對話方塊的方式，處理 Cookie 過期。</span><span class="sxs-lookup"><span data-stu-id="da152-374">The `SaveSettings` method handles cookie expiration by calling <xref:System.Web.Security.Membership.ValidateUser%2A> to display the login dialog box.</span></span> <span data-ttu-id="da152-375">如果使用者成功登入， `SaveSettings` 方法會呼叫本身以嘗試再次儲存設定。</span><span class="sxs-lookup"><span data-stu-id="da152-375">If the user logs in successfully, the `SaveSettings` method tries to save the settings again by calling itself.</span></span>  
  
     <span data-ttu-id="da152-376">如同先前的程式碼，如果遠端服務無法使用， `SaveSettings` 方法會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="da152-376">Like in previous code, the `SaveSettings` method displays an error message if the remote service is unavailable.</span></span> <span data-ttu-id="da152-377">如果設定提供者無法存取遠端服務，則設定仍然會儲存在本機快取中，然後在應用程式重新啟動時重新載入。</span><span class="sxs-lookup"><span data-stu-id="da152-377">If the settings provider cannot access the remote service, the settings are still saved to the local cache and reloaded when the application restarts.</span></span>  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. <span data-ttu-id="da152-378">將下列方法加入 Form1 類別的結尾。</span><span class="sxs-lookup"><span data-stu-id="da152-378">Add the following method to the end of the Form1 class.</span></span>  
  
     <span data-ttu-id="da152-379">這段程式碼會處理 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> 事件，並在無法儲存任何設定時顯示警告。</span><span class="sxs-lookup"><span data-stu-id="da152-379">This code handles the <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> event and displays a warning if any of the settings could not be saved.</span></span> <span data-ttu-id="da152-380">如果設定服務無法使用或驗證 Cookie 已過期，則不會發生 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> 事件。</span><span class="sxs-lookup"><span data-stu-id="da152-380">The <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> event does not occur if the settings service is unavailable or if the authentication cookie has expired.</span></span> <span data-ttu-id="da152-381"><xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> 事件發生時機的其中一個範例是如果使用者已經登出。您可以在呼叫 `SaveSettings` 方法之前，將登出程式碼直接加入 <xref:System.Configuration.ApplicationSettingsBase.Save%2A> 方法以測試這個事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="da152-381">One example of when the <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> event will occur is if the user has already logged out. You can test this event handler by adding logout code to the `SaveSettings` method directly before the <xref:System.Configuration.ApplicationSettingsBase.Save%2A> method call.</span></span> <span data-ttu-id="da152-382">下一節將說明您可以使用的登出程式碼。</span><span class="sxs-lookup"><span data-stu-id="da152-382">Logout code that you can use is described in the next section.</span></span>  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. <span data-ttu-id="da152-383">如果是使用 C#，請將下列程式碼加入 `Form1_Load` 方法的結尾。</span><span class="sxs-lookup"><span data-stu-id="da152-383">For C#, add the following code to the end of the `Form1_Load` method.</span></span> <span data-ttu-id="da152-384">這段程式碼會將在上一個步驟中加入的方法與 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> 事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="da152-384">This code associates the method you added in the last step with the <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> event.</span></span>  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 <span data-ttu-id="da152-385">此時若要測試應用程式，請同時使用 employee 和 manager 身分執行數次，並在文字方塊中輸入不同的值。</span><span class="sxs-lookup"><span data-stu-id="da152-385">To test the application at this point, run it multiple times as both employee and manager, and type different values into the text box.</span></span> <span data-ttu-id="da152-386">這些值會保存在每個使用者的工作階段中。</span><span class="sxs-lookup"><span data-stu-id="da152-386">The values will persist across sessions on a per-user basis.</span></span>  
  
## <a name="implementing-logout"></a><span data-ttu-id="da152-387">實作登出</span><span class="sxs-lookup"><span data-stu-id="da152-387">Implementing Logout</span></span>  
 <span data-ttu-id="da152-388">如果使用者在登入時選取 [記住我]  核取方塊，應用程式在後續執行時會自動驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="da152-388">When the user selects the **Remember me** check box when logging in, the application will automatically authenticate the user on subsequent runs.</span></span> <span data-ttu-id="da152-389">當應用程式在離線模式時，自動驗證仍然會繼續執行直到驗證 Cookie 過期為止。</span><span class="sxs-lookup"><span data-stu-id="da152-389">Automatic authentication will then continue while the application is in offline mode or until the authentication cookie expires.</span></span> <span data-ttu-id="da152-390">不過，有時候多個使用者會需要同時存取應用程式，或是單一使用者可能會偶爾使用不同的認證登入。</span><span class="sxs-lookup"><span data-stu-id="da152-390">Sometimes, however, multiple users will need access to the application or a single user might occasionally log in with different credentials.</span></span> <span data-ttu-id="da152-391">若要實現這類案例，您必須實作登出功能，如同下列程序所述。</span><span class="sxs-lookup"><span data-stu-id="da152-391">To enable this scenario, you must implement logout functionality, as described in the following procedure.</span></span>  
  
#### <a name="to-implement-logout-functionality"></a><span data-ttu-id="da152-392">實作登出功能</span><span class="sxs-lookup"><span data-stu-id="da152-392">To implement logout functionality</span></span>  
  
1.  <span data-ttu-id="da152-393">在 Form1 設計工具中，從 [工具箱] 將 <xref:System.Windows.Forms.Button> 控制項新增表單。</span><span class="sxs-lookup"><span data-stu-id="da152-393">In the Form1 designer, add a <xref:System.Windows.Forms.Button> control to the form from the **ToolBox**.</span></span>  
  
2.  <span data-ttu-id="da152-394">在 [屬性] 視窗中，將 [(名稱)] 值指定為 `logoutButton`，並將 [文字] 值指定為 [登出(&L)]。</span><span class="sxs-lookup"><span data-stu-id="da152-394">In the **Properties** window, specify a **(Name)** value of `logoutButton` and a **Text** value of **&Log Out**.</span></span>  
  
3.  <span data-ttu-id="da152-395">按兩下 `logoutButton`，以產生 <xref:System.Windows.Forms.Control.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="da152-395">Double-click the `logoutButton` to generate a <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     <span data-ttu-id="da152-396">程式碼編輯器隨即出現，並將游標置於 `logoutButton_Click` 方法中。</span><span class="sxs-lookup"><span data-stu-id="da152-396">The code editor appears with the cursor in the `logoutButton_Click` method.</span></span>  
  
4.  <span data-ttu-id="da152-397">以下列程式碼取代所產生的 `logoutButton_Click` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-397">Replace the generated `logoutButton_Click` method with the following code.</span></span>  
  
     <span data-ttu-id="da152-398">這個事件處理常式會先呼叫在上一節中加入的 `SaveSettings` 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-398">This event handler first calls the `SaveSettings` method that you added in the previous section.</span></span> <span data-ttu-id="da152-399">接著，事件處理常式會呼叫 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="da152-399">Then, the event handler calls the <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="da152-400">如果驗證服務無法使用， <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> 方法會擲回 <xref:System.Net.WebException>。</span><span class="sxs-lookup"><span data-stu-id="da152-400">If the authentication service is unavailable, the <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> method will throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="da152-401">在這種情況下， `logoutButton_Click` 方法會顯示警告訊息，並暫時切換至離線模式將使用者登出。下一節將說明離線模式。</span><span class="sxs-lookup"><span data-stu-id="da152-401">In this case, the `logoutButton_Click` method displays a warning message and switches temporarily to offline mode to log the user out. Offline mode is described in the next section.</span></span>  
  
     <span data-ttu-id="da152-402">登出會刪除本機驗證 Cookie，因此當重新啟動應用程式時就需要登入。</span><span class="sxs-lookup"><span data-stu-id="da152-402">Logout deletes the local authentication cookie so that login will be required when the application is restarted.</span></span> <span data-ttu-id="da152-403">在登出後，事件處理常式會重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-403">After logout, the event handler restarts the application.</span></span> <span data-ttu-id="da152-404">應用程式重新啟動時，會在歡迎訊息後顯示 [登入] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="da152-404">When the application restarts, it displays the welcome message followed by the login dialog box.</span></span> <span data-ttu-id="da152-405">歡迎訊息清楚表示應用程式已重新啟動。</span><span class="sxs-lookup"><span data-stu-id="da152-405">The welcome message makes it clear that the application has restarted.</span></span> <span data-ttu-id="da152-406">如果使用者必須登入才能儲存設定，而且之後由於應用程式重新啟動又必須再登入一次，歡迎訊息可避免可能發生的混淆情況。</span><span class="sxs-lookup"><span data-stu-id="da152-406">This prevents potential confusion if the user must log in to save settings, and then must log in again because the application has restarted.</span></span>  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 <span data-ttu-id="da152-407">若要測試登出功能，請執行應用程式，然後在 [登入] 對話方塊中選取 [記住我]  。</span><span class="sxs-lookup"><span data-stu-id="da152-407">To test the logout functionality, run the application and select **Remember me** on the Login dialog box.</span></span> <span data-ttu-id="da152-408">接著，關閉再重新啟動應用程式以確認不再需要登入。</span><span class="sxs-lookup"><span data-stu-id="da152-408">Next, close and restart the application to confirm that you no longer have to log in.</span></span> <span data-ttu-id="da152-409">最後，按一下 [登出] 重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-409">Finally, restart the application by clicking Log out.</span></span>  
  
## <a name="enabling-offline-mode"></a><span data-ttu-id="da152-410">啟用離線模式</span><span class="sxs-lookup"><span data-stu-id="da152-410">Enabling Offline Mode</span></span>  
 <span data-ttu-id="da152-411">在下列程序中，您會將核取方塊加入表單，讓使用者能夠進入離線模式。</span><span class="sxs-lookup"><span data-stu-id="da152-411">In the following procedure, you add a check box to the form to enable the user to enter offline mode.</span></span> <span data-ttu-id="da152-412">您的應用程式可透過將 `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> 屬性設定為 `true`來進入離線模式。</span><span class="sxs-lookup"><span data-stu-id="da152-412">Your application indicates offline mode by setting the `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="da152-413">離線狀態會儲存在 <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> 屬性所表示的本機硬碟位置。</span><span class="sxs-lookup"><span data-stu-id="da152-413">The offline status is stored on the local hard disk at the location indicated by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="da152-414">這表示離線狀態是以個別使用者和個別應用程式為基礎來儲存。</span><span class="sxs-lookup"><span data-stu-id="da152-414">This means that the offline status is stored on a per-user, per-application basis.</span></span>  
  
 <span data-ttu-id="da152-415">在離線模式中，所有用戶端應用程式服務要求會從本機快取擷取資料，而不是嘗試存取服務。</span><span class="sxs-lookup"><span data-stu-id="da152-415">In offline mode, all client application service requests retrieve data from the local cache instead of trying to access the services.</span></span> <span data-ttu-id="da152-416">在預設組態中，本機資料包含以加密格式儲存的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="da152-416">In the default configuration, the local data includes an encrypted form of the user's password.</span></span> <span data-ttu-id="da152-417">這可讓使用者在應用程式處於離線模式時仍能登入。</span><span class="sxs-lookup"><span data-stu-id="da152-417">This enables the user to log in while the application is in offline mode.</span></span> <span data-ttu-id="da152-418">如需詳細資訊，請參閱 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。</span><span class="sxs-lookup"><span data-stu-id="da152-418">For more information, see [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).</span></span>  
  
#### <a name="to-enable-offline-mode-in-your-application"></a><span data-ttu-id="da152-419">在應用程式中啟用離線模式</span><span class="sxs-lookup"><span data-stu-id="da152-419">To enable offline mode in your application</span></span>  
  
1.  <span data-ttu-id="da152-420">在 [方案總管] 中，選取 ClientAppServicesDemo 專案中的 Form1，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 [檢視 &#124; 設計工具]。</span><span class="sxs-lookup"><span data-stu-id="da152-420">In **Solution Explorer**, in the ClientAppServicesDemo project, select Form1 and then select **View &#124; Designer** from the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] main menu.</span></span>  
  
2.  <span data-ttu-id="da152-421">在設計工具中，將 <xref:System.Windows.Forms.CheckBox> 控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="da152-421">In the designer, add a <xref:System.Windows.Forms.CheckBox> control to the form.</span></span>  
  
3.  <span data-ttu-id="da152-422">在 [屬性] 視窗中，將 [(名稱)] 值指定為 `workOfflineCheckBox`，並將 [文字] 值指定為 [離線工作(&W)]。</span><span class="sxs-lookup"><span data-stu-id="da152-422">In the **Properties** window, specify a **(Name)** value of `workOfflineCheckBox` and a **Text** value of **&Work offline**.</span></span>  
  
4.  <span data-ttu-id="da152-423">在 [屬性] 視窗中，按一下 [事件] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="da152-423">In the **Properties** window, click the **Events** button.</span></span>  
  
5.  <span data-ttu-id="da152-424">選取 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件，然後按 ENTER 鍵產生事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="da152-424">Select the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event and then press ENTER to generate an event handler.</span></span>  
  
6.  <span data-ttu-id="da152-425">以下列程式碼取代所產生的方法。</span><span class="sxs-lookup"><span data-stu-id="da152-425">Replace the generated method with the following code.</span></span>  
  
     <span data-ttu-id="da152-426">這段程式碼會更新 <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> 值，然後在返回線上模式時以無訊息模式重新驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="da152-426">This code updates the <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> value and silently revalidates the user when they return to online mode.</span></span> <span data-ttu-id="da152-427"><xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> 方法會使用快取認證，因此使用者不需要明確地登入。</span><span class="sxs-lookup"><span data-stu-id="da152-427">The <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> method uses the cached credentials so that the user does not have to explicitly log in.</span></span> <span data-ttu-id="da152-428">如果驗證服務無法使用，就會出現警告訊息，而應用程式仍然保持離線狀態。</span><span class="sxs-lookup"><span data-stu-id="da152-428">If the authentication service is unavailable, a warning message appears and the application stays offline.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da152-429"><xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> 方法只是為了方便而使用。</span><span class="sxs-lookup"><span data-stu-id="da152-429">The <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> method is for convenience only.</span></span> <span data-ttu-id="da152-430">因為它沒有傳回值，所以無法表示重新驗證是否失敗。</span><span class="sxs-lookup"><span data-stu-id="da152-430">Because it does not have a return value, it cannot indicate whether revalidation has failed.</span></span> <span data-ttu-id="da152-431">例如，如果在伺服器上的使用者認證已變更，重新驗證就可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="da152-431">Revalidation can fail, for example, if the user credentials have changed on the server.</span></span> <span data-ttu-id="da152-432">在這種情況下，您可能想要加入在服務呼叫失敗之後能夠明確驗證使用者的程式碼。</span><span class="sxs-lookup"><span data-stu-id="da152-432">In this case, you might want to include code that explicitly validates users after a service call fails.</span></span> <span data-ttu-id="da152-433">如需詳細資訊，請參閱本逐步解說稍早的＜存取 Web 設定＞一節。</span><span class="sxs-lookup"><span data-stu-id="da152-433">For more information, see the Accessing Web Settings section earlier in this walkthrough.</span></span>  
  
     <span data-ttu-id="da152-434">重新驗證後，這段程式碼會呼叫先前加入的 `SaveSettings` 方法，以儲存對本機 Web 設定所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="da152-434">After revalidation, this code saves any changes to the local Web settings by calling the `SaveSettings` method that you added previously.</span></span> <span data-ttu-id="da152-435">然後呼叫專案 `Settings` 類別 (在 C# 中當作 `Properties.Settings.Default` 存取，而在 Visual Basic 中則當作 `My.Settings` 存取) 的 <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> 方法，擷取伺服器上任何新增的值。</span><span class="sxs-lookup"><span data-stu-id="da152-435">It then retrieves any new values on the server by calling the <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> method of the project's `Settings` class (accessed as `Properties.Settings.Default` in C# and `My.Settings` in Visual Basic).</span></span>  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  <span data-ttu-id="da152-436">將下列程式碼加入 `Form1_Load` 方法的結尾，以確定核取方塊會顯示目前的連接狀態。</span><span class="sxs-lookup"><span data-stu-id="da152-436">Add the following code to the end of the `Form1_Load` method to make sure that the check box displays the current connection state.</span></span>  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 <span data-ttu-id="da152-437">如此即完成範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-437">This completes the example application.</span></span> <span data-ttu-id="da152-438">若要測試離線功能，請執行應用程式，以 employee 或 manager 的身分登入，然後選取 [離線工作] 。</span><span class="sxs-lookup"><span data-stu-id="da152-438">To test the offline capability, run the application, log in as either employee or manager, and then select **Work offline**.</span></span> <span data-ttu-id="da152-439">修改文字方塊中的值，然後關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-439">Modify the value in the text box, and then close the application.</span></span> <span data-ttu-id="da152-440">重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="da152-440">Restart the application.</span></span> <span data-ttu-id="da152-441">登入前，以滑鼠右鍵按一下工作列上通知區域中的 ASP.NET 程式開發伺服器圖示，然後按一下 [停止] 。</span><span class="sxs-lookup"><span data-stu-id="da152-441">Before you log in, right-click the ASP.NET Development Server icon in the notification area of the taskbar and then click **Stop**.</span></span> <span data-ttu-id="da152-442">接著以正常的方式登入。</span><span class="sxs-lookup"><span data-stu-id="da152-442">Then, log in like normal.</span></span> <span data-ttu-id="da152-443">即使伺服器不在執行中，您仍然可以登入。</span><span class="sxs-lookup"><span data-stu-id="da152-443">Even when the server is not running, you can still log in.</span></span> <span data-ttu-id="da152-444">修改文字方塊的值、結束，然後再重新啟動，以查看修改過的值。</span><span class="sxs-lookup"><span data-stu-id="da152-444">Modify the text box value, exit, and restart to see the modified value.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="da152-445">總結</span><span class="sxs-lookup"><span data-stu-id="da152-445">Summary</span></span>  
 <span data-ttu-id="da152-446">在本逐步解說中，您已了解如何在 Windows Form 應用程式中啟用及使用用戶端應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="da152-446">In this walkthrough, you learned how to enable and use client application services in a Windows Forms application.</span></span> <span data-ttu-id="da152-447">設定測試伺服器之後，您可以將程式碼加入應用程式以驗證使用者，並從伺服器擷取使用者角色和應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="da152-447">After setting up a test server, you added code to your application to authenticate users and retrieve user roles and application settings from the server.</span></span> <span data-ttu-id="da152-448">您也了解如何啟用離線模式，以便讓應用程式在無法連接時，使用本機資料快取而不是遠端服務。</span><span class="sxs-lookup"><span data-stu-id="da152-448">You also learned how to enable offline mode so that your application uses a local data cache instead of the remote services when connectivity is not available.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="da152-449">後續步驟</span><span class="sxs-lookup"><span data-stu-id="da152-449">Next Steps</span></span>  
 <span data-ttu-id="da152-450">在真實世界應用程式中，您會從遠端伺服器存取許多使用者的資料，而遠端伺服器並非隨時都能使用，或是可能會在未告知的情況下離線。</span><span class="sxs-lookup"><span data-stu-id="da152-450">In a real-world application, you will access data for many users from a remote server that may not always be available, or may go down without notice.</span></span> <span data-ttu-id="da152-451">為了讓應用程式更強固，您必須能夠適當地回應服務無法使用的各種情況。</span><span class="sxs-lookup"><span data-stu-id="da152-451">To make your application robust, you must respond appropriately to situations where the service is not available.</span></span> <span data-ttu-id="da152-452">本逐步解說包含 try/catch 區塊，可攔截 <xref:System.Net.WebException> ，並在服務無法使用時顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="da152-452">This walkthrough includes try/catch blocks to catch a <xref:System.Net.WebException> and display an error message when the service is not available.</span></span> <span data-ttu-id="da152-453">在實際執行的程式碼中，您可能想要藉由切換至離線模式、結束應用程式，或拒絕存取特定功能的方式處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="da152-453">In production code, you might want to handle this case by switching to offline mode, exiting the application, or denying access to specific functionality.</span></span>  
  
 <span data-ttu-id="da152-454">為了加強應用程式的安全性，請務必在部署前徹底測試應用程式和伺服器。</span><span class="sxs-lookup"><span data-stu-id="da152-454">To increase the security of your application, make sure to thoroughly test the application and server before deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da152-455">請參閱</span><span class="sxs-lookup"><span data-stu-id="da152-455">See Also</span></span>  
 [<span data-ttu-id="da152-456">用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="da152-456">Client Application Services</span></span>](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [<span data-ttu-id="da152-457">用戶端應用程式服務概觀</span><span class="sxs-lookup"><span data-stu-id="da152-457">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [<span data-ttu-id="da152-458">如何：設定用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="da152-458">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [<span data-ttu-id="da152-459">ASP.NET 網站管理工具</span><span class="sxs-lookup"><span data-stu-id="da152-459">ASP.NET Web Site Administration Tool</span></span>](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [<span data-ttu-id="da152-460">建立及設定 SQL Server 的應用程式服務資料庫</span><span class="sxs-lookup"><span data-stu-id="da152-460">Creating and Configuring the Application Services Database for SQL Server</span></span>](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [<span data-ttu-id="da152-461">逐步解說：使用 ASP.NET 應用程式服務</span><span class="sxs-lookup"><span data-stu-id="da152-461">Walkthrough: Using ASP.NET Application Services</span></span>](http://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
