---
title: "自訂通道發送器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5814850b3d5a25f5f3c118e732930168f9489d9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="custom-channel-dispatcher"></a>自訂通道發送器
此範例示範如何使用自訂的方式，直接實作 <xref:System.ServiceModel.ServiceHostBase> 來建立通道堆疊，以及如何在 Web 主機環境中建立自訂通道發送器。 通道發送器會與 <xref:System.ServiceModel.Channels.IChannelListener> 互動，以接受通道並擷取來自通道堆疊的訊息。 此範例也提供基本範例，示範如何在 Web 主機環境中使用 <xref:System.ServiceModel.Activation.VirtualPathExtension> 建立通道堆疊。  
  
## <a name="custom-servicehostbase"></a>自訂 ServiceHostBase  
 此範例實作基底類型 <xref:System.ServiceModel.ServiceHostBase> (而非 <xref:System.ServiceModel.ServiceHost>) 來示範如何使用通道堆疊頂端的自訂訊息處理層取代 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 堆疊實作。 您要覆寫虛擬方法 <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> 才能建立通道接聽項和通道發送器。  
  
 若要實作 Web 裝載的服務，請從 <xref:System.ServiceModel.Activation.VirtualPathExtension> 集合取得服務延伸 <xref:System.ServiceModel.ServiceHostBase.Extensions%2A>，並將其加入至 <xref:System.ServiceModel.Channels.BindingParameterCollection>，讓傳輸層知道如何根據裝載環境設定 (亦即，Internet Information Services (IIS)/Windows Process Activation Service (WAS) 設定) 來設定通道接聽項。  
  
## <a name="custom-channel-dispatcher"></a>自訂通道發送器  
 自訂通道發送器會延伸 <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase> 類型。 此類型會實作通道層的程式設計邏輯。 在此範例中，要求-回覆訊息交換模式只支援 <xref:System.ServiceModel.Channels.IReplyChannel>，但自訂通道發送器可以輕易地延伸到其他通道類型。  
  
 發送器會先開啟通道接聽項，然後接受單一回覆通道。 它會利用通道，開始以無限迴圈傳送訊息 (要求)。 針對每個要求，它都會建立一個回覆訊息，並將其傳回用戶端。  
  
## <a name="creating-a-response-message"></a>建立回應訊息  
 訊息處理是以 `MyServiceManager` 類型實作。 在 `HandleRequest` 方法中，會先檢查訊息的 `Action` 標頭，以查看是否支援要求。 系統會定義預先定義的 SOAP 動作 "http://tempuri.org/HelloWorld/Hello" 來提供訊息篩選。 這類似於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之 <xref:System.ServiceModel.ServiceHost> 實作中的服務合約概念。  
  
 若是正確的 SOAP 動作案例，此範例會擷取要求的訊息資料，並針對要求產生類似於 <xref:System.ServiceModel.ServiceHost> 案例中看到的對應回應。  
  
 在此情況下，您要透過傳回自訂 HTML 訊息來明確地處理 HTTP-GET 動詞命令，讓您可以從瀏覽器瀏覽服務，以查看它是否正確編譯。 如果 SOAP 動作不相符，請傳回錯誤訊息以指出此要求不受到支援。  
  
 此範例的用戶端是一個標準的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，不會假定來自服務的任何事項。 因此，此服務是特別針對符合您從一般 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.ServiceHost> 實作所取得的項目而設計。 所以，在用戶端上只需要一個服務合約。  
  
## <a name="using-the-sample"></a>使用範例  
 執行用戶端應用程式會直接產生下列輸出。  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 您也可以從瀏覽器瀏覽服務，讓 HTTP-GET 訊息在伺服器上繼續執行。 如此會回覆您正確格式的 HTML 文字。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
