---
title: 在 Visual Studio 中建立啟用 AJAX 的 WCF 服務和 ASP.NET 用戶端
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471261"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>HOW TO：建立啟用 AJAX 的 WCF 服務和存取該服務的 ASP.NET 用戶端

本主題說明如何使用 Visual Studio 來建立啟用 AJAX 的 Windows Communication Foundation (WCF) 服務和 ASP.NET 用戶端存取服務。

## <a name="create-an-aspnet-web-app"></a>建立 ASP.NET Web 應用程式

1. 開啟 Visual Studio。

1. 從**檔案**功能表上，選取**新增** > **專案**

1. 在**新的專案**] 對話方塊中，展開**已安裝** > **Visual C#** > **Web**類別目錄，然後選取 [ **ASP.NET Web 應用程式 (.NET Framework)**。

1. 將專案命名為**SandwichServices**然後按一下**確定**。

1. 在 **新的 ASP.NET Web 應用程式**對話方塊中，選取**空白**，然後選取**確定**。

   ![Visual Studio 中 ASP.NET web 應用程式類型對話方塊](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>加入 web form

1. 中的 SandwichServices 專案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新項目**。

1. 在**加入新項目**] 對話方塊中，展開**已安裝** > **Visual C#** > **Web**類別目錄，然後選取 [ **Web Form**範本。

1. 接受預設名稱 (**WebForm1**)，然後選取**新增**。

   *WebForm1.aspx*以開啟**來源**檢視。

1. 將下列標記內加入**\<主體 >** 標記：

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>建立啟用 AJAX 的 WCF 服務

1. 中的 SandwichServices 專案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新項目**。

1. 在**加入新項目**] 對話方塊中，展開**已安裝** > **Visual C#** > **Web**類別目錄，然後選取 [ **WCF 服務 (ajax)** 範本。

   ![在 Visual Studio 中的 WCF 服務 (ajax) 的項目範本](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. 將服務命名**CostService** ，然後選取**新增**。

   *CostService.svc.cs*編輯器中開啟。

1. 在服務中實作的作業。 若要計算的三明治數量成本 CostService 類別新增下列方法：

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>設定用戶端存取服務

1. 開啟*WebForm1.aspx*檔案，然後選取**設計**檢視。

2. 從**檢視**功能表上，選取**工具箱**。

3. 依序展開**AJAX Extensions**節點拖曳和置放**ScriptManager**拖曳至表單。

4. 回到**來源**檢視中，新增下列程式碼之間 **\<ScriptManager >** 標記，以指定 WCF 服務的路徑：

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. 新增 Javascript 函式的程式碼`Calculate()`。 將下列程式碼中的放**head** web 表單的區段：

    ```javascript
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   此程式碼呼叫的方法來計算的三個三明治，價格 CostService，然後呼叫範圍中顯示的結果**additionResult**。

## <a name="run-the-program"></a>執行程式

請確定*WebForm1.aspx*具有焦點，，然後按下**開始**按鈕以啟動 web 用戶端。 按鈕具有綠色的三角形，並顯示類似**IIS Express (Microsoft Edge)**。 或者，您可以按下**F5**。 按一下 **價格的 3 個三明治**按鈕，以產生預期的"3.75"輸出。

## <a name="example-code"></a>範例程式碼

以下是完整的程式碼中*CostService.svc.cs*檔案：

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

以下是完整的內容*WebForm1.aspx*頁面：

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
