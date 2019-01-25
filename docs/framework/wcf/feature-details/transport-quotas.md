---
title: 傳輸配額
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: 0664dbb70df61c0f68d34c4ab364db6623805bfa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542765"
---
# <a name="transport-quotas"></a>傳輸配額
傳輸配額是用來判斷連線何時過度使用資源的原則機制。 配額是硬性限制，一旦超出配額值，就會無法使用其他資源。 傳輸配額能夠防範惡意或無意間發生的阻絕服務攻擊。  
  
 Windows Communication Foundation (WCF) 傳輸的保守的資源配置為基礎的預設配額值。 這些預設值適用於開發環境和小規模的安裝情況。 如果安裝時資源不足，或者不論是否有額外的資源，連線都會受到限制時，服務系統管理員就應該檢查傳輸配額，並且調整個別的配額值。  
  
## <a name="types-of-transport-quotas"></a>傳輸配額的類型  
 WCF 傳輸有三種配額類型：  
  
-   *逾時*降低阻絕服務攻擊依賴佔用資源一段時間。  
  
-   *記憶體配置限制*防止單一連線用盡系統記憶體和拒絕服務其他連線。  
  
-   *限制集合大小*繫結的間接配置記憶體或有限供應資源耗用量。  
  
## <a name="transport-quota-descriptions"></a>傳輸配額描述  
 本節說明適用於標準 WCF 傳輸的傳輸配額：HTTP (S)、 TCP/IP 和具名的管道。 自訂傳輸會公開未包含在下列清單的可設定配額。 如需自訂傳輸配額的詳細資訊，請參閱自訂傳輸的相關文件。  
  
 每個配額設定都各有型別、最小值和預設值。 配額的最大值受到其型別限制。 由於機器限制，不一定都能將配額設定為最大值。  
  
|名稱|類型|最小<br /><br /> value|預設<br /><br /> value|描述|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 次滴答聲|5 秒|初始讀取期間，等待連線傳送前序編碼 (Preamble) 的最長時間。 在發生驗證之前會接收到這項資料。 這個設定通常比 `ReceiveTimeout` 配額值小很多。|  
|`CloseTimeout`|TimeSpan|0|1 分鐘|在傳輸引發例外狀況之前，等待連線關閉的最長時間。|  
|`ConnectionBufferSize`|整數|1|8 KB|基礎傳輸的傳輸和接收緩衝區大小 (以位元組為單位)。 增加緩衝區大小，可以在傳送大型訊息時提高輸送量。|  
|`IdleTimeout`|TimeSpan|0|2 分鐘|共用連線關閉之前，可以保持在閒置狀態的最長時間。<br /><br /> 這個設定只適用於共用連線。|  
|`LeaseTimeout`|TimeSpan|0|5 分鐘|作用中共用連線的最長存留期。 當超過指定的時間後，一旦已服務目前要求，就會關閉連線。<br /><br /> 這個設定只適用於共用連線。|  
|`ListenBacklog`|整數|1|10|在拒絕端點的其他連線之前，接聽項尚未服務之連線的最大數目。|  
|`MaxBufferPoolSize`|Long|0|512 KB|傳輸專用於共用可重複使用之訊息緩衝區的最大記憶體 (以位元組為單位)。 當集區無法提供訊息緩衝區時，就會配置新緩衝區，暫時使用。<br /><br /> 建立許多通道處理站或接聽項的安裝，可以為緩衝集區配置大量記憶體。 減少這個緩衝區大小，在這個情況下會大幅降低記憶體使用量。|  
|`MaxBufferSize`|整數|1|64 KB|用於串流資料的最大緩衝區大小 (以位元組為單位)。 如果未設定這個傳輸配額，或者傳輸不是使用資料流，配額值就是 `MaxReceivedMessageSize` 配額值和 <xref:System.Int32.MaxValue> 兩者的較小值。|  
|`MaxOutboundConnectionsPerEndpoint`|整數|1|10|可與特定端點相關聯之傳出連線的最大數目。<br /><br /> 這個設定只適用於共用連線。|  
|`MaxOutputDelay`|TimeSpan|0|200 毫秒|等待傳送作業在單一作業中批次處理其他訊息的最長時間。 如果基礎傳輸的緩衝區已滿，就會提早傳送訊息。 傳送額外訊息並不會重設延遲期間。|  
|`MaxPendingAccepts`|整數|1|1|接聽項上等待通道接受的最大數目。<br /><br /> 在完成接受和啟動新接受之間有段時間間隔。 增加這個集合大小，可以防止這個間隔期間內進行連線的用戶端遭到捨棄。|  
|`MaxPendingConnections`|整數|1|10|接聽項上等待應用程式接受連線的最大數目。 當超過這個配額值時，新的傳入連線會被捨棄，而不是等待被接受。<br /><br /> 如訊息安全性等連線功能，可能會導致用戶端開啟一個以上的連線。 在設定這個配額值時，服務系統管理員應該考量到其他連線。|  
|`MaxReceivedMessageSize`|Long|1|64 KB|在傳輸引發例外狀況之前，已接收的訊息 (包括標頭) 大小上限 (以位元組為單位)。|  
|`OpenTimeout`|TimeSpan|0|1 分鐘|在傳輸引發例外狀況之前，等待建立連線的最長時間。|  
|`ReceiveTimeout`|TimeSpan|0|10 分鐘|在傳輸引發例外狀況之前，等待讀取作業完成的最長時間。|  
|`SendTimeout`|Timespan|0|1 分鐘|在傳輸引發例外狀況之前，等待寫入作業完成的最長時間。|  
  
 透過繫結或組態進行設定時，傳輸配額 `MaxPendingConnections` 和 `MaxOutboundConnectionsPerEndpoint` 會結合為一個名為 `MaxConnections` 的傳輸配額。 只有繫結項目才能允許個別設定這些配額值。 `MaxConnections` 傳輸配額具有相同的最小值和預設值。  
  
