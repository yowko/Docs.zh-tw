---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50049291"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>語法  
  
```csharp
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
