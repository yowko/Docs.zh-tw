---
title: '&lt;逾時&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148327"
---
# <a name="lttimeoutsgt"></a>&lt;逾時&gt;
表示組態項目，指定允許服務主機開啟或關閉的時間間隔。  
  
 \<system.ServiceModel>  
\<用戶端 >  
\<端點 >  
\<主控件 >  
\<逾時 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。|  
|`openTimeout`|<xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<主控件 >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|指定服務主機設定的組態項目。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)
