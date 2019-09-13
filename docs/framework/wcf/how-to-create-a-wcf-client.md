---
title: 教學課程：建立 Windows Communication Foundation 用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928897"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="43dc6-102">教學課程：建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="43dc6-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="43dc6-103">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第四個。</span><span class="sxs-lookup"><span data-stu-id="43dc6-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="43dc6-104">如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。</span><span class="sxs-lookup"><span data-stu-id="43dc6-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="43dc6-105">建立 WCF 應用程式的下一個工作是從 WCF 服務抓取中繼資料來建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="43dc6-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="43dc6-106">您可以使用 Visual Studio 加入服務參考，以取得來自服務 MEX 端點的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="43dc6-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="43dc6-107">Visual Studio 接著會以您選擇的語言，產生用戶端 proxy 的 managed 原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="43dc6-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="43dc6-108">它也會建立用戶端設定檔（*app.config*）。</span><span class="sxs-lookup"><span data-stu-id="43dc6-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="43dc6-109">此檔案可讓用戶端應用程式連接到端點上的服務。</span><span class="sxs-lookup"><span data-stu-id="43dc6-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="43dc6-110">如果您從 Visual Studio 的類別庫專案中呼叫 WCF 服務，請使用**加入服務參考**功能來自動產生 proxy 和相關聯的設定檔。</span><span class="sxs-lookup"><span data-stu-id="43dc6-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="43dc6-111">不過，因為類別庫專案不使用此設定檔，所以您必須將產生的設定檔中的設定，新增至呼叫類別庫之可執行檔的*app.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="43dc6-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="43dc6-112">或者，使用 [ [System.servicemodel 中繼資料公用程式] 工具](#servicemodel-metadata-utility-tool)，而不是 [Visual Studio] 來產生 proxy 類別和設定檔。</span><span class="sxs-lookup"><span data-stu-id="43dc6-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="43dc6-113">用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="43dc6-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="43dc6-114">本程式說明于[教學課程：使用用戶端](how-to-use-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="43dc6-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="43dc6-115">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="43dc6-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="43dc6-116">為 WCF 用戶端建立和設定主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="43dc6-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="43dc6-117">將服務參考加入至 WCF 服務，以產生 proxy 類別和設定檔。</span><span class="sxs-lookup"><span data-stu-id="43dc6-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="43dc6-118">建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="43dc6-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="43dc6-119">在 Visual Studio 中建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="43dc6-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="43dc6-120">從 [**檔案] 功能表中，選取 [** **開啟** > **專案/方案**]，然後流覽至您先前建立的**GettingStarted**方案（*GettingStarted*）。</span><span class="sxs-lookup"><span data-stu-id="43dc6-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="43dc6-121">選取 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-121">Select **Open**.</span></span>

    2. <span data-ttu-id="43dc6-122">從 [ **View** ] 功能表中，選取 [**方案總管**]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="43dc6-123">在 [**方案總管**] 視窗中，選取 [ **GettingStarted** ] 解決方案（最上層節點），然後從快捷方式功能表選取 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="43dc6-124">在左側的 [**加入新專案**] 視窗中，選取 [  **C#視覺效果**] 或 [ **Visual Basic**] 底下的 [ **Windows 桌面**] 類別。</span><span class="sxs-lookup"><span data-stu-id="43dc6-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="43dc6-125">選取 [**主控台應用程式（.NET Framework）** ] 範本，然後在 [**名稱**] 中輸入*GettingStartedClient* 。</span><span class="sxs-lookup"><span data-stu-id="43dc6-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="43dc6-126">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-126">Select **OK**.</span></span>

2. <span data-ttu-id="43dc6-127">將**GettingStartedClient**專案中的參考新增至<xref:System.ServiceModel>元件：</span><span class="sxs-lookup"><span data-stu-id="43dc6-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="43dc6-128">在 [**方案總管**] 視窗中，選取 [ **GettingStartedClient** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="43dc6-129">在 [**加入參考**] 視窗中，于視窗左側的 [**元件**] 底下，選取 [**架構**]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="43dc6-130">尋找並選取 [ **System.servicemodel**]，然後選擇 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="43dc6-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="43dc6-131">選取 > [檔案] [**全部儲存**]**以儲存方案**。</span><span class="sxs-lookup"><span data-stu-id="43dc6-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="43dc6-132">將服務參考新增至計算機服務：</span><span class="sxs-lookup"><span data-stu-id="43dc6-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="43dc6-133">在 [**方案總管**] 視窗中，選取 [ **GettingStartedClient** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入服務參考**]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="43dc6-134">在 [**加入服務參考**] 視窗中，選取 [**探索**]。</span><span class="sxs-lookup"><span data-stu-id="43dc6-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="43dc6-135">CalculatorService 服務會啟動，並 Visual Studio 顯示在 [**服務**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="43dc6-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="43dc6-136">選取 [ **CalculatorService** ] 將其展開，並顯示服務所執行的服務合約。</span><span class="sxs-lookup"><span data-stu-id="43dc6-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="43dc6-137">保留預設的**命名空間**，然後選擇 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="43dc6-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="43dc6-138">Visual Studio 會在**GettingStartedClient**專案的 [**已連線的服務**] 資料夾下加入新的專案。</span><span class="sxs-lookup"><span data-stu-id="43dc6-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="43dc6-139">System.servicemodel 中繼資料公用程式工具</span><span class="sxs-lookup"><span data-stu-id="43dc6-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="43dc6-140">下列範例示範如何選擇性地使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](servicemodel-metadata-utility-tool-svcutil-exe.md)來產生 proxy 類別檔案。</span><span class="sxs-lookup"><span data-stu-id="43dc6-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="43dc6-141">此工具會產生 proxy 類別檔案和*app.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="43dc6-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="43dc6-142">下列範例顯示如何分別在和 Visual Basic 中C#產生 proxy：</span><span class="sxs-lookup"><span data-stu-id="43dc6-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="43dc6-143">用戶端設定檔</span><span class="sxs-lookup"><span data-stu-id="43dc6-143">Client configuration file</span></span>

