---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769264"
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
 資料類型：ChannelPoolSettings  
  
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

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
