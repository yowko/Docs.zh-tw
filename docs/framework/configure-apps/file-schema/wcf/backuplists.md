---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 6e44dbe3c0966c6d243db343b9f9b0dec2480cb1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134442"
---
# <a name="backuplists"></a>\<backupLists>
代表組態區段，用於定義錯誤處理中使用的一組備份服務。 每個子項目是備份清單會列舉一組您希望路由服務在無法找到主要端點時使用的端點。 如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。  如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。  
  
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
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|包含一份您希望路由服務在無法找到主要端點時使用的端點。 。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>評估內送訊息，以及路由資料表定義目標端點時要使用將訊息傳送至篩選條件的比對。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
