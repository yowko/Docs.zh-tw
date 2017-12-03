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
ms.openlocfilehash: e66d1383c42310c2f61b0b3059cb8b347ad55a15
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="commentout-activity"></a><span data-ttu-id="02eb9-102">CommentOut 活動</span><span class="sxs-lookup"><span data-stu-id="02eb9-102">CommentOut Activity</span></span>
<span data-ttu-id="02eb9-103">這個範例示範如何撰寫可從執行路徑移除其他活動的自訂活動，實際上將這些活動標記為註解。</span><span class="sxs-lookup"><span data-stu-id="02eb9-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="02eb9-104">CommentOut 活動</span><span class="sxs-lookup"><span data-stu-id="02eb9-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="02eb9-105">為了達成其目標，CommentOut 活動會繼承自 <xref:System.Activities.CodeActivity> 基底類別，並且實作空的 <xref:System.Activities.CodeActivity.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="02eb9-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="02eb9-106">這個類別的宣告方式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="02eb9-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="02eb9-107">`Designer` 屬性會指定在設計階段實作活動之虛擬化介面的類別。</span><span class="sxs-lookup"><span data-stu-id="02eb9-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="02eb9-108">`ContentProperty` 屬性 (Attribute) 會宣告可以在這個活動執行個體的 XAML 表示中略過 `"Body"` 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="02eb9-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="02eb9-109">在設計工具類別中，XAML 可用來建立活動的自訂視覺表示方式。</span><span class="sxs-lookup"><span data-stu-id="02eb9-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="02eb9-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> 是提供視覺編輯器的一種類別。</span><span class="sxs-lookup"><span data-stu-id="02eb9-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="02eb9-111">單一活動可以放至 `CommentOut` 活動介面上。</span><span class="sxs-lookup"><span data-stu-id="02eb9-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="02eb9-112">如果您要將多個活動加入至這個介面，請先將 Sequence 活動拖曳到這裡。</span><span class="sxs-lookup"><span data-stu-id="02eb9-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="02eb9-113">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="02eb9-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="02eb9-114">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [CommentOut.sln]。</span><span class="sxs-lookup"><span data-stu-id="02eb9-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="02eb9-115">按下 CTRL+SHIFT+B 編譯方案。</span><span class="sxs-lookup"><span data-stu-id="02eb9-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="02eb9-116">按 CTRL+F5 啟動範例，但不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="02eb9-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="02eb9-117">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="02eb9-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="02eb9-118">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="02eb9-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="02eb9-119">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="02eb9-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="02eb9-120">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="02eb9-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
