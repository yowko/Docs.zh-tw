---
title: 如何：轉換傳入宣告
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: f836356125f1462f302b7e9f45a841c869c9a690
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344633"
---
# <a name="how-to-transform-incoming-claims"></a>如何：轉換傳入宣告
## <a name="applies-to"></a>適用於  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web Forms  
  
## <a name="summary"></a>總結  
 此操作說明提供詳細逐步程序，以建立簡單宣告感知 ASP.NET Web Forms 應用程式和轉換傳入宣告。 此外，還提供一些指示，說明如何測試應用程式，以確認應用程式執行時會呈現宣告。  
  
## <a name="contents"></a>內容  
  
-   目標  
  
-   總覽  
  
-   步驟摘要  
  
-   步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
  
-   步驟 2 – 使用自訂的 ClaimsAuthenticationManager 實作宣告轉換  
  
-   步驟 3 – 測試方案  
  
## <a name="objectives"></a>目標  
  
-   設定宣告型驗證的 ASP.NET Web Forms 應用程式  
  
-   藉由新增系統管理員角色宣告來轉換傳入宣告  
  
-   測試 ASP.NET Web Forms 應用程式以查看它是否正常運作  
  
## <a name="overview"></a>總覽  
 WIF 會公開一個名為 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別，其可讓使用者在向信賴憑證者 (RP) 應用程式呈現宣告之前，修改這些宣告。 <xref:System.Security.Claims.ClaimsAuthenticationManager> 可用來分隔驗證與基礎應用程式程式碼之間的問題。 下列範例示範如何在 RP 可能需要的傳入 <xref:System.Security.Claims.ClaimsPrincipal> 宣告中加入角色。  
  
## <a name="summary-of-steps"></a>步驟摘要  
  
-   步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
  
-   步驟 2 – 使用自訂的 ClaimsAuthenticationManager 實作宣告轉換  
  
-   步驟 3 – 測試方案  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
 在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>建立簡單的 ASP.NET 應用程式  
  
1. 以系統管理員身分的高階權限模式來啟動 Visual Studio。  
  
2. 在 Visual Studio 中，依序按一下 [檔案]、[新增] 和 [專案]。  
  
3. 在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。  
  
4. 在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。  
  
5. 以滑鼠右鍵按一下方案總管底下的 [TestApp] 專案，然後選取 [身分識別與存取]。  
  
6. [身分識別與存取] 視窗隨即出現。 在 [提供者] 底下，選取 [Test your application with the Local Development STS] (使用本機開發 STS 測試應用程式}，然後按一下 [套用]。  
  
7. 在 *Default.aspx* 檔案中，將現有標記取代為下列標記，然後儲存檔案：  
  
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
  
8. 開啟名為 *Default.aspx.cs* 的程式碼後置檔案。 將現有程式碼取代為下列程式碼，然後儲存檔案：  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>步驟 2 – 使用自訂的 ClaimsAuthenticationManager 實作宣告轉換  
 在此步驟中，您將覆寫 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別中的預設功能，以便將系統管理員角色新增到傳入主體。  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>使用自訂的 ClaimsAuthenticationManager 實作宣告轉換  
  
1. 在 Visual Studio 中，以滑鼠右鍵按一下方案，然後依序按一下 [新增] 和 [新增專案]。  
  
2. 在 [新增專案] 視窗中，選取 [Visual C#] 範本清單中的 [類別庫]，輸入 `ClaimsTransformation`，然後按 [確定]。 您的方案資料夾中就會建立新的專案。  
  
3. 以滑鼠右鍵按一下 [ClaimsTransformation] 專案底下的 [參考]，然後按一下 [新增參考]。  
  
4. 在 [參考管理員] 視窗中，選取 **System.IdentityModel**，然後按一下 [確定]。  
  
5. 開啟 **Class1.cs**，如果沒有該檔案，請以滑鼠右鍵按一下 [ClaimsTransformation]，然後依序按一下 [新增] 和 [類別...]  
  
6. 將下列 using 指示詞新增程式碼檔案：  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7. 在程式碼檔案中新增下列類別和方法。  
  
    > [!WARNING]
    >  下列程式碼僅供示範之用；請務必在生產環境程式碼中驗證預期權限。  
  
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
  
8. 儲存檔案，並建置 **ClaimsTransformation** 專案。  
  
9. 在 [TestApp] ASP.NET 專案中，以滑鼠右鍵按一下參考，然後按一下 [新增參考]。  
  
10. 在 [參考管理員] 視窗中，選取左側功能表中的 [方案]，從填入的選項中選取 [ClaimsTransformation]，然後按一下 [確定]。  
  
11. 在根 **Web.config** 檔案中，巡覽至 **\<system.identityModel>** 項目。 在 **\<identityConfiguration>** 項目內，新增下列一行並儲存檔案：  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>步驟 3 – 測試方案  
 在此步驟中，您將測試 ASP.NET Web Forms 應用程式，並確認使用者使用表單驗證登入時呈現宣告。  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>測試使用表單驗證之宣告的 ASP.NET Web Forms 應用程式  
  
1. 按 **F5** 鍵建置並執行應用程式。 您應該會看到 *Default.aspx*。  
  
2. 在 *Default.aspx* 頁面上，您應該會看到 [Your Claims] (您的宣告) 標題下方有一個資料表，其中包含有關您帳戶的 **Issuer**、**OriginalIssuer**、**Type**、**Value** 和 **ValueType** 宣告資訊。 應該會以下列方式呈現最後一個資料列：  
  
    ||||||  
    |-|-|-|-|-|  
    |LOCAL AUTHORITY|LOCAL AUTHORITY|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|系統管理員|<https://www.w3.org/2001/XMLSchema#string>|
