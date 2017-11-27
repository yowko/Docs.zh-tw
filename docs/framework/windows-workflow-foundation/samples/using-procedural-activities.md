---
title: "使用程序性活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c391316959829c77d16dd87af51d9fe1915dc88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-procedural-activities"></a>使用程序性活動
這個範例會使用 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Assign>、<xref:System.Activities.Statements.If>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.Switch%601>、<xref:System.Activities.Statements.TryCatch> 和 <xref:System.Activities.Statements.WriteLine> 活動實作猜測遊戲。 猜測遊戲會選取一個隨機數字，而玩家必須猜測該數字。 當玩家送出不正確的猜測時，工作流程會提供一個提示，告訴玩家應該猜大一點或小一點的數字。 如果玩家在 7 次內猜到數字，則會對使用者顯示特別的恭賀畫面。  
  
## <a name="custom-activities-in-this-sample"></a>這個範例中的自訂活動  
  
### <a name="readline"></a>ReadLine  
 從主控台讀取一行文字。 這個活動衍生自 <xref:System.Activities.NativeActivity> 類別，並且會建立書籤，主控台應用程式會在讀取一行之後繼續執行該書籤。  
  
### <a name="promptint"></a>PromptInt  
 提示使用者輸入數字，然後從主控台視窗讀取該數字。 此活動衍生自 <xref:System.Activities.Activity%601>，並且會使用 <xref:System.Activities.Statements.WriteLine> 和 `ReadLine` 活動。  
  
##### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [GuessingGame.sln] 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`  
  
## <a name="see-also"></a>另請參閱
