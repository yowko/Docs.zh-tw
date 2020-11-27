---
title: 設定繫結上的逾時值
description: 瞭解如何管理 WCF 系結的 timeout 設定，以提升服務的效能、可用性和安全性。
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 6582568f3579f784d4c91c707dbb35c38533551d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284039"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="d112c-103">設定繫結上的逾時值</span><span class="sxs-lookup"><span data-stu-id="d112c-103">Configuring Timeout Values on a Binding</span></span>

<span data-ttu-id="d112c-104">WCF 繫結有一些逾時設定可供使用。</span><span class="sxs-lookup"><span data-stu-id="d112c-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="d112c-105">正確設定這些逾時設定可以改善服務的效能，但也會對服務的可用性和安全性造成影響。</span><span class="sxs-lookup"><span data-stu-id="d112c-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="d112c-106">可在 WCF 繫結上使用的逾時如下：</span><span class="sxs-lookup"><span data-stu-id="d112c-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="d112c-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="d112c-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="d112c-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="d112c-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="d112c-109">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="d112c-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="d112c-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="d112c-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="d112c-111">WCF 繫結逾時</span><span class="sxs-lookup"><span data-stu-id="d112c-111">WCF Binding Timeouts</span></span>  

 <span data-ttu-id="d112c-112">本主題中討論的每個設定，不論在程式碼還是組態中，都是對繫結本身進行設定。</span><span class="sxs-lookup"><span data-stu-id="d112c-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="d112c-113">下列程式碼示範如何在自我裝載服務的內容中，以程式設計方式對 WCF 繫結設定逾時。</span><span class="sxs-lookup"><span data-stu-id="d112c-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="d112c-114">下列範例示範如何在應用程式組態檔中設定繫結上的逾時。</span><span class="sxs-lookup"><span data-stu-id="d112c-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d112c-115">這些設定的其他資訊可以在 <xref:System.ServiceModel.Channels.Binding> 類別的文件中找到。</span><span class="sxs-lookup"><span data-stu-id="d112c-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="d112c-116">用戶端逾時</span><span class="sxs-lookup"><span data-stu-id="d112c-116">Client-side Timeouts</span></span>  

 <span data-ttu-id="d112c-117">在用戶端：</span><span class="sxs-lookup"><span data-stu-id="d112c-117">On the client side:</span></span>  
  
1. <span data-ttu-id="d112c-118">SendTimeout – 用來初始化 OperationTimeout，這會控制整個傳送訊息程序，包括接收要求/回覆服務作業的回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="d112c-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="d112c-119">從合約回呼方法傳送回覆郵件時，也適用這個逾時。</span><span class="sxs-lookup"><span data-stu-id="d112c-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="d112c-120">OpenTimeout –未指定明確的超時值時，用於開啟通道。</span><span class="sxs-lookup"><span data-stu-id="d112c-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="d112c-121">CloseTimeout –未指定明確的超時值時，用於關閉通道。</span><span class="sxs-lookup"><span data-stu-id="d112c-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="d112c-122">ReceiveTimeout –未使用。</span><span class="sxs-lookup"><span data-stu-id="d112c-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="d112c-123">服務端的超時</span><span class="sxs-lookup"><span data-stu-id="d112c-123">Service-side Timeouts</span></span>  

 <span data-ttu-id="d112c-124">在服務端：</span><span class="sxs-lookup"><span data-stu-id="d112c-124">On the service side:</span></span>  
  
1. <span data-ttu-id="d112c-125">SendTimeout、OpenTimeout、CloseTimeout 與用戶端上的相同。</span><span class="sxs-lookup"><span data-stu-id="d112c-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="d112c-126">ReceiveTimeout – 由服務架構層用來初始化工作階段閒置逾時，這會控制工作階段在逾時前可以處於閒置狀態多久。</span><span class="sxs-lookup"><span data-stu-id="d112c-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
