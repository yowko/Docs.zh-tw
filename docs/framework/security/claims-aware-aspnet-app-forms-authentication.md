---
title: 如何：使用表單型驗證建置宣告感知 ASP.NET 應用程式
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971840"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>如何：使用表單型驗證建置宣告感知 ASP.NET 應用程式

## <a name="applies-to"></a>適用於

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>總結

此＜如何＞一文提供詳細逐步程序，以建立使用表單驗證的簡單宣告感知 ASP.NET Web Forms 應用程式。 它也提供指示，有關如何測試應用程式來確認在使用者利用表單驗證登入時呈現宣告。

## <a name="contents"></a>內容

- 目標

- 總覽

- 步驟摘要

- 步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式

- 步驟 2 - 設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式

- 步驟 3 – 測試方案

## <a name="objectives"></a>目標

- 設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式

- 測試 ASP.NET Web Forms 應用程式以查看它是否正常運作

## <a name="overview"></a>總覽

在 .NET 4.5 中，WIF 和其宣告型授權已包含為 Framework 的不可或缺部分。 以前，如果您想要來自 ASP.NET 使用者的宣告，需要安裝 WIF，然後將介面轉換為主體物件，例如 `Thread.CurrentPrincipal` 或 `HttpContext.Current.User`。 現在，這些主體物件會自動提供宣告。

表單驗證受益於 .NET 4.5 中包含 WIF，因為表單驗證的所有使用者都會自動具有與其建立關聯的宣告。 如這個使用方法所示範，您可以在使用表單驗證的 ASP.NET 應用程式中立即開始使用這些宣告。

## <a name="summary-of-steps"></a>步驟摘要

- 步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式

- 步驟 2 - 設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式

- 步驟 3 – 測試方案

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>步驟 1 - 建立簡單 ASP.NET Web Forms 應用程式

在此步驟中，您將建立新的 ASP.NET Web Forms 應用程式。

### <a name="to-create-a-simple-aspnet-application"></a>建立簡單的 ASP.NET 應用程式

1. 啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。

2. 在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。

3. 在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>步驟 2 - 設定使用表單驗證之宣告的 ASP.NET Web Forms 應用程式

在此步驟中，您將組態項目新增至 *Web.config* 組態檔，並編輯 *Default.aspx* 檔案來顯示帳戶的宣告資訊。

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>設定使用表單驗證之宣告的 ASP.NET 應用程式

1. 在 *Default.aspx* 檔案中，將現有標記取代為下列標記：

    ```aspx
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

    這個步驟會將 GridView 控制項新增至您的 *Default.aspx* 網頁，其中填入擷取自表單驗證的宣告。

2. 儲存 *Default.aspx* 檔案，然後開啟其名為 *Default.aspx.cs* 的程式碼後置檔案。 將現有的程式碼取代為下列程式碼：

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

    上述程式碼會顯示已驗證使用者的宣告，包含表單驗證所識別的使用者。

## <a name="step-3--test-your-solution"></a>步驟 3 – 測試方案

在此步驟中，您將測試 ASP.NET Web Forms 應用程式，並確認使用者使用表單驗證登入時呈現宣告。

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>測試使用表單驗證之宣告的 ASP.NET Web Forms 應用程式

1. 按 **F5** 鍵建置並執行應用程式。 應該會向您呈現 *Default.aspx*，而頁面右上方會有 [註冊] 和 [登入] 連結。 按一下 [註冊]。

2. 在 [註冊] 頁面上，建立使用者帳戶，然後按一下 [註冊]。 將使用表單驗證建立您的帳戶，並自動將您登入。

3. 將您重新導向至首頁之後，應該會看到 [Your Claims] (您的宣告) 標題下方有一個資料表，其中包含有關您帳戶的 **Issuer**、**OriginalIssuer**、**Type**、**Value** 和 **ValueType** 宣告資訊。
