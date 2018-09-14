---
title: 和 3.5 規則集互通
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 5ea5454ef80bfd83611ed20392782d99cd8c0c25
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45510139"
---
# <a name="interop-with-35-rule-set"></a><span data-ttu-id="ed122-102">和 3.5 規則集互通</span><span class="sxs-lookup"><span data-stu-id="ed122-102">Interop with 3.5 Rule Set</span></span>
<span data-ttu-id="ed122-103">此範例示範如何使用<xref:System.Activities.Statements.Interop>活動中的自訂活動的整合[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]使用<!--zz <xref:System.Workflow.Activities.Policy> -->`System.Workflow.Activities.Policy`和規則。</span><span class="sxs-lookup"><span data-stu-id="ed122-103">This sample demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` and rules.</span></span> <span data-ttu-id="ed122-104">範例中會透過將 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 變數繫結至自訂活動公開之相依性屬性的方式，將資料傳遞至自訂活動。</span><span class="sxs-lookup"><span data-stu-id="ed122-104">It passes data to the custom activity by binding [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed122-105">需求</span><span class="sxs-lookup"><span data-stu-id="ed122-105">Requirements</span></span>  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a><span data-ttu-id="ed122-106">示範</span><span class="sxs-lookup"><span data-stu-id="ed122-106">Demonstrates</span></span>  
 <span data-ttu-id="ed122-107"><xref:System.Activities.Statements.Interop> 活動<!--zz <xref:System.Workflow.Activities.Policy> -->`System.Workflow.Activities.Policy`中的活動[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]與相依性屬性</span><span class="sxs-lookup"><span data-stu-id="ed122-107"><xref:System.Activities.Statements.Interop> activity, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] with dependency properties</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ed122-108">討論</span><span class="sxs-lookup"><span data-stu-id="ed122-108">Discussion</span></span>  
 <span data-ttu-id="ed122-109">此範例示範整合 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 活動的其中一個整合案例。</span><span class="sxs-lookup"><span data-stu-id="ed122-109">The sample demonstrates one of the integration scenarios for integrating with a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] activity.</span></span> <span data-ttu-id="ed122-110">此範例包含[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]叫用的自訂活動<!--zz <xref:System.Workflow.Activities.Policy> -->`System.Workflow.Activities.Policy`活動。</span><span class="sxs-lookup"><span data-stu-id="ed122-110">This sample includes a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] custom activity that invokes a <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity.</span></span>  
  
## <a name="travelrulelibrary"></a><span data-ttu-id="ed122-111">TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="ed122-111">TravelRuleLibrary</span></span>  
 <span data-ttu-id="ed122-112">在設計工具中開啟 TravelRuleSet.cs，顯示包含 Policy 活動的自訂循序活動，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ed122-112">Opening TravelRuleSet.cs in the designer shows a custom sequential activity that contains a Policy activity as follows</span></span>  
  
 <span data-ttu-id="ed122-113">![Interop 活動](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span><span class="sxs-lookup"><span data-stu-id="ed122-113">![Interop Activity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span></span>  
  
 <span data-ttu-id="ed122-114">按兩下**DiscountPolicy**原則活動以檢查規則。</span><span class="sxs-lookup"><span data-stu-id="ed122-114">Double-click the **DiscountPolicy** policy activity to examine the rules.</span></span> <span data-ttu-id="ed122-115">規則編輯器會出現並顯示規則。</span><span class="sxs-lookup"><span data-stu-id="ed122-115">The Rules editor appears to show the rules.</span></span>  
  
 <span data-ttu-id="ed122-116">![規則集編輯器](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span><span class="sxs-lookup"><span data-stu-id="ed122-116">![Rule Set Editor](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span></span>  
  
 <span data-ttu-id="ed122-117">以滑鼠右鍵按一下**DiscountPolicy**活動，然後選取**檢視程式碼**檢查程式碼除外 C# 程式碼，此活動的選項。</span><span class="sxs-lookup"><span data-stu-id="ed122-117">Right-click the **DiscountPolicy** activity and select the **View Code** option to examine the code-beside C# code that goes with this activity.</span></span> <span data-ttu-id="ed122-118">您會看見 `DiscountLevel` 的相依性屬性設定。</span><span class="sxs-lookup"><span data-stu-id="ed122-118">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="ed122-119">這相當於 <xref:System.Activities.Argument> 中的 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ed122-119">This is equivalent to an <xref:System.Activities.Argument> in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span>  
  
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
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="ed122-120">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="ed122-120">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="ed122-121">這是 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 循序工作流程專案，該專案會使用 <xref:System.Activities.Statements.Interop> 活動整合 TravelRuleLibrary 專案中建立的自訂規則集。</span><span class="sxs-lookup"><span data-stu-id="ed122-121">This is a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom rule set created in the TravelRuleLibrary project.</span></span> <span data-ttu-id="ed122-122">變數會在 <xref:System.Activities.Statements.Sequence> 的最上層建立，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ed122-122">Variables are created on the top-level <xref:System.Activities.Statements.Sequence> as follows.</span></span>  
  
 <span data-ttu-id="ed122-123">![變數](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span><span class="sxs-lookup"><span data-stu-id="ed122-123">![Variables](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span></span>  
  
 <span data-ttu-id="ed122-124">![方案總管](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span><span class="sxs-lookup"><span data-stu-id="ed122-124">![Solution Explorer](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span></span>  
  
 <span data-ttu-id="ed122-125">最後，<xref:System.Activities.Statements.Interop> 活動會用來與 TravelRuleSet 整合。</span><span class="sxs-lookup"><span data-stu-id="ed122-125">Lastly, the <xref:System.Activities.Statements.Interop> activity is used to integrate with the TravelRuleSet.</span></span> <span data-ttu-id="ed122-126">稍早在 <xref:System.Activities.Statements.Sequence> 上宣告的變數會用來繫結至相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="ed122-126">The variables that were declared earlier on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
 <span data-ttu-id="ed122-127">![活動型別](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span><span class="sxs-lookup"><span data-stu-id="ed122-127">![Activity Type](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span></span>  
  
 <span data-ttu-id="ed122-128">![箭號](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span><span class="sxs-lookup"><span data-stu-id="ed122-128">![Arrow](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span></span>  
  
 <span data-ttu-id="ed122-129">![屬性](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span><span class="sxs-lookup"><span data-stu-id="ed122-129">![Properties](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed122-130">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ed122-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed122-131">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ed122-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed122-132">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ed122-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed122-133">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ed122-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
