---
title: "如何：轉換傳入宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# 如何：轉換傳入宣告
## 適用於  
  
-   Microsoft® Windows®識別基礎 \(WIF\)  
  
-   ASP.NET® Web Form  
  
## 摘要  
 本 HOW TO 來建立簡單的需求明確的 ASP.NET Web Form 應用程式和轉換連入要求提供詳細的逐步程序。  它提供如何測試應用程式也提供指示驗證提議已轉換的需求，在應用程式執行時。  
  
## 內容  
  
-   目標  
  
-   概觀  
  
-   步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-使用自訂 ClaimsAuthenticationManager，實作需要轉換  
  
-   步驟 3 \-測試方案。  
  
## 目標  
  
-   設定為以要求驗證的 ASP.NET Web Form 應用程式  
  
-   藉由將 Administrators 角色轉換連入要求  
  
-   測試 ASP.NET Web Form 應用程式以查看是否正常運作。  
  
## 概觀  
 WIF 公開可讓使用者修改需要名為的 <xref:System.Security.Claims.ClaimsAuthenticationManager> 的類別，然後才會呈現至相依的一方 \(RP\) 應用程式。  <xref:System.Security.Claims.ClaimsAuthenticationManager> 為重點分開適用於驗證與基礎應用程式程式碼之間的差異。  下列範例示範如何將角色加入至需求可能由 RP 需要傳入的 <xref:System.Security.Claims.ClaimsPrincipal> 。  
  
## 步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-使用自訂 ClaimsAuthenticationManager，實作需要轉換  
  
-   步驟 3 \-測試方案。  
  
## 步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
 在這個步驟中，您將建立新的 ASP.NET Web Form 應用程式。  
  
#### 建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio 以更高階的權限模式為系統管理員。  
  
2.  在 Visual Studio 中，按一下 **檔案**，按一下 **新增**，然後按一下 **專案**。  
  
3.  在 **新增專案** 視窗，請按一下 **ASP.NET Web Form 應用程式**。  
  
4.  在 **名稱**，請輸入並按下 `TestApp`**確定**。  
  
5.  以滑鼠右鍵按一下 **機碼** 專案在 **方案總管**下的，然後選取 **識別和存取**。  
  
6.  **識別和存取** 視窗隨即出現。  在 **提供者**下，選取的 **測試您的變更與本機開發 STS 的應用程式**，然後按一下 **套用**。  
  
7.  在 *Default.aspx 檔案中* ，以下列內容取代現有的標記，然後儲存檔案:  
  
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
  
8.  開啟名為的 *Default.aspx.cs。*程式碼後置檔案  以下列內容取代現有的程式碼，然後儲存檔案:  
  
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
  
## 步驟 2 \-使用自訂 ClaimsAuthenticationManager，實作需要轉換  
 在這個步驟會覆寫 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別的預設功能將 Administrators 角色至傳入的主體。  
  
#### 使用自訂 ClaimsAuthenticationManager，實作需要轉換  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下方案，然後按一下 **新增**，然後按一下 **新增專案**。  
  
2.  在 **新增專案** 視窗，請從 **Visual C\#** 範本的 SELECT **類別庫** 清單中，輸入，然後按 `ClaimsTransformation`**確定**。  新的專案在您的方案資料夾中建立。  
  
3.  以滑鼠右鍵按一下 **參考** 在 **ClaimsTransformation** 專案底下，然後按一下 **新增參考**。  
  
4.  在 **參考管理員** 視窗中，選取的 **System.IdentityModel**，然後按一下 **確定**。  
  
5.  開啟 **Class1.cs**，或者，如果不存在，請以滑鼠右鍵按一下 **ClaimsTransformation**，按一下 \[**新增**\]，然後按一下 **分類…**  
  
6.  將下列 using 指示詞加入至程式碼檔:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  加入下列類別和方法在程式碼檔。  
  
    > [!WARNING]
    >  下列程式碼僅供示範使用;務必確認您所需的使用權限在實際執行程式碼。  
  
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
  
8.  儲存檔案並建立 **ClaimsTransformation** 專案。  
  
9. 在您的 **機碼** ASP.NET 專案中，以滑鼠右鍵按一下參考，然後按一下 **新增參考**。  
  
10. 在 **參考管理員** 視窗中，從左功能表上選取 **方案** ，從填入選取的 SELECT **ClaimsTransformation** ，然後按一下 **確定**。  
  
11. 在根 **Web.config** 檔案，巡覽至 **\<system.identityModel\>** 輸入。  在 **\<identityConfiguration\>** 項目內，加入下列程式碼行並儲存檔案:  
  
    ```  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## 步驟 3 \-測試方案。  
 在這個步驟會測試 ASP.NET Web Form 應用程式，並確認提出要求，當使用者登入使用表單驗證。  
  
#### 使用表單驗證，測試您的變更要求的 ASP.NET Web Form 應用程式  
  
1.  按 **F5** 建置並執行應用程式。  您應該顯示 *Default.aspx。*  
  
2.  在 *Default.aspx* 網頁中，您會看到包含 **簽發者**、 **OriginalIssuer**、 **類型**、 **值**和 **實質型別** 要求有關您的帳戶的 **您的要求** 標題下的資料表。  應以下列方式來顯示最後一個資料列:  
  
    ||||||  
    |-|-|-|-|-|  
    |位置政府|位置政府|http:\/\/schemas.microsoft.com\/ws\/2008\/06\/identity\/claims\/role|Admin|http:\/\/www.w3.org\/2001\/XMLSchema\#string|