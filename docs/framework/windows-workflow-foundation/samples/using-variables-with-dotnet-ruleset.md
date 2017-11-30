---
title: "搭配 .NET Framework 3.5 Ruleset 使用變數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9b5cc982aaad92258102b313d8fc19a9ff1521a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>搭配 .NET Framework 3.5 Ruleset 使用變數
這個範例示範如何建立使用 <xref:System.Activities.Statements.Interop> 活動整合 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 中使用原則和規則所撰寫自訂活動的工作流程。 工作流程會透過將變數繫結至自訂活動公開之相依性屬性的方式，將資料傳遞至自訂活動。  
  
## <a name="sample-walkthrough"></a>範例逐步解說  
  
#### <a name="to-examine-travelrulelibrary"></a>若要檢查 TravelRuleLibrary  
  
1.  使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開啟 [InteropWith35RuleSet.sln] 方案檔案。  
  
2.  在工作流程設計工具中開啟 [TravelRuleSet.cs]。  
  
     包含 <xref:System.Workflow.Activities.PolicyActivity> 的自訂循序活動隨即顯示。  
  
3.  按兩下 [DiscountPolicy] 原則活動以檢查規則。  
  
     規則編輯器會出現並顯示規則。  
  
4.  以滑鼠右鍵按一下`DiscountPolicy`選取**檢視程式碼**選項，檢查程式碼旁置 C# 程式碼活動。  
  
     您會看見 `DiscountLevel` 的相依性屬性設定。 這相當於 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 中的引數。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]引數，請參閱[變數和引數](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md)。  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 這是循序工作流程專案，該專案會使用 <xref:System.Activities.Statements.Interop> 活動整合 `TravelRuleLibrary` 專案中建立的自訂規則集。 變數會在 <xref:System.Activities.Statements.Sequence> 活動的最上層建立。 <xref:System.Activities.Statements.Interop> 活動會用來與 `TravelRuleSet` 活動整合。 <xref:System.Activities.Statements.Sequence> 上宣告的變數會用來繫結至相依性屬性。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [InteropWith35RuleSet.sln] 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`  
  
## <a name="see-also"></a>另請參閱
