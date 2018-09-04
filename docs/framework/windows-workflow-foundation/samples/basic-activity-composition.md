---
title: 基本活動撰寫
ms.date: 03/30/2017
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
ms.openlocfilehash: ade8187ca44a8182b55cf0f01e5bfe5a9a747255
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518372"
---
# <a name="basic-activity-composition"></a>基本活動撰寫
這個範例會示範如何撰寫自訂活動和系統提供的活動，以建置更多自訂活動。  
  
 使用調查活動的工作流程會以問題清單來排程調查，然後輸出收到的回覆。  
  
## <a name="sample-details"></a>範例詳細資料  
 此範例使用三個自訂活動。 `ReadLine` 是一項簡單<xref:System.Activities.NativeActivity>\<字串 > 會建立<xref:System.Activities.Bookmark>排程，然後設定時會`Return`<xref:System.Activities.OutArgument%601>值<xref:System.Activities.Bookmark>繼續。 `Prompt` 已<xref:System.Activities.Activity%601>\<字串 > 採用<xref:System.Activities.InArgument%601>< 字串\>名為`Text`並在回應中傳回使用者`Result` <xref:System.Activities.OutArgument%601>\<字串 >。 `Prompt` 活動會使用 .NET Framework 所隨附的 <xref:System.Activities.Statements.Sequence> 和 <xref:System.Activities.Statements.WriteLine> 活動，而且也會併入自訂 `ReadLine` 活動來取得使用者輸入。 上一個自訂活動是 `Survey` 活動。 很<xref:System.Activities.Activity>< ICollection\<字串 >>。  這個活動會採用<xref:System.Activities.InArgument%601>< IEnumerable < 字串\>> 具名`Questions`並於其中填入`Result`out 引數的回應。 `Survey` 活動會使用來自 .NET Framework 的 <xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.Sequence> 和 <xref:System.Activities.Statements.AddToCollection%601>，並利用 `Prompt` 活動來詢問調查問題並取得回覆。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  開啟**BasicActivityComposition.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`