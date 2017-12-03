---
title: "設定繫結上的逾時值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd6206d3b9445b321230bf5968891773abcac9c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a>設定繫結上的逾時值
WCF 繫結有一些逾時設定可供使用。 正確設定這些逾時設定可以改善服務的效能，但也會對服務的可用性和安全性造成影響。 可在 WCF 繫結上使用的逾時如下：  
  
1.  OpenTimeout  
  
2.  CloseTimeout  
  
3.  SendTimeout  
  
4.  ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>WCF 繫結逾時  
 本主題中討論的每個設定，不論在程式碼還是組態中，都是對繫結本身進行設定。 下列程式碼示範如何在自我裝載服務的內容中，以程式設計方式對 WCF 繫結設定逾時。  
  
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
  
 下列範例示範如何在應用程式組態檔中設定繫結上的逾時。  
  
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
  
 這些設定的其他資訊可以在 <xref:System.ServiceModel.Channels.Binding> 類別的文件中找到。  
  
### <a name="client-side-timeouts"></a>用戶端逾時  
 在用戶端：  
  
1.  SendTimeout – 用來初始化 OperationTimeout，這會控制整個傳送訊息程序，包括接收要求/回覆服務作業的回覆訊息。 從合約回呼方法傳送回覆郵件時，也適用這個逾時。  
  
2.  OpenTimeout – 在沒有明確指定逾時值的情況下開啟通道時使用  
  
3.  CloseTimeout – 在沒有明確指定逾時值的情況下關閉通道時使用  
  
4.  ReceiveTimeout – 不使用  
  
### <a name="service-side-timeouts"></a>服務端逾時  
 在服務端：  
  
1.  SendTimeout、OpentTimeout、CloseTimeout 與用戶端上的相同  
  
2.  ReceiveTimeout – 由服務架構層用來初始化工作階段閒置逾時，這會控制工作階段在逾時前可以處於閒置狀態多久。
