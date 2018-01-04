---
title: "公告範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 485a5f98ead246b02aab4ffc5abebd5c88ea92dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="announcements-sample"></a>公告範例
此範例示範如何使用探索功能的公告功能。 公告功能可讓服務送出包含服務相關中繼資料的公告訊息。 當服務啟動時，預設會傳送一個 Hello 公告，而當服務關閉時，則會傳送一個 Bye 公告。 這些公告可以多點傳送，也可以點對點傳送。 這個範例包含兩個專案，也就是服務和用戶端。  
  
## <a name="service"></a>服務  
 此專案包含自我裝載的計算機服務。 在 `Main` 方法中會建立一個服務主機，並在其中加入一個服務端點。 接著，建立 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。 若要啟用公告，公告端點必須加入至 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。 在此情況下，標準端點會使用 UDP 多點傳送，當做公告端點加入。 這樣會透過已知的 UDP 位址廣播公告。  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>用戶端  
 請注意，此專案中的用戶端會裝載 <xref:System.ServiceModel.Discovery.AnnouncementService>。 此外，系統會向事件註冊兩個委派。 這些事件會控制收到線上和離線公告時的用戶端作法。  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` 和 `OnOfflineEvent` 方法會分別處理 Hello 和 Bye 公告訊息。  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  這個範例使用 HTTP 端點，若要執行此範例中，適當的 URL Acl 必須新增，請參閱[設定 HTTP 和 HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊。 以更高的權限執行下列命令應該就能加入適當的 ACL。 如果命令未正確執行，您可能要將 Domain 和 Username 替換成下列引數。 `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  建置方案。  
  
3.  執行 client.exe 應用程式。  
  
4.  執行 service.exe 應用程式。 請注意，用戶端會收到線上公告。  
  
5.  關閉 service.exe 應用程式。 請注意，用戶端會收到離線公告。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>請參閱
