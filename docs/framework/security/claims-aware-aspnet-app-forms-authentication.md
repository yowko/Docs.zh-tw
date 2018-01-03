---
title: "如何：使用表單型驗證建置宣告感知的 ASP.NET 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f4977a40d440ca45a3130fb1b06e0b286a2ab2f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="ca16e-102">如何：使用表單型驗證建置宣告感知的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="ca16e-103">適用於</span><span class="sxs-lookup"><span data-stu-id="ca16e-103">Applies To</span></span>  
  
-   <span data-ttu-id="ca16e-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="ca16e-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="ca16e-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="ca16e-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="ca16e-106">摘要</span><span class="sxs-lookup"><span data-stu-id="ca16e-106">Summary</span></span>  
 <span data-ttu-id="ca16e-107">此＜如何＞一文提供詳細逐步程序，以建立使用表單驗證的簡單宣告感知 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca16e-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="ca16e-108">它也提供指示，有關如何測試應用程式來確認在使用者利用表單驗證登入時呈現宣告。</span><span class="sxs-lookup"><span data-stu-id="ca16e-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="ca16e-109">內容</span><span class="sxs-lookup"><span data-stu-id="ca16e-109">Contents</span></span>  
  
-   <span data-ttu-id="ca16e-110">目標</span><span class="sxs-lookup"><span data-stu-id="ca16e-110">Objectives</span></span>  
  
-   <span data-ttu-id="ca16e-111">概觀</span><span class="sxs-lookup"><span data-stu-id="ca16e-111">Overview</span></span>  
  
-   <span data-ttu-id="ca16e-112">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="ca16e-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ca16e-113">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="ca16e-114">步驟 2 - 設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="ca16e-115">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="ca16e-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="ca16e-116">目標</span><span class="sxs-lookup"><span data-stu-id="ca16e-116">Objectives</span></span>  
  
-   <span data-ttu-id="ca16e-117">設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="ca16e-118">測試 ASP.NET Web Forms 應用程式以查看它是否正常運作</span><span class="sxs-lookup"><span data-stu-id="ca16e-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ca16e-119">概觀</span><span class="sxs-lookup"><span data-stu-id="ca16e-119">Overview</span></span>  
 <span data-ttu-id="ca16e-120">在 .NET 4.5 中，WIF 和其宣告型授權已包含為 Framework 的不可或缺部分。</span><span class="sxs-lookup"><span data-stu-id="ca16e-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="ca16e-121">以前，如果您想要來自 ASP.NET 使用者的宣告，需要安裝 WIF，然後將介面轉換為主體物件，例如 `Thread.CurrentPrincipal` 或 `HttpContext.Current.User`。</span><span class="sxs-lookup"><span data-stu-id="ca16e-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="ca16e-122">現在，這些主體物件會自動提供宣告。</span><span class="sxs-lookup"><span data-stu-id="ca16e-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="ca16e-123">表單驗證受益於 .NET 4.5 中包含 WIF，因為表單驗證的所有使用者都會自動具有與其建立關聯的宣告。</span><span class="sxs-lookup"><span data-stu-id="ca16e-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="ca16e-124">如這個使用方法所示範，您可以在使用表單驗證的 ASP.NET 應用程式中立即開始使用這些宣告。</span><span class="sxs-lookup"><span data-stu-id="ca16e-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="ca16e-125">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="ca16e-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ca16e-126">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="ca16e-127">步驟 2 - 設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="ca16e-128">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="ca16e-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="ca16e-129">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="ca16e-130">在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca16e-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="ca16e-131">建立簡單的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="ca16e-132">啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="ca16e-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="ca16e-133">在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="ca16e-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="ca16e-134">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ca16e-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="ca16e-135">步驟 2 - 設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="ca16e-136">在此步驟中，您將組態項目新增至 *Web.config* 組態檔，並編輯 *Default.aspx* 檔案來顯示帳戶的宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="ca16e-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="ca16e-137">設定使用表單驗證之宣告的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="ca16e-138">在 *Default.aspx* 檔案中，將現有標記取代為下列標記：</span><span class="sxs-lookup"><span data-stu-id="ca16e-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
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
  
     <span data-ttu-id="ca16e-139">這個步驟會將 GridView 控制項新增至您的 *Default.aspx* 網頁，其中填入擷取自表單驗證的宣告。</span><span class="sxs-lookup"><span data-stu-id="ca16e-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="ca16e-140">儲存 *Default.aspx* 檔案，然後開啟其名為 *Default.aspx.cs* 的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="ca16e-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="ca16e-141">將現有的程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ca16e-141">Replace the existing code with the following:</span></span>  
  
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
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="ca16e-142">上述程式碼會顯示已驗證使用者的宣告，包含表單驗證所識別的使用者。</span><span class="sxs-lookup"><span data-stu-id="ca16e-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="ca16e-143">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="ca16e-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="ca16e-144">在此步驟中，您將測試 ASP.NET Web Forms 應用程式，並確認使用者使用表單驗證登入時呈現宣告。</span><span class="sxs-lookup"><span data-stu-id="ca16e-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="ca16e-145">測試使用表單驗證之宣告的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca16e-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="ca16e-146">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca16e-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="ca16e-147">應該會向您呈現 *Default.aspx*，而頁面右上方會有 [註冊] 和 [登入] 連結。</span><span class="sxs-lookup"><span data-stu-id="ca16e-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="ca16e-148">按一下 [註冊]。</span><span class="sxs-lookup"><span data-stu-id="ca16e-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="ca16e-149">在 [註冊] 頁面上，建立使用者帳戶，然後按一下 [註冊]。</span><span class="sxs-lookup"><span data-stu-id="ca16e-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="ca16e-150">將使用表單驗證建立您的帳戶，並自動將您登入。</span><span class="sxs-lookup"><span data-stu-id="ca16e-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="ca16e-151">將您重新導向至首頁之後，應該會看到 [Your Claims] (您的宣告) 標題下方有一個資料表，其中包含有關您帳戶的 **Issuer**、**OriginalIssuer**、**Type**、**Value** 和 **ValueType** 宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="ca16e-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
