---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093512"
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings
TcpConnectionPoolSettings  
  
## <a name="syntax"></a>語法  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>方法  
 TcpConnectionPoolSettings 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 TcpConnectionPoolSettings 類別具有下列屬性：  
  
### <a name="groupname"></a>GroupName  
 資料型別：字串  
  
 存取類型：唯讀  
  
 繫結項目所使用之連線集區的群組名稱。  
  
### <a name="idletimeout"></a>IdleTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 連線中斷之前可閒置的最長時間。  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 逾時前可完成租用作業的最長時間。  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 每個端點的傳出連線數目上限。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
