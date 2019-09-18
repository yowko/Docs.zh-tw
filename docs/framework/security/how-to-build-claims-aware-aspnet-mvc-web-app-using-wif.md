---
title: 如何：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045440"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="01964-102">如何：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="01964-103">適用於</span><span class="sxs-lookup"><span data-stu-id="01964-103">Applies To</span></span>  
  
- <span data-ttu-id="01964-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="01964-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="01964-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="01964-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="01964-106">總結</span><span class="sxs-lookup"><span data-stu-id="01964-106">Summary</span></span>  
 <span data-ttu-id="01964-107">此操作說明提供詳細逐步程序，以建立簡單宣告感知 ASP.NET MVC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01964-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="01964-108">還提供了一些指示，說明如何測試簡單宣告感知 ASP.NET MVC Web 應用程式成功實作宣告型驗證。</span><span class="sxs-lookup"><span data-stu-id="01964-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="01964-109">此操作說明沒有提供建立安全性權杖服務 (STS) 的詳細指示，並假設您已設定 STS。</span><span class="sxs-lookup"><span data-stu-id="01964-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="01964-110">內容</span><span class="sxs-lookup"><span data-stu-id="01964-110">Contents</span></span>  
  
- <span data-ttu-id="01964-111">目標</span><span class="sxs-lookup"><span data-stu-id="01964-111">Objectives</span></span>  
  
- <span data-ttu-id="01964-112">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="01964-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="01964-113">步驟 1 – 建立簡單的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="01964-114">步驟 2 – 設定宣告型驗證的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="01964-115">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="01964-115">Step 3 – Test Your Solution</span></span>  
  
- <span data-ttu-id="01964-116">相關項目:</span><span class="sxs-lookup"><span data-stu-id="01964-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="01964-117">目標</span><span class="sxs-lookup"><span data-stu-id="01964-117">Objectives</span></span>  
  
- <span data-ttu-id="01964-118">設定宣告型驗證的 ASP.NET MVC Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
- <span data-ttu-id="01964-119">測試成功宣告感知 ASP.NET MVC Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="01964-120">步驟摘要</span><span class="sxs-lookup"><span data-stu-id="01964-120">Summary of Steps</span></span>  
  
- <span data-ttu-id="01964-121">步驟 1 – 建立簡單的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="01964-122">步驟 2 – 設定宣告型驗證的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="01964-123">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="01964-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="01964-124">步驟 1 – 建立簡單的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="01964-125">在此步驟中，您將建立新的 ASP.NET MVC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01964-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="01964-126">建立簡單的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-126">To create simple ASP.NET MVC application</span></span>  
  
1. <span data-ttu-id="01964-127">啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。</span><span class="sxs-lookup"><span data-stu-id="01964-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="01964-128">在 [新增專案] 視窗中，按一下 [ASP.NET MVC 3 Web 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="01964-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3. <span data-ttu-id="01964-129">在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="01964-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="01964-130">在 [新增 ASP.NET MVC 3 專案] 對話方塊中，從可用的範本中選取 [網際網路應用程式]，確定 [檢視引擎] 設定為 [Razor]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="01964-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="01964-131">當新的專案開啟時，以滑鼠右鍵按一下方案總管中的 **TestApp** 專案，然後選取 [屬性] 選項。</span><span class="sxs-lookup"><span data-stu-id="01964-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6. <span data-ttu-id="01964-132">在專案的屬性頁面上，按一下左側的 [Web] 索引標籤，並確定已選取 [使用本機 IIS Web 伺服器] 選項。</span><span class="sxs-lookup"><span data-stu-id="01964-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="01964-133">步驟 2 – 設定宣告型驗證的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="01964-134">在此步驟中，您將組態項目新增至 ASP.NET MVC Web 應用程式的 *Web.config* 組態檔，使其成為宣告感知。</span><span class="sxs-lookup"><span data-stu-id="01964-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="01964-135">設定宣告型驗證的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="01964-136">將下列組態區段定義新增至 *Web.config* 組態檔。</span><span class="sxs-lookup"><span data-stu-id="01964-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="01964-137">它們會定義 Windows Identity Foundation 所需的組態區段。</span><span class="sxs-lookup"><span data-stu-id="01964-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="01964-138">緊接在 **\<configuration>** 開啟項目之後新增定義：</span><span class="sxs-lookup"><span data-stu-id="01964-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="01964-139">新增 **\<location>** 項目，以允許存取應用程式的同盟中繼資料：</span><span class="sxs-lookup"><span data-stu-id="01964-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="01964-140">在 **\<system.web>** 項目內新增下列組態項目，以拒絕使用者、停用原始驗證，以及啟用 WIF 來管理驗證。</span><span class="sxs-lookup"><span data-stu-id="01964-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="01964-141">新增下列 Windows Identity Foundation 相關組態項目，並確認 ASP.NET 應用程式的 URL 和連接埠編號符合 **\<audienceUris>** 項目、 **\<wsFederation>** 項目的 **realm** 屬性和 **\<wsFederation>** 項目的 **reply** 屬性。</span><span class="sxs-lookup"><span data-stu-id="01964-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="01964-142">也請確認 **issuer** 值符合安全性權杖服務 (STS) 的 URL。</span><span class="sxs-lookup"><span data-stu-id="01964-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. <span data-ttu-id="01964-143">新增 <xref:System.IdentityModel> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="01964-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6. <span data-ttu-id="01964-144">編譯方案，以確定含有錯誤。</span><span class="sxs-lookup"><span data-stu-id="01964-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="01964-145">步驟 3 – 測試方案</span><span class="sxs-lookup"><span data-stu-id="01964-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="01964-146">在此步驟中，您將測試針對宣告型驗證設定的 ASP.NET MVC Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01964-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="01964-147">為了執行基本測試，您將新增簡單的程式碼以顯示安全性權杖服務 (STS) 所發行之權杖中的宣告。</span><span class="sxs-lookup"><span data-stu-id="01964-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="01964-148">測試宣告型驗證的 ASP.NET MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="01964-149">在方案總管 中，展開 [控制器] 資料夾，然後在編輯器中開啟 *HomeController.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="01964-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="01964-150">將下列程式碼新增至 **Index** 方法：</span><span class="sxs-lookup"><span data-stu-id="01964-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. <span data-ttu-id="01964-151">在方案總管中，依序展開 [檢視] 和 [首頁] 資料夾，然後在編輯器中開啟 *Index.cshtml*檔案。</span><span class="sxs-lookup"><span data-stu-id="01964-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="01964-152">刪除其內容，並新增下列標記：</span><span class="sxs-lookup"><span data-stu-id="01964-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. <span data-ttu-id="01964-153">按 **F5** 鍵執行方案。</span><span class="sxs-lookup"><span data-stu-id="01964-153">Run the solution by pressing the **F5** key.</span></span>  
  
4. <span data-ttu-id="01964-154">您應該會看到頁面，其中顯示安全性權杖服務所發出之權杖中的宣告。</span><span class="sxs-lookup"><span data-stu-id="01964-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="01964-155">相關項目:</span><span class="sxs-lookup"><span data-stu-id="01964-155">Related Items</span></span>  
  
- [<span data-ttu-id="01964-156">如何：使用 WIF 建立宣告感知 ASP.NET Web Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="01964-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
