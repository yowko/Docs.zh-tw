---
title: 如何：使用 WIF 顯示登入的狀態
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: 7d3d23dc1f2e081c0a7c53fbdfaef749c9729fd4
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584385"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="e2f5c-102">如何：使用 WIF 顯示登入的狀態</span><span class="sxs-lookup"><span data-stu-id="e2f5c-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="e2f5c-103">適用於</span><span class="sxs-lookup"><span data-stu-id="e2f5c-103">Applies To</span></span>  
  
-   <span data-ttu-id="e2f5c-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="e2f5c-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
-   <span data-ttu-id="e2f5c-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="e2f5c-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e2f5c-106">總結</span><span class="sxs-lookup"><span data-stu-id="e2f5c-106">Summary</span></span>  
 <span data-ttu-id="e2f5c-107">本主題描述如何在啟用 WIF 的 ASP.NET 應用程式中顯示登入狀態。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="e2f5c-108">WIF 提供了一些機制，可讓您的應用程式成為宣告感知，以及管理應用程式資源的驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e2f5c-109">內容</span><span class="sxs-lookup"><span data-stu-id="e2f5c-109">Contents</span></span>  
  
-   <span data-ttu-id="e2f5c-110">總覽</span><span class="sxs-lookup"><span data-stu-id="e2f5c-110">Overview</span></span>  
  
-   <span data-ttu-id="e2f5c-111">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="e2f5c-111">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e2f5c-112">步驟 1 – 安裝識別身分與存取延伸模組</span><span class="sxs-lookup"><span data-stu-id="e2f5c-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="e2f5c-113">步驟 2 – 建立信賴憑證者的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="e2f5c-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="e2f5c-114">步驟 3 – 啟用本機開發 STS 以驗證使用者</span><span class="sxs-lookup"><span data-stu-id="e2f5c-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="e2f5c-115">步驟 4 – 修改 ASP.NET 應用程式以顯示登入狀態</span><span class="sxs-lookup"><span data-stu-id="e2f5c-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="e2f5c-116">步驟 5 – 測試 WIF 與 ASP.NET 應用程式之間的整合</span><span class="sxs-lookup"><span data-stu-id="e2f5c-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e2f5c-117">總覽</span><span class="sxs-lookup"><span data-stu-id="e2f5c-117">Overview</span></span>  
 <span data-ttu-id="e2f5c-118">本主題示範如何使用 WIF 建立簡單的宣告感知應用程式，以及如何輕鬆顯示使用者是否已登入。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="e2f5c-119">下列步驟會使用 Visual Studio 身分識別與存取延伸模組所隨附的本機開發 STS 。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="e2f5c-120">本機開發 STS 是用來測試和開發環境，可提供簡單的方法，將宣告整合到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="e2f5c-121">它永遠不應該用於生產環境中，因為它不會執行實際的驗證，而且不需要認證。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="e2f5c-122">不過，對於使用實際的驗證準備好用於生產環境的應用程式而言，下列步驟中的命令式程式碼都相同。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e2f5c-123">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="e2f5c-123">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e2f5c-124">步驟 1 – 安裝識別身分與存取延伸模組</span><span class="sxs-lookup"><span data-stu-id="e2f5c-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="e2f5c-125">步驟 2 – 建立信賴憑證者的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="e2f5c-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="e2f5c-126">步驟 3 – 啟用本機開發 STS 以驗證使用者</span><span class="sxs-lookup"><span data-stu-id="e2f5c-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="e2f5c-127">步驟 4 – 修改 ASP.NET 應用程式以顯示登入狀態</span><span class="sxs-lookup"><span data-stu-id="e2f5c-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="e2f5c-128">步驟 5 – 測試 WIF 與 ASP.NET 應用程式之間的整合</span><span class="sxs-lookup"><span data-stu-id="e2f5c-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="e2f5c-129">步驟 1 – 安裝識別身分與存取延伸模組</span><span class="sxs-lookup"><span data-stu-id="e2f5c-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="e2f5c-130">此步驟描述如何設定 Visual Studio 2012 的身分識別與存取延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="e2f5c-131">這項延伸模組會將設定您的應用程式與 STS 端點進行通訊的程序自動化。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="e2f5c-132">安裝識別身分與存取延伸模組</span><span class="sxs-lookup"><span data-stu-id="e2f5c-132">To install the Identity and Access extension</span></span>  
  
1.  <span data-ttu-id="e2f5c-133">以系統管理員身分的高階權限模式來啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="e2f5c-134">在 Visual Studio 中，依序按一下 [工具]  和 [延伸模組管理員] 。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="e2f5c-135">[延伸模組管理員] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-135">The **Extension Manager** window appears.</span></span>  
  
