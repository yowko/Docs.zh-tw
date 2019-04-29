---
title: 工作流程追蹤與追查
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: dbc5c0b51024c7b88b8c6cd9a052addd74e6f7e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669405"
---
# <a name="workflow-tracking-and-tracing"></a>工作流程追蹤與追查
Windows 工作流程追蹤是專為提供工作流程可見性而設計的 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 功能。 它提供追蹤基礎架構，可追蹤工作流程執行個體的執行。 WF 追蹤基礎結構會透明化地檢測工作流程，在執行期間發出記錄以反映重要事件。 根據預設，任何 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程都可使用這個功能。 不需要對 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 工作流程做任何變更，即可進行追蹤。 只需決定您想接收多少追蹤資料即可。 當工作流程執行個體開始或完成時，會發出處理的追蹤記錄。 追蹤也可以擷取與工作流程變數相關聯的商務相關資料。 例如，如果工作流程代表訂單處理系統，則訂單識別碼可與 <xref:System.Activities.Tracking.TrackingRecord> 物件一併擷取。 一般而言，啟用 WF 追蹤有助於對從執行工作流程而存取的資料進行診斷或業務分析。  
  
 這些追蹤元件等同於 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 中的追蹤服務。 在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中已改善效能，且已為 WF 追蹤功能簡化程式設計的模型。 追蹤執行階段會檢測工作流程執行個體，以發出與工作流程生命週期相關的事件、工作流程活動和自訂事件。  
  
 Windows Server App Fabric 還提供可監視 WCF 和工作流程服務執行的功能。 如需詳細資訊，請參閱 < [Windows Server App Fabric 監控](https://go.microsoft.com/fwlink/?LinkId=201273)和[使用 Windows Server AppFabric 監視應用程式](https://go.microsoft.com/fwlink/?LinkId=201287)  
  
 若要針對工作流程執行階段進行疑難排解，您可開啟診斷工作流程追蹤。 如需詳細資訊，請參閱 <<c0> [ 工作流程追蹤](workflow-tracing.md)。  
  
 若要了解程式設計的模型，本主題已針對追蹤基礎結構的主要元件進行討論：  
  
- 從工作流程執行階段發出的 <xref:System.Activities.Tracking.TrackingRecord> 物件。 如需詳細資訊，請參閱 <<c0> [ 追蹤記錄](tracking-records.md)。  
  
- 訂閱 <xref:System.Activities.Tracking.TrackingParticipant> 物件的 <xref:System.Activities.Tracking.TrackingRecord> 物件。 追蹤參與者包含處理來自 <xref:System.Activities.Tracking.TrackingRecord> 物件之裝載的邏輯 (例如，他們可以選擇寫入檔案)。 如需詳細資訊，請參閱 <<c0> [ 追蹤參與者](tracking-participants.md)。  
  
- 從工作流程執行個體發出的 <xref:System.Activities.Tracking.TrackingProfile> 物件篩選追蹤記錄。 如需詳細資訊，請參閱 <<c0> [ 追蹤設定檔](tracking-profiles.md)。  
  
## <a name="workflow-tracking-infrastructure"></a>工作流程追蹤基礎結構  
 工作流程追蹤基礎結構會依照發行與訂閱的範例。 工作流程執行個體是追蹤記錄的發行者，而追蹤記錄的訂閱者則是註冊為工作流程的延伸。 訂閱 <xref:System.Activities.Tracking.TrackingRecord> 物件的這些延伸稱為追蹤參與者。 追蹤參與者是可延伸點，可存取 <xref:System.Activities.Tracking.TrackingRecord> 物件，並以編寫它們的任何方式進行處理。 追蹤基礎結構可讓應用程式篩選外送的追蹤記錄，讓參與者訂閱記錄的子集。 這個篩選機制是透過追蹤設定檔來完成。  
  
 追蹤基礎結構的高層級檢視是由下列圖所示：  
  
 ![如果螢幕擷取畫面顯示工作流程追蹤基礎結構。](./media/workflow-tracking-and-tracing/workflow-tracking-infrastructure.gif "WV")  
  
## <a name="in-this-section"></a>本節內容  
 [追蹤記錄](tracking-records.md)  
 描述工作流程執行階段發出的追蹤記錄。  
  
 [追蹤設定檔](tracking-profiles.md)  
 討論如何使用追蹤設定檔。  
  
 [追蹤參與者](tracking-participants.md)  
 描述如何使用系統提供的追蹤參與者，或如何建立自訂追蹤參與者。  
  
 [設定工作流程的追蹤](configuring-tracking-for-a-workflow.md)  
 描述如何配置工作流程的追蹤。  
  
 [工作流程追蹤](workflow-tracing.md)  
 描述兩種啟用工作流程偵錯追蹤的方式。  
  
## <a name="see-also"></a>另請參閱

- [SQL 追蹤](./samples/sql-tracking.md)
