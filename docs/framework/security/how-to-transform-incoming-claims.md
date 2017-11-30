---
title: "如何：轉換傳入宣告"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="ad30e-102">如何：轉換傳入宣告</span><span class="sxs-lookup"><span data-stu-id="ad30e-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="ad30e-103">適用於</span><span class="sxs-lookup"><span data-stu-id="ad30e-103">Applies To</span></span>  
  
-   <span data-ttu-id="ad30e-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="ad30e-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="ad30e-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="ad30e-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="ad30e-106">摘要</span><span class="sxs-lookup"><span data-stu-id="ad30e-106">Summary</span></span>  
 <span data-ttu-id="ad30e-107">此操作說明提供詳細逐步程序，以建立簡單宣告感知 ASP.NET Web Forms 應用程式和轉換傳入宣告。</span><span class="sxs-lookup"><span data-stu-id="ad30e-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="ad30e-108">此外，還提供一些指示，說明如何測試應用程式，以確認應用程式執行時會呈現宣告。</span><span class="sxs-lookup"><span data-stu-id="ad30e-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="ad30e-109">內容</span><span class="sxs-lookup"><span data-stu-id="ad30e-109">Contents</span></span>  
  
-   <span data-ttu-id="ad30e-110">目標</span><span class="sxs-lookup"><span data-stu-id="ad30e-110">Objectives</span></span>  
  
-   <span data-ttu-id="ad30e-111">概觀</span><span class="sxs-lookup"><span data-stu-id="ad30e-111">Overview</span></span>  
  
-   <span data-ttu-id="ad30e-112">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="ad30e-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ad30e-113">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ad30e-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="ad30e-114">步驟 2 – 使用自訂的 ClaimsAuthenticationManager 實作宣告轉換</span><span class="sxs-lookup"><span data-stu-id="ad30e-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="ad30e-115">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="ad30e-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="ad30e-116">目標</span><span class="sxs-lookup"><span data-stu-id="ad30e-116">Objectives</span></span>  
  
-   <span data-ttu-id="ad30e-117">設定宣告型驗證的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ad30e-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="ad30e-118">藉由新增系統管理員角色宣告來轉換傳入宣告</span><span class="sxs-lookup"><span data-stu-id="ad30e-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="ad30e-119">測試 ASP.NET Web Forms 應用程式以查看它是否正常運作</span><span class="sxs-lookup"><span data-stu-id="ad30e-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ad30e-120">概觀</span><span class="sxs-lookup"><span data-stu-id="ad30e-120">Overview</span></span>  
 <span data-ttu-id="ad30e-121">WIF 會公開一個名為 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別，其可讓使用者在向信賴憑證者 (RP) 應用程式呈現宣告之前，修改這些宣告。</span><span class="sxs-lookup"><span data-stu-id="ad30e-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="ad30e-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> 可用來分隔驗證與基礎應用程式程式碼之間的問題。</span><span class="sxs-lookup"><span data-stu-id="ad30e-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="ad30e-123">下列範例示範如何在 RP 可能需要的傳入 <xref:System.Security.Claims.ClaimsPrincipal> 宣告中加入角色。</span><span class="sxs-lookup"><span data-stu-id="ad30e-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="ad30e-124">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="ad30e-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ad30e-125">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ad30e-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="ad30e-126">步驟 2 – 使用自訂的 ClaimsAuthenticationManager 實作宣告轉換</span><span class="sxs-lookup"><span data-stu-id="ad30e-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="ad30e-127">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="ad30e-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="ad30e-128">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ad30e-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="ad30e-129">在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad30e-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="ad30e-130">建立簡單的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="ad30e-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="ad30e-131">以系統管理員身分的高階權限模式來啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ad30e-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="ad30e-132">在 Visual Studio 中，依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="ad30e-133">在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="ad30e-134">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="ad30e-135">以滑鼠右鍵按一下方案總管底下的 [TestApp] 專案，然後選取 [身分識別與存取]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="ad30e-136">[身分識別與存取] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ad30e-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="ad30e-137">在 [提供者] 底下，選取 [Test your application with the Local Development STS] (使用本機開發 STS 測試應用程式}，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="ad30e-138">在 *Default.aspx* 檔案中，將現有標記取代為下列標記，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="ad30e-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
          <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
