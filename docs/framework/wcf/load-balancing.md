---
title: 負載平衡
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: d3b24ef892e1fe3dd28fee4ce8fa44f7373c7c01
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645484"
---
# <a name="load-balancing"></a><span data-ttu-id="83438-102">負載平衡</span><span class="sxs-lookup"><span data-stu-id="83438-102">Load Balancing</span></span>
<span data-ttu-id="83438-103">增加 Windows Communication Foundation (WCF) 應用程式容量的一種方法是將其相應放大程式部署到負載平衡的伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="83438-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="83438-104">WCF 應用程式可以進行負載平衡使用標準負載平衡技術，包括軟體負載平衡器，例如 Windows 網路負載平衡，以及硬體架構的負載平衡裝置。</span><span class="sxs-lookup"><span data-stu-id="83438-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="83438-105">下列各節討論負載平衡使用各種不同的系統提供繫結所建置的 WCF 應用程式的考量。</span><span class="sxs-lookup"><span data-stu-id="83438-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="83438-106">使用基本 HTTP 繫結的負載平衡</span><span class="sxs-lookup"><span data-stu-id="83438-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="83438-107">從負載平衡，使用進行通訊的 WCF 應用程式的觀點來看<xref:System.ServiceModel.BasicHttpBinding>與其他常見的 HTTP 網路流量 （靜態 HTML 內容、 ASP.NET 網頁或 ASMX Web 服務） 並無不同。</span><span class="sxs-lookup"><span data-stu-id="83438-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="83438-108">使用這個繫結的 WCF 通道是原本就是無狀態，並在通道關閉時終止其連線。</span><span class="sxs-lookup"><span data-stu-id="83438-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="83438-109">因此，<xref:System.ServiceModel.BasicHttpBinding> 可搭配現有的 HTTP 負載平衡技術正常運作。</span><span class="sxs-lookup"><span data-stu-id="83438-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="83438-110">根據預設，<xref:System.ServiceModel.BasicHttpBinding> 會在訊息中傳送包含 `Keep-Alive` 值的連線 HTTP 標頭，該值可以讓使用者建立服務 (指支援使用者的服務) 的持續連線。</span><span class="sxs-lookup"><span data-stu-id="83438-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="83438-111">這項組態會改進處理能力，因為先前建立的連線可以重複使用，並將後續訊息傳送到相同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="83438-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="83438-112">不過，重複使用連線可能會使用戶端與負載平衡陣列內的特定伺服器產生強烈的關聯性，這樣就會降低循環配置資源的有效性。</span><span class="sxs-lookup"><span data-stu-id="83438-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="83438-113">如果不希望發生這種行為，請針對 `Keep-Alive` 或使用者定義的 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> 使用 <xref:System.ServiceModel.Channels.CustomBinding> 屬性，停用伺服器上的 HTTP <xref:System.ServiceModel.Channels.Binding>。</span><span class="sxs-lookup"><span data-stu-id="83438-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="83438-114">下列範例會示範如何使用組態來做到這點。</span><span class="sxs-lookup"><span data-stu-id="83438-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="83438-115">使用 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中導入的簡化組態時，就可以透過下列簡化組態完成相同的行為。</span><span class="sxs-lookup"><span data-stu-id="83438-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="83438-116">如需預設端點、繫結和行為的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="83438-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="83438-117">使用 WSHttp 繫結和 WSDualHttp 繫結的負載平衡</span><span class="sxs-lookup"><span data-stu-id="83438-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="83438-118">只要對預設的繫結組態進行一些修改，即可透過 HTTP 負載平衡技術來使 <xref:System.ServiceModel.WSHttpBinding> 與 <xref:System.ServiceModel.WSDualHttpBinding> 兩者達成負載平衡。</span><span class="sxs-lookup"><span data-stu-id="83438-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="83438-119">關閉安全性內容建立：將 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> 上的 <xref:System.ServiceModel.WSHttpBinding> 屬性設定為 `false`，即可做到這點。</span><span class="sxs-lookup"><span data-stu-id="83438-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="83438-120">或者，如果需要安全性工作階段，就可以使用具狀態的安全性工作階段中所述[安全工作階段](../../../docs/framework/wcf/feature-details/secure-sessions.md)主題。</span><span class="sxs-lookup"><span data-stu-id="83438-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](../../../docs/framework/wcf/feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="83438-121">具狀態的安全性工作階段讓服務能夠保持無狀態，因為安全性工作階段的所有狀態都會隨著每項要求傳輸為保護安全性權杖的一部分。</span><span class="sxs-lookup"><span data-stu-id="83438-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="83438-122">請注意，為了啟用可設定狀態的安全性工作階段，這時必須使用 <xref:System.ServiceModel.Channels.CustomBinding> 或是使用者定義的 <xref:System.ServiceModel.Channels.Binding>，因為系統提供的 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.WSDualHttpBinding> 上面並未公開 (Expose) 這些必要的組態設定。</span><span class="sxs-lookup"><span data-stu-id="83438-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="83438-123">請勿使用可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="83438-123">Do not use reliable sessions.</span></span> <span data-ttu-id="83438-124">這項功能預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="83438-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="83438-125">負載平衡 Net.TCP 繫結</span><span class="sxs-lookup"><span data-stu-id="83438-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="83438-126"><xref:System.ServiceModel.NetTcpBinding> 可以使用 IP 層負載平衡技術來達成負載平衡。</span><span class="sxs-lookup"><span data-stu-id="83438-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="83438-127">不過，根據預設，<xref:System.ServiceModel.NetTcpBinding> 會建立 TCP 連線集區來縮短連線延遲時間。</span><span class="sxs-lookup"><span data-stu-id="83438-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="83438-128">這種最佳化方式會干擾到負載平衡的基本機制。</span><span class="sxs-lookup"><span data-stu-id="83438-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="83438-129">進行 <xref:System.ServiceModel.NetTcpBinding> 最佳化的主要組態值是租用逾時，這個值是「連線集區設定」的一部分。</span><span class="sxs-lookup"><span data-stu-id="83438-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="83438-130">連線集區會導致用戶端連線與陣列內的特定伺服器產生關聯。</span><span class="sxs-lookup"><span data-stu-id="83438-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="83438-131">隨著這些連線的存留期 (Lifetime) 延長 (由租用逾時設定所控制的因素)，在陣列內各個伺服器中的負載散佈會出現不平衡的情形。</span><span class="sxs-lookup"><span data-stu-id="83438-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="83438-132">結果一來，就會提高平均的呼叫時間。</span><span class="sxs-lookup"><span data-stu-id="83438-132">As a result the average call time increases.</span></span> <span data-ttu-id="83438-133">所以，當您在負載平衡案例中使用 <xref:System.ServiceModel.NetTcpBinding> 時，請考慮降低繫結所使用的預設租用逾時。</span><span class="sxs-lookup"><span data-stu-id="83438-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="83438-134">對負載平衡案例來說，30 秒的租用逾時是合理的起始值，不過最佳值會視應用程式而定。</span><span class="sxs-lookup"><span data-stu-id="83438-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="83438-135">如需通道租用逾時和其他傳輸配額的詳細資訊，請參閱[傳輸配額](../../../docs/framework/wcf/feature-details/transport-quotas.md)。</span><span class="sxs-lookup"><span data-stu-id="83438-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="83438-136">為了在負載平衡案例中創造最佳效能，請考慮使用 <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> 或 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>)。</span><span class="sxs-lookup"><span data-stu-id="83438-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83438-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83438-137">See also</span></span>

- [<span data-ttu-id="83438-138">Internet Information Services 裝載最佳做法</span><span class="sxs-lookup"><span data-stu-id="83438-138">Internet Information Services Hosting Best Practices</span></span>](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
