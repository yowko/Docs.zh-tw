---
title: 公開及叫用 ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 2d369ec4b028b047ce02016dd511c1c088b46a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exposing-and-invoking-activityactions"></a>公開及叫用 ActivityActions
這個範例示範如何開發有 <xref:System.Activities.ActivityAction> 的自訂活動。 此外，也示範如何提供 <xref:System.Activities.ActivityAction> 實作，使用此活動。  
  
 <xref:System.Activities.ActivityAction>允許活動作者公開 「 洞 」 特定的簽章與位置，活動使用者也可以插入自訂行為。 例如， <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach`活動，（項目集合），有<xref:System.Activities.ActivityAction>，可讓活動使用者插入目前的反覆項目項目運作的行為。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  開啟**ActivityAction.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`