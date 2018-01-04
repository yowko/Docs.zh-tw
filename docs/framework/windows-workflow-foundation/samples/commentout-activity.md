---
title: "CommentOut 活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 900f6647eadb04a783fe0a3a143a71d9c766a48c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="commentout-activity"></a>CommentOut 活動
這個範例示範如何撰寫可從執行路徑移除其他活動的自訂活動，實際上將這些活動標記為註解。  
  
## <a name="the-commentout-activity"></a>CommentOut 活動  
 為了達成其目標，CommentOut 活動會繼承自 <xref:System.Activities.CodeActivity> 基底類別，並且實作空的 <xref:System.Activities.CodeActivity.Execute%2A> 方法。  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 這個類別的宣告方式如下列範例所示。  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 `Designer` 屬性會指定在設計階段實作活動之虛擬化介面的類別。 `ContentProperty` 屬性 (Attribute) 會宣告可以在這個活動執行個體的 XAML 表示中略過 `"Body"` 屬性 (Property)。  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 在設計工具類別中，XAML 可用來建立活動的自訂視覺表示方式。 <xref:System.Activities.Presentation.WorkflowItemPresenter> 是提供視覺編輯器的一種類別。  
  
 單一活動可以放至 `CommentOut` 活動介面上。 如果您要將多個活動加入至這個介面，請先將 Sequence 活動拖曳到這裡。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [CommentOut.sln]。  
  
2.  按下 CTRL+SHIFT+B 編譯方案。  
  
3.  按 CTRL+F5 啟動範例，但不進行偵錯。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
