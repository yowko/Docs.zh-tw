---
title: '&lt;faultPropagationQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58196baafe92cd34986acbfae9e44ade3212cb33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationqueriesgt"></a>&lt;faultPropagationQueries&gt;
代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。  每當 FaultHandler 處理錯誤時，都會發生這個事件。 您應該使用這種查詢來追蹤活動中發生的錯誤處理。 追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。  
  
 如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
\<system.serviceModel >  
\<追蹤 >  
\<trackingProfile >  
\<工作流程 >  
\<faultPropagationQueries >  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<faultPropagationQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|用來追蹤活動中發生之錯誤處理的查詢。  每當 FaultHandler 處理錯誤時，都會發生這個事件。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<工作流程 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|包含所有的查詢所識別的特定工作流程的組態項目**activityDefinitionId**屬性。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [工作流程追蹤及追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
