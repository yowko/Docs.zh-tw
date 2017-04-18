---
title: "如何：使用表單型驗證建置宣告感知的 ASP.NET 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# 如何：使用表單型驗證建置宣告感知的 ASP.NET 應用程式
## 適用於  
  
-   Microsoft® Windows®識別基礎 \(WIF\)  
  
-   ASP.NET® Web Form  
  
## 摘要  
 本 HOW TO 用於建立表單驗證的簡單明確要求的 ASP.NET Web Form 應用程式提供詳細的逐步程序。  它提供如何測試應用程式也提供指示驗證提出要求，當使用者登入使用表單驗證時。  
  
## 內容  
  
-   目標  
  
-   概觀  
  
-   步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-使用表單驗證， ASP.NET 設定為要求的 Web Form 應用程式  
  
-   步驟 3 \-測試方案。  
  
## 目標  
  
-   使用表單驗證，設定所要求的 ASP.NET Web Form 應用程式  
  
-   測試 ASP.NET Web Form 應用程式以查看是否正常運作。  
  
## 概觀  
 在 .NET Framework 4.5， WIF 和其以要求的授權納入為架構的整數部分。  在過去，，如果您想將 ASP.NET 使用者的需求，您必須先安裝 WIF，然後轉換 \(Cast\) 為介面主體物件 \(例如 `Thread.CurrentPrincipal` 或 `HttpContext.Current.User`。  現在，要求 \(這些物件會自動提供服務。  
  
 因為表單驗證的所有使用者都會自動使用要求關聯，表單驗證會因 .NET 4.5 中的 WIF 中。  您可以開始使用這些要求會立即在使用表單驗證的 ASP.NET 應用程式，因為如此一來， HOW TO 示範。  
  
## 步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
  
-   步驟 2 \-使用表單驗證， ASP.NET 設定為要求的 Web Form 應用程式  
  
-   步驟 3 \-測試方案。  
  
## 步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式  
 在這個步驟中，您將建立新的 ASP.NET Web Form 應用程式。  
  
#### 建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio 並按一下 **檔案**、 **新增**然後 **專案**。  
  
2.  在 **新增專案** 視窗，請按一下 **ASP.NET Web Form 應用程式**。  
  
3.  在 **名稱**，請輸入並按下 `TestApp`**確定**。  
  
## 步驟 2 \-使用表單驗證， ASP.NET 設定為要求的 Web Form 應用程式  
 在這個步驟會將組態項目加入至 *Web.config 組態檔* 和編輯 *Default.aspx* 檔案顯示帳戶的要求資訊。  
  
#### 使用表單驗證，設定所要求的 ASP.NET 應用程式  
  
1.  在 *Default.aspx 檔案中* ，以下列內容取代現有的標記:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
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
  
     這個步驟中加入 GridView 控制項中會填入從表單驗證擷取所需要的 *Default.aspx 網頁* 。  
  
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
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     上述程式碼會顯示已驗證使用者的需求，包含表單驗證識別的使用者。  
  
## 步驟 3 \-測試方案。  
 在這個步驟會測試 ASP.NET Web Form 應用程式，並確認提出要求，當使用者登入使用表單驗證。  
  
#### 使用表單驗證，測試您的變更要求的 ASP.NET Web Form 應用程式  
  
1.  按 **F5** 建置並執行應用程式。  您應該顯示 *Default.aspx，*有 **暫存器** 和 **登入** 連結在頁面右側的中。  按一下 \[**註冊**\]。  
  
2.  在 **暫存器** 網頁，請建立使用者帳戶，然後按一下 **暫存器**。  使用表單驗證，您的帳戶時，就會建立，而且您會自動登入。  
  
3.  在您將被重新導向至首頁之後，您應該會在 **簽發者** **OriginalIssuer**包括、、、和 **類型** **值** **實質型別** 要求有關您的帳戶的 **您的要求。** 標題下的資料表。