---
title: ConnectionOrientedTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42974d0f1de639370d6fac2346572758e1d19d46
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a>方法  
 ConnectionOrientedTransportBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ConnectionOrientedTransportBindingElement 類別有下列屬性：  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 指定在逾時之前必須完成通道初始化的時間範圍。  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 用於從用戶端或服務在網路上傳輸已序列化訊息之區塊的緩衝區大小。  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表主機名稱是否用於連線到服務的值 (當符合 URI 時)。  
  
### <a name="maxbuffersize"></a>MaxBufferSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 要使用之緩衝區的大小上限。  
  
### <a name="maxoutputdelay"></a>MaxOutputDelay  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。  
  
### <a name="maxpendingaccepts"></a>MaxPendingAccepts  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可用來處理服務之連入連線的擱置中非同步接受執行緒數目上限。  
  
### <a name="maxpendingconnections"></a>MaxPendingConnections  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 服務的擱置連線數目上限。  
  
### <a name="transfermode"></a>TransferMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定訊息是否使用連線導向傳輸進行緩衝或資料流處理的值。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
