---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397542"
---
# <a name="workflowidle"></a>\<workflowIdle>
這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowIdle >**  
  
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
|timeToPersist|Timespan 值，指定工作流程閒置和保存之間的持續時間。 預設值為 Timespan.zero。<br /><br /> 持續期間會開始在工作流程執行個體閒置時開始消逝。 如果您想要更積極地保存工作流程實例，但仍將實例保持在記憶體中最長的時間，這個屬性就很有用。 只有在其值小於**timeToUnload**屬性時，這個屬性才有效。 如果此屬性的值較大，則會忽略此屬性。 如果此屬性在**timeToUnload**屬性所指定的值之前過期，則持續性必須在卸載工作流程之前完成。 也就是說，卸載作業可能會延遲到保存工作流程之後。 保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。 因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。|  
|timeToUnload|Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。 預設值為 1 分鐘。<br /><br /> 卸載工作流程表示會同時保存該工作流程。 如果此屬性設定為零，則會在工作流程變成閒置之後，立即保存工作流程實例並將其卸載。 將此屬性設定為 TimeSpan，會有效地停用卸載作業。 閒置的工作流程執行個體永遠不會卸載。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceBehaviors > 的\<行為 >](behavior-of-servicebehaviors-of-workflow.md)|指定行為項目。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
