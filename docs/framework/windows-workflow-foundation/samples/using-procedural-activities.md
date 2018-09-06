---
title: 使用程序性活動
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804746"
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
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`