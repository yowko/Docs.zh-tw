---
title: 執行屬性
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748190"
---
# <a name="execution-properties"></a>執行屬性
這個範例示範如何使用定義及使用自訂活動中的執行屬性。 在這個範例中，執行屬性決定主控台的前景色彩。 範例工作流程將示範不同的執行邏輯路徑 (<xref:System.Activities.Statements.Parallel> 活動的分支) 如何在活動交錯執行 (跨 <xref:System.Activities.Statements.Parallel> 活動的分支) 的情況下維持不同的主控台色彩。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [ExecutionProperties.sln] 範例方案。  
  
    > [!NOTE]
    >  在建置方案之前檢視 ThreeColors.xaml 會顯示錯誤，因為使用的自訂活動必須與方案同時建置。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`