---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 4a3e45140765f99f4a30b77fc9d02b167601b50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591470"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>語法  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>方法  
 ChannelPoolSettings 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ChannelPoolSettings 類別具有下列屬性：  
  
### <a name="idletimeout"></a>IdleTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 連線中斷之前可閒置的最長時間。  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 逾時前可完成租用作業的最長時間。  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 每個端點的傳出通道數目上限。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
