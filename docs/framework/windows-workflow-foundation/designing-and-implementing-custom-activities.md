---
title: "設計和實作自訂活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9243761803bc8b68ce37b3d3ad310e8bb7f93d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-and-implementing-custom-activities"></a>設計和實作自訂活動
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中的自訂活動建立方法，是將系統提供的活動組合到複合活動中，或是建立衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 或 <xref:System.Activities.NativeActivity> 的新型別。 本節描述如何以上述兩種方法建立自訂活動。  
  
> [!IMPORTANT]
>  在工作流程設計工具中，自訂活動預設會顯示成附有活動名稱的簡單矩形。 若要在工作流程設計工具中提供自訂的視覺化活動表示形式，您還必須建立自訂的設計工具。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][使用自訂活動設計工具和範本](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [活動撰寫選項](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 討論 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中可用的撰寫樣式。  
  
 [使用自訂活動](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 說明如何將自訂活動加入至工作流程專案。  
  
  [建立非同步活動](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 說明如何建立非同步活動。  
  
 [設定活動驗證](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 說明如何使用活動驗證，在執行活動之前識別及報告活動組態中的錯誤。  
  
 [於執行階段建立活動](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 討論如何在執行階段使用 <xref:System.Activities.DynamicActivity> 建立活動。  
  
 [工作流程執行屬性](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 說明如何使用工作流程執行屬性，將內容特定屬性加入至活動的環境中  
  
 [使用活動委派](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 討論如何編寫和使用包含活動委派的活動。  
  
 [活動當地語系化](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 說明如何在活動中使用當地語系化的字串資源。  
  
 [使用活動延伸模組](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 說明如何編寫和使用活動延伸模組。  
  
 [從工作流程使用 OData 摘要](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 說明從工作流程中呼叫 WCF 資料服務的幾種方法。  
  
 [活動定義範圍與可見度](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 說明定義資料範圍和活動成員可視性的選項及規則。
