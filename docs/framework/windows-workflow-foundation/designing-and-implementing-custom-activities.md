---
title: 設計和實作自訂活動
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 61a5de5a15835c728c18c0136952cf7ffdbaf000
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945843"
---
# <a name="designing-and-implementing-custom-activities"></a>設計和實作自訂活動
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中的自訂活動建立方法，是將系統提供的活動組合到複合活動中，或是建立衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 或 <xref:System.Activities.NativeActivity> 的新型別。 本節描述如何以上述兩種方法建立自訂活動。  
  
> [!IMPORTANT]
>  在工作流程設計工具中，自訂活動預設會顯示成附有活動名稱的簡單矩形。 若要在工作流程設計工具中提供自訂的視覺化活動表示形式，您還必須建立自訂的設計工具。 如需詳細資訊，請參閱 <<c0> [ 使用的自訂活動設計工具和範本](using-custom-activity-designers-and-templates.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [活動撰寫選項](activity-authoring-options-in-wf.md)  
 討論 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 中可用的撰寫樣式。  
  
 [使用自訂活動](using-a-custom-activity.md)  
 說明如何將自訂活動加入至工作流程專案。  
  
  [建立非同步活動](creating-asynchronous-activities-in-wf.md)  
 說明如何建立非同步活動。  
  
 [設定活動驗證](configuring-activity-validation.md)  
 說明如何使用活動驗證，在執行活動之前識別及報告活動組態中的錯誤。  
  
 [於執行階段建立活動](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 討論如何在執行階段使用 <xref:System.Activities.DynamicActivity> 建立活動。  
  
 [工作流程執行屬性](workflow-execution-properties.md)  
 說明如何使用工作流程執行屬性，將內容特定屬性加入至活動的環境中  
  
 [使用活動委派](using-activity-delegates.md)  
 討論如何編寫和使用包含活動委派的活動。
  
 [使用活動延伸模組](using-activity-extensions.md)  
 說明如何編寫和使用活動延伸模組。  
  
 [從工作流程使用 OData 摘要](consuming-odata-feeds-from-a-workflow.md)  
 說明從工作流程中呼叫 WCF 資料服務的幾種方法。  
  
 [活動定義範圍與可見度](activity-definition-scoping-and-visibility.md)  
 說明定義資料範圍和活動成員可視性的選項及規則。
