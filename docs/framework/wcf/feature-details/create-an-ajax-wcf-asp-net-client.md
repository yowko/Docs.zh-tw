---
title: 在 Visual Studio 中建立啟用 AJAX 的 WCF 服務和 ASP.NET 用戶端
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: a6d6e87de6200a5cb9bba566d595066673cdf9cf
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834781"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>HOW TO：建立已啟用 AJAX 的 WCF 服務，以及存取服務的 ASP.NET 用戶端

本主題說明如何使用 Visual Studio 來建立啟用 AJAX 的 Windows Communication Foundation （WCF）服務，以及存取服務的 ASP.NET 用戶端。

## <a name="create-an-aspnet-web-app"></a>建立 ASP.NET Web 應用程式

1. 開啟 Visual Studio。

1. 從 [**檔案**] 功能表中，選取 [**新增** > **專案**]

1. 在 [**新增專案**] 對話方塊中，展開 [**已安裝** >   > 的**視覺C#**  **Web** ] 類別，然後選取 [ **ASP.NET Web 應用程式（.NET Framework）** ]。

1. 將專案命名為**SandwichServices** ，然後按一下 **[確定]** 。

1. 在 [**新增 ASP.NET Web 應用程式**] 對話方塊中，選取 [**空白**]，然後選取 **[確定]** 。

   ![Visual Studio 中的 [ASP.NET web 應用程式類型] 對話方塊](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>新增 web 表單

1. 以滑鼠右鍵按一下**方案總管**中的 SandwichServices 專案，然後選取 [**加入** > **新專案**]。

1. 在 [**加入新專案**] 對話方塊中，展開 [  > **已安裝** > 的**視覺C#**  **Web** ] 類別，然後選取 [ **Web 表單**] 範本。

1. 接受預設名稱（**webform1.aspx**），然後選取 [**新增**]。

   *Webform1.aspx*會在**來源**視圖中開啟。

1. 將下列標記內加入 **\<主體>** 標記：

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>建立啟用 AJAX 的 WCF 服務

1. 以滑鼠右鍵按一下**方案總管**中的 SandwichServices 專案，然後選取 [**加入** > **新專案**]。

1. 在 [**加入新專案**] 對話方塊中，  > 展開 [**已安裝** > 的**視覺C#**  **Web** ] 類別，然後選取 [ **WCF 服務（啟用 AJAX）** ] 範本。

   ![Visual Studio 中的 WCF 服務（啟用 AJAX）專案範本](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. 將服務命名為**並將 costservice.svc** ，然後選取 [**新增**]。

   *CostService.svc.cs*會在編輯器中開啟。

1. 在服務中執行作業。 將下列方法新增至並將 costservice.svc 類別，以計算三明治數量的成本：

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>設定用戶端以存取服務

1. 開啟*webform1.aspx .aspx*檔案，然後選取**設計**視圖。

2. 從 [ **View** ] 功能表中，選取 [**工具箱**]。

3. 展開 [ **AJAX 擴充**功能] 節點，並將**ScriptManager**拖放到表單上。

4. 回到**來源**視圖，在 **\<ScriptManager >** 標記之間加入下列程式碼，以指定 WCF 服務的路徑：

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. 新增 JAVAscript `Calculate()`函式的程式碼。 將下列程式碼放在 web 表單的**標頭**區段中：

    ```html
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

   這段程式碼會呼叫並將 costservice.svc 的方法，以計算三個三明治的價格，然後在範圍中顯示名為**additionResult**的結果。

## <a name="run-the-program"></a>執行程式

請確定*webform1.aspx*具有焦點，然後按 [**啟動**] 按鈕以啟動 web 用戶端。 按鈕有綠色三角形，並顯示類似**IIS Express （Microsoft Edge）** 。 或者，您可以按<kbd>F5</kbd>。 按一下 [ **3 三明治**] 按鈕的價格，以產生 "3.75" 的預期輸出。

## <a name="example"></a>範例

下列是*CostService.svc.cs*檔案中的完整程式碼：

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

以下是*webform1.aspx*的完整內容：

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
