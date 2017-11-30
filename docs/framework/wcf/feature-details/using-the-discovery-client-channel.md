---
title: "使用探索用戶端通道"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 655885aa392420cc0f35955e6146fd6a1f8e50d7
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-discovery-client-channel"></a><span data-ttu-id="fa562-102">使用探索用戶端通道</span><span class="sxs-lookup"><span data-stu-id="fa562-102">Using the Discovery Client Channel</span></span>
<span data-ttu-id="fa562-103">撰寫 WCF 用戶端應用程式時，您需要知道您所呼叫之服務的端點位址。</span><span class="sxs-lookup"><span data-stu-id="fa562-103">When writing a WCF client application you need to know the endpoint address of the service you are calling.</span></span> <span data-ttu-id="fa562-104">在很多情況下，無法事先知道服務的端點位址，或是服務的位址可能會隨著時間改變。</span><span class="sxs-lookup"><span data-stu-id="fa562-104">In many situations the endpoint address of a service is not known in advance or the address of the service changes over time.</span></span> <span data-ttu-id="fa562-105">探索用戶端通道可讓您撰寫 WCF 用戶端應用程式、描述您要呼叫的服務，然後用戶端會自動傳送探查要求。</span><span class="sxs-lookup"><span data-stu-id="fa562-105">The Discovery Client Channel allows you to write a WCF client application, describe the service you want to call, and the client channel automatically sends a probe request.</span></span> <span data-ttu-id="fa562-106">服務回應的時候，探索用戶端通道會從探查回應擷取服務的端點位址，並且使用此位址呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="fa562-106">When a service responds, the discovery client channel retrieves the endpoint address for the service from the probe response and uses it to call the service.</span></span>  
  
## <a name="using-the-discovery-client-channel"></a><span data-ttu-id="fa562-107">使用探索用戶端通道</span><span class="sxs-lookup"><span data-stu-id="fa562-107">Using the Discovery Client Channel</span></span>  
 <span data-ttu-id="fa562-108">若要使用探索用戶端通道，請將 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 的執行個體加入到您的用戶端通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="fa562-108">To use the Discovery Client Channel, add an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your client channel stack.</span></span> <span data-ttu-id="fa562-109">另一種方法是使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，如果繫結還沒有 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>，就會自動加入至繫結。</span><span class="sxs-lookup"><span data-stu-id="fa562-109">Alternatively you can use the <xref:System.ServiceModel.Discovery.DynamicEndpoint> and a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is automatically added to your binding if not already present.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fa562-110">建議以 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 做為用戶端通道堆疊最上方的項目。</span><span class="sxs-lookup"><span data-stu-id="fa562-110">It is recommended that the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is the top-most element on your client channel stack.</span></span> <span data-ttu-id="fa562-111">任何加到 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 上方的繫結項目，都必須確保建立的 <xref:System.ServiceModel.ChannelFactory> 或通道不會使用該端點位址或 `Via` 位址 (傳遞給 `CreateChannel` 方法)，因為這些可能沒有包含正確的位址。</span><span class="sxs-lookup"><span data-stu-id="fa562-111">Any binding element that is added on top of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the <xref:System.ServiceModel.ChannelFactory> or channel it creates does not use the endpoint address or `Via` address (passed to the `CreateChannel` method) because they may not contain the correct address.</span></span>  
  
 <span data-ttu-id="fa562-112"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 類別包含兩個公用屬性：</span><span class="sxs-lookup"><span data-stu-id="fa562-112">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> class contains two public properties:</span></span>  
  
1.  <span data-ttu-id="fa562-113"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>，用來描述您要呼叫的服務。</span><span class="sxs-lookup"><span data-stu-id="fa562-113"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, which is used to describe the service you want to call.</span></span>  
  
