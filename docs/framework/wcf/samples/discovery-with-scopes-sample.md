---
title: "探索範圍範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 184c4a5c31969ee060f72d937ab02af733340ca4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-with-scopes-sample"></a>探索範圍範例
此範例示範如何使用範圍分類可探索的端點，以及如何使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 執行端點的非同步搜尋。 在服務上，此範例會示範如何透過加入端點探索行為並使用該行為將範圍加入至端點，以及控制端點的可搜尋性來自訂每個端點的探索。 在用戶端上，此範例會檢查用戶端如何建立 <xref:System.ServiceModel.Discovery.DiscoveryClient> 並微調搜尋參數，以便透過將範圍加入至 <xref:System.ServiceModel.Discovery.FindCriteria> 來納入範圍。 此範例也會示範用戶端如何透過加入終止準則來限制回應。  
  
## <a name="service-features"></a>服務功能  
 此專案顯示要加入到 <xref:System.ServiceModel.ServiceHost> 的兩個服務端點。 每個端點都有一個相關聯的 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>。 此行為用來為兩個端點加入 URI 範圍。 範圍是用來區別每個端點，讓用戶端可以微調搜尋。 您可以針對第二個端點，將 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> 屬性設定為 `false` 來停用可搜尋性。 這可確保與此端點相關聯的探索中繼資料不會當做任何探索訊息的一部分傳送。  
  
## <a name="client-features"></a>用戶端功能  
 `FindCalculatorServiceAddress()` 方法會示範如何使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 並使用兩個限制傳入 <xref:System.ServiceModel.Discovery.FindCriteria>。 範圍會加入到準則中，而且 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 屬性會設定為 1。 此範圍會將結果限制為僅發行相同範圍的服務。 將 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 設定為 1 會限制 <xref:System.ServiceModel.Discovery.DiscoveryClient> 等待的回應，最多為 1 個端點。 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 呼叫是一種非同步作業，在達到逾時或找到某個端點之前，這個作業會封鎖執行緒。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  這個範例使用 HTTP 端點，若要執行這個範例，則必須加入正確的 URL ACL。 請參閱[設定 HTTP 和 HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊。 以更高的權限執行下列命令應該就能加入適當的 ACL。 如果命令未正確執行，您可能要將 Domain 和 Username 替換成下列引數：`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  建置方案。  
  
3.  從組建目錄執行服務的可執行檔。  
  
4.  執行用戶端可執行檔。 請注意，用戶端可以尋找服務。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a>另請參閱
