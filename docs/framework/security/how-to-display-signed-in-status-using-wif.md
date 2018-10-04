---
title: 如何：使用 WIF 顯示登入的狀態
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: 7d3d23dc1f2e081c0a7c53fbdfaef749c9729fd4
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584385"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>如何：使用 WIF 顯示登入的狀態
## <a name="applies-to"></a>適用於  
  
-   Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
-   ASP.NET® Web Forms  
  
## <a name="summary"></a>總結  
 本主題描述如何在啟用 WIF 的 ASP.NET 應用程式中顯示登入狀態。 WIF 提供了一些機制，可讓您的應用程式成為宣告感知，以及管理應用程式資源的驗證和授權。  
  
## <a name="contents"></a>內容  
  
-   總覽  
  
-   步驟摘要  
  
-   步驟 1 – 安裝識別身分與存取延伸模組  
  
-   步驟 2 – 建立信賴憑證者的 ASP.NET 應用程式  
  
-   步驟 3 – 啟用本機開發 STS 以驗證使用者  
  
-   步驟 4 – 修改 ASP.NET 應用程式以顯示登入狀態  
  
-   步驟 5 – 測試 WIF 與 ASP.NET 應用程式之間的整合  
  
## <a name="overview"></a>總覽  
 本主題示範如何使用 WIF 建立簡單的宣告感知應用程式，以及如何輕鬆顯示使用者是否已登入。 下列步驟會使用 Visual Studio 身分識別與存取延伸模組所隨附的本機開發 STS 。 本機開發 STS 是用來測試和開發環境，可提供簡單的方法，將宣告整合到您的應用程式。 它永遠不應該用於生產環境中，因為它不會執行實際的驗證，而且不需要認證。 不過，對於使用實際的驗證準備好用於生產環境的應用程式而言，下列步驟中的命令式程式碼都相同。  
  
## <a name="summary-of-steps"></a>步驟摘要  
  
-   步驟 1 – 安裝識別身分與存取延伸模組  
  
-   步驟 2 – 建立信賴憑證者的 ASP.NET 應用程式  
  
-   步驟 3 – 啟用本機開發 STS 以驗證使用者  
  
-   步驟 4 – 修改 ASP.NET 應用程式以顯示登入狀態  
  
-   步驟 5 – 測試 WIF 與 ASP.NET 應用程式之間的整合  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>步驟 1 – 安裝識別身分與存取延伸模組  
 此步驟描述如何設定 Visual Studio 2012 的身分識別與存取延伸模組。 這項延伸模組會將設定您的應用程式與 STS 端點進行通訊的程序自動化。  
  
#### <a name="to-install-the-identity-and-access-extension"></a>安裝識別身分與存取延伸模組  
  
1.  以系統管理員身分的高階權限模式來啟動 Visual Studio。  
  
2.  在 Visual Studio 中，依序按一下 [工具]  和 [延伸模組管理員] 。 [延伸模組管理員] 視窗隨即出現。  
  
3.  在 [延伸模組管理員] 中，按一下左側功能表中的 [Online Extensions] (線上延伸模組)，然後選取 [Visual Studio 組件庫]。  
  
4.  在右上角的 [延伸模組管理員] 中，搜尋 [身分識別與存取]。  
  
5.  [身分識別與存取] 項目會出現在搜尋結果中。 按一下它，然後按一下 [下載]。  
  
6.  [下載並安裝]  對話方塊隨即出現。 如果您同意授權條款，請按一下 [安裝]。  
  
7.  當 [身分識別與存取] 延伸模組已完成安裝後，請以系統管理員模式重新啟動 Visual Studio。  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>步驟 2 – 建立信賴憑證者的 ASP.NET 應用程式  
 此步驟描述如何建立將與 WIF 整合的信賴憑證者 ASP.NET Web Forms 應用程式。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。  
  
2.  在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。  
  
3.  在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>步驟 3 – 啟用本機開發 STS 以驗證使用者  
 此步驟描述如何在應用程式中啟用本機開發 STS。 透過使用 Visual Studio 的身分識別與存取延伸模組，即可啟用本機開發 STS。  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>在 ASP.NET 應用程式中啟用本機開發 STS  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下方案總管底下的 [TestService]，然後選取 [身分識別與存取]。  
  
2.  [身分識別與存取] 視窗隨即出現。 在 [提供者] 底下，選取 [Test your application with the Local Development STS] (使用本機開發 STS 測試應用程式}，然後按一下 [套用]。  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>步驟 4 – 修改 ASP.NET 應用程式以顯示登入狀態  
 此步驟描述如何修改 ASP.NET 應用程式，以動態方式顯示目前的使用者是否已登入。 一旦設定了 STS 提供者，WIF 就會處理連入宣告。 現在，您需要設定應用程式的程式碼，以顯示驗證的結果。  
  
#### <a name="to-display-sign-in-status"></a>顯示登入狀態  
  
1.  在 Visual Studio 中，開啟 **TestApp** 專案底下的 **Default.aspx** 檔案。  
  
2.  使用下列標記取代 **Default.aspx** 檔案中的現有標記：  
  
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
  
3.  儲存 **Default.aspx**，然後開啟其名為 **Default.aspx.cs** 的程式碼後置檔案。  
  
    > [!NOTE]
    >  在方案總管中，**Default.aspx.cs** 可能隱藏在 **Default.aspx** 的下方。 如果看不到 **Default.aspx.cs**，請按一下 **Default.aspx** 旁邊的三角形來展開它。  
  
4.  使用下列程式碼取代 **Default.aspx.cs** 中的現有程式碼：  
  
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
  
5.  儲存 **Default.aspx.cs**，然後建置應用程式。  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>步驟 5 – 測試 WIF 與 ASP.NET 應用程式之間的整合  
 此步驟描述如何測試 WIF 與 ASP.NET 應用程式之間的整合。  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>測試 WIF 與 ASP.NET 之間的整合  
  
1.  在 Visual Studio 中，按 **F5** 鍵開始對應用程式進行偵錯。 如果沒有發現任何錯誤，則會開啟新的瀏覽器視窗。  
  
2.  您可能會注意到瀏覽器以無訊息模式將您的要求重新導向至 STS，然後開啟 Default.aspx 網頁。 如果 WIF 已正確設定，您應該會看到網站顯示下列文字：**"You are signed in"**。
