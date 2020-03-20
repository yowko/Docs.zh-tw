---
title: 教程：創建 Windows 通信基礎用戶端
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184106"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="5e17b-102">教程：創建 Windows 通信基礎用戶端</span><span class="sxs-lookup"><span data-stu-id="5e17b-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="5e17b-103">本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五項任務中的第四個。</span><span class="sxs-lookup"><span data-stu-id="5e17b-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="5e17b-104">有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="5e17b-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="5e17b-105">創建 WCF 應用程式的下一個任務是通過從 WCF 服務檢索中繼資料來創建用戶端。</span><span class="sxs-lookup"><span data-stu-id="5e17b-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="5e17b-106">您可以使用 Visual Studio 添加服務引用，該服務引用從服務的 MEX 終結點獲取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5e17b-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="5e17b-107">然後，Visual Studio 會以您選擇的語言為用戶端代理生成託管原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="5e17b-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="5e17b-108">它還創建一個用戶端設定檔 *（App.config*）。</span><span class="sxs-lookup"><span data-stu-id="5e17b-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="5e17b-109">此檔使用戶端應用程式能夠在終結點連接到服務。</span><span class="sxs-lookup"><span data-stu-id="5e17b-109">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="5e17b-110">如果從 Visual Studio 中的類庫專案調用 WCF 服務，請使用 **"添加服務參考"** 功能自動生成代理和相關設定檔。</span><span class="sxs-lookup"><span data-stu-id="5e17b-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="5e17b-111">但是，由於類庫專案不使用此設定檔，因此您需要將生成的設定檔中的設置添加到調用類庫的可執行檔*App.config*檔中。</span><span class="sxs-lookup"><span data-stu-id="5e17b-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="5e17b-112">作為替代方法，請使用[ServiceModel 中繼資料實用程式工具](#servicemodel-metadata-utility-tool)而不是 Visual Studio 來生成代理類和設定檔。</span><span class="sxs-lookup"><span data-stu-id="5e17b-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="5e17b-113">用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="5e17b-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="5e17b-114">此過程在教程中描述[：使用用戶端](how-to-use-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="5e17b-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="5e17b-115">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="5e17b-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5e17b-116">為 WCF 用戶端創建和配置主控台應用專案。</span><span class="sxs-lookup"><span data-stu-id="5e17b-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="5e17b-117">向 WCF 服務添加服務引用以生成代理類和設定檔。</span><span class="sxs-lookup"><span data-stu-id="5e17b-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="5e17b-118">創建 Windows 通信基礎用戶端</span><span class="sxs-lookup"><span data-stu-id="5e17b-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="5e17b-119">在視覺化工作室中創建主控台應用專案：</span><span class="sxs-lookup"><span data-stu-id="5e17b-119">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="5e17b-120">在 **"檔"** 功能表中，選擇 **"打開** > **專案/解決方案**"並流覽到您以前創建的**入門**解決方案 （*獲取入門.sln*）。</span><span class="sxs-lookup"><span data-stu-id="5e17b-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="5e17b-121">選取 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e17b-121">Select **Open**.</span></span>

    2. <span data-ttu-id="5e17b-122">在 **"查看"** 功能表中，選擇 **"解決方案資源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="5e17b-123">在 **"解決方案資源管理器"** 視窗中，選擇 **"入門"** 解決方案（頂部節點），然後從快顯功能表中選擇 **"添加新** > **專案**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="5e17b-124">在左側的 **"添加新專案**"視窗中，在 **"可視 C#"** 或"**可視基本**"下選擇**Windows 桌面**類別。</span><span class="sxs-lookup"><span data-stu-id="5e17b-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="5e17b-125">選擇**主控台應用 （.NET 框架）** 範本，然後輸入"*開始用戶端*"**名稱**。</span><span class="sxs-lookup"><span data-stu-id="5e17b-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="5e17b-126">選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e17b-126">Select **OK**.</span></span>

