---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。  
  
 \<系統。ServiceModel >  
\<診斷 >  
\<endToEndTracing >  
  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`activityTracing`|布林值，指定是否啟用活動追蹤。|  
|`messageFlowTracing`|布林值，指定是否啟用訊息流程追蹤。|  
|`propagateActivity`|布林值，指定傳播屬性是否設為 true。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<診斷 >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|為系統管理員定義執行階段檢查和控制的 WCF 設定。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [端對端追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
