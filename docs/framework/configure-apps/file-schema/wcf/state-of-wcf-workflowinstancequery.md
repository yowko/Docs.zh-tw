---
title: WCF 的 &lt;state&gt;、&lt;workflowInstanceQuery&gt;
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 69ebedec40243d3e6580b8350c1253fca83e0802
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754567"
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a>WCF 的 &lt;state&gt;、&lt;workflowInstanceQuery&gt;
表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。  
  
 如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<system.serviceModel>  
\<追蹤 >  
\<trackingProfile>  
\<工作流程 >  
\<workflowInstanceQueries>  
\<w >  
\<狀態 >  
\<狀態 >  
  
## <a name="syntax"></a>語法  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|字串，可指定建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。|  
  
## <a name="remarks"></a>備註  
 按照此集合中的狀態篩選傳回的記錄。  
  
 下表說明可能的狀態值。  
  
|狀態|描述|  
|-----------|-----------------|  
|已中止|工作流程執行個體已中止。|  
|已完成|工作流程執行個體已完成。|  
|Deleted|工作流程執行個體已刪除。|  
|閒置|工作流程執行個體閒置中。|  
|已保存|工作流程執行個體已保存。|  
|已繼續|工作流程執行個體已繼續。|  
|已啟動|工作流程執行個體已啟動。|  
|未處理的例外狀況|工作流程執行個體發生未處理的例外狀況。|  
|Unloaded|工作流程執行個體已卸載。|  
|已取消|工作流程執行個體已取消。|  
|暫停|工作流程執行個體已暫停。|  
|已終止|工作流程執行個體已終止。|  
|Unsuspended|工作流程執行個體已取消暫停。|  
  
## <a name="example"></a>範例  
 下列組態可使用這個查詢，訂閱 `Started` 執行個體狀態之工作流程執行個體層級的追蹤記錄。  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [工作流程追蹤及追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
