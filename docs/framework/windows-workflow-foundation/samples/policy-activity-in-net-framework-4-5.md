---
title: ".NET Framework 4.5 中的原則活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1374bc086923b9ffef288a7fa90427710bdd91b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="policy-activity-in-net-framework-45"></a>.NET Framework 4.5 中的原則活動
Policy4 活動透過直接使用 WF 3.5 隨附的規則引擎，可在 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 4.5) 中使用 <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 3.5) [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 物件。 您可以使用這個活動來建立及執行 WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]包含在 Windows Workflow Foundation 中之 WF 3.5 規則引擎的詳細資訊，請參閱＜Windows Workflow Foundation 規則引擎簡介＞。 如需有關移轉到 WF 中的規則[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]，請閱讀[移轉指引](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>這個範例中的專案  
  
|專案名稱|描述|主要檔案|  
|------------------|-----------------|----------------|  
|Policy4|包含 Policy4 活動及其 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 設計工具。|**Policy4.cs**: Policy4 活動定義。<br /><br /> **PolicyDesigner.xaml**: Policy4 活動的自訂設計工具。 它會使用規則編輯器 ([RuleSetDialog 類別](http://go.microsoft.com/fwlink/?LinkId=150378)) 從[!INCLUDE[wf1](../../../../includes/wf1-md.md)]規則引擎。|  
|ImperativeCodeClientSample|範例用戶端應用程式，透過使用命令式 C# 程式碼 (未使用 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 設計工具) 的 Policy4 應用程式，來設定及執行工作流程。|**ApplyDiscount.rules**： 檔案與[!INCLUDE[wf1](../../../../includes/wf1-md.md)]規則定義。<br /><br /> **Order.cs**： 代表客戶訂單的類型。 規則套用至這個類型的物件。<br /><br /> **Program.cs**： 設定及執行工作流程，其中有 Policy4 活動套用至 Order 物件執行個體 ApplyDiscount.rules 中定義的規則。<br /><br /> **App.config**： 具有規則檔路徑的組態檔。|  
|DesignerClientSample|範例用戶端應用程式，透過使用 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 設計工具的 Policy4 應用程式，來設定及執行工作流程。|**Sequence1.xaml**： 使用 Policy4 活動執行規則評估的循序工作流程。<br /><br /> `Program.cs`：執行 Sequence1.xaml 中定義的工作流程執行個體。|  
  
## <a name="the-policy4-activity"></a>Policy4 活動  
 Policy4 活動是衍生自 <xref:System.Activities.NativeActivity%601> 的類別，允許工作流程執行 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets。 下列程式碼範例是活動的公用 OM 簡化定義。  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|屬性|描述|  
|--------------|-----------------|  
|RuleSet|在 WF [RuleSet 類別](http://go.microsoft.com/fwlink/?LinkId=150379)的.NET Framework 3.5，才能在活動執行時進行評估。|  
|TargetObject|針對物件中的規則[RuleSet 類別](http://go.microsoft.com/fwlink/?LinkId=150379)會進行評估。|  
|ValidationError|所傳回的驗證錯誤的清單[!INCLUDE[wf1](../../../../includes/wf1-md.md)]適用於驗證時，.NET Framework 3.5 規則引擎[RuleSet 類別](http://go.microsoft.com/fwlink/?LinkId=150379)對目標物件之前執行。|  
  
## <a name="policy4-activity-designer"></a>Policy4 活動設計工具  
 在不需要撰寫程式碼的情況下，Policy4 設計工具加入設定 Policy4 活動的功能。 建置方案之後, 它位於工具箱的區段中**Microsoft.Samples.Activities.Rules**。  
  
 WF 設計工具可讓您設定目標物件和 RuleSet。 當**Edit RuleSet**按一下按鈕時，WF [RuleSetDialog 類別](http://go.microsoft.com/fwlink/?LinkId=150378)如[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]隨即出現。 這個對話方塊是重新裝載的 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 規則編輯器。 使用此編輯器來建立及編輯 Policy4 活動執行的規則。  
  
## <a name="using-this-sample"></a>使用這個範例  
 不需要特殊設定即可執行此範例。 只要在 Visual Studio 中開啟方案，然後按 F5 執行應用程式。  
  
 這個範例包含兩個用戶端應用程式：ImperativeCodeClientSample 和 DesignerClientSample。 ImperativeCodeClientSample 用戶端示範如何透過 C# 命令式程式碼來設定及執行 Policy4 活動。 DesignerClientSample 示範如何透過設計工具來設定及執行 Policy4 活動。  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>若要執行 ImperativeCodeClientSample 用戶端應用程式  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 Policy4Sample.sln 方案檔案。  
  
2.  在**方案總管 中**，以滑鼠右鍵按一下**ImperativeCodeClientSample**專案，然後選取**設定為啟始專案**。  
  
3.  若要執行專案，請按 CTRL+F5。  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>若要執行 ImperativeCodeClientSample 用戶端應用程式  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 Policy4Sample.sln 方案檔案。  
  
2.  在**方案總管 中**，以滑鼠右鍵按一下**DesignerClientSample**專案。  
  
    -   選取**設定為啟始專案**。  
  
3.  若要編譯專案，請按 CTRL+SHIFT+B。  
  
4.  若要執行專案，請按 CTRL+F5。  
  
## <a name="see-also"></a>另請參閱
