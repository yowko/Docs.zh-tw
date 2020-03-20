---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151906"
---
# <a name="tracking"></a>\<跟蹤>
代表定義工作流程服務之追蹤設定的組態區段。  
  
 有關工作流跟蹤及其配置的詳細資訊，請參閱工作流[的工作流跟蹤和跟蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)和[配置跟蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<跟蹤>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<參與者>](participants.md)|組態項目的集合，這些項目會定義訂閱追蹤記錄的參與者。 追蹤參與者包含處理來自追蹤記錄之裝載的邏輯 (例如，他們可以選擇寫入檔案)。|  
|[\<跟蹤設定檔>](trackingprofile.md)|篩選工作流程執行個體發出之追蹤記錄的追蹤設定檔。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|system.ServiceModel|所有工作流程組態項目的根項目。|  
  
## <a name="remarks"></a>備註  
 追蹤可提供您檢查工作流程執行的能力。 工作流程追蹤基礎結構會檢測工作流程，在執行期間發出記錄以反映重要事件。 例如，工作流程執行個體開始或完成時會發出追蹤記錄。 追蹤也可以擷取與工作流程變數相關聯的商務相關資料。 例如，如果工作流程代表訂單處理系統，則訂單識別碼可與追蹤記錄一併擷取。 一般而言，啟用 WF 追蹤有助於對工作流程的執行進行診斷或業務分析。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [工作流程追蹤及追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
