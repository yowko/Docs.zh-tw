---
title: "如何：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# 如何：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式
## 適用於  
  
-   Microsoft® Windows®識別基礎 \(WIF\)  
  
-   ASP.NET® MVC  
  
## 摘要  
 本 HOW TO 用於建立簡單的明確要求的 ASP.NET MVC Web 應用程式提供詳細的逐步程序。  它也說明如何測試以要求的驗證成功實作的簡單明確要求的 ASP.NET MVC Web 應用程式。  本 HOW TO 沒有建立的安全性權杖服務 \(STS\) 詳細說明，並假設您已設定 STS。  
  
## 內容  
  
-   目標  
  
-   步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET MVC 應用程式  
  
-   步驟 2 \-配置會根據要求的驗證的 ASP.NET MVC 應用程式  
  
-   步驟 3 \-測試方案。  
  
-   相關項目  
  
## 目標  
  
-   設定 ASP.NET MVC 架構要求驗證的 Web 應用程式  
  
-   測試成功的要求明確的 ASP.NET MVC Web 應用程式  
  
## 步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET MVC 應用程式  
  
-   步驟 2 \-配置會根據要求的驗證的 ASP.NET MVC 應用程式  
  
-   步驟 3 \-測試方案。  
  
## 步驟 1 \-建立簡單的 ASP.NET MVC 應用程式  
 在這個步驟中，您將建立新的 ASP.NET MVC 應用程式。  
  
#### 建立簡單的 ASP.NET MVC 應用程式  
  
1.  啟動 Visual Studio 並按一下 **檔案**、 **新增**然後 **專案**。  
  
2.  在 **新增專案** 視窗，請按一下 **ASP.NET MVC 3 Web 應用程式**。  
  
3.  在 **名稱**，請輸入並按下 `TestApp`**確定**。  
  
4.  在 \[**新的 ASP.NET MVC 3 專案**\] 對話方塊中，選取 \[**網際網路應用程式**\] 從可用的範本，以確保 \[**檢視引擎**\] 設為 \[**Razor**\]，然後按一下 \[**確定**\]。  
  
5.  在新專案中開啟時，請以滑鼠右鍵按一下 **方案總管** 的 \[**機碼**\] 專案並選取 \[**屬性**\] 選項。  
  
6.  在專案的 \[屬性\] 頁上，按一下索引標籤 \[**Web**\] 左邊並確定 \[**使用本機 IIS Web 伺服器**\] 選取選項。  
  
## 步驟 2 \-配置會根據要求的驗證的 ASP.NET MVC 應用程式  
 在這個步驟會將組態項目加入至 ASP.NET MVC Web 應用程式 *Web.config 組態檔* 可讓它需要明確。  
  
#### 設定為以要求驗證的 ASP.NET MVC 應用程式  
  
1.  將下列組態區段定義加入至 *Web.config 組態檔* 。  這些定義 Windows 識別基礎所需的組態區段。  將在 \[**\<configuration\>**\] 開頭項目之後的定義:  
  
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
  
4.  將下列 Windows 識別基礎相關的設定輸入並確認您的 ASP.NET 應用程式的 URL 和通訊埠編號是否符合在 **\<audienceUris\>** 輸入、 **\<wsFederation\>** 項目的 **領域** 屬性和 **\<wsFederation\>** 項目的 **復原** 屬性的值。  並請確定 \[**簽發者**\] 值調整您的安全性權杖服務 \(STS\) URL。  
  
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
  
5.  將物件加入至 [System.IdentityModel](assetId:///System.IdentityModel?qualifyHint=False&amp;autoUpgrade=True) 組件的參考。  
  
6.  編譯方案判斷發生錯誤。  
  
## 步驟 3 \-測試方案。  
 在這個步驟會測試 ASP.NET MVC Web 應用程式設定根據要求的驗證。  若要執行基本測試加入簡單的程式碼在安全性權杖服務發出的語彙基元 \(Token\) 的顯示要求 \(STS\)。  
  
#### 測試以要求驗證的 ASP.NET MVC 應用程式  
  
1.  在 **方案總管**，展開 **控制器** 資料夾和開啟 *HomeController.cs 檔* 隨即在編輯器中。  將下列程式碼加入至 \[**索引**\] 方法:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
  
    ```  
  
2.  在 **方案總管** 展開 \[**檢視**\] 然後 \[**首頁**\] 資料夾和開啟 *Index.cshtml* 檔案隨即在編輯器中。  刪除其內容並加入下列標記:  
  
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
  
3.  方案 **F5** 向上鍵來執行。  
  
4.  您應該會看到顯示中的要求語彙基元發行給您由安全性權杖服務的網頁。  
  
## 相關項目  
  
-   [如何：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)