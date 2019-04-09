---
title: 在查詢中使用附註
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: fd2d98852ca44e3485ddcf4be29d505b39011698
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208640"
---
# <a name="using-annotation-in-queries"></a>在查詢中使用附註
附註可讓您使用值任意標記追蹤記錄，該值可在建置階段後設定。 比方說，您可能會想數個追蹤記錄，跨多個工作流程，加上"Mail Server"= ="Mail Server1"。 當您稍後查詢追蹤記錄時，就可以更輕鬆地找到所有具有這個標記的記錄。  
  
## <a name="adding-annotations"></a>加入註解  
 註解可加入至追蹤查詢，如下列範例所示。  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
>  這些追蹤查詢項目可用來建立追蹤設定檔。 追蹤設定檔可在組態中建立，或是使用程式碼建立。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)
- [工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
