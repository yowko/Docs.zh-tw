---
title: 如何：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4a003acbf4e182a0493368b586a3add229d8b526
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087667"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>如何：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式
## <a name="applies-to"></a>適用於  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® MVC  
  
## <a name="summary"></a>總結  
 此操作說明提供詳細逐步程序，以建立簡單宣告感知 ASP.NET MVC 應用程式。 還提供了一些指示，說明如何測試簡單宣告感知 ASP.NET MVC Web 應用程式成功實作宣告型驗證。 此操作說明沒有提供建立安全性權杖服務 (STS) 的詳細指示，並假設您已設定 STS。  
  
## <a name="contents"></a>內容  
  
-   目標  
  
-   步驟摘要  
  
-   步驟 1 – 建立簡單的 ASP.NET MVC 應用程式  
  
-   步驟 2 – 設定宣告型驗證的 ASP.NET MVC 應用程式  
  
-   步驟 3 – 測試方案  
  
-   相關項目  
  
## <a name="objectives"></a>目標  
  
-   設定宣告型驗證的 ASP.NET MVC Web 應用程式  
  
-   測試成功宣告感知 ASP.NET MVC Web 應用程式  
  
## <a name="summary-of-steps"></a>步驟摘要  
  
-   步驟 1 – 建立簡單的 ASP.NET MVC 應用程式  
  
-   步驟 2 – 設定宣告型驗證的 ASP.NET MVC 應用程式  
  
-   步驟 3 – 測試方案  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>步驟 1 – 建立簡單的 ASP.NET MVC 應用程式  
 在此步驟中，您將建立新的 ASP.NET MVC 應用程式。  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>建立簡單的 ASP.NET MVC 應用程式  
  
1.  啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。  
  
2.  在 [新增專案] 視窗中，按一下 [ASP.NET MVC 3 Web 應用程式]。  
  
3.  在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。  
  
4.  在 [新增 ASP.NET MVC 3 專案] 對話方塊中，從可用的範本中選取 [網際網路應用程式]，確定 [檢視引擎] 設定為 [Razor]，然後按一下 [確定]。  
  
5.  當新的專案開啟時，以滑鼠右鍵按一下方案總管中的 **TestApp** 專案，然後選取 [屬性] 選項。  
  
6.  在專案的屬性頁面上，按一下左側的 [Web] 索引標籤，並確定已選取 [使用本機 IIS Web 伺服器] 選項。  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>步驟 2 – 設定宣告型驗證的 ASP.NET MVC 應用程式  
 在此步驟中，您將組態項目新增至 ASP.NET MVC Web 應用程式的 *Web.config* 組態檔，使其成為宣告感知。  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>設定宣告型驗證的 ASP.NET MVC 應用程式  
  
1.  將下列組態區段定義新增至 *Web.config* 組態檔。 它們會定義 Windows Identity Foundation 所需的組態區段。 緊接在 **\<configuration>** 開啟項目之後新增定義：  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  新增 **\<location>** 項目，以允許存取應用程式的同盟中繼資料：  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  在 **\<system.web>** 項目內新增下列組態項目，以拒絕使用者、停用原始驗證，以及啟用 WIF 來管理驗證。  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  新增下列 Windows Identity Foundation 相關組態項目，並確認 ASP.NET 應用程式的 URL 和連接埠編號符合 **\<audienceUris>** 項目、**\<wsFederation>** 項目的 **realm** 屬性和 **\<wsFederation>** 項目的 **reply** 屬性。 也請確認 **issuer** 值符合安全性權杖服務 (STS) 的 URL。  
  
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
  
5.  新增 <xref:System.IdentityModel> 組件的參考。  
  
6.  編譯方案，以確定含有錯誤。  
  
## <a name="step-3--test-your-solution"></a>步驟 3 – 測試方案  
 在此步驟中，您將測試針對宣告型驗證設定的 ASP.NET MVC Web 應用程式。 為了執行基本測試，您將新增簡單的程式碼以顯示安全性權杖服務 (STS) 所發行之權杖中的宣告。  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>測試宣告型驗證的 ASP.NET MVC 應用程式  
  
1.  在方案總管 中，展開 [控制器] 資料夾，然後在編輯器中開啟 *HomeController.cs* 檔案。 將下列程式碼新增至 **Index** 方法：  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  在方案總管中，依序展開 [檢視] 和 [首頁] 資料夾，然後在編輯器中開啟 *Index.cshtml*檔案。 刪除其內容，並新增下列標記：  
  
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
  
3.  按 **F5** 鍵執行方案。  
  
4.  您應該會看到頁面，其中顯示安全性權杖服務所發出之權杖中的宣告。  
  
## <a name="related-items"></a>相關項目  
  
-   [操作說明：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
