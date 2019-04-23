---
title: 公告範例
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 895043976fd39ac0057c8dbc1c7daf0394393984
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771669"
---
# <a name="announcements-sample"></a>公告範例
此範例示範如何使用探索功能的公告功能。 公告功能可讓服務送出包含服務相關中繼資料的公告訊息。 當服務啟動時，預設會傳送一個 Hello 公告，而當服務關閉時，則會傳送一個 Bye 公告。 這些公告可以多點傳送，也可以點對點傳送。 這個範例包含兩個專案，也就是服務和用戶端。  
  
## <a name="service"></a>服務  
 此專案包含自我裝載的計算機服務。 在 `Main` 方法中會建立一個服務主機，並在其中加入一個服務端點。 接著，建立 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。 若要啟用公告，公告端點必須加入至 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。 在此情況下，標準端點會使用 UDP 多點傳送，當做公告端點加入。 這樣會透過已知的 UDP 位址廣播公告。  
  
```csharp
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
  
```csharp
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` 和 `OnOfflineEvent` 方法會分別處理 Hello 和 Bye 公告訊息。  
  
```csharp
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
  
1. 此範例使用 HTTP 端點，若要執行這個範例，適當的 URL Acl 必須加入，請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊。 以更高的權限執行下列命令應該就能加入適當的 ACL。 如果命令未正確執行，您可能要將 Domain 和 Username 替換成下列引數。 `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. 建置方案。  
  
3. 執行 client.exe 應用程式。  
  
4. 執行 service.exe 應用程式。 請注意，用戶端會收到線上公告。  
  
5. 關閉 service.exe 應用程式。 請注意，用戶端會收到離線公告。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
