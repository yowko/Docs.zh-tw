---
title: HOW TO：設定基本 Windows Communication Foundation 用戶端
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 3f267edf87711de8a5969e3e0b577648008c5a75
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323635"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="55157-102">HOW TO：設定基本 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="55157-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>

<span data-ttu-id="55157-103">這是建立基本的 Windows Communication Foundation (WCF) 應用程式所需的六個工作的第五個。</span><span class="sxs-lookup"><span data-stu-id="55157-103">This is the fifth of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="55157-104">如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="55157-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="55157-105">本主題討論使用所產生用戶端組態檔**加入服務參考**Visual Studio 的功能或有[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="55157-105">This topic discusses the client configuration file that was generated using the **Add Service Reference** functionality of Visual Studio or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="55157-106">設定用戶端包含指定用戶端用來存取服務的端點。</span><span class="sxs-lookup"><span data-stu-id="55157-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="55157-107">端點位址、 繫結和合約，而且每一種必須設定用戶端的過程中指定。</span><span class="sxs-lookup"><span data-stu-id="55157-107">An endpoint has an address, a binding, and a contract, and each of these must be specified in the process of configuring the client.</span></span>

## <a name="configure-a-windows-communication-foundation-client"></a><span data-ttu-id="55157-108">設定 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="55157-108">Configure a Windows Communication Foundation client</span></span>

<span data-ttu-id="55157-109">從 GettingStartedClient 專案開啟產生的組態檔 (App.config)。</span><span class="sxs-lookup"><span data-stu-id="55157-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="55157-110">下列範例是產生之組態檔的外觀。</span><span class="sxs-lookup"><span data-stu-id="55157-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="55157-111">底下[ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)區段中，尋找[\<端點 >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目。</span><span class="sxs-lookup"><span data-stu-id="55157-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>

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

<span data-ttu-id="55157-112">這個範例會設定用戶端用以存取位於下列位址的服務端點： `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="55157-112">This example configures the endpoint that the client uses to access the service that is located at the following address: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.</span></span>

<span data-ttu-id="55157-113">端點元素會指定將 `ServiceReference1.ICalculator` 服務合約用於 WCF 用戶端和服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="55157-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="55157-114">WCF 通道是透過系統提供的 <xref:System.ServiceModel.WSHttpBinding> 進行設定。</span><span class="sxs-lookup"><span data-stu-id="55157-114">The WCF channel is configured with the system-provided <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="55157-115">此合約由使用產生**加入服務參考**Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="55157-115">This contract was generated by using **Add Service Reference** in Visual Studio.</span></span> <span data-ttu-id="55157-116">它基本上是 GettingStartedLib 專案中所定義之合約的複本。</span><span class="sxs-lookup"><span data-stu-id="55157-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="55157-117"><xref:System.ServiceModel.WSHttpBinding> 繫結會指定 HTTP 為傳輸、互通安全性，與其他組態詳細資料。</span><span class="sxs-lookup"><span data-stu-id="55157-117">The <xref:System.ServiceModel.WSHttpBinding> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

<span data-ttu-id="55157-118">如需如何使用產生的用戶端使用此設定的詳細資訊，請參閱[如何： 使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="55157-118">For more information about how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="55157-119">後續步驟</span><span class="sxs-lookup"><span data-stu-id="55157-119">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55157-120">如何： 使用 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="55157-120">How to: Use a WCF client</span></span>](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a><span data-ttu-id="55157-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55157-121">See also</span></span>

- [<span data-ttu-id="55157-122">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="55157-122">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="55157-123">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="55157-123">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="55157-124">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="55157-124">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="55157-125">快速入門</span><span class="sxs-lookup"><span data-stu-id="55157-125">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="55157-126">自我裝載</span><span class="sxs-lookup"><span data-stu-id="55157-126">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)