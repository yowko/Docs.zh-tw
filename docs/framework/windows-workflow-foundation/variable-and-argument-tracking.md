---
title: 變數及引數追蹤
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 4e59a6838d93a57302f0c894445ab9da5d4252ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625207"
---
# <a name="variable-and-argument-tracking"></a>變數及引數追蹤
追蹤工作流程的執行時，擷取資料通常很實用。 它可在存取追蹤記錄後期執行時，提供額外的內容。 在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中，您可以在使用追蹤的工作流程中的任何活動範圍內擷取任何可見的變數或引數。 追蹤設定檔讓擷取資料變得非常容易。  
  
## <a name="variables-and-arguments"></a>變數與引數  
 變數和引數的擷取會在活動發出 ActivityStateRecord 時進行。  如果變數在活動的範圍內，則僅供擷取使用。 要在活動內擷取的變數會以下列方式指定：  
  
-   如果以變數名稱指定變數，則追蹤會在目前所追蹤的活動及父活動內尋找該變數。 追蹤會在目前活動範圍及父範圍中搜尋變數。  
  
-   如果要擷取的變數會指定利用名稱 ="*"，則會擷取目前追蹤之活動內的所有變數。 在此情況下，則不會擷取在範圍內但未在父活動中定義的變數。  
  
 擷取引數時，會根據活動的狀態擷取引數。 當活動的狀態是 Executing 時，則只有 `InArguments` 可供擷取。 若為其他任何活動狀態 (Closed、Faulted、Canceled)，則 InArgument 和 OutArgument 皆可供擷取。  
  
 下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。 變數和引數只能使用 <xref:System.Activities.Tracking.ActivityStateRecord> 擷取，因此可在追蹤設定檔中使用 <xref:System.Activities.Tracking.ActivityStateQuery> 訂閱。  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>保護變數和引數中所儲存的資訊  
 WF 執行階段預設會顯示所追蹤的變數或引數。 工作流程開發人員可以採取以下步驟，保護變數或引數不受存取：  
  
1.  加密變數的值。  
  
2.  控制追蹤設定檔的撰寫，以防止擷取變數或引數。  
  
3.  若為自訂追蹤參與者，請確定 WF 程式碼不會公開儲存在變數或引數中的機密資訊。  
  
## <a name="see-also"></a>另請參閱
- [Windows Server App Fabric 監控](https://go.microsoft.com/fwlink/?LinkId=201273)
- [使用 App Fabric 監控應用程式](https://go.microsoft.com/fwlink/?LinkId=201275)
