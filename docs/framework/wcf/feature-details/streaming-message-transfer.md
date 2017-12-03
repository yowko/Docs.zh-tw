---
title: "資料流訊息傳輸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ff5fbf570c826f5c430109d9f79b3d5f39382f6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="streaming-message-transfer"></a>資料流訊息傳輸
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 傳輸支援兩種傳輸訊息的模式：  
  
-   緩衝處理的傳輸會將整個訊息保留在記憶體緩衝區中，直到完成傳輸作業為止。 必須等到緩衝處理的訊息完全傳送出去後，接收者才能開始讀取。  
  
-   資料流處理的傳輸會將訊息公開為資料流。 在訊息完全傳送出去之前，接收者就可開始處理訊息。  
  
-   資料流處理的傳輸可以藉由消除大量記憶體緩衝區的需求來改善服務的延展性 (Scalability)。 變更傳輸模式是否能夠改善延展性，需視所傳輸的訊息大小而定。 大型訊息適合使用資料流處理傳輸方式來傳輸。  
  
 根據預設，HTTP、TCP/IP 和具名管道等傳輸都使用緩衝處理的傳輸方式。 本文件將說明如何從緩衝處理的傳輸模式切換到資料流處理的傳輸模式，以及這麼做將有何影響。  
  
## <a name="enabling-streamed-transfers"></a>啟用資料流處理的傳輸  
 在設定傳輸的繫結項目時，便已完成選取使用緩衝處理的傳輸模式還是資料流處理的傳輸模式。 繫結項目包含可設為 <xref:System.ServiceModel.TransferMode>、`Buffered`、`Streamed` 或 `StreamedRequest` 的 `StreamedResponse` 屬性。 將傳輸模式設為 `Streamed` 可啟用雙向資料流通訊。 將傳輸模式設為 `StreamedRequest` 或 `StreamedResponse` 只能啟用指定方向的資料流通訊。  
  
 <xref:System.ServiceModel.BasicHttpBinding>、<xref:System.ServiceModel.NetTcpBinding> 和 <xref:System.ServiceModel.NetNamedPipeBinding> 繫結會公開 <xref:System.ServiceModel.TransferMode> 屬性。 如果是其他傳輸模式，您必須建立自訂繫結才能設定傳輸模式。  
  
 使用緩衝或資料流傳輸是由端點處決定。 如果是 HTTP 傳輸模式，則傳輸模式不會在連線之間，或是在伺服器與其他媒介之間進行傳播。 設定傳輸模式不會反映在服務介面的描述中。 在產生服務的用戶端類別之後，您必須為搭配資料流傳輸使用的服務編輯其組態檔，以設定模式。 如果是 TCP 和具名管道傳輸，會傳播傳輸模式做為原則判斷提示。  
  
 如需程式碼範例，請參閱[How to： 啟用資料流](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)。  
  
## <a name="enabling-asynchronous-streaming"></a>啟用非同步資料流處理  
 若要啟用非同步資料流，請將 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> 端點行為加入至服務主機，並將其 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> 屬性設定為 `true`。  
  
 這個版本的 WCF 還加入了在傳送端進行真實非同步資料流處理的功能。 在將訊息串流至多個用戶端，但部分用戶端可能因為網路擁塞或完全不讀取而造成讀取速度緩慢的案例中，這項功能可以提升服務的延展性。 在這些案例中，WCF 不再針對用戶端封鎖服務上的個別執行緒。 這樣可確保服務可以處理更多的用戶端，從而提升服務的延展性。  
  
## <a name="restrictions-on-streamed-transfers"></a>資料流處理的傳輸限制  
 使用資料流處理的傳輸模式會導致執行階段強制執行其他限制。  
  
 在資料流處理的傳輸中發生的作業，會與最多一個輸入或輸出參數簽訂合約。 此參數會對應至整個訊息本文，而且必須是一個 <xref:System.ServiceModel.Channels.Message>、<xref:System.IO.Stream> 的衍生型別，或是 <xref:System.Xml.Serialization.IXmlSerializable> 實作。 擁有作業的傳回值，相當於擁有輸出參數。  
  
 某些 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 功能，例如可靠的訊息傳送、交易，與 SOAP 訊息層級安全性，都需仰賴緩衝處理的訊息來進行傳輸。 使用這些功能可能減少或消除使用資料流處理模式而獲得的效能優勢。 若要保護資料流處理傳輸的安全，請單純使用傳輸層級安全性，或是使用傳輸層級安全性加上僅限於驗證的訊息安全性。  
  
 SOAP 標頭一律經過緩衝處理，就算將傳輸模式設為資料流處理也是一樣。 訊息的標頭不得超出 `MaxBufferSize` 傳輸配額的大小。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]此設定，請參閱[傳輸配額](../../../../docs/framework/wcf/feature-details/transport-quotas.md)。  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>緩衝處理的傳輸與資料流處理的傳輸之間的差異  
 將傳輸模式由緩衝處理變更為資料流處理，會同時變更 TCP 與具名管道傳輸的原生通道類型。 對於緩衝處理的傳輸來說，原生的通道類型為 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>。 對於資料流處理的傳輸來說，原生通道為 <xref:System.ServiceModel.Channels.IRequestChannel> 和 <xref:System.ServiceModel.Channels.IReplyChannel>。 在直接使用這些傳輸 (亦即，並未透過服務合約) 的現有應用程式中變更傳輸模式，需要變更通道處理站與接聽項的預期通道類型。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 啟用資料流](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
