---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 572e458f08c4717207667db9940296c4a957199a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771763"
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>語法  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceThrottlingBehavior 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceThrottlingBehavior 類別具有下列屬性：  
  
### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 在 ServiceHost 中的所有發送器物件上主動處理的訊息數目上限。  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 一次可執行的服務物件數目上限。  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 主機一次可接受的工作階段數目上限。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
