---
title: 教學課程：建立 Windows Communication Foundation 用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: a16a0ccabfd0f9fbe69db1ea88d4613185f3c1da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002075"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="360af-102">教學課程：建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="360af-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="360af-103">本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的第四個。</span><span class="sxs-lookup"><span data-stu-id="360af-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="360af-104">如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="360af-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="360af-105">建立 WCF 應用程式的下一個工作是藉由從 WCF 服務擷取中繼資料來建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="360af-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="360af-106">您可以使用 Visual Studio 加入服務參考，就會從服務的 MEX 端點取得中繼資料。</span><span class="sxs-lookup"><span data-stu-id="360af-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="360af-107">Visual Studio 接著會產生您所選擇的語言用戶端 proxy 的 managed 的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="360af-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="360af-108">它也會建立用戶端組態檔 (*App.config*)。</span><span class="sxs-lookup"><span data-stu-id="360af-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="360af-109">此檔案可讓用戶端應用程式連接到端點的服務。</span><span class="sxs-lookup"><span data-stu-id="360af-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="360af-110">如果您從 Visual Studio 中的類別庫專案中呼叫 WCF 服務，使用**加入服務參考**功能來自動產生 proxy 和相關聯的組態檔。</span><span class="sxs-lookup"><span data-stu-id="360af-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="360af-111">不過，因為類別庫專案不使用此組態檔，您需要將設定新增至產生的組態檔中*App.config*呼叫類別庫之可執行檔的檔案。</span><span class="sxs-lookup"><span data-stu-id="360af-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="360af-112">或者，使用[ServiceModel Metadata Utility 工具](#servicemodel-metadata-utility-tool)而非 Visual Studio 來產生 proxy 類別及組態檔。</span><span class="sxs-lookup"><span data-stu-id="360af-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="360af-113">用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="360af-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="360af-114">此程序所述[教學課程：使用用戶端](how-to-use-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="360af-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="360af-115">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="360af-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="360af-116">建立及設定 WCF 用戶端的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="360af-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="360af-117">加入服務參考至 WCF 服務，以產生 proxy 類別和組態檔。</span><span class="sxs-lookup"><span data-stu-id="360af-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="360af-118">建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="360af-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="360af-119">Visual Studio 中建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="360af-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="360af-120">從**檔案**功能表上，選取**開放** > **專案/方案**並瀏覽至**GettingStarted**解決方案您先前建立 (*GettingStarted.sln*)。</span><span class="sxs-lookup"><span data-stu-id="360af-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="360af-121">選取 [開啟] 。</span><span class="sxs-lookup"><span data-stu-id="360af-121">Select **Open**.</span></span>

    2. <span data-ttu-id="360af-122">從**檢視**功能表上，選取**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="360af-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="360af-123">在 [**方案總管] 中**視窗中，選取**GettingStarted**方案 （最上層節點），然後再選取**新增** > **新專案**快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="360af-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="360af-124">在 [**加入新的專案**視窗中的，在左側，選取**Windows 桌面**] 類別下的**Visual C#** 或**Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="360af-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="360af-125">選取 **主控台應用程式 (.NET Framework)** 範本，然後輸入*GettingStartedClient*如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="360af-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="360af-126">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="360af-126">Select **OK**.</span></span>

2. <span data-ttu-id="360af-127">加入參考**GettingStartedClient**專案加入<xref:System.ServiceModel>組件：</span><span class="sxs-lookup"><span data-stu-id="360af-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="360af-128">在 **方案總管 中**視窗中，選取**參考**下的資料夾**GettingStartedClient**專案，然後再選取**加入參考**快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="360af-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="360af-129">在 [**加入參考**] 視窗底下**組件**在視窗的左側，選取**Framework**。</span><span class="sxs-lookup"><span data-stu-id="360af-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="360af-130">尋找並選取**System.ServiceModel**，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="360af-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="360af-131">選取儲存方案**檔案** > **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="360af-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="360af-132">加入計算機服務的服務參考：</span><span class="sxs-lookup"><span data-stu-id="360af-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="360af-133">在 [**方案總管] 中**視窗中，選取**參考**下的資料夾**GettingStartedClient**專案，然後再選取**加入服務參考**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="360af-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="360af-134">在 **加入服務參考**視窗中，選取**Discover**。</span><span class="sxs-lookup"><span data-stu-id="360af-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="360af-135">CalculatorService 服務啟動和 Visual Studio 會顯示在**Services**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="360af-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="360af-136">選取  **CalculatorService**將它展開並顯示服務所實作的服務合約。</span><span class="sxs-lookup"><span data-stu-id="360af-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="360af-137">保留預設值**命名空間**，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="360af-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="360af-138">Visual Studio 會加入新項目底下**已連線的服務**中的資料夾**GettingStartedClient**專案。</span><span class="sxs-lookup"><span data-stu-id="360af-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="360af-139">ServiceModel Metadata Utility 工具</span><span class="sxs-lookup"><span data-stu-id="360af-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="360af-140">下列範例示範如何選擇性地使用[ServiceModel Metadata Utility 工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)來產生 proxy 類別檔案。</span><span class="sxs-lookup"><span data-stu-id="360af-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="360af-141">此工具會產生 proxy 類別檔案和*App.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="360af-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="360af-142">下列範例示範如何產生的 proxy，在C#和 Visual Basic 中，分別：</span><span class="sxs-lookup"><span data-stu-id="360af-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="360af-143">用戶端組態檔</span><span class="sxs-lookup"><span data-stu-id="360af-143">Client configuration file</span></span>

<span data-ttu-id="360af-144">您已建立用戶端之後，Visual Studio 會建立**App.config**中的設定檔**GettingStartedClient**專案，應該會類似下列的範例：</span><span class="sxs-lookup"><span data-stu-id="360af-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="360af-145">底下[ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md)區段中，注意[\<端點 >](../configure-apps/file-schema/wcf/endpoint-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="360af-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="360af-146">**&lt;端點&gt;** 項目定義的端點，讓用戶端來存取服務，如下所示：</span><span class="sxs-lookup"><span data-stu-id="360af-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>
- <span data-ttu-id="360af-147">地址： `http://localhost:8000/GettingStarted/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="360af-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="360af-148">端點的位址。</span><span class="sxs-lookup"><span data-stu-id="360af-148">The address of the endpoint.</span></span>
- <span data-ttu-id="360af-149">服務合約： `ServiceReference1.ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="360af-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="360af-150">服務合約處理 WCF 用戶端與服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="360af-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="360af-151">當您使用時，visual Studio 會產生此合約及其**加入服務參考**函式。</span><span class="sxs-lookup"><span data-stu-id="360af-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="360af-152">它基本上是複本在 GettingStartedLib 專案中所定義的合約。</span><span class="sxs-lookup"><span data-stu-id="360af-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="360af-153">繫結： <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="360af-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="360af-154">繫結會指定 HTTP 傳輸、 互通安全性，以及其他組態詳細資料。</span><span class="sxs-lookup"><span data-stu-id="360af-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="360af-155">後續步驟</span><span class="sxs-lookup"><span data-stu-id="360af-155">Next steps</span></span>

<span data-ttu-id="360af-156">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="360af-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="360af-157">建立及設定 WCF 用戶端的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="360af-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="360af-158">加入服務參考至 WCF 服務，以產生用戶端應用程式的 proxy 類別和組態檔。</span><span class="sxs-lookup"><span data-stu-id="360af-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="360af-159">請前進到下一個教學課程，以了解如何使用產生的用戶端。</span><span class="sxs-lookup"><span data-stu-id="360af-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="360af-160">教學課程：使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="360af-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