3.  <span data-ttu-id="e2f5c-136">在 [延伸模組管理員] 中，按一下左側功能表中的 [Online Extensions] (線上延伸模組)，然後選取 [Visual Studio 組件庫]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4.  <span data-ttu-id="e2f5c-137">在右上角的 [延伸模組管理員] 中，搜尋 [身分識別與存取]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5.  <span data-ttu-id="e2f5c-138">[身分識別與存取] 項目會出現在搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="e2f5c-139">按一下它，然後按一下 [下載]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-139">Click it, and then click **Download**.</span></span>  
  
6.  <span data-ttu-id="e2f5c-140">[下載並安裝]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="e2f5c-141">如果您同意授權條款，請按一下 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-141">If you agree with the license terms, click **Install**.</span></span>  
  
7.  <span data-ttu-id="e2f5c-142">當 [身分識別與存取] 延伸模組已完成安裝後，請以系統管理員模式重新啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="e2f5c-143">步驟 2 – 建立信賴憑證者的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="e2f5c-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="e2f5c-144">此步驟描述如何建立將與 WIF 整合的信賴憑證者 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e2f5c-145">建立簡單的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="e2f5c-145">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="e2f5c-146">啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="e2f5c-147">在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e2f5c-148">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="e2f5c-149">步驟 3 – 啟用本機開發 STS 以驗證使用者</span><span class="sxs-lookup"><span data-stu-id="e2f5c-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="e2f5c-150">此步驟描述如何在應用程式中啟用本機開發 STS。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="e2f5c-151">透過使用 Visual Studio 的身分識別與存取延伸模組，即可啟用本機開發 STS。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="e2f5c-152">在 ASP.NET 應用程式中啟用本機開發 STS</span><span class="sxs-lookup"><span data-stu-id="e2f5c-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1.  <span data-ttu-id="e2f5c-153">在 Visual Studio 中，以滑鼠右鍵按一下方案總管底下的 [TestService]，然後選取 [身分識別與存取]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2.  <span data-ttu-id="e2f5c-154">[身分識別與存取] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="e2f5c-155">在 [提供者] 底下，選取 [Test your application with the Local Development STS] (使用本機開發 STS 測試應用程式}，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="e2f5c-156">步驟 4 – 修改 ASP.NET 應用程式以顯示登入狀態</span><span class="sxs-lookup"><span data-stu-id="e2f5c-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="e2f5c-157">此步驟描述如何修改 ASP.NET 應用程式，以動態方式顯示目前的使用者是否已登入。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="e2f5c-158">一旦設定了 STS 提供者，WIF 就會處理連入宣告。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="e2f5c-159">現在，您需要設定應用程式的程式碼，以顯示驗證的結果。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="e2f5c-160">顯示登入狀態</span><span class="sxs-lookup"><span data-stu-id="e2f5c-160">To display sign in status</span></span>  
  
1.  <span data-ttu-id="e2f5c-161">在 Visual Studio 中，開啟 **TestApp** 專案底下的 **Default.aspx** 檔案。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2.  <span data-ttu-id="e2f5c-162">使用下列標記取代 **Default.aspx** 檔案中的現有標記：</span><span class="sxs-lookup"><span data-stu-id="e2f5c-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  <span data-ttu-id="e2f5c-163">儲存 **Default.aspx**，然後開啟其名為 **Default.aspx.cs** 的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2f5c-164">在方案總管中，**Default.aspx.cs** 可能隱藏在 **Default.aspx** 的下方。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="e2f5c-165">如果看不到 **Default.aspx.cs**，請按一下 **Default.aspx** 旁邊的三角形來展開它。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4.  <span data-ttu-id="e2f5c-166">使用下列程式碼取代 **Default.aspx.cs** 中的現有程式碼：</span><span class="sxs-lookup"><span data-stu-id="e2f5c-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="e2f5c-167">儲存 **Default.aspx.cs**，然後建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="e2f5c-168">步驟 5 – 測試 WIF 與 ASP.NET 應用程式之間的整合</span><span class="sxs-lookup"><span data-stu-id="e2f5c-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="e2f5c-169">此步驟描述如何測試 WIF 與 ASP.NET 應用程式之間的整合。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="e2f5c-170">測試 WIF 與 ASP.NET 之間的整合</span><span class="sxs-lookup"><span data-stu-id="e2f5c-170">To test the integration between WIF and ASP.NET</span></span>  
  
1.  <span data-ttu-id="e2f5c-171">在 Visual Studio 中，按 **F5** 鍵開始對應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="e2f5c-172">如果沒有發現任何錯誤，則會開啟新的瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-172">If no errors are found, a new browser window will open.</span></span>  
  
2.  <span data-ttu-id="e2f5c-173">您可能會注意到瀏覽器以無訊息模式將您的要求重新導向至 STS，然後開啟 Default.aspx 網頁。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="e2f5c-174">如果 WIF 已正確設定，您應該會看到網站顯示下列文字：**"You are signed in"**。</span><span class="sxs-lookup"><span data-stu-id="e2f5c-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
