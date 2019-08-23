---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926440"
---
# <a name="backuplists"></a>\<backupLists>
代表組態區段，用於定義錯誤處理中使用的一組備份服務。 每個子專案都是一個備份清單, 它會列舉一組您希望路由服務在無法連上主要端點時使用的端點。 如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。  如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。  
  
 \<system.serviceModel>  
\<路由 >  
\<backupLists>  
  
## <a name="syntax"></a>語法  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filter>](filter.md)|包含您希望路由服務在無法連上主要端點時使用的端點清單。 .|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<routing>](routing.md)|表示定義一組路由篩選的設定區段, 其決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) 類型, 以及將目標端點定義為的路由表。當篩選準則相符時, 將訊息傳送至。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
