---
title: "使用 CacheMetadata 公開資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aea620d740b7b95747395821d622f267943352da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="31f65-102">使用 CacheMetadata 公開資料</span><span class="sxs-lookup"><span data-stu-id="31f65-102">Exposing data with CacheMetadata</span></span>
<span data-ttu-id="31f65-103">執行活動之前，工作流程執行階段會取得維持其執行作業所需的所有活動相關資訊。</span><span class="sxs-lookup"><span data-stu-id="31f65-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="31f65-104">工作流程執行階段會在 <xref:System.Activities.Activity.CacheMetadata%2A> 方法執行期間取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="31f65-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="31f65-105">此方法的預設實作會為執行階段提供活動執行時所公開的所有公用引數、變數和子活動。如果活動需要提供更多資訊給執行階段 (例如私用成員或要由活動排程的其他活動)，您就可以覆寫此方法以提供這些資訊。</span><span class="sxs-lookup"><span data-stu-id="31f65-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>  
  
## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="31f65-106">預設 CacheMetadata 行為</span><span class="sxs-lookup"><span data-stu-id="31f65-106">Default CacheMetadata behavior</span></span>  
 <span data-ttu-id="31f65-107">衍生自 <xref:System.Activities.NativeActivity.CacheMetadata%2A> 之活動 <xref:System.Activities.NativeActivity> 的預設實作會以下列方式處理下列方法類型：</span><span class="sxs-lookup"><span data-stu-id="31f65-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>  
  
-   <span data-ttu-id="31f65-108"><xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 或 <xref:System.Activities.InOutArgument%601> (泛型引數)：這些引數會公開至執行階段當做引數 (其名稱和型別等於公開的屬性名稱和型別)、正確的引數方向和一些驗證資料。</span><span class="sxs-lookup"><span data-stu-id="31f65-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>  
  
-   <span data-ttu-id="31f65-109"><xref:System.Activities.Variable> 或其任何子類別：這些成員會公開至執行階段當做公用變數。</span><span class="sxs-lookup"><span data-stu-id="31f65-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="31f65-110"><xref:System.Activities.Activity> 或其任何子類別：這些成員會公開至執行階段當做公用子活動。</span><span class="sxs-lookup"><span data-stu-id="31f65-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="31f65-111">您可以透過呼叫 <xref:System.Activities.ActivityMetadata.AddImportedChild%2A> 並傳入子活動，明確實作預設行為。</span><span class="sxs-lookup"><span data-stu-id="31f65-111">The default behavior can be implemented explicity by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>  
  
-   <span data-ttu-id="31f65-112"><xref:System.Activities.ActivityDelegate> 或其任何子類別：這些成員會公開至執行階段當做公用委派。</span><span class="sxs-lookup"><span data-stu-id="31f65-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>  
  
-   <span data-ttu-id="31f65-113">型別為 <xref:System.Collections.ICollection> 的 <xref:System.Activities.Variable>：集合中的所有項目都會公開至執行階段當做公用變數。</span><span class="sxs-lookup"><span data-stu-id="31f65-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="31f65-114">型別為 <xref:System.Collections.ICollection> 的 <xref:System.Activities.Activity>：集合中的所有項目都會公開至執行階段當做公用子系。</span><span class="sxs-lookup"><span data-stu-id="31f65-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>  
  
-   <span data-ttu-id="31f65-115">型別為 <xref:System.Collections.ICollection> 的 <xref:System.Activities.ActivityDelegate>：集合中的所有項目都會公開至執行階段當做公用委派。</span><span class="sxs-lookup"><span data-stu-id="31f65-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>  
  
 <span data-ttu-id="31f65-116">衍生自 <xref:System.Activities.Activity.CacheMetadata%2A>、<xref:System.Activities.Activity> 和 <xref:System.Workflow.Activities.CodeActivity> 之活動的 <xref:System.Activities.AsyncCodeActivity> 也會依照上述方式運作，不過具有下列差異：</span><span class="sxs-lookup"><span data-stu-id="31f65-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>  
  
-   <span data-ttu-id="31f65-117">衍生自 <xref:System.Activities.Activity> 的類別無法排程子活動或委派，因此這類成員會公開成匯入的子系和委派。</span><span class="sxs-lookup"><span data-stu-id="31f65-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>  
  
-   <span data-ttu-id="31f65-118">衍生自 <xref:System.Activities.CodeActivity> 和 <xref:System.Activities.AsyncCodeActivity> 的類別不支援變數、子系或委派，因此只會公開引數。</span><span class="sxs-lookup"><span data-stu-id="31f65-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="31f65-119">覆寫 CacheMetadata 以提供資訊給執行階段</span><span class="sxs-lookup"><span data-stu-id="31f65-119">Overriding CacheMetadata to provide information to the runtime</span></span>  
 <span data-ttu-id="31f65-120">下列程式碼片段示範如何在 <xref:System.Activities.Activity.CacheMetadata%2A> 方法執行期間，將成員的相關資訊加入至活動的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31f65-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="31f65-121">請注意，系統會呼叫此方法的基底，以便快取活動的所有相關公用資料。</span><span class="sxs-lookup"><span data-stu-id="31f65-121">Note that the base of the method is called to cache all public data about the activity.</span></span>  
  
```  
protected override void CacheMetadata(NativeActivityMetadata metadata)  
{      
    base.CacheMetadata(metadata);  
    metadata.AddImplementationChild(this._writeLine);  
    metadata.AddVariable(this._myVariable);  
    metadata.AddImplementationVariable(this._myImplementationVariable);  
  
    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));  
    metadata.Bind(argument, this.SomeName);  
    metadata.AddArgument(argument);  
}  
```  
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="31f65-122">使用 CacheMetadata 來公開實作子系</span><span class="sxs-lookup"><span data-stu-id="31f65-122">Using CacheMetadata to expose implementation children</span></span>  
 <span data-ttu-id="31f65-123">若要使用變數將資料傳遞給要由活動排程的子活動，您必須加入這些變數當做實作變數。公用變數無法以這種方式設定其值。</span><span class="sxs-lookup"><span data-stu-id="31f65-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="31f65-124">這是因為活動的執行方式比較相似於函式 (具有參數) 的實作，而非封裝的類別 (具有屬性)。</span><span class="sxs-lookup"><span data-stu-id="31f65-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="31f65-125">不過，在某些情況下，您必須明確設定引數，例如使用 <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> 時，因為排程的活動無法存取父活動的引數 (子活動卻可以)。</span><span class="sxs-lookup"><span data-stu-id="31f65-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>  
  
 <span data-ttu-id="31f65-126">下列程式碼片段示範如何使用 <xref:System.Activities.Activity.CacheMetadata%2A>，將引數從原生活動傳入排程的活動。</span><span class="sxs-lookup"><span data-stu-id="31f65-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>  
  
```  
public sealed class ChildActivity : NativeActivity  
{  
    public WriteLine _writeLine;  
    public InArgument<string> Message { get; set; }  
    private Variable<string> MessageVariable { get; set; }  
    public ChildActivity()  
    {  
        MessageVariable = new Variable<string>();  
        _writeLine = new WriteLine  
        {  
            Text = new InArgument<string>(MessageVariable),  
        };  
    }  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        metadata.AddImplementationVariable(this.MessageVariable);  
        metadata.AddImplementationChild(this._writeLine);  
    }  
    protected override void Execute(NativeActivityContext context)  
    {  
        string configuredMessage = context.GetValue(Message);  
        context.SetValue(MessageVariable, configuredMessage);  
        context.ScheduleActivity(this._writeLine);  
    }  
}  
```
