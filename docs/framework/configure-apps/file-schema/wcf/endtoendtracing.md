---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919006"
---
# <a name="endtoendtracing"></a>\<endToEndTracing>
組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。  
  
 \<system.ServiceModel>  
\<診斷 >  
\<endToEndTracing>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`activityTracing`|布林值，指定是否啟用活動追蹤。|  
|`messageFlowTracing`|布林值，指定是否啟用訊息流程追蹤。|  
|`propagateActivity`|布林值，指定傳播屬性是否設為 true。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|為系統管理員定義執行階段檢查和控制的 WCF 設定。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [端對端追蹤](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
