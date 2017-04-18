---
title: "和 3.5 規則集互通 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 和 3.5 規則集互通
這個範例示範使用 <xref:System.Activities.Statements.Interop> 活動透過 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 和規則整合 <xref:System.Workflow.Activities.Policy> 中的自訂活動。  範例中會透過將 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 變數繫結至自訂活動公開之相依性屬性的方式，將資料傳遞至自訂活動。  
  
## 需求  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## 示範  
 <xref:System.Activities.Statements.Interop> 活動、<xref:System.Workflow.Activities.Policy> 中具有相依性屬性的 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 活動  
  
## 討論  
 此範例示範整合 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 活動的其中一個整合案例。  這個範例包含一個叫用 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 活動的 <xref:System.Workflow.Activities.Policy> 的自訂活動。  
  
## TravelRuleLibrary  
 在設計工具中開啟 TravelRuleSet.cs，顯示包含 Policy 活動的自訂循序活動，如下所示。  
  
 ![Interop 活動](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 按兩下 \[**DiscountPolicy**\] 原則活動以檢查規則。  規則編輯器會出現並顯示規則。  
  
 ![規則集編輯器](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 以滑鼠右鍵按一下 \[**DiscountPolicy**\] 活動，然後選取 \[**檢視程式碼**\] 選項，檢查此活動的程式碼旁置 C\# 程式碼。  您會看見 `DiscountLevel` 的相依性屬性設定。  這相當於 <xref:System.Activities.Argument> 中的 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]。  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## InteropWith35RuleSet  
 這是 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 循序工作流程專案，該專案會使用 <xref:System.Activities.Statements.Interop> 活動整合 TravelRuleLibrary 專案中建立的自訂規則集。  變數會在 <xref:System.Activities.Statements.Sequence> 的最上層建立，如下所示。  
  
 ![變數](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![方案總管](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 最後，<xref:System.Activities.Statements.Interop> 活動會用來與 TravelRuleSet 整合。  稍早在 <xref:System.Activities.Statements.Sequence> 上宣告的變數會用來繫結至相依性屬性。  
  
 ![活動類型](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![箭號](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![屬性](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。  請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[適用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。  此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`