<span data-ttu-id="43dc6-144">建立用戶端之後，Visual Studio 會在**GettingStartedClient**專案中建立**app.config**設定檔，此檔案應該類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="43dc6-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="43dc6-145">在 [ [ \<system.servicemodel >](../configure-apps/file-schema/wcf/system-servicemodel.md) ] [ \<](../configure-apps/file-schema/wcf/endpoint-element.md)區段下，請注意端點 > 元素。</span><span class="sxs-lookup"><span data-stu-id="43dc6-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="43dc6-146">端點元素會定義用戶端用來存取服務的端點，如下所示： **&lt; &gt;**</span><span class="sxs-lookup"><span data-stu-id="43dc6-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="43dc6-147">位址： `http://localhost:8000/GettingStarted/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="43dc6-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="43dc6-148">端點的位址。</span><span class="sxs-lookup"><span data-stu-id="43dc6-148">The address of the endpoint.</span></span>
- <span data-ttu-id="43dc6-149">服務合約： `ServiceReference1.ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="43dc6-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="43dc6-150">服務合約會處理 WCF 用戶端與服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="43dc6-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="43dc6-151">當您使用其**加入服務參考**函數時，Visual Studio 產生此合約。</span><span class="sxs-lookup"><span data-stu-id="43dc6-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="43dc6-152">基本上，它是您在 GettingStartedLib 專案中定義的合約複本。</span><span class="sxs-lookup"><span data-stu-id="43dc6-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="43dc6-153">系結<xref:System.ServiceModel.WSHttpBinding>：。</span><span class="sxs-lookup"><span data-stu-id="43dc6-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="43dc6-154">系結會將 HTTP 指定為傳輸、互通安全性，以及其他設定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="43dc6-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="43dc6-155">後續步驟</span><span class="sxs-lookup"><span data-stu-id="43dc6-155">Next steps</span></span>

<span data-ttu-id="43dc6-156">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="43dc6-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="43dc6-157">為 WCF 用戶端建立和設定主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="43dc6-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="43dc6-158">將服務參考加入至 WCF 服務，以產生用戶端應用程式的 proxy 類別和設定檔。</span><span class="sxs-lookup"><span data-stu-id="43dc6-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="43dc6-159">請前進到下一個教學課程，以瞭解如何使用產生的用戶端。</span><span class="sxs-lookup"><span data-stu-id="43dc6-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43dc6-160">教學課程：使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="43dc6-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
