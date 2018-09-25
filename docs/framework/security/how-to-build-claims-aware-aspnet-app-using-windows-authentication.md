---
title: 如何：使用 Windows 驗證建置宣告感知 ASP.NET 應用程式
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 2c7877c452c729b30029cad1a8e17600f3dc9661
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112422"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>如何：使用 Windows 驗證建置宣告感知 ASP.NET 應用程式
## <a name="applies-to"></a>適用於  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web Forms  
  
## <a name="summary"></a>總結  
 此操作說明提供詳細逐步程序，以建立使用 Windows 驗證的簡單宣告感知 ASP.NET Web Forms 應用程式。 還提供了一些指示，說明如何測試應用程式，以確認在使用者使用 Windows 驗證登入時會呈現宣告。  
  
## <a name="contents"></a>內容  
  
-   目標  
  
-   總覽  
  
-   步驟摘要  
  
-   步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
  
-   步驟 2 – 設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式  
  
-   步驟 3 – 測試方案  
  
## <a name="objectives"></a>目標  
  
-   設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式  
  
-   測試 ASP.NET Web Forms 應用程式以查看它是否正常運作  
  
## <a name="overview"></a>總覽  
 在 .NET 4.5 中，WIF 和其宣告型授權已包含為 Framework 的不可或缺部分。 以前，如果您想要來自 ASP.NET 使用者的宣告，需要安裝 WIF，然後將介面轉換為主體物件，例如 `Thread.CurrentPrincipal` 或 `HttpContext.Current.User`。 現在，這些主體物件會自動提供宣告。  
  
 Windows 驗證受益於 .NET 4.5 中包含 WIF，因為 Windows 認證所驗證的所有使用者都會自動具有與其建立關聯的宣告。 如這個使用方法所示範，您可以在使用 Windows 驗證的 ASP.NET 應用程式中立即開始使用這些宣告。  
  
## <a name="summary-of-steps"></a>步驟摘要  
  
-   步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
  
-   步驟 2 – 設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式  
  
-   步驟 3 – 測試方案  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式  
 在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio，然後依序按一下 [檔案]、[新增] 和 [專案]。  
  
2.  在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。  
  
3.  在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。  
  
4.  建立 **TestApp** 專案之後，在方案總管中按一下該專案。 專案的屬性會出現在方案總管下方的 [屬性] 窗格中。 將 **Windows 驗證**屬性設定為 [已啟用]。  
  
    > [!WARNING]
    >  在新的 ASP.NET 應用程式中，預設會停用 Windows 驗證，因此您必須以手動方式啟用它。  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>步驟 2 – 設定使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式  
 在此步驟中，您將組態項目新增至 *Web.config* 組態檔，並修改 *Default.aspx* 檔案來顯示帳戶的宣告資訊。  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>設定使用 Windows 驗證之宣告的 ASP.NET 應用程式  
  
1.  在 **TestApp** 專案的 *Default.aspx* 檔案中，將現有標記取代為下列標記：  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
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
  
     這個步驟會將 GridView 控制項新增至您的 *Default.aspx* 網頁，其中填入擷取自 Windows 驗證的宣告。  
  
2.  儲存 *Default.aspx* 檔案，然後開啟其名為 *Default.aspx.cs* 的程式碼後置檔案。 將現有的程式碼取代為下列程式碼：  
  
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
  
     上述程式碼會顯示有關已驗證使用者的宣告。  
  
3.  若要變更應用程式的驗證類型，請修改專案的根 *Web.config* 檔案中 **\<system.web>** 區段的 **\<authentication>** 區塊，使其只包含下列組態項目：  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  最後，修改相同 *Web.config* 檔案中 **\<system.web>** 區段的 **\<authorization>** 區塊，以強制執行驗證：  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>步驟 3 – 測試方案  
 在此步驟中，您將測試 ASP.NET Web Forms 應用程式，並確認在使用者使用 Windows 驗證登入時會呈現宣告。  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>測試使用 Windows 驗證之宣告的 ASP.NET Web Forms 應用程式  
  
1.  按 **F5** 鍵以建置並執行應用程式。 您應該會看到 *Default.aspx*，而且您的 Windows 帳戶名稱 (包括網域名稱) 應該已經在網頁的右上方顯示為已驗證的使用者。 頁面的內容應該包含一個資料表，其中填入了擷取自 Windows 帳戶的宣告。
