---
title: HOW TO：設定基本 Windows Communication Foundation 用戶端
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bde13abeac782da1c553afa290943eeff925fa4
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="bd2c6-102">HOW TO：設定基本 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="bd2c6-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="bd2c6-103">這是在建立基本 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六項工作中的第五項。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-103">This is the fifth of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="bd2c6-104">六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="bd2c6-105">此主題 disuccess 使用的 [加入服務參考] 功能產生的用戶端組態檔[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]或[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-105">This topic disuccess the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="bd2c6-106">設定用戶端包含指定用戶端用來存取服務的端點。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="bd2c6-107">端點內含位址、繫結和合約，每一項都必須在設定用戶端的過程中加以指定。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="bd2c6-108">若要設定 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="bd2c6-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="bd2c6-109">從 GettingStartedClient 專案開啟產生的組態檔 (App.config)。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="bd2c6-110">下列範例是產生之組態檔的外觀。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="bd2c6-111">在下[ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)區段中，尋找[\<端點 >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
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
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     <span data-ttu-id="bd2c6-112">這個範例會設定用戶端用來存取位於下列位址的服務端點： http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span><span class="sxs-lookup"><span data-stu-id="bd2c6-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="bd2c6-113">端點元素會指定將 `ServiceReference1.ICalculator` 服務合約用於 WCF 用戶端和服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="bd2c6-114">系統提供設定 WCF 通道 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-114">The WCF channel is configured with the system-provided <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span></span> <span data-ttu-id="bd2c6-115">這個合約是使用 Visual Studio 中的 [加入服務參考] 所產生。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="bd2c6-116">它基本上是 GettingStartedLib 專案中所定義之合約的複本。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="bd2c6-117"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 繫結會指定 HTTP 傳輸、 互通安全性，以及其他組態詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-117">The <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  <span data-ttu-id="bd2c6-118">如需如何搭配這項設定使用產生的用戶端的詳細資訊，請參閱[How to： 使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="bd2c6-118">For more information about how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2c6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd2c6-119">See Also</span></span>  
 [<span data-ttu-id="bd2c6-120">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="bd2c6-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="bd2c6-121">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="bd2c6-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="bd2c6-122">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="bd2c6-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="bd2c6-123">快速入門</span><span class="sxs-lookup"><span data-stu-id="bd2c6-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="bd2c6-124">自我裝載</span><span class="sxs-lookup"><span data-stu-id="bd2c6-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
