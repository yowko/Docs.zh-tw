---
title: 在 Visual Studio 中建立啟用 AJAX 的 WCF 服務和 ASP.NET 用戶端
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009306"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="80899-102">HOW TO：建立啟用 AJAX 的 WCF 服務和存取該服務的 ASP.NET 用戶端</span><span class="sxs-lookup"><span data-stu-id="80899-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="80899-103">本主題說明如何使用 Visual Studio 來建立啟用 AJAX 的 Windows Communication Foundation (WCF) 服務和 ASP.NET 用戶端存取服務。</span><span class="sxs-lookup"><span data-stu-id="80899-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="80899-104">建立 ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="80899-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="80899-105">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="80899-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="80899-106">從**檔案**功能表上，選取**新增** > **專案**</span><span class="sxs-lookup"><span data-stu-id="80899-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="80899-107">在**新的專案**] 對話方塊中，展開**已安裝** > **Visual C#** > **Web**類別目錄，然後選取 [ **ASP.NET Web 應用程式 (.NET Framework)**。</span><span class="sxs-lookup"><span data-stu-id="80899-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="80899-108">將專案命名為**SandwichServices**然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="80899-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="80899-109">在 **新的 ASP.NET Web 應用程式**對話方塊中，選取**空白**，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="80899-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Visual Studio 中 ASP.NET web 應用程式類型對話方塊](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="80899-111">加入 web form</span><span class="sxs-lookup"><span data-stu-id="80899-111">Add a web form</span></span>

1. <span data-ttu-id="80899-112">中的 SandwichServices 專案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新項目**。</span><span class="sxs-lookup"><span data-stu-id="80899-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="80899-113">在**加入新項目**] 對話方塊中，展開**已安裝** > **Visual C#** > **Web**類別目錄，然後選取 [ **Web Form**範本。</span><span class="sxs-lookup"><span data-stu-id="80899-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="80899-114">接受預設名稱 (**WebForm1**)，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="80899-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="80899-115">*WebForm1.aspx*以開啟**來源**檢視。</span><span class="sxs-lookup"><span data-stu-id="80899-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="80899-116">將下列標記內加入**\<主體 >** 標記：</span><span class="sxs-lookup"><span data-stu-id="80899-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="80899-117">建立啟用 AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="80899-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="80899-118">中的 SandwichServices 專案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新項目**。</span><span class="sxs-lookup"><span data-stu-id="80899-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="80899-119">在**加入新項目**] 對話方塊中，展開**已安裝** > **Visual C#** > **Web**類別目錄，然後選取 [ **WCF 服務 (ajax)** 範本。</span><span class="sxs-lookup"><span data-stu-id="80899-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![在 Visual Studio 中的 WCF 服務 (ajax) 的項目範本](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="80899-121">將服務命名**CostService** ，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="80899-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="80899-122">*CostService.svc.cs*編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="80899-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="80899-123">在服務中實作的作業。</span><span class="sxs-lookup"><span data-stu-id="80899-123">Implement the operation in the service.</span></span> <span data-ttu-id="80899-124">若要計算的三明治數量成本 CostService 類別新增下列方法：</span><span class="sxs-lookup"><span data-stu-id="80899-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="80899-125">設定用戶端存取服務</span><span class="sxs-lookup"><span data-stu-id="80899-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="80899-126">開啟*WebForm1.aspx*檔案，然後選取**設計**檢視。</span><span class="sxs-lookup"><span data-stu-id="80899-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="80899-127">從**檢視**功能表上，選取**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="80899-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="80899-128">依序展開**AJAX Extensions**節點拖曳和置放**ScriptManager**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="80899-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="80899-129">回到**來源**檢視中，新增下列程式碼之間 **\<ScriptManager >** 標記，以指定 WCF 服務的路徑：</span><span class="sxs-lookup"><span data-stu-id="80899-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. <span data-ttu-id="80899-130">新增 Javascript 函式的程式碼`Calculate()`。</span><span class="sxs-lookup"><span data-stu-id="80899-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="80899-131">將下列程式碼中的放**head** web 表單的區段：</span><span class="sxs-lookup"><span data-stu-id="80899-131">Place the following code in the **head** section of the web form:</span></span>

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

   <span data-ttu-id="80899-132">此程式碼呼叫的方法來計算的三個三明治，價格 CostService，然後呼叫範圍中顯示的結果**additionResult**。</span><span class="sxs-lookup"><span data-stu-id="80899-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="80899-133">執行程式</span><span class="sxs-lookup"><span data-stu-id="80899-133">Run the program</span></span>

<span data-ttu-id="80899-134">請確定*WebForm1.aspx*具有焦點，，然後按下**開始**按鈕以啟動 web 用戶端。</span><span class="sxs-lookup"><span data-stu-id="80899-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="80899-135">按鈕具有綠色的三角形，並顯示類似**IIS Express (Microsoft Edge)**。</span><span class="sxs-lookup"><span data-stu-id="80899-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="80899-136">或者，您可以按下**F5**。</span><span class="sxs-lookup"><span data-stu-id="80899-136">Or, you can press **F5**.</span></span> <span data-ttu-id="80899-137">按一下 **價格的 3 個三明治**按鈕，以產生預期的"3.75"輸出。</span><span class="sxs-lookup"><span data-stu-id="80899-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example-code"></a><span data-ttu-id="80899-138">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="80899-138">Example code</span></span>

<span data-ttu-id="80899-139">以下是完整的程式碼中*CostService.svc.cs*檔案：</span><span class="sxs-lookup"><span data-stu-id="80899-139">Following is the full code in the *CostService.svc.cs* file :</span></span>

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

<span data-ttu-id="80899-140">以下是完整的內容*WebForm1.aspx*頁面：</span><span class="sxs-lookup"><span data-stu-id="80899-140">Following is the full contents of the *WebForm1.aspx* page:</span></span>

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
