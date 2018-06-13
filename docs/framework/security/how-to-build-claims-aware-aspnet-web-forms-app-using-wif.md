---
title: 如何：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e8dc6b1c5073ac55be224eb0d410ad7f87d135d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400090"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>如何：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式
## <a name="applies-to"></a>適用於  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web Forms  
  
## <a name="summary"></a>總結  
 此操作說明提供詳細逐步程序，以建立簡單宣告感知 ASP.NET Web Forms 應用程式。 還提供了一些指示，說明如何測試簡單宣告感知 ASP.NET Web Forms 應用程式成功實作同盟驗證。 此操作說明沒有提供建立安全性權杖服務 (STS) 的詳細指示，並假設您已設定 STS。  
  
## <a name="contents"></a>內容  
  
-   目標  
  
-   步驟摘要  
  
-   步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
  
-   步驟 2 – 設定宣告型驗證的 ASP.NET Web Forms 應用程式  
  
-   步驟 3 – 測試方案  
  
## <a name="objectives"></a>目標  
  
-   設定宣告型驗證的 ASP.NET Web Forms 應用程式  
  
-   測試成功宣告感知 ASP.NET Web Forms 應用程式  
  
## <a name="summary-of-steps"></a>步驟摘要  
  
-   步驟 1 – 建立簡單的 ASP.NET Web Forms 應用程式  
  
-   步驟 2 – 設定同盟驗證的 ASP.NET Web Forms 應用程式  
  
-   步驟 3 – 測試方案  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
 在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。  
  
2.  在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。  
  
3.  在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>步驟 2 – 設定宣告型驗證的 ASP.NET Web Forms 應用程式  
 在此步驟中，您將組態項目新增至 ASP.NET Web Forms 應用程式的 *Web.config* 組態檔，使其成為宣告感知。  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>設定宣告型驗證的 ASP.NET 應用程式  
  
1.  緊接在 **\<configuration>** 開啟項目後，將下列組態區段項目新增至 *Web.config* 組態檔：  
  
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
  
4.  新增 **\<system.webServer>** 項目，以定義同盟驗證的模組。 請注意，*PublicKeyToken* 屬性必須與先前新增之 **\<configSections>** 項目的 *PublicKeyToken* 屬性相同：  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  新增下列 Windows Identity Foundation 相關組態項目，並確認 ASP.NET 應用程式的 URL 和連接埠編號符合 **\<audienceUris>** 項目、**\<wsFederation>** 項目的 **realm** 屬性和 **\<wsFederation>** 項目的 **reply** 屬性。 也請確認 **issuer** 值符合安全性權杖服務 (STS) 的 URL。  
  
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
  
6.  新增 <xref:System.IdentityModel> 組件的參考。  
  
7.  編譯方案，以確定沒有任何錯誤。  
  
## <a name="step-3--test-your-solution"></a>步驟 3 – 測試方案  
 在此步驟中，您將測試針對宣告型驗證設定的 ASP.NET Web Forms 應用程式。 為了執行基本測試，您將新增程式碼以顯示安全性權杖服務 (STS) 所發行之權杖中的宣告。  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>測試宣告型驗證的 ASP.NET Web Forms 應用程式  
  
1.  開啟 **TestApp** 專案下的 **Default.aspx** 檔案，並將其現有標記取代為下列標記：  
  
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
  
2.  儲存 **Default.aspx**，然後開啟其名為 **Default.aspx.cs** 的程式碼後置檔案。  
  
    > [!NOTE]
    >  在方案總管中，**Default.aspx.cs** 可能隱藏在 **Default.aspx** 的下方。 如果看不到 **Default.aspx.cs**，請按一下 **Default.aspx** 旁邊的三角形來展開它。  
  
3.  將 **Default.aspx.cs** 之 **Page_Load** 方法中的現有程式碼，取代為下列程式碼：  
  
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
  
4.  儲存 **Default.aspx.cs**，然後建置方案。  
  
5.  按 **F5** 鍵執行方案。  
  
6.  您應該會看到頁面，其中顯示安全性權杖服務所發出之權杖中的宣告。
