---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151841"
---
# <a name="workflowidle"></a>\<工作流 空閒>
這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務行為>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<工作流 空閒>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|timeToPersist|Timespan 值，可指定在工作流程進入閒置狀態以及保存之間的持續期間。 預設值為 TimeSpan.MaxValue。<br /><br /> 持續期間會開始在工作流程執行個體閒置時開始消逝。 如果您想要透過盡可能延長將該執行個體保留在記憶體的時間，更積極地保存工作流程執行個體，這個屬性就非常實用。 僅當此屬性的值小於**timeToUnload**屬性時，此屬性才有效。 如果此屬性的值較大，則會忽略此屬性。 如果此屬性在**timeToUnload**屬性指定的值之前經過，則在卸載工作流之前必須完成持久性。 也就是說，卸載作業可能會延遲到保存工作流程之後。 保存層負責處理重試暫時性錯誤，而且只會針對無法復原的錯誤擲回例外狀況。 因此，在保存期間擲回的所有例外狀況都會視為嚴重例外狀況，並且會中止工作流程執行個體。|  
|timeToUnload|Timespan 值，可指定在工作流程進入閒置狀態以及卸載之間的持續期間。 預設值為 1 分鐘。<br /><br /> 卸載工作流程表示會同時保存該工作流程。 如果將這個屬性設定為零，則會在工作流程閒置之後，立刻保留及卸載工作流程執行個體。 將這個屬性設定為 TimeSpan.MaxValue 可有效地停用卸載作業。 閒置的工作流程執行個體永遠不會卸載。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<服務行為行為\<>>](behavior-of-servicebehaviors-of-workflow.md)|指定行為項目。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
