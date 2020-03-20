---
title: HOW TO：在 WAS 中裝載 WCF 服務
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184905"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="dae6b-102">HOW TO：在 WAS 中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="dae6b-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="dae6b-103">本主題概述了創建 Windows 進程啟動服務（也稱為 WAS） 託管 Windows 通信基礎 （WCF） 服務所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="dae6b-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="dae6b-104">WAS 是新的處理序啟用服務，其為一般化的 Internet Information Services (IIS) 功能，與非 HTTP 傳輸通訊協定搭配使用。</span><span class="sxs-lookup"><span data-stu-id="dae6b-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="dae6b-105">WCF 使用攔截器配接器介面來通信通過 WCF 支援的非 HTTP 協定（如 TCP、具名管道和訊息佇列）收到的啟動請求。</span><span class="sxs-lookup"><span data-stu-id="dae6b-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="dae6b-106">這個裝載選項要求 WAS 啟用元件必須正確安裝與設定，但不要求將任何裝載程式碼撰寫為應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="dae6b-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="dae6b-107">有關安裝和配置 WAS 的詳細資訊，請參閱[如何：安裝和配置 WCF 啟動元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)。</span><span class="sxs-lookup"><span data-stu-id="dae6b-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="dae6b-108">如果 Web 伺服器的要求處理管線設定為「傳統」模式，就不支援 WAS 啟動。</span><span class="sxs-lookup"><span data-stu-id="dae6b-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="dae6b-109">若要使用 WAS 啟動，Web 伺服器的要求處理管線就必須設定為「整合」模式。</span><span class="sxs-lookup"><span data-stu-id="dae6b-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="dae6b-110">當 WCF 服務託管在 WAS 中時，標準綁定以通常的方式使用。</span><span class="sxs-lookup"><span data-stu-id="dae6b-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="dae6b-111">但是，當透過 <xref:System.ServiceModel.NetTcpBinding> 和 <xref:System.ServiceModel.NetNamedPipeBinding> 來設定 WAS 裝載的服務時，就必須滿足下列限制。</span><span class="sxs-lookup"><span data-stu-id="dae6b-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="dae6b-112">當不同的端點使用同一個傳輸，繫結設定必須符合下列七項屬性：</span><span class="sxs-lookup"><span data-stu-id="dae6b-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="dae6b-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="dae6b-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="dae6b-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="dae6b-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="dae6b-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="dae6b-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="dae6b-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="dae6b-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="dae6b-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="dae6b-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="dae6b-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="dae6b-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="dae6b-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="dae6b-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="dae6b-120">否則，先初始化的端點一律直接決定這些屬性的值，而稍後新增的端點則會在這些屬性值未符合上述設定值時擲回 <xref:System.ServiceModel.ServiceActivationException>。</span><span class="sxs-lookup"><span data-stu-id="dae6b-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="dae6b-121">有關此示例的源副本，請參閱[TCP 啟動](../../../../docs/framework/wcf/samples/tcp-activation.md)。</span><span class="sxs-lookup"><span data-stu-id="dae6b-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="dae6b-122">若要建立 WAS 裝載的基本服務</span><span class="sxs-lookup"><span data-stu-id="dae6b-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="dae6b-123">定義服務類型的服務合約。</span><span class="sxs-lookup"><span data-stu-id="dae6b-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="dae6b-124">在服務類別中實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="dae6b-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="dae6b-125">請注意，服務的實作內並未指定位址或繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="dae6b-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="dae6b-126">同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dae6b-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="dae6b-127">建立 Web.config 檔案，定義 <xref:System.ServiceModel.NetTcpBinding> 端點要使用的 `CalculatorService` 繫結。</span><span class="sxs-lookup"><span data-stu-id="dae6b-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="dae6b-128">建立包含下列程式碼的 Service.svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="dae6b-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="dae6b-129">將 Service.svc 檔放入您的 IIS 虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="dae6b-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="dae6b-130">若要建立用戶端來使用服務</span><span class="sxs-lookup"><span data-stu-id="dae6b-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="dae6b-131">使用[命令列中的 ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務中繼資料生成代碼。</span><span class="sxs-lookup"><span data-stu-id="dae6b-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="dae6b-132">所產生的用戶端會包含 `ICalculator` 介面，其中定義了用戶端實作所必須滿足的服務合約。</span><span class="sxs-lookup"><span data-stu-id="dae6b-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="dae6b-133">產生的用戶端應用程式也包含 `ClientCalculator` 的實作。</span><span class="sxs-lookup"><span data-stu-id="dae6b-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="dae6b-134">請注意，服務的實作內部並未指定位址和繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="dae6b-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="dae6b-135">同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dae6b-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="dae6b-136">使用 <xref:System.ServiceModel.NetTcpBinding> 的用戶端組態也是由 Svcutil.exe 所產生的。</span><span class="sxs-lookup"><span data-stu-id="dae6b-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="dae6b-137">使用 Visual Studio 時，此檔案應該命名為 App.config。</span><span class="sxs-lookup"><span data-stu-id="dae6b-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="dae6b-138">在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="dae6b-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="dae6b-139">請編譯並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="dae6b-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae6b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dae6b-140">See also</span></span>

- [<span data-ttu-id="dae6b-141">TCP 啟用</span><span class="sxs-lookup"><span data-stu-id="dae6b-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- <span data-ttu-id="dae6b-142">[Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="dae6b-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
