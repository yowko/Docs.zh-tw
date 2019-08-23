---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fd0b57d7d08cf77ba7792e079b7abd2ff8f2839e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947399"
---
# <a name="states"></a>\<狀態 >
表示建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態集合。  
  
 如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<追蹤 >  
\<trackingProfile>  
\<工作流程 >  
\<workflowInstanceQueries>  
\<workflowInstanceQuery>  
\<狀態 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<state>](states.md)|建立追蹤記錄時，追蹤的工作流程執行個體中的訂閱狀態。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|追蹤工作流程執行個體生命週期變更的查詢，例如已開始或已完成的事件。|  
  
## <a name="remarks"></a>備註  
 按照此集合中的狀態篩選傳回的記錄。  
  
 下表說明可能的狀態值。  
  
|State|描述|  
|-----------|-----------------|  
|已中止|工作流程執行個體已中止。|  
|已完成|工作流程執行個體已完成。|  
|Deleted|工作流程執行個體已刪除。|  
|閒置|工作流程執行個體閒置中。|  
|已保存|工作流程執行個體已保存。|  
|已繼續|工作流程執行個體已繼續。|  
|自|工作流程執行個體已啟動。|  
|未處理的例外狀況|工作流程執行個體發生未處理的例外狀況。|  
|已卸載|工作流程執行個體已卸載。|  
|已取消|工作流程執行個體已取消。|  
|擱置|工作流程執行個體已暫停。|  
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

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [工作流程追蹤及追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
