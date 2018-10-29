---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2e2e36486c3788cd714ffd0ed545fbb14f831476
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197037"
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>語法  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>方法  
 ReliableSessionBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ReliableSessionBindingElement 類別具有下列屬性：  
  
### <a name="acknowledgementinterval"></a>AcknowledgementInterval  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 目的地傳送確認到可靠通道 (由處理站所建立) 上的訊息來源之前等候的時間間隔。  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否已啟用流量控制的布林值。  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 指定將通道判定為失敗之前可允許另一個通訊方不傳送任何訊息的最長期間。  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可在接聽項上等候接受的通道數目上限。  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可靠通道透過在其基礎通道呼叫 `Send`，以嘗試重新傳輸尚未收到確認之訊息的最大次數。  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可靠工作階段的傳輸窗口大小上限。  
  
### <a name="ordered"></a>Ordered  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，指定是否保證訊息以傳送順序送達。  
  
### <a name="reliablemessagingversion"></a>ReliableMessagingVersion  
 資料型別：整數  
  
 存取類型：唯讀  
  
 指定用於可靠工作階段中 WS-ReliableMessaging 通訊協定版本的整數。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
