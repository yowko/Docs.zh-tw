---
title: <trackingProfile> WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: 97a494e492fcdd298dd14fd989f00d972e815f85
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201404"
---
# <a name="trackingprofile-of-wcf"></a>\<trackingProfile> WCF

代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。 追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。 追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。  
  
如需工作流程追蹤及其設定的詳細資訊，請參閱[工作流程追蹤和追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
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
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|指定追蹤設定檔名稱的字串。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|包括特定工作流程之所有查詢的組態項目，這個工作流程可由 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> 屬性識別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|代表定義工作流程服務之追蹤設定的組態區段。|  
  
## <a name="remarks"></a>備註  

 追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。 根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。 反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。  
  
 追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。 有少數的查詢類型可讓您訂閱不同類別的 <xref:System.Activities.Tracking.TrackingRecord> 物件。 如需查詢的完整清單，請參閱 [\<participants>](../windows-workflow-foundation/participants.md) 和 [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。
  
下列範例顯示設定檔中的追蹤設定檔，可讓追蹤參與者訂閱 `Started` 和 `Completed` 工作流程事件。  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [工作流程追蹤與追查](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
