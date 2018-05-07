---
title: 基本驗證
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: db7db339d0b7bfd756d8ba22fb8488b8f7ecfa3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="basic-validation"></a>基本驗證
這個範例包含 `CreateProduct` 活動，會驗證其 `Cost` 引數小於或等於其 `Price` 引數。  
  
## <a name="sample-details"></a>範例詳細資料  
 有兩個作者會使用驗證：建立活動驗證邏輯的活動作者，以及在特定工作流程上呼叫驗證服務的工作流程作者。 在這個案例中，活動作者想要強制每個活動執行個體的成本必須小於或等於價格。  
  
 活動作者 (在活動中) 必須：  
  
-   建立條件約束 (`PriceGreaterThanCost`)。 這是所有驗證邏輯的所在位置。  
  
-   覆寫 `System.Activities.CodeActivity.OnGetConstraints()`，並將條件約束 (`PriceGreaterThanCost`) 加入至條件約束 <xref:System.Collections.IList>。  
  
 工作流程作者 (主程式) 必須：  
  
-   建立具有要驗證之活動執行個體 (`CreateProduct`) 的工作流程。  
  
-   呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，傳回 <xref:System.Activities.Validation.ValidationResults> 的 <xref:System.Activities.Validation.ValidationError> 集合。  
  
-   (選擇性) 列印 <xref:System.Activities.Validation.ValidationError> 物件。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 BasicValidation.sln 範例方案。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`