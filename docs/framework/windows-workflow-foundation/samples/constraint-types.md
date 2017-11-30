---
title: "Constraint 型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f78337ebc643b584b89f26ca39e400fb8e6e9c26
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="constraint-types"></a>Constraint 型別
這個範例示範兩種不同的方式將條件約束套用至工作流程：一個是從活動中 (建置)，另一個是從活動外部 (原則)。 在這個案例中，活動作者 (來自協力軟體廠商) 想要驗證兩個引數之間的關聯性。 在此情況下，成本應該小於或等於價格。 這是一般驗證建置條件約束。  
  
 接著店主想要在這個泛型活動中加入驗證。 在此情況下，他希望大部分產品等於或小於 $9.99。 因此，他在 `CreateProduct` 活動上使用原則條件約束。  
  
 在範例中：  
  
 活動作者 (建置) 必須：  
  
-   建立條件約束 (`PriceGreaterThanCost`)。 這是所有驗證邏輯的所在位置。  
  
-   覆寫 `System.Activities.CodeActivity.OnGetConstraints()`，並將條件約束 (`PriceGreaterThanCost`) 加入至條件約束 <xref:System.Collections.IList>。  
  
 工作流程作者 (原則) 必須：  
  
-   建立具有要驗證之活動執行個體 (`CreateProduct`) 的工作流程。  
  
-   建立條件約束 (`MaxPrice`)。  
  
-   建立 <xref:System.Activities.Validation.ValidationSettings> 執行個體 (`validationSettings`)，並將條件約束 (`MaxPrice`) 加入至集合 `AdditionalConstraints`。 在這裡工作流程作者可以將原則條件約束加入至任何活動，例如序列或平行活動。  
  
-   呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，傳回 <xref:System.Activities.Validation.ValidationResults> 物件的 <xref:System.Activities.Validation.ValidationError> 集合。  
  
-   (選擇性) 列印 <xref:System.Activities.Validation.ValidationError> 物件。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ConstraintTypes.sln 範例方案。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`  
  
## <a name="see-also"></a>另請參閱
