---
title: 在查詢中使用附註
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 3dd5d19cc303314386ae62ba67f7eec978f6d80b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185362"
---
# <a name="using-annotation-in-queries"></a>在查詢中使用附註

附註可讓您使用值任意標記追蹤記錄，該值可在建置階段後設定。 例如，您可能想要將數個工作流程的追蹤記錄標記為「郵件伺服器」 = = 「郵件 Server1」。 當您稍後查詢追蹤記錄時，就可以更輕鬆地找到所有具有這個標記的記錄。  
  
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
> 這些追蹤查詢項目可用來建立追蹤設定檔。 追蹤設定檔可在組態中建立，或是使用程式碼建立。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [工作流程追蹤與追查](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
