---
title: 外部活動驗證
ms.date: 03/30/2017
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
ms.openlocfilehash: 1ceb1d2b2f7e8926479fa4c53cfb82a5cdb3a83f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517796"
---
# <a name="external-activity-validation"></a>外部活動驗證
這個範例示範如何將驗證邏輯加入至不是您撰寫的內建活動。 驗證邏輯包含強制工作流程中的所有 <xref:System.Activities.Statements.If> 活動應設定 <xref:System.Activities.Statements.If.Then%2A> 屬性或 <xref:System.Activities.Statements.If.Else%2A> 屬性。 此外，驗證邏輯也包含檢查工作流程中的所有 <xref:System.Activities.Statements.Pick> 活動都有一個以上的分支，否則會產生警告。  
  
## <a name="sample-details"></a>範例詳細資料  
 這個範例會建立工作流程，其中每個活動執行個體都要驗證：<xref:System.Activities.Statements.If> 活動和 <xref:System.Activities.Statements.Pick> 活動。 每個驗證行為都會建立 <xref:System.Activities.Validation.Constraint>。 在這個範例中建立的條件約束是 `ConstraintError_IfShouldHaveThenOrElse` 和 `ConstraintWarning_PickHasOneBranch`。 接著，將這些條件約束加入至 `AdditionalConstraints` 執行個體的 <xref:System.Activities.Validation.ValidationSettings> 集合。 最後，呼叫 `static` 的 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A><xref:System.Activities.Validation.ActivityValidationServices> 方法，以驗證工作流程中的活動，並將驗證結果印出至主控台。  
  
> [!NOTE]
>  您可以將原則條件約束加入至任何活動。 例如，您可以將原則條件約束加入至 <xref:System.Activities.Statements.Sequence> 或 <xref:System.Activities.Statements.Parallel> 活動。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ExternalActivityValidation.sln 檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行方案，請按下 Ctrl + F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`