2.  <span data-ttu-id="fa562-114"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>指定要傳送探索訊息的探索端點。</span><span class="sxs-lookup"><span data-stu-id="fa562-114"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> which specifies the discovery endpoint to send discovery messages to.</span></span>  
  
 <span data-ttu-id="fa562-115"><xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> 屬性可以指定您要搜尋的服務合約、任何必要的範圍 URI，以及開啟通道嘗試次數的上限。</span><span class="sxs-lookup"><span data-stu-id="fa562-115">The <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> property allows you to specify the service contract you are searching for, any required scope URIs, and the maximum number of time to attempt to open the channel.</span></span> <span data-ttu-id="fa562-116">藉由呼叫建構函式指定合約類型<xref:System.ServiceModel.Discovery.FindCriteria>。</span><span class="sxs-lookup"><span data-stu-id="fa562-116">The contract type is specified by calling the constructor  <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span> <span data-ttu-id="fa562-117">範圍 URI 可以加入至 <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fa562-117">Scope URIs can be added to the <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> property.</span></span> <span data-ttu-id="fa562-118"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 屬性可讓您指定用戶端嘗試連接的結果數目上限。</span><span class="sxs-lookup"><span data-stu-id="fa562-118">The <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> property allows you to specify the maximum number of results to which the client tries to connect to.</span></span> <span data-ttu-id="fa562-119">收到探查回應時，用戶端會使用探查回應中的端點位址，嘗試開啟通道。</span><span class="sxs-lookup"><span data-stu-id="fa562-119">When a probe response is received the client attempts to open the channel using the endpoint address from the probe response.</span></span> <span data-ttu-id="fa562-120">如果發生例外狀況，用戶端會移至下一個探查回應，若有必要，則會等候更多回應。</span><span class="sxs-lookup"><span data-stu-id="fa562-120">If an exception occurs the client moves on to the next probe response, waiting for more responses to be received if necessary.</span></span> <span data-ttu-id="fa562-121">這個動作會繼續執行，直到通道已成功開啟，或是達到結果數目上限為止。</span><span class="sxs-lookup"><span data-stu-id="fa562-121">It continues to do this until the channel is successfully opened or the maximum number of results is reached.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fa562-122">這些設定，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。</span><span class="sxs-lookup"><span data-stu-id="fa562-122"> these settings, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>  
  
 <span data-ttu-id="fa562-123"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> 屬性可讓您指定要使用的探索端點。</span><span class="sxs-lookup"><span data-stu-id="fa562-123">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> property allows you to specify the discovery endpoint to use.</span></span> <span data-ttu-id="fa562-124">通常這會是 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>，但也可能是任何有效的端點。</span><span class="sxs-lookup"><span data-stu-id="fa562-124">Normally this is a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, but it can be any valid endpoint.</span></span>  
  
 <span data-ttu-id="fa562-125">您必須特別注意，建立要使用的繫結以便與服務通訊時，要使用與服務完全相同的繫結。</span><span class="sxs-lookup"><span data-stu-id="fa562-125">When you are creating the binding to use to communicate with the service, you must be careful to use the exact same binding as the service.</span></span> <span data-ttu-id="fa562-126">唯一的差異是，用戶端繫結在堆疊的最上方會有一個 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="fa562-126">The only difference is the client binding has a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> on the top of the stack.</span></span> <span data-ttu-id="fa562-127">如果服務正在使用系統提供的其中一個繫結，請建立新的 <xref:System.ServiceModel.Channels.CustomBinding>，並且在系統提供的繫結中傳遞給 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> 建構函式。</span><span class="sxs-lookup"><span data-stu-id="fa562-127">If service is using one of the system-provided bindings, create a new <xref:System.ServiceModel.Channels.CustomBinding> and pass in the system-provided binding to the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor.</span></span> <span data-ttu-id="fa562-128">然後，您可以透過在 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 屬性上呼叫 `Insert` 的方式，加入 <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A>。</span><span class="sxs-lookup"><span data-stu-id="fa562-128">Then you can add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> by calling `Insert` on the <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> property.</span></span>  
  
 <span data-ttu-id="fa562-129">一旦將 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 加入至您的繫結並妥善設定之後，您可以建立 WCF 用戶端類別的執行個體、開啟此執行個體，然後呼叫其方法。</span><span class="sxs-lookup"><span data-stu-id="fa562-129">Once you have added the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your binding and configured it, you can create an instance of the WCF client class, open it, and call its methods.</span></span> <span data-ttu-id="fa562-130">下列範例使用探索用戶端通道，探索實作 `ICalculator` 類別 (用於「WCF 快速入門」教學課程) 並呼叫其 `Add` 方法的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fa562-130">The following example uses the Discovery Client Channel to discover a WCF service that implements the `ICalculator` class (used in the Getting Started WCF tutorial) and calls its `Add` method.</span></span>  
  
```  
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the   
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a><span data-ttu-id="fa562-131">安全性與探索用戶端通道</span><span class="sxs-lookup"><span data-stu-id="fa562-131">Security and the Discovery Client Channel</span></span>  
 <span data-ttu-id="fa562-132">使用探索用戶端通道時，會指定兩個端點。</span><span class="sxs-lookup"><span data-stu-id="fa562-132">When using the discovery client channel, two endpoints are being specified.</span></span> <span data-ttu-id="fa562-133">一個會用來探索訊息 (通常是 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>)，另一個則是應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="fa562-133">One is used for discovery messages, usually <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, and the other is the application endpoint.</span></span> <span data-ttu-id="fa562-134">實作安全服務時，請務必謹慎，以確保兩個端點的安全。</span><span class="sxs-lookup"><span data-stu-id="fa562-134">When implementing a secure service, care must be taken to secure both endpoints.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fa562-135">安全性，請參閱[保護服務和用戶端](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="fa562-135"> security, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span>
