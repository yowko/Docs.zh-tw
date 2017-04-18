---
title: "如何：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# 如何：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式
## 適用於  
  
-   Microsoft® Windows®識別基礎 \(WIF\)  
  
-   ASP.NET® Web Form  
  
## 摘要  
 本 HOW TO 用於建立簡單的明確要求的 ASP.NET Web Form 應用程式提供詳細的逐步程序。  它提供如何測試是否為 \(W3C\) 的驗證成功實作的簡單明確要求的 ASP.NET Web Form 應用程式也提供指示。  本 HOW TO 沒有建立的安全性權杖服務 \(STS\) 詳細說明，並假設您已設定 STS。  
  
## 內容  
  
-   目標  
  
-   步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-設定 ASP.NET 會根據要求的驗證的 Web Form 應用程式  
  
-   步驟 3 \-測試方案。  
  
## 目標  
  
-   設定 ASP.NET 會根據要求的驗證的 Web Form 應用程式  
  
-   測試成功的要求明確的 ASP.NET Web Form 應用程式  
  
## 步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-設定 ASP.NET 會向上驗證的 Web Form 應用程式  
  
-   步驟 3 \-測試方案。  
  
## 步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
 在這個步驟中，您將建立新的 ASP.NET Web Form 應用程式。  
  
#### 建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio 並按一下 **檔案**、 **新增**然後 **專案**。  
  
2.  在 **新增專案** 視窗，請按一下 **ASP.NET Web Form 應用程式**。  
  
3.  在 **名稱**，請輸入並按下 `TestApp`**確定**。  
  
## 步驟 2 \-設定 ASP.NET 會根據要求的驗證的 Web Form 應用程式  
 在這個步驟會將項目加入至您的 ASP.NET Web Form 應用程式 *Web.config 組態檔* 可讓它需要明確。  
  
#### 設定為以要求的驗證的 ASP.NET 應用程式  
  
1.  將下列組態區段項目加入開頭項目之後的 \[**\<configuration\>**\]*Web.config 組態檔* :  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  加入可對應用程式的 \(W3C\) 中繼資料的一個 **\<location\>** 項目:  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  將 **\<system.web\>** 項目內的下列設定輸入拒絕使用者，原生停用驗證，並且讓 WIF 管理驗證。  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  加入可定義 \(W3C\) 的驗證模組的一個 **\<system.webServer\>** 項目。  請注意 *PublicKeyToken* 屬性必須是 **\<configSections\>** 輸入的 *PublicKeyToken* 屬性先前所加入的相同:  
  
    ```  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  將下列 Windows 識別基礎相關的設定輸入並確認您的 ASP.NET 應用程式的 URL 和通訊埠編號是否符合在 **\<audienceUris\>** 輸入、 **\<wsFederation\>** 項目的 **領域** 屬性和 **\<wsFederation\>** 項目的 **復原** 屬性的值。  並請確定 \[**簽發者**\] 值調整您的安全性權杖服務 \(STS\) URL。  
  
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
  
6.  將物件加入至 [System.IdentityModel](assetId:///System.IdentityModel?qualifyHint=False&amp;autoUpgrade=True) 組件的參考。  
  
7.  編譯方案判斷發生錯誤。  
  
## 步驟 3 \-測試方案。  
 在這個步驟會測試 ASP.NET Web Form 應用程式設定為根據要求的驗證。  若要執行基本的測試，您將加入程式碼以安全性權杖服務發出的語彙基元 \(Token\) 的顯示要求 \(STS\)。  
  
#### 若要測試 ASP.NET Web 表單以要求的驗證的應用程式  
  
1.  開啟 **Default.aspx** 檔案在 **機碼** 專案下的以下列標記取代現有的標記:  
  
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
  
2.  **Default.aspx**，儲存在名為的檔案。 **Default.aspx.cs**後再開啟它的程式碼。  
  
    > [!NOTE]
    >  **Default.aspx.cs** 可能在方案總管中的 **Default.aspx** 下隱藏。  如果 **Default.aspx.cs** 看不到，請按一下 **Default.aspx** 在三角形旁邊。  
  
3.  使用下列程式碼取代 **Default.aspx.cs** **Page\_Load** 方法中的現有程式碼:  
  
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
  
4.  儲存 **Default.aspx.cs**，並建置方案。  
  
5.  方案 **F5** 向上鍵來執行。  
  
6.  您應該會看到顯示中的要求語彙基元發行給您由安全性權杖服務的網頁。