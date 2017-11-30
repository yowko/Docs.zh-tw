---
title: "使用唯一的接聽 URI 模式探索服務範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48b49def3f8f009eeb4ffa0204e9c616b5acfec7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>使用唯一的接聽 URI 模式探索服務範例
此範例示範如何探索其 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> 屬性設定為 <xref:System.ServiceModel.Description.ListenUriMode.Unique> 的服務。 當 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> 屬性設定為 <xref:System.ServiceModel.Description.ListenUriMode.Unique> 時，透過將連接埠設定成唯一的，或者透過附加 GUID 讓路徑變成唯一的，來確保 ListenUri 是唯一的。  
  
### <a name="features-on-the-service"></a>服務的功能  
 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> 屬性會針對 TCP 端點設定為 <xref:System.ServiceModel.Description.ListenUriMode.Unique>。 接著，服務就可以透過 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 端點搜尋。  
  
### <a name="features-on-the-client"></a>用戶端的功能  
 此用戶端會使用正確的 `Via.Uri`，透過 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法連接至服務。 接著，系統會查詢從方法傳回的 <xref:System.ServiceModel.Discovery.FindResponse> 是否包含有效的 <xref:System.ServiceModel.Endpoint.ListenUri%2A>，以及是否不同於 `Address.Uri`。 然後，系統會將適當的資訊傳遞到 `InvokeCalculatorService` 方法。 在 `InvokeCalculatorService` 方法中，呼叫者會傳入 <xref:System.ServiceModel.Endpoint.ListenUri%2A>，然後將具有正確 `ClientViaBehavior` 的 `Via.Uri` 加入至用戶端的端點中。  
  
##### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 UniqueListenUriMode.sln。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  執行服務應用程式，這通常在 [方案基底目錄]\service\bin\debug 資料夾下產生。  
  
4.  執行用戶端應用程式，這通常在 [方案基底目錄]\Client\bin\debug 資料夾下產生。  
  
     用戶端會尋找執行中的服務，並寫入到服務端點所發行的主控台中繼資料。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>另請參閱
