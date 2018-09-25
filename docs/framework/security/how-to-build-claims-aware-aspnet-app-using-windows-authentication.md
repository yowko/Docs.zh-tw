---
title: 如何：使用 Windows 驗證建置宣告感知 ASP.NET 應用程式
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 2c7877c452c729b30029cad1a8e17600f3dc9661
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112422"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="277c0-102">如何：使用 Windows 驗證建置宣告感知 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="277c0-103">適用於</span><span class="sxs-lookup"><span data-stu-id="277c0-103">Applies To</span></span>  
  
-   <span data-ttu-id="277c0-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="277c0-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="277c0-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="277c0-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="277c0-106">總結</span><span class="sxs-lookup"><span data-stu-id="277c0-106">Summary</span></span>  
 <span data-ttu-id="277c0-107">此操作說明提供詳細逐步程序，以建立使用 Windows 驗證的簡單宣告感知 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="277c0-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="277c0-108">還提供了一些指示，說明如何測試應用程式，以確認在使用者使用 Windows 驗證登入時會呈現宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="277c0-109">內容</span><span class="sxs-lookup"><span data-stu-id="277c0-109">Contents</span></span>  
  
-   <span data-ttu-id="277c0-110">目標</span><span class="sxs-lookup"><span data-stu-id="277c0-110">Objectives</span></span>  
  
-   <span data-ttu-id="277c0-111">總覽</span><span class="sxs-lookup"><span data-stu-id="277c0-111">Overview</span></span>  
  
-   <span data-ttu-id="277c0-112">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="277c0-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="277c0-113">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="277c0-114">步驟 2 – 設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="277c0-115">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="277c0-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="277c0-116">目標</span><span class="sxs-lookup"><span data-stu-id="277c0-116">Objectives</span></span>  
  
-   <span data-ttu-id="277c0-117">設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="277c0-118">測試 ASP.NET Web Forms 應用程式以查看它是否正常運作</span><span class="sxs-lookup"><span data-stu-id="277c0-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="277c0-119">總覽</span><span class="sxs-lookup"><span data-stu-id="277c0-119">Overview</span></span>  
 <span data-ttu-id="277c0-120">在 .NET 4.5 中，WIF 和其宣告型授權已包含為 Framework 的不可或缺部分。</span><span class="sxs-lookup"><span data-stu-id="277c0-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="277c0-121">以前，如果您想要來自 ASP.NET 使用者的宣告，需要安裝 WIF，然後將介面轉換為主體物件，例如 `Thread.CurrentPrincipal` 或 `HttpContext.Current.User`。</span><span class="sxs-lookup"><span data-stu-id="277c0-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="277c0-122">現在，這些主體物件會自動提供宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="277c0-123">Windows 驗證受益於 .NET 4.5 中包含 WIF，因為 Windows 認證所驗證的所有使用者都會自動具有與其建立關聯的宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="277c0-124">如這個使用方法所示範，您可以在使用 Windows 驗證的 ASP.NET 應用程式中立即開始使用這些宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="277c0-125">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="277c0-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="277c0-126">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="277c0-127">步驟 2 – 設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="277c0-128">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="277c0-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="277c0-129">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="277c0-130">在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="277c0-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="277c0-131">建立簡單的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="277c0-132">啟動 Visual Studio，然後依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="277c0-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="277c0-133">在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="277c0-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="277c0-134">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="277c0-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="277c0-135">建立 **TestApp** 專案之後，在方案總管中按一下該專案。</span><span class="sxs-lookup"><span data-stu-id="277c0-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="277c0-136">專案的屬性會出現在方案總管下方的 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="277c0-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="277c0-137">將 **Windows 驗證**屬性設定為 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="277c0-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="277c0-138">在新的 ASP.NET 應用程式中，預設會停用 Windows 驗證，因此您必須以手動方式啟用它。</span><span class="sxs-lookup"><span data-stu-id="277c0-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="277c0-139">步驟 2 – 設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="277c0-140">在此步驟中，您將組態項目新增至 *Web.config* 組態檔，並修改 *Default.aspx* 檔案來顯示帳戶的宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="277c0-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="277c0-141">設定使用 Windows 驗證之宣告的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="277c0-142">在 **TestApp** 專案的 *Default.aspx* 檔案中，將現有標記取代為下列標記：</span><span class="sxs-lookup"><span data-stu-id="277c0-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     <span data-ttu-id="277c0-143">這個步驟會將 GridView 控制項新增至您的 *Default.aspx* 網頁，其中填入擷取自 Windows 驗證的宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2.  <span data-ttu-id="277c0-144">儲存 *Default.aspx* 檔案，然後開啟其名為 *Default.aspx.cs* 的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="277c0-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="277c0-145">將現有的程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="277c0-145">Replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="277c0-146">上述程式碼會顯示有關已驗證使用者的宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-146">The above code will display claims about an authenticated user.</span></span>  
  
3.  <span data-ttu-id="277c0-147">若要變更應用程式的驗證類型，請修改專案的根 *Web.config* 檔案中 **\<system.web>** 區段的 **\<authentication>** 區塊，使其只包含下列組態項目：</span><span class="sxs-lookup"><span data-stu-id="277c0-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  <span data-ttu-id="277c0-148">最後，修改相同 *Web.config* 檔案中 **\<system.web>** 區段的 **\<authorization>** 區塊，以強制執行驗證：</span><span class="sxs-lookup"><span data-stu-id="277c0-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="277c0-149">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="277c0-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="277c0-150">在此步驟中，您將測試 ASP.NET Web Forms 應用程式，並確認在使用者使用 Windows 驗證登入時會呈現宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="277c0-151">測試使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="277c0-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="277c0-152">按 **F5** 鍵以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="277c0-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="277c0-153">您應該會看到 *Default.aspx*，而且您的 Windows 帳戶名稱 (包括網域名稱) 應該已經在網頁的右上方顯示為已驗證的使用者。</span><span class="sxs-lookup"><span data-stu-id="277c0-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="277c0-154">頁面的內容應該包含一個資料表，其中填入了擷取自 Windows 帳戶的宣告。</span><span class="sxs-lookup"><span data-stu-id="277c0-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
