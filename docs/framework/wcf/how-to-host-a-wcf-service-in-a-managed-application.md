---
title: 作法：在受控應用程式中裝載 WCF 服務
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: b6d1c9c38e2cc5f1b1b7b5538af0339987563de6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637585"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="e12e4-102">HOW TO：將 WCF 服務裝載於受管理的應用程式</span><span class="sxs-lookup"><span data-stu-id="e12e4-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="e12e4-103">若要將服務裝載於 Managed 應用程式中，請將服務的程式碼嵌入 Managed 應用程式的程式碼，再以命令式程式碼或透過組態以宣告方式定義服務的端點 (亦可使用預設端點)，然後建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e12e4-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="e12e4-104">若要開始接收訊息，請呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="e12e4-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e12e4-105">這樣會建立並開啟服務的接聽項。</span><span class="sxs-lookup"><span data-stu-id="e12e4-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="e12e4-106">用這種方式來裝載服務一般稱為「自我裝載」，因為 Managed 應用程式會自行執行裝載工作。</span><span class="sxs-lookup"><span data-stu-id="e12e4-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="e12e4-107">若要關閉服務，請呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="e12e4-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="e12e4-108">服務也可以裝載在 Managed Windows 服務、Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 中。</span><span class="sxs-lookup"><span data-stu-id="e12e4-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="e12e4-109">如需有關如何裝載服務的選項的詳細資訊，請參閱[裝載的服務](../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e12e4-109">For more information about hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

<span data-ttu-id="e12e4-110">將服務裝載在 Managed 應用程式中是最有彈性的選項，因為這麼做只需要部署最基本基礎結構。</span><span class="sxs-lookup"><span data-stu-id="e12e4-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="e12e4-111">如需有關如何在受管理的應用程式中裝載服務的詳細資訊，請參閱 <<c0> [ 受管理的應用程式中裝載](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e12e4-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="e12e4-112">下列程序示範如何在主控台應用程式中實作自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="e12e4-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="e12e4-113">建立自我裝載的服務</span><span class="sxs-lookup"><span data-stu-id="e12e4-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="e12e4-114">建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="e12e4-114">Create a new console application:</span></span>

   1. <span data-ttu-id="e12e4-115">開啟 Visual Studio，然後選取**的新** > **專案**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="e12e4-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="e12e4-116">在 **已安裝的範本**清單中，選取**Visual C#** 或**Visual Basic**，然後選取**Windows Desktop**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="e12e4-117">選取 **主控台應用程式**範本。</span><span class="sxs-lookup"><span data-stu-id="e12e4-117">Select the **Console App** template.</span></span> <span data-ttu-id="e12e4-118">型別`SelfHost`中**名稱**方塊，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="e12e4-119">以滑鼠右鍵按一下**SelfHost**中**方案總管**，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="e12e4-120">選取  **System.ServiceModel**從 **.NET**索引標籤，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="e12e4-121">如果**方案總管**視窗未顯示，選取**方案總管**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="e12e4-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="e12e4-122">按兩下**Program.cs**或是**Module1.vb**中**方案總管 中**開啟在 程式碼 視窗中，如果它尚未開啟。</span><span class="sxs-lookup"><span data-stu-id="e12e4-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="e12e4-123">在檔案頂端新增下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="e12e4-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="e12e4-124">定義與實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="e12e4-124">Define and implement a service contract.</span></span> <span data-ttu-id="e12e4-125">本範例會定義 `HelloWorldService` 以根據輸入服務的資料傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="e12e4-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="e12e4-126">如需如何定義和實作服務介面的詳細資訊，請參閱[How to:定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)和[How to:實作服務合約](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="e12e4-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="e12e4-127">在 `Main` 方法頂端使用服務的基底位址，建立 <xref:System.Uri> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e12e4-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="e12e4-128">建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體，並將代表服務型別與基底位址統一資源識別元 (URI) 的 <xref:System.Type> 傳入 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>。</span><span class="sxs-lookup"><span data-stu-id="e12e4-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="e12e4-129">啟用中繼資料發行，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 的 <xref:System.ServiceModel.ServiceHost> 方法初始化服務並準備接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e12e4-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="e12e4-130">本範例將使用預設端點，所以這項服務不需要組態檔。</span><span class="sxs-lookup"><span data-stu-id="e12e4-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="e12e4-131">如果沒有設定端點，執行階段就會針對服務所實作的每份服務合約，為每個基底位址各建立一個端點。</span><span class="sxs-lookup"><span data-stu-id="e12e4-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="e12e4-132">如需有關預設端點的詳細資訊，請參閱 < [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e12e4-132">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="e12e4-133">按下**Ctrl**+**Shift**+**B**建置方案。</span><span class="sxs-lookup"><span data-stu-id="e12e4-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="e12e4-134">測試服務</span><span class="sxs-lookup"><span data-stu-id="e12e4-134">Test the service</span></span>

1. <span data-ttu-id="e12e4-135">按下**Ctrl**+**F5**來執行服務。</span><span class="sxs-lookup"><span data-stu-id="e12e4-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="e12e4-136">開啟**WCF 測試用戶端**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="e12e4-137">若要開啟  **WCF 測試用戶端**，開啟適用於 Visual Studio 的開發人員命令提示字元並執行**WcfTestClient.exe**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="e12e4-138">選取 **新增服務**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="e12e4-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="e12e4-139">型別`http://localhost:8080/hello`輸入地址 方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="e12e4-140">請確認服務正在執行中，否則這個步驟會失敗。</span><span class="sxs-lookup"><span data-stu-id="e12e4-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="e12e4-141">若您已從程式碼變更了基底位址，即應在此步驟中使用修改後的基底位址。</span><span class="sxs-lookup"><span data-stu-id="e12e4-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="e12e4-142">按兩下**SayHello**下方**我的服務專案**節點。</span><span class="sxs-lookup"><span data-stu-id="e12e4-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="e12e4-143">輸入您的名稱到**值**中的資料行**要求**清單，然後按**Invoke**。</span><span class="sxs-lookup"><span data-stu-id="e12e4-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="e12e4-144">回覆訊息會出現在**回應**清單。</span><span class="sxs-lookup"><span data-stu-id="e12e4-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="e12e4-145">範例</span><span class="sxs-lookup"><span data-stu-id="e12e4-145">Example</span></span>

<span data-ttu-id="e12e4-146">下列範例會建立 <xref:System.ServiceModel.ServiceHost> 物件來裝載型別為 `HelloWorldService` 的服務，然後呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 上的 <xref:System.ServiceModel.ServiceHost> 方法。</span><span class="sxs-lookup"><span data-stu-id="e12e4-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e12e4-147">基底位址由程式碼提供、中繼資料發行已啟用，而且將使用預設端點。</span><span class="sxs-lookup"><span data-stu-id="e12e4-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="e12e4-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e12e4-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="e12e4-149">如何：裝載在 IIS 中的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="e12e4-149">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="e12e4-150">自我裝載</span><span class="sxs-lookup"><span data-stu-id="e12e4-150">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="e12e4-151">裝載服務</span><span class="sxs-lookup"><span data-stu-id="e12e4-151">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="e12e4-152">如何：定義服務合約</span><span class="sxs-lookup"><span data-stu-id="e12e4-152">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="e12e4-153">如何：實作服務合約</span><span class="sxs-lookup"><span data-stu-id="e12e4-153">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="e12e4-154">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e12e4-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="e12e4-155">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="e12e4-155">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e12e4-156">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e12e4-156">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
