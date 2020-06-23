---
title: 教學課程：建立 Windows Communication Foundation 用戶端
description: 瞭解如何藉由從 WCF 服務抓取中繼資料來建立用戶端，作為一系列文章的一部分，協助您開始建立 WCF 應用程式。
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246320"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="e41f3-103">教學課程：建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="e41f3-103">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="e41f3-104">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第四個。</span><span class="sxs-lookup"><span data-stu-id="e41f3-104">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e41f3-105">如需教學課程的總覽，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e41f3-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="e41f3-106">建立 WCF 應用程式的下一個工作是從 WCF 服務抓取中繼資料來建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="e41f3-106">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="e41f3-107">您可以使用 Visual Studio 加入服務參考，以取得來自服務 MEX 端點的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e41f3-107">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="e41f3-108">Visual Studio 接著會以您選擇的語言，產生用戶端 proxy 的 managed 原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="e41f3-108">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="e41f3-109">它也會建立用戶端設定檔案（*App.config*）。</span><span class="sxs-lookup"><span data-stu-id="e41f3-109">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="e41f3-110">此檔案可讓用戶端應用程式連接到端點上的服務。</span><span class="sxs-lookup"><span data-stu-id="e41f3-110">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="e41f3-111">如果您從 Visual Studio 的類別庫專案中呼叫 WCF 服務，請使用**加入服務參考**功能來自動產生 proxy 和相關聯的設定檔。</span><span class="sxs-lookup"><span data-stu-id="e41f3-111">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="e41f3-112">不過，因為類別庫專案不使用此設定檔，所以您必須將產生的設定檔中的設定，新增至呼叫類別庫之可執行檔的*App.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="e41f3-112">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="e41f3-113">或者，使用 [ [System.servicemodel 中繼資料公用程式] 工具](#servicemodel-metadata-utility-tool)，而不是 [Visual Studio] 來產生 proxy 類別和設定檔。</span><span class="sxs-lookup"><span data-stu-id="e41f3-113">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="e41f3-114">用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e41f3-114">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="e41f3-115">[教學課程：使用用戶端](how-to-use-a-wcf-client.md)會說明此程式。</span><span class="sxs-lookup"><span data-stu-id="e41f3-115">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="e41f3-116">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="e41f3-116">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e41f3-117">為 WCF 用戶端建立和設定主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="e41f3-117">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="e41f3-118">將服務參考加入至 WCF 服務，以產生 proxy 類別和設定檔。</span><span class="sxs-lookup"><span data-stu-id="e41f3-118">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="e41f3-119">建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="e41f3-119">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="e41f3-120">在 Visual Studio 中建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="e41f3-120">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="e41f3-121">從 [檔案]**功能表中，選取 [** **開啟**  >  **專案/方案**]，然後流覽至您先前建立的**GettingStarted**方案（*GettingStarted*）。</span><span class="sxs-lookup"><span data-stu-id="e41f3-121">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="e41f3-122">選取 [開啟] 。</span><span class="sxs-lookup"><span data-stu-id="e41f3-122">Select **Open**.</span></span>

    2. <span data-ttu-id="e41f3-123">從 [ **View** ] 功能表中，選取 [**方案總管**]。</span><span class="sxs-lookup"><span data-stu-id="e41f3-123">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="e41f3-124">在 [**方案總管**] 視窗中，選取 [ **GettingStarted** ] 解決方案（最上層節點），然後從快捷方式功能表選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="e41f3-124">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="e41f3-125">在 [**加入新專案**] 視窗的左側，選取 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **Windows 桌面**] 類別。</span><span class="sxs-lookup"><span data-stu-id="e41f3-125">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="e41f3-126">選取 [**主控台應用程式（.NET Framework）** ] 範本，然後在 [**名稱**] 中輸入*GettingStartedClient* 。</span><span class="sxs-lookup"><span data-stu-id="e41f3-126">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="e41f3-127">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e41f3-127">Select **OK**.</span></span>

