---
title: "如何：使用 Windows 驗證建置宣告感知 ASP.NET 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# 如何：使用 Windows 驗證建置宣告感知 ASP.NET 應用程式
## 適用於  
  
-   Microsoft® Windows®識別基礎 \(WIF\)  
  
-   ASP.NET® Web Form  
  
## 摘要  
 本 HOW TO 用於建立 Windows 驗證的簡單明確要求的 ASP.NET Web Form 應用程式提供詳細的逐步程序。  它提供如何測試應用程式也提供指示驗證會需要使用 Windows 驗證時，在中，當使用者登入。  
  
## 內容  
  
-   目標  
  
-   概觀  
  
-   步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-使用 Windows 驗證， ASP.NET 設定為要求的 Web Form 應用程式  
  
-   步驟 3 \-測試方案。  
  
## 目標  
  
-   使用 Windows 驗證，設定所要求的 ASP.NET Web Form 應用程式  
  
-   測試 ASP.NET Web Form 應用程式以查看是否正常運作。  
  
## 概觀  
 在 .NET Framework 4.5， WIF 和其以要求的授權納入為架構的整數部分。  在過去，，如果您想將 ASP.NET 使用者的需求，您必須先安裝 WIF，然後轉換 \(Cast\) 為介面主體物件 \(例如 `Thread.CurrentPrincipal` 或 `HttpContext.Current.User`。  現在，要求 \(這些物件會自動提供服務。  
  
 因為 Windows 驗證的所有使用者都會自動使用要求關聯， Windows 驗證受益於 .NET 4.5 中的 WIF 中。  您可以開始使用這些要求會立即在使用 Windows 驗證的 ASP.NET 應用程式，因為如此一來， HOW TO 示範。  
  
## 步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-使用 Windows 驗證， ASP.NET 設定為要求的 Web Form 應用程式  
  
-   步驟 3 \-測試方案。  
  
## 步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
 在這個步驟中，您將建立新的 ASP.NET Web Form 應用程式。  
  
#### 建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio，然後按一下 **檔案**、 **新增**然後 **專案**。  
  
2.  在 **新增專案** 視窗，請按一下 **ASP.NET Web Form 應用程式**。  
  
3.  在 **名稱**，請輸入並按下 `TestApp`**確定**。  
  
4.  在 **機碼** 建立專案之後，請按一下 **方案總管**。  專案的屬性會出現在 **屬性** 窗格在 **方案總管**之下。  設定 **Windows 驗證** 屬性設定為 **已啟用**。  
  
    > [!WARNING]
    >  預設 Windows 驗證在新的 ASP.NET 應用程式停用，因此，您必須以手動方式加以啟用。  
  
## 步驟 2 \-使用 Windows 驗證， ASP.NET 設定為要求的 Web Form 應用程式  
 在這個步驟會將組態項目加入 *Web.config 組態檔* 並修改 *Default.aspx* 檔案顯示帳戶的要求資訊。  
  
#### 使用 Windows 驗證，設定所要求的 ASP.NET 應用程式  
  
1.  在 **機碼** 項目的 *Default.aspx* 檔案中，以下列內容取代現有的標記:  
  
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
  
     這個步驟中加入 GridView 控制項中會填入從 Windows 驗證擷取所需要的 *Default.aspx 網頁* 。  
  
2.  儲存 *Default.aspx* 檔案，然後開啟檔案的程式碼後置檔案命名為 *Default.aspx.cs*。  以下列內容取代現有的程式碼:  
  
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
  
     上述程式碼會顯示已驗證使用者的需求。  
  
3.  若要變更應用程式的驗證類型，請修改專案中的根 *Web.config 檔中的* **\<system.web\>** 部分的 **\<authentication\>** 區塊，使其僅包含下列設定輸入:  
  
    ```  
    <authentication mode="Windows" />  
    ```  
  
4.  最後，請修改相同 *Web.config 檔案的* 區段中 **\<system.web\>** **\<authorization\>** 區塊強制驗證:  
  
    ```  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## 步驟 3 \-測試方案。  
 在這個步驟會測試 ASP.NET Web Form 應用程式，並確認提出要求，當使用者登入使用 Windows 驗證。  
  
#### 使用 Windows 驗證，測試您的變更要求的 ASP.NET Web Form 應用程式  
  
1.  按 **F5** 建置並執行應用程式。  您應該顯示 *Default.aspx，然後，*您的 Windows 帳戶名稱 \(包括網域名稱\) 應該已經顯示為頁面右側的中的已驗證使用者。  網頁的內容應該包含資料表填入從您的 Windows 帳戶擷取的要求。