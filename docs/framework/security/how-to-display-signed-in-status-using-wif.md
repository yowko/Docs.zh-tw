---
title: "如何：使用 WIF 顯示登入的狀態 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# 如何：使用 WIF 顯示登入的狀態
## 適用於  
  
-   Microsoft® Windows® Windows Identity Foundation \(WIF\) 4.5  
  
-   ASP.NET® Web Form  
  
## 摘要  
 本主題說明如何在狀態的標記在 WIF 可讓 ASP.NET 應用程式。  WIF 提供讓您的應用程式提供這個機制宣告明確和管理驗證和授權應用程式資源的。  
  
## 內容  
  
-   概觀  
  
-   步驟摘要  
  
-   步驟 1 \- 安裝識別和存取擴充功能  
  
-   步驟 2 \- 建立信賴憑證者 ASP.NET 應用程式  
  
-   步驟 3 \- 讓本機開發 STS 驗證使用者  
  
-   步驟 4 \- 修改您的 ASP.NET 應用程式會顯示登入狀態  
  
-   步驟 5 \- 測試在 WIF 且 ASP.NET 應用程式間的整合  
  
## 概觀  
 本主題示範如何建立簡單的宣告感知應用程式使用 WIF 和如何輕鬆地顯示使用者是否已簽署。  下列步驟會使用包含識別和存取 Visual Studio 擴充功能的本機開發 STS。  本機開發 STS 供測試和開發環境使用提供整合宣告簡單方法加入您的應用程式。  不應該在實際執行環境，，因為它不會執行實際的驗證，而且不需要驗證。  不過，使用真正的驗證，如下列步驟所需的程式碼是同一個專案產生的應用程式。  
  
## 步驟摘要  
  
-   步驟 1 \- 安裝識別和存取擴充功能  
  
-   步驟 2 \- 建立信賴憑證者 ASP.NET 應用程式  
  
-   步驟 3 \- 讓本機開發 STS 驗證使用者  
  
-   步驟 4 \- 修改您的 ASP.NET 應用程式會顯示登入狀態  
  
-   步驟 5 \- 測試在 WIF 且 ASP.NET 應用程式間的整合  
  
## 步驟 1 \- 安裝識別和存取擴充功能  
 這個步驟說明如何設定識別和存取擴充到 Visual Studio 2012。  此擴充功能自動化會設定您的應用程式處理序與 STS 端點進行通訊。  
  
#### 安裝識別和存取擴充  
  
1.  啟動 Visual Studio 以更高階的權限模式為系統管理員。  
  
2.  在 Visual Studio 中，按一下 **工具** 並按一下 **增益集管理員**。  **增益集管理員** 視窗隨即出現。  
  
3.  在 **增益集管理員**中，從左功能表按一下 **線上擴充功能** \]，然後選取 **Visual Studio 繪製廊**。  
  
4.  在 **增益集管理員**的右上角，請搜尋 *識別和存取*。  
  
5.  **識別和存取** 項目會顯示在搜尋結果。  按一下它，然後按一下 **下載**。  
  
6.  **下載和安裝。** 對話方塊隨即出現。  如果您同意授權條款，請按一下 **安裝**。  
  
7.  當 **識別和存取** 擴充功能已安裝時，請重新啟動 Visual Studio 以系統管理員模式。  
  
## 步驟 2 \- 建立信賴憑證者 ASP.NET 應用程式  
 這個步驟說明如何建立將整合 WIF 的信賴憑證者 ASP.NET Web Form 應用程式。  
  
#### 建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio 並按一下 **檔案**、 **新增**和 **專案**。  
  
2.  在 **新的專案** 視窗中，按一下 **ASP.NET Web Form 應用程式**。  
  
3.  在 **名稱**中，輸入 `TestApp` 並按 **好**。  
  
## 步驟 3 \- 讓本機開發 STS 驗證使用者  
 這個步驟說明如何啟用應用程式的本機開發 STS。  使用 Visual Studio 中，識別和存取擴充本機開發 STS 啟用。  
  
#### 在您的 ASP.NET 應用程式的本機開發 STS  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下 **機碼** 中的 **方案總管**，然後選取 **識別和存取**。  
  
2.  **識別和存取** 視窗隨即出現。  在 **提供者**下，選取 **測試與本機開發 STS 的應用程式**\]，然後按一下 **應用程式**。  
  
## 步驟 4 \- 修改您的 ASP.NET 應用程式會顯示登入狀態  
 這個步驟說明如何修改您的 ASP.NET 應用程式中動態顯示目前使用者是否登入。  一旦設定了 STS 提供者， WIF 處理傳入的宣告。  現在您必須設定您的應用程式程式碼顯示驗證的結果。  
  
#### 若要顯示請登入狀態  
  
1.  在 Visual Studio 中，開啟 **Default.aspx** 檔案位於 **機碼** 的專案之下。  
  
2.  以下列標記取代 **Default.aspx** 檔案中現有的標記:  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  將 **Default.aspx**\]，然後開啟程式碼後置檔案命名為 **Default.aspx.cs**。  
  
    > [!NOTE]
    >  **Default.aspx.cs** 可以在方案總管中的 **Default.aspx** 下隱藏。  如果看不到 **Default.aspx.cs** ，請按一下展開 **Default.aspx** 在三角形旁邊。  
  
4.  以下列程式碼取代 **Default.aspx.cs** 中的現有程式碼:  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  將 **Default.aspx.cs**，並建立應用程式。  
  
## 步驟 5 \- 測試在 WIF 且 ASP.NET 應用程式間的整合  
 這個步驟說明如何測試在 WIF 且 ASP.NET 應用程式之間的整合。  
  
#### 測試在 WIF ASP.NET 和之間的整合  
  
1.  在 Visual Studio 中，按 **F5** 開始偵錯應用程式。  如果未發現任何錯誤，則新的瀏覽器視窗中開啟。  
  
2.  您可能會注意瀏覽器會自動將要求重新導向至 STS，然後開啟 Default.aspx 網頁。  如果正確設定 WIF，您應該會看到網站就會顯示下列文字: **請登出」**。