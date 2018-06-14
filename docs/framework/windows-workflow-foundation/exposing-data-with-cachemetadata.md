---
title: 使用 CacheMetadata 公開資料
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: 386bbb8734e26eff8079f2913284668125a8a774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515248"
---
# <a name="exposing-data-with-cachemetadata"></a>使用 CacheMetadata 公開資料
執行活動之前，工作流程執行階段會取得維持其執行作業所需的所有活動相關資訊。 工作流程執行階段會在 <xref:System.Activities.Activity.CacheMetadata%2A> 方法執行期間取得這項資訊。 此方法的預設實作會為執行階段提供活動執行時所公開的所有公用引數、變數和子活動。如果活動需要提供更多資訊給執行階段 (例如私用成員或要由活動排程的其他活動)，您就可以覆寫此方法以提供這些資訊。  
  
## <a name="default-cachemetadata-behavior"></a>預設 CacheMetadata 行為  
 衍生自 <xref:System.Activities.NativeActivity.CacheMetadata%2A> 之活動 <xref:System.Activities.NativeActivity> 的預設實作會以下列方式處理下列方法類型：  
  
-   <xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 或 <xref:System.Activities.InOutArgument%601> (泛型引數)：這些引數會公開至執行階段當做引數 (其名稱和型別等於公開的屬性名稱和型別)、正確的引數方向和一些驗證資料。  
  
-   <xref:System.Activities.Variable> 或其任何子類別：這些成員會公開至執行階段當做公用變數。  
  
-   <xref:System.Activities.Activity> 或其任何子類別：這些成員會公開至執行階段當做公用子活動。 您可以透過呼叫 <xref:System.Activities.ActivityMetadata.AddImportedChild%2A> 並傳入子活動，明確實作預設行為。  
  
-   <xref:System.Activities.ActivityDelegate> 或其任何子類別：這些成員會公開至執行階段當做公用委派。  
  
-   型別為 <xref:System.Collections.ICollection> 的 <xref:System.Activities.Variable>：集合中的所有項目都會公開至執行階段當做公用變數。  
  
-   型別為 <xref:System.Collections.ICollection> 的 <xref:System.Activities.Activity>：集合中的所有項目都會公開至執行階段當做公用子系。  
  
-   型別為 <xref:System.Collections.ICollection> 的 <xref:System.Activities.ActivityDelegate>：集合中的所有項目都會公開至執行階段當做公用委派。  
  
 衍生自 <xref:System.Activities.Activity.CacheMetadata%2A>、<xref:System.Activities.Activity> 和 <xref:System.Workflow.Activities.CodeActivity> 之活動的 <xref:System.Activities.AsyncCodeActivity> 也會依照上述方式運作，不過具有下列差異：  
  
-   衍生自 <xref:System.Activities.Activity> 的類別無法排程子活動或委派，因此這類成員會公開成匯入的子系和委派。  
  
-   衍生自 <xref:System.Activities.CodeActivity> 和 <xref:System.Activities.AsyncCodeActivity> 的類別不支援變數、子系或委派，因此只會公開引數。  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>覆寫 CacheMetadata 以提供資訊給執行階段  
 下列程式碼片段示範如何在 <xref:System.Activities.Activity.CacheMetadata%2A> 方法執行期間，將成員的相關資訊加入至活動的中繼資料。 請注意，系統會呼叫此方法的基底，以便快取活動的所有相關公用資料。  
  
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
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a>使用 CacheMetadata 來公開實作子系  
 若要使用變數將資料傳遞給要由活動排程的子活動，您必須加入這些變數當做實作變數。公用變數無法以這種方式設定其值。 這是因為活動的執行方式比較相似於函式 (具有參數) 的實作，而非封裝的類別 (具有屬性)。 不過，在某些情況下，您必須明確設定引數，例如使用 <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> 時，因為排程的活動無法存取父活動的引數 (子活動卻可以)。  
  
 下列程式碼片段示範如何使用 <xref:System.Activities.Activity.CacheMetadata%2A>，將引數從原生活動傳入排程的活動。  
  
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