2. <span data-ttu-id="e41f3-128">將**GettingStartedClient**專案中的參考新增至 <xref:System.ServiceModel> 元件：</span><span class="sxs-lookup"><span data-stu-id="e41f3-128">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="e41f3-129">在 [**方案總管**] 視窗中，選取 [ **GettingStartedClient** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="e41f3-129">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="e41f3-130">在 [**加入參考**] 視窗中，于視窗左側的 [**元件**] 底下，選取 [**架構**]。</span><span class="sxs-lookup"><span data-stu-id="e41f3-130">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="e41f3-131">尋找並選取 [ **System.servicemodel**]，然後選擇 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e41f3-131">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="e41f3-132">選取 [檔案] [ **File**  >  **全部儲存**] 以儲存方案。</span><span class="sxs-lookup"><span data-stu-id="e41f3-132">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="e41f3-133">將服務參考新增至計算機服務：</span><span class="sxs-lookup"><span data-stu-id="e41f3-133">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="e41f3-134">在 [**方案總管**] 視窗中，選取 [ **GettingStartedClient** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入服務參考**]。</span><span class="sxs-lookup"><span data-stu-id="e41f3-134">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="e41f3-135">在 [**加入服務參考**] 視窗中，選取 [**探索**]。</span><span class="sxs-lookup"><span data-stu-id="e41f3-135">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="e41f3-136">CalculatorService 服務會啟動，並 Visual Studio 顯示在 [**服務**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="e41f3-136">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="e41f3-137">選取 [ **CalculatorService** ] 將其展開，並顯示服務所執行的服務合約。</span><span class="sxs-lookup"><span data-stu-id="e41f3-137">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="e41f3-138">保留預設的**命名空間**，然後選擇 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e41f3-138">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="e41f3-139">Visual Studio 會在**GettingStartedClient**專案的 [**已連線的服務**] 資料夾下加入新的專案。</span><span class="sxs-lookup"><span data-stu-id="e41f3-139">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="e41f3-140">System.servicemodel 中繼資料公用程式工具</span><span class="sxs-lookup"><span data-stu-id="e41f3-140">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="e41f3-141">下列範例示範如何選擇性地使用[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)來產生 proxy 類別檔案。</span><span class="sxs-lookup"><span data-stu-id="e41f3-141">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="e41f3-142">此工具會產生 proxy 類別檔案和*App.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="e41f3-142">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="e41f3-143">下列範例示範如何以 c # 和 Visual Basic 分別產生 proxy：</span><span class="sxs-lookup"><span data-stu-id="e41f3-143">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="e41f3-144">用戶端組態檔</span><span class="sxs-lookup"><span data-stu-id="e41f3-144">Client configuration file</span></span>

<span data-ttu-id="e41f3-145">建立用戶端之後，Visual Studio 會在**GettingStartedClient**專案中建立**App.config**設定檔，此檔案應該類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="e41f3-145">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="e41f3-146">在 [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) 區段底下，請注意 [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="e41f3-146">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="e41f3-147">\*\* &lt; 端點 &gt; \*\*元素會定義用戶端用來存取服務的端點，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e41f3-147">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="e41f3-148">位址： `http://localhost:8000/GettingStarted/CalculatorService` 。</span><span class="sxs-lookup"><span data-stu-id="e41f3-148">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="e41f3-149">端點的位址。</span><span class="sxs-lookup"><span data-stu-id="e41f3-149">The address of the endpoint.</span></span>
- <span data-ttu-id="e41f3-150">服務合約： `ServiceReference1.ICalculator` 。</span><span class="sxs-lookup"><span data-stu-id="e41f3-150">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="e41f3-151">服務合約會處理 WCF 用戶端與服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="e41f3-151">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="e41f3-152">當您使用其**加入服務參考**函數時，Visual Studio 產生此合約。</span><span class="sxs-lookup"><span data-stu-id="e41f3-152">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="e41f3-153">基本上，它是您在 GettingStartedLib 專案中定義的合約複本。</span><span class="sxs-lookup"><span data-stu-id="e41f3-153">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="e41f3-154">系結： <xref:System.ServiceModel.WSHttpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="e41f3-154">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="e41f3-155">系結會將 HTTP 指定為傳輸、互通安全性，以及其他設定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e41f3-155">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e41f3-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e41f3-156">Next steps</span></span>

<span data-ttu-id="e41f3-157">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="e41f3-157">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e41f3-158">為 WCF 用戶端建立和設定主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="e41f3-158">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="e41f3-159">將服務參考加入至 WCF 服務，以產生用戶端應用程式的 proxy 類別和設定檔。</span><span class="sxs-lookup"><span data-stu-id="e41f3-159">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="e41f3-160">請前進到下一個教學課程，以瞭解如何使用產生的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e41f3-160">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e41f3-161">教學課程：使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="e41f3-161">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
