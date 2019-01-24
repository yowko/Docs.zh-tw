---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 9d9eb45090367fb2cc18fc357c219e74d63fb667
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628093"
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。  
  
\<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<workflowIdle>  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|timeToPersist|Timespan 值，指定工作流程變成閒置，且會保存的時間之間的持續時間。 預設值為 TimeSpan.MaxValue。<br /><br /> 持續期間會開始在工作流程執行個體閒置時開始消逝。 這個屬性是很有用，如果您想要更積極地保存工作流程執行個體，同時仍保留在記憶體中的 盡可能長時間的執行個體。 這個屬性才有效，如果其值為小於**timeToUnload**屬性。 如果此屬性的值較大，則會忽略此屬性。 如果這個屬性所指定的值之前要經過**timeToUnload**屬性持續性必須先完成工作流程已卸載。 也就是說，卸載作業可能會延遲到保存工作流程之後。 保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。 因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。|  
|timeToUnload|Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。 預設值為 1 分鐘。<br /><br /> 卸載工作流程表示會同時保存該工作流程。 如果這個屬性設定為零的工作流程執行個體保留及卸載之後立即工作流程變成閒置狀態。 將此屬性設定為 timespan.maxvalue 可有效地停用卸載作業。 閒置的工作流程執行個體永遠不會卸載。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 > 的\<v >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|指定行為項目。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
