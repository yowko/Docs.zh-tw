---
title: '&lt;bufferReceive&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 07d5b66b14d9495808f972734cdce4476efaefde
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766832"
---
# <a name="ltbufferreceivegt"></a>&lt;bufferReceive&gt;
讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。  
  
\<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<bufferReceive >  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|maxPendingMessagesPerChannel|整數，可指定每個通道允許的暫止訊息數目上限。 預設值為 512。 這個屬性會限制工作流程服務所能接收的失序訊息數目。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 > 的\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|指定行為項目。|  
  
## <a name="see-also"></a>另請參閱  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
