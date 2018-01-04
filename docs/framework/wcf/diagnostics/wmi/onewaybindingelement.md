---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>方法  
 OneWayBindingElement 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 OneWayBindingElement 類別具有下列屬性：  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 資料型別：ChannelPoolSettings  
  
 存取類型：唯讀  
  
 通道集區設定。  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 已接受之通道的數目上限。  
  
### <a name="packetroutable"></a>PacketRoutable  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表封包是否為可路由傳送的值。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
