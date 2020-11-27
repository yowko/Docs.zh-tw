---
title: 探索路由器服務
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: f3ea32d10e27eceb3edcee8b6aeacbf9c5ebc6f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292645"
---
# <a name="discovery-router-service"></a>探索路由器服務

此範例示範如何將探索訊息轉送到其他端點。  
  
## <a name="demonstrates"></a>示範  

 探索路由  
  
## <a name="discussion"></a>討論  

 如果用戶端要使用 Proxy 尋找服務，而且 Proxy 不知道此種服務，但知道其他 Proxy，則探索路由相當實用。 這個 Proxy 可以將探索封包從此用戶端轉送到第二個 Proxy。 第二個 Proxy 可以尋找服務，並將回應傳回原始用戶端。  
  
 在此範例中，用戶端會將訊息傳送到探索路由元件。 此訊息會傳送到探索路由器中的特定端點。 接著，路由器會將訊息轉送至 UDP 多點傳送端點。 探查訊息會傳出多點傳送端點，而在 UDP 多點傳送位址上接聽的服務，則會回應該探索路由器。 探索路由器會收集回應，並將其傳送回用戶端。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 建置範例。  
  
2. 執行 DiscoveryRouter 可執行檔。  
  
3. 從組建目錄執行服務的可執行檔。  
  
4. 執行用戶端可執行檔。 請注意，用戶端會尋找服務。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