## <a name="setting-transport-quotas"></a>設定傳輸配額  
 傳輸配額可以透過傳輸繫結項目、傳輸繫結、應用程式組態或主機原則來設定。 本文件未涵蓋透過主應用程式原則來設定傳輸的內容。 如需探索主機原則配額設定的詳細資訊，請參閱基礎傳輸的相關文件。 [設定 HTTP 和 HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)主題說明 Http.sys 驅動程式的配額設定。 如需在 HTTP、TCP/IP 和具名管道連線上設定 Windows 限制的詳細資訊，請搜尋 Microsoft 知識庫。  
  
 其他類型的配額會間接套用至傳輸。 傳輸用來將訊息轉換為位元組的訊息編碼器，可以有自己的配額設定。 不過，這些配額與所要使用的傳輸類型無關。  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>從繫結項目控制傳輸配額  
 透過繫結項目來設定傳輸配額，可提供控制傳輸行為的最大彈性。 在建置通道時，會從繫結取得 Close、Open、Receive 和 Send 作業的預設逾時。  
  
|名稱|HTTP|TCP/IP|具名管道|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||X|X|  
|`CloseTimeout`||||  
|`ConnectionBufferSize`||X|X|  
|`IdleTimeout`||X|X|  
|`LeaseTimeout`||X||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|X|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||X|X|  
|`MaxOutputDelay`||X|X|  
|`MaxPendingAccepts`||X|X|  
|`MaxPendingConnections`||X|X|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`||||  
|`ReceiveTimeout`||||  
|`SendTimeout`||||  
  
### <a name="controlling-transport-quotas-from-the-binding"></a>從繫結控制傳輸配額  
 透過繫結來設定傳輸配額，會提供一組可從中選擇的簡化配額，同時仍會提供存取最常用的配額值。  
  
|名稱|HTTP|TCP/IP|具名管道|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|X|X|X|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|1|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`|X|X|X|  
|`ReceiveTimeout`|X|X|X|  
|`SendTimeout`|X|X|X|  
  
1.  `MaxBufferSize` 傳輸配額只適用於 `BasicHttp` 繫結。 `WSHttp` 繫結適用於不支援資料流傳輸模式的情況中。  
  
2.  傳輸配額 `MaxPendingConnections` 和 `MaxOutboundConnectionsPerEndpoint` 會結合為一個名為 `MaxConnections` 的傳輸配額。  
  
### <a name="controlling-transport-quotas-from-configuration"></a>從組態控制傳輸配額  
 應用程式組態可以像直接存取繫結上的屬性一樣，設定相同的傳輸配額。 在組態檔中，傳輸配額的名稱一律以小寫字母為開頭。 例如，繫結上的 `CloseTimeout` 屬性會對應至組態中的 `closeTimeout` 設定，而繫結上的 `MaxConnections` 屬性則會對應至組態中的 `maxConnections` 設定。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