8.  <span data-ttu-id="ad30e-139">開啟名為 *Default.aspx.cs* 的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="ad30e-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="ad30e-140">將現有程式碼取代為下列程式碼，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="ad30e-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="ad30e-141">步驟 2 – 使用自訂的 ClaimsAuthenticationManager 實作宣告轉換</span><span class="sxs-lookup"><span data-stu-id="ad30e-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="ad30e-142">在此步驟中，您將覆寫 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別中的預設功能，以便將系統管理員角色新增到傳入主體。</span><span class="sxs-lookup"><span data-stu-id="ad30e-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="ad30e-143">使用自訂的 ClaimsAuthenticationManager 實作宣告轉換</span><span class="sxs-lookup"><span data-stu-id="ad30e-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="ad30e-144">在 Visual Studio 中，以滑鼠右鍵按一下方案，然後依序按一下 [新增] 和 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="ad30e-145">在 [新增專案] 視窗中，選取 [Visual C#] 範本清單中的 [類別庫]，輸入 `ClaimsTransformation`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="ad30e-146">您的方案資料夾中就會建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="ad30e-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="ad30e-147">以滑鼠右鍵按一下 [ClaimsTransformation] 專案底下的 [參考]，然後按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="ad30e-148">在 [參考管理員] 視窗中，選取 **System.IdentityModel**，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ad30e-149">開啟 **Class1.cs**，如果沒有該檔案，請以滑鼠右鍵按一下 [ClaimsTransformation]，然後依序按一下 [新增] 和 [類別...]</span><span class="sxs-lookup"><span data-stu-id="ad30e-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="ad30e-150">將下列 using 指示詞新增程式碼檔案：</span><span class="sxs-lookup"><span data-stu-id="ad30e-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="ad30e-151">在程式碼檔案中新增下列類別和方法。</span><span class="sxs-lookup"><span data-stu-id="ad30e-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="ad30e-152">下列程式碼僅供示範之用；請務必在生產環境程式碼中驗證預期權限。</span><span class="sxs-lookup"><span data-stu-id="ad30e-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
    ```csharp  
    public class ClaimsTransformationModule : ClaimsAuthenticationManager  
    {  
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)  
        {  
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)  
            {  
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));  
            }  
  
            return incomingPrincipal;  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="ad30e-153">儲存檔案，並建置 **ClaimsTransformation** 專案。</span><span class="sxs-lookup"><span data-stu-id="ad30e-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="ad30e-154">在 [TestApp] ASP.NET 專案中，以滑鼠右鍵按一下參考，然後按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="ad30e-155">在 [參考管理員] 視窗中，選取左側功能表中的 [方案]，從填入的選項中選取 [ClaimsTransformation]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ad30e-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="ad30e-156">在根 **Web.config** 檔案中，巡覽至 **\<system.identityModel>** 項目。</span><span class="sxs-lookup"><span data-stu-id="ad30e-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="ad30e-157">在 **\<identityConfiguration>** 項目內，新增下列一行並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="ad30e-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="ad30e-158">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="ad30e-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="ad30e-159">在此步驟中，您將測試 ASP.NET Web Forms 應用程式，並確認使用者使用表單驗證登入時呈現宣告。</span><span class="sxs-lookup"><span data-stu-id="ad30e-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="ad30e-160">測試使用表單驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ad30e-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="ad30e-161">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad30e-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="ad30e-162">您應該會看到 *Default.aspx*。</span><span class="sxs-lookup"><span data-stu-id="ad30e-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="ad30e-163">在 *Default.aspx* 頁面上，您應該會看到 [Your Claims] (您的宣告) 標題下方有一個資料表，其中包含有關您帳戶的 **Issuer**、**OriginalIssuer**、**Type**、**Value** 和 **ValueType** 宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="ad30e-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="ad30e-164">應該會以下列方式呈現最後一個資料列：</span><span class="sxs-lookup"><span data-stu-id="ad30e-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="ad30e-165">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="ad30e-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="ad30e-166">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="ad30e-166">LOCAL AUTHORITY</span></span>|<span data-ttu-id="ad30e-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span><span class="sxs-lookup"><span data-stu-id="ad30e-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span></span>|<span data-ttu-id="ad30e-168">系統管理員</span><span class="sxs-lookup"><span data-stu-id="ad30e-168">Admin</span></span>|<span data-ttu-id="ad30e-169">http://www.w3.org/2001/XMLSchema#string</span><span class="sxs-lookup"><span data-stu-id="ad30e-169">http://www.w3.org/2001/XMLSchema#string</span></span>|
