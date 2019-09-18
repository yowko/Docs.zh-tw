---
title: 在 Visual Studio 中建立啟用 AJAX 的 WCF 服務和 ASP.NET 用戶端
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 1f5c9eb1750b0df28836f147d5b4be1b223bb52e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053685"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="b2d36-102">作法：建立已啟用 AJAX 的 WCF 服務，以及存取服務的 ASP.NET 用戶端</span><span class="sxs-lookup"><span data-stu-id="b2d36-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="b2d36-103">本主題說明如何使用 Visual Studio 來建立啟用 AJAX 的 Windows Communication Foundation （WCF）服務，以及存取服務的 ASP.NET 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2d36-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="b2d36-104">建立 ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2d36-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="b2d36-105">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b2d36-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="b2d36-106">從 [**檔案**] 功能表中，選取 [**新增** > **專案**]</span><span class="sxs-lookup"><span data-stu-id="b2d36-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="b2d36-107">在 [**新增專案**] 對話方塊中，展開 [**已安裝** >   > 的**視覺C#**  **Web** ] 類別，然後選取 [ **ASP.NET Web 應用程式（.NET Framework）** ]。</span><span class="sxs-lookup"><span data-stu-id="b2d36-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="b2d36-108">將專案命名為**SandwichServices** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b2d36-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="b2d36-109">在 [**新增 ASP.NET Web 應用程式**] 對話方塊中，選取 [**空白**]，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b2d36-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Visual Studio 中的 [ASP.NET web 應用程式類型] 對話方塊](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="b2d36-111">新增 web 表單</span><span class="sxs-lookup"><span data-stu-id="b2d36-111">Add a web form</span></span>

1. <span data-ttu-id="b2d36-112">以滑鼠右鍵按一下**方案總管**中的 SandwichServices 專案，然後選取 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="b2d36-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="b2d36-113">在 [**加入新專案**] 對話方塊中，展開 [  > **已安裝** > 的**視覺C#**  **Web** ] 類別，然後選取 [ **Web 表單**] 範本。</span><span class="sxs-lookup"><span data-stu-id="b2d36-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="b2d36-114">接受預設名稱（**webform1.aspx**），然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="b2d36-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="b2d36-115">*Webform1.aspx*會在**來源**視圖中開啟。</span><span class="sxs-lookup"><span data-stu-id="b2d36-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="b2d36-116">將下列標記內加入 **\<主體>** 標記：</span><span class="sxs-lookup"><span data-stu-id="b2d36-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="b2d36-117">建立啟用 AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b2d36-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="b2d36-118">以滑鼠右鍵按一下**方案總管**中的 SandwichServices 專案，然後選取 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="b2d36-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="b2d36-119">在 [**加入新專案**] 對話方塊中，  > 展開 [**已安裝** > 的**視覺C#**  **Web** ] 類別，然後選取 [ **WCF 服務（啟用 AJAX）** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="b2d36-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Visual Studio 中的 WCF 服務（啟用 AJAX）專案範本](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="b2d36-121">將服務命名為**並將 costservice.svc** ，然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="b2d36-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="b2d36-122">*CostService.svc.cs*會在編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="b2d36-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="b2d36-123">在服務中執行作業。</span><span class="sxs-lookup"><span data-stu-id="b2d36-123">Implement the operation in the service.</span></span> <span data-ttu-id="b2d36-124">將下列方法新增至並將 costservice.svc 類別，以計算三明治數量的成本：</span><span class="sxs-lookup"><span data-stu-id="b2d36-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="b2d36-125">設定用戶端以存取服務</span><span class="sxs-lookup"><span data-stu-id="b2d36-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="b2d36-126">開啟*webform1.aspx .aspx*檔案，然後選取**設計**視圖。</span><span class="sxs-lookup"><span data-stu-id="b2d36-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="b2d36-127">從 [ **View** ] 功能表中，選取 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="b2d36-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="b2d36-128">展開 [ **AJAX 擴充**功能] 節點，並將**ScriptManager**拖放到表單上。</span><span class="sxs-lookup"><span data-stu-id="b2d36-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="b2d36-129">回到**來源**視圖，在 **\<ScriptManager >** 標記之間加入下列程式碼，以指定 WCF 服務的路徑：</span><span class="sxs-lookup"><span data-stu-id="b2d36-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="b2d36-130">新增 JAVAscript `Calculate()`函式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2d36-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="b2d36-131">將下列程式碼放在 web 表單的**標頭**區段中：</span><span class="sxs-lookup"><span data-stu-id="b2d36-131">Place the following code in the **head** section of the web form:</span></span>

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

   <span data-ttu-id="b2d36-132">這段程式碼會呼叫並將 costservice.svc 的方法，以計算三個三明治的價格，然後在範圍中顯示名為**additionResult**的結果。</span><span class="sxs-lookup"><span data-stu-id="b2d36-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="b2d36-133">執行程式</span><span class="sxs-lookup"><span data-stu-id="b2d36-133">Run the program</span></span>

<span data-ttu-id="b2d36-134">請確定*webform1.aspx*具有焦點，然後按 [**啟動**] 按鈕以啟動 web 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2d36-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="b2d36-135">按鈕有綠色三角形，並顯示類似**IIS Express （Microsoft Edge）** 。</span><span class="sxs-lookup"><span data-stu-id="b2d36-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="b2d36-136">或者，您可以按**F5**。</span><span class="sxs-lookup"><span data-stu-id="b2d36-136">Or, you can press **F5**.</span></span> <span data-ttu-id="b2d36-137">按一下 [ **3 三明治**] 按鈕的價格，以產生 "3.75" 的預期輸出。</span><span class="sxs-lookup"><span data-stu-id="b2d36-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example-code"></a><span data-ttu-id="b2d36-138">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="b2d36-138">Example code</span></span>

<span data-ttu-id="b2d36-139">以下是*CostService.svc.cs*檔案中的完整程式碼：</span><span class="sxs-lookup"><span data-stu-id="b2d36-139">Following is the full code in the *CostService.svc.cs* file :</span></span>

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

<span data-ttu-id="b2d36-140">以下是*webform1.aspx*的完整內容：</span><span class="sxs-lookup"><span data-stu-id="b2d36-140">Following is the full contents of the *WebForm1.aspx* page:</span></span>

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
