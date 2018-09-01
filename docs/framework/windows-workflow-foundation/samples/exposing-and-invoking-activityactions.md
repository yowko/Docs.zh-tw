---
title: 公開及叫用 ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: f36d88fc54e5150927113ed8825fbccad84129d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387590"
---
# <a name="exposing-and-invoking-activityactions"></a>公開及叫用 ActivityActions
這個範例示範如何開發有 <xref:System.Activities.ActivityAction> 的自訂活動。 此外，也示範如何提供 <xref:System.Activities.ActivityAction> 實作，使用此活動。  
  
 <xref:System.Activities.ActivityAction>可讓活動作者公開 「 洞孔 」 裡使用特定的簽章，活動使用者可以在這裡插入自訂行為。 例如， <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach`活動 （其上運作的項目集合），有<xref:System.Activities.ActivityAction>，讓活動使用者插入會在目前反覆項目運作的行為。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  開啟**ActivityAction.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`