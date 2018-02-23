---
title: "設定繫結上的逾時值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce70b8bca923645ea1e00a55ec4d41903d828a99
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2018
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="6dfc0-102">設定繫結上的逾時值</span><span class="sxs-lookup"><span data-stu-id="6dfc0-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="6dfc0-103">WCF 繫結有一些逾時設定可供使用。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="6dfc0-104">正確設定這些逾時設定可以改善服務的效能，但也會對服務的可用性和安全性造成影響。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="6dfc0-105">可在 WCF 繫結上使用的逾時如下：</span><span class="sxs-lookup"><span data-stu-id="6dfc0-105">The following timeouts are available on WCF bindings:</span></span>  
  
1.  <span data-ttu-id="6dfc0-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="6dfc0-106">OpenTimeout</span></span>  
  
2.  <span data-ttu-id="6dfc0-107">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="6dfc0-107">CloseTimeout</span></span>  
  
3.  <span data-ttu-id="6dfc0-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="6dfc0-108">SendTimeout</span></span>  
  
4.  <span data-ttu-id="6dfc0-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="6dfc0-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="6dfc0-110">WCF 繫結逾時</span><span class="sxs-lookup"><span data-stu-id="6dfc0-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="6dfc0-111">本主題中討論的每個設定，不論在程式碼還是組態中，都是對繫結本身進行設定。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="6dfc0-112">下列程式碼示範如何在自我裝載服務的內容中，以程式設計方式對 WCF 繫結設定逾時。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");
    
    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));
        
        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);
        
        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();
        
        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="6dfc0-113">下列範例示範如何在應用程式組態檔中設定繫結上的逾時。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00" 
                 closeTimeout="00:10:00" 
                 sendTimeout="00:10:00" 
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="6dfc0-114">這些設定的其他資訊可以在 <xref:System.ServiceModel.Channels.Binding> 類別的文件中找到。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="6dfc0-115">用戶端逾時</span><span class="sxs-lookup"><span data-stu-id="6dfc0-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="6dfc0-116">在用戶端：</span><span class="sxs-lookup"><span data-stu-id="6dfc0-116">On the client side:</span></span>  
  
1.  <span data-ttu-id="6dfc0-117">SendTimeout – 用來初始化 OperationTimeout，這會控制整個傳送訊息程序，包括接收要求/回覆服務作業的回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="6dfc0-118">從合約回呼方法傳送回覆郵件時，也適用這個逾時。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2.  <span data-ttu-id="6dfc0-119">OpenTimeout – 使用開啟通道時未不指定任何明確的逾時的值。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3.  <span data-ttu-id="6dfc0-120">CloseTimeout – 使用關閉通道時未不指定任何明確的逾時的值。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4.  <span data-ttu-id="6dfc0-121">ReceiveTimeout – 不在使用中。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="6dfc0-122">服務端逾時</span><span class="sxs-lookup"><span data-stu-id="6dfc0-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="6dfc0-123">在服務端：</span><span class="sxs-lookup"><span data-stu-id="6dfc0-123">On the service side:</span></span>  
  
1.  <span data-ttu-id="6dfc0-124">SendTimeout、 OpenTimeout、 CloseTimeout 是用戶端上的一樣。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2.  <span data-ttu-id="6dfc0-125">ReceiveTimeout – 由服務架構層用來初始化工作階段閒置逾時，這會控制工作階段在逾時前可以處於閒置狀態多久。</span><span class="sxs-lookup"><span data-stu-id="6dfc0-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
