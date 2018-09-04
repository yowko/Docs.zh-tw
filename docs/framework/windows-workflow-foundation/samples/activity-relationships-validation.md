---
title: 活動關聯性驗證
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: 50f08118fb5ad4d9b8fe809e7ab3cc5d57f28149
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556160"
---
# <a name="activity-relationships-validation"></a>活動關聯性驗證
這個範例包含三個活動：`CreateCity`、`CreateState` 和 `CreateCountry`。 `CreateCity` 必須在 `CreateState` 活動內部，而 `CreateState` 必須在 `CreateCountry` 活動內部。 基於此範例的目的，`CreateState` 活動的驗證邏輯為程式碼形式，而 `CreateCity` 活動的驗證邏輯為 XAML 形式。 這兩個條件約束有相同的行為。  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 提供下列三個協助程式活動，可讓開發人員驗證活動之間的關聯性：  
  
 <xref:System.Activities.Validation.GetParentChain>  
 提供屬於目前節點父系之所有活動的集合  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 提供屬於目前節點子樹狀結構所有活動的集合，但排除目前節點  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 提供和目前節點位於相同樹狀結構之所有活動的集合  
  
 在此範例中，<xref:System.Activities.Statements.ForEach%601> 活動是用來逐一查核 <xref:System.Activities.Validation.GetParentChain> 所傳回的集合。 針對集合中的每個元素，其類型會與 `CreateCountry` 比較 (如果是驗證 `CreateState`，則為 `CreateCity`)，如果找到相符元素，結果旗標會設為 `true`。 最後，如果結果旗標設為 <xref:System.Activities.Validation.AssertValidation>，`false` 會用來產生驗證錯誤。  
  
### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ContainmentValidation.sln 範例方案。  
  
2.  建置方案。  
  
3.  按 CTRL+F5 啟動程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
