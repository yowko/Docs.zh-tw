---
title: 如何：使用 WIF 建置宣告感知 ASP.NET Web Forms 應用程式
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 74f15c3ac6e5192ce3565579d515198d3b7e39f5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302266"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="e6f23-102">如何：使用 WIF 建置宣告感知 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="e6f23-103">適用於</span><span class="sxs-lookup"><span data-stu-id="e6f23-103">Applies To</span></span>  
  
-   <span data-ttu-id="e6f23-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e6f23-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="e6f23-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="e6f23-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e6f23-106">總結</span><span class="sxs-lookup"><span data-stu-id="e6f23-106">Summary</span></span>  
 <span data-ttu-id="e6f23-107">此操作說明提供詳細逐步程序，以建立簡單宣告感知 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6f23-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="e6f23-108">還提供了一些指示，說明如何測試簡單宣告感知 ASP.NET Web Forms 應用程式成功實作同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="e6f23-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="e6f23-109">此操作說明沒有提供建立安全性權杖服務 (STS) 的詳細指示，並假設您已設定 STS。</span><span class="sxs-lookup"><span data-stu-id="e6f23-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e6f23-110">內容</span><span class="sxs-lookup"><span data-stu-id="e6f23-110">Contents</span></span>  
  
-   <span data-ttu-id="e6f23-111">目標</span><span class="sxs-lookup"><span data-stu-id="e6f23-111">Objectives</span></span>  
  
-   <span data-ttu-id="e6f23-112">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="e6f23-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e6f23-113">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e6f23-114">步驟 2 – 設定宣告型驗證的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="e6f23-115">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="e6f23-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="e6f23-116">目標</span><span class="sxs-lookup"><span data-stu-id="e6f23-116">Objectives</span></span>  
  
-   <span data-ttu-id="e6f23-117">設定宣告型驗證的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="e6f23-118">測試成功宣告感知 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e6f23-119">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="e6f23-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e6f23-120">步驟 1 – 建立簡單的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e6f23-121">步驟 2 – 設定同盟驗證的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
-   <span data-ttu-id="e6f23-122">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="e6f23-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="e6f23-123">步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="e6f23-124">在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6f23-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e6f23-125">建立簡單的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-125">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="e6f23-126">啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="e6f23-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="e6f23-127">在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="e6f23-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="e6f23-128">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e6f23-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="e6f23-129">步驟 2 – 設定宣告型驗證的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="e6f23-130">在此步驟中，您將組態項目新增至 ASP.NET Web Forms 應用程式的 *Web.config* 組態檔，使其成為宣告感知。</span><span class="sxs-lookup"><span data-stu-id="e6f23-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="e6f23-131">設定宣告型驗證的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="e6f23-132">緊接在 **\<configuration>** 開啟項目後，將下列組態區段項目新增至 *Web.config* 組態檔：</span><span class="sxs-lookup"><span data-stu-id="e6f23-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="e6f23-133">新增 **\<location>** 項目，以允許存取應用程式的同盟中繼資料：</span><span class="sxs-lookup"><span data-stu-id="e6f23-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="e6f23-134">在 **\<system.web>** 項目內新增下列組態項目，以拒絕使用者、停用原始驗證，以及啟用 WIF 來管理驗證。</span><span class="sxs-lookup"><span data-stu-id="e6f23-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="e6f23-135">新增 **\<system.webServer>** 項目，以定義同盟驗證的模組。</span><span class="sxs-lookup"><span data-stu-id="e6f23-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="e6f23-136">請注意，*PublicKeyToken* 屬性必須與先前新增之 **\<configSections>** 項目的 *PublicKeyToken* 屬性相同：</span><span class="sxs-lookup"><span data-stu-id="e6f23-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. <span data-ttu-id="e6f23-137">新增下列 Windows Identity Foundation 相關組態項目，並確認 ASP.NET 應用程式的 URL 和連接埠編號符合 **\<audienceUris>** 項目、**\<wsFederation>** 項目的 **realm** 屬性和 **\<wsFederation>** 項目的 **reply** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f23-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="e6f23-138">也請確認 **issuer** 值符合安全性權杖服務 (STS) 的 URL。</span><span class="sxs-lookup"><span data-stu-id="e6f23-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. <span data-ttu-id="e6f23-139">新增 <xref:System.IdentityModel> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e6f23-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7. <span data-ttu-id="e6f23-140">編譯方案，以確定沒有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6f23-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="e6f23-141">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="e6f23-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="e6f23-142">在此步驟中，您將測試針對宣告型驗證設定的 ASP.NET Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6f23-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="e6f23-143">為了執行基本測試，您將新增程式碼以顯示安全性權杖服務 (STS) 所發行之權杖中的宣告。</span><span class="sxs-lookup"><span data-stu-id="e6f23-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="e6f23-144">測試宣告型驗證的 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="e6f23-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="e6f23-145">開啟 **TestApp** 專案下的 **Default.aspx** 檔案，並將其現有標記取代為下列標記：</span><span class="sxs-lookup"><span data-stu-id="e6f23-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2. <span data-ttu-id="e6f23-146">儲存 **Default.aspx**，然後開啟其名為 **Default.aspx.cs** 的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="e6f23-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e6f23-147">在方案總管中，**Default.aspx.cs** 可能隱藏在 **Default.aspx** 的下方。</span><span class="sxs-lookup"><span data-stu-id="e6f23-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="e6f23-148">如果看不到 **Default.aspx.cs**，請按一下 **Default.aspx** 旁邊的三角形來展開它。</span><span class="sxs-lookup"><span data-stu-id="e6f23-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3. <span data-ttu-id="e6f23-149">將 **Default.aspx.cs** 之 **Page_Load** 方法中的現有程式碼，取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e6f23-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4. <span data-ttu-id="e6f23-150">儲存 **Default.aspx.cs**，然後建置方案。</span><span class="sxs-lookup"><span data-stu-id="e6f23-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5. <span data-ttu-id="e6f23-151">按 **F5** 鍵執行方案。</span><span class="sxs-lookup"><span data-stu-id="e6f23-151">Run the solution by pressing the **F5** key.</span></span>  
  
6. <span data-ttu-id="e6f23-152">您應該會看到頁面，其中顯示安全性權杖服務所發出之權杖中的宣告。</span><span class="sxs-lookup"><span data-stu-id="e6f23-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