2. <span data-ttu-id="5e17b-127">在**入門用戶端**專案中向<xref:System.ServiceModel>程式集增加參考：</span><span class="sxs-lookup"><span data-stu-id="5e17b-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="5e17b-128">在 **"解決方案資源管理器"** 視窗中，選擇 **"入門用戶端**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"增加參考**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="5e17b-129">在"**增加參考**"視窗中，在視窗左側的 **"程式集**"下，選擇 **"框架**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="5e17b-130">查找並選擇 **"系統.服務模式**"，然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="5e17b-131">通過選擇 **"全部保存檔** > **"保存**解決方案。</span><span class="sxs-lookup"><span data-stu-id="5e17b-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="5e17b-132">向計算機服務添加服務引用：</span><span class="sxs-lookup"><span data-stu-id="5e17b-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="5e17b-133">在 **"解決方案資源管理器"** 視窗中，選擇 **"入門用戶端**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"添加服務參考**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="5e17b-134">在 **"添加服務參考"** 視窗中，選擇 **"發現**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="5e17b-135">計算機服務啟動，視覺化工作室在 **"服務**"框中顯示它。</span><span class="sxs-lookup"><span data-stu-id="5e17b-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="5e17b-136">選擇**計算機服務**以展開它並顯示服務實現的服務協定。</span><span class="sxs-lookup"><span data-stu-id="5e17b-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="5e17b-137">保留預設**命名空間**並選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="5e17b-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="5e17b-138">Visual Studio 在 **"入門用戶端**"專案中的 **"已連接服務**"資料夾下添加新專案。</span><span class="sxs-lookup"><span data-stu-id="5e17b-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="5e17b-139">服務模型中繼資料實用程式工具</span><span class="sxs-lookup"><span data-stu-id="5e17b-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="5e17b-140">以下示例演示如何選擇使用[ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)來生成代理類檔。</span><span class="sxs-lookup"><span data-stu-id="5e17b-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="5e17b-141">此工具生成代理類檔和*App.config*檔。</span><span class="sxs-lookup"><span data-stu-id="5e17b-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="5e17b-142">以下示例分別演示如何在 C# 和 Visual Basic 中生成代理：</span><span class="sxs-lookup"><span data-stu-id="5e17b-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="5e17b-143">用戶端組態檔</span><span class="sxs-lookup"><span data-stu-id="5e17b-143">Client configuration file</span></span>

<span data-ttu-id="5e17b-144">創建用戶端後，Visual Studio 將在 **"入門Client"** 專案中創建**App.config**設定檔，該檔應類似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="5e17b-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="5e17b-145">在[\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md)部分下，請注意[\<終結點>](../configure-apps/file-schema/wcf/endpoint-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5e17b-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="5e17b-146">\*\* &lt;終結點&gt;\*\* 元素定義用戶端用於訪問服務的終結點，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5e17b-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="5e17b-147">位址： `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="5e17b-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="5e17b-148">端點的位址。</span><span class="sxs-lookup"><span data-stu-id="5e17b-148">The address of the endpoint.</span></span>
- <span data-ttu-id="5e17b-149">服務合同： `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="5e17b-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="5e17b-150">服務協定處理 WCF 用戶端和服務之間的通信。</span><span class="sxs-lookup"><span data-stu-id="5e17b-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="5e17b-151">當您使用其 **"添加服務參考"** 功能時，Visual Studio 生成了此協定。</span><span class="sxs-lookup"><span data-stu-id="5e17b-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="5e17b-152">它實質上是您在入門專案中定義的合同副本。</span><span class="sxs-lookup"><span data-stu-id="5e17b-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="5e17b-153">綁定： <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5e17b-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="5e17b-154">綁定指定 HTTP 作為傳輸、可交互操作的安全性和其他配置詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5e17b-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5e17b-155">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5e17b-155">Next steps</span></span>

<span data-ttu-id="5e17b-156">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="5e17b-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5e17b-157">為 WCF 用戶端創建和配置主控台應用專案。</span><span class="sxs-lookup"><span data-stu-id="5e17b-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="5e17b-158">向 WCF 服務添加服務引用，以生成用戶端應用程式的代理類和設定檔。</span><span class="sxs-lookup"><span data-stu-id="5e17b-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="5e17b-159">前進至下一個教程，瞭解如何使用生成的用戶端。</span><span class="sxs-lookup"><span data-stu-id="5e17b-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e17b-160">教程：使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="5e17b-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
