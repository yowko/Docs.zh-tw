---
title: 工作流程執行屬性
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 87775ba6efb9ec26ed2445e1f9d0944c379ba04f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988591"
---
# <a name="workflow-execution-properties"></a>工作流程執行屬性
CLR 會透過執行緒區域儲存區 (TLS) 維護每個執行緒的執行內容。 這個執行內容會管理眾所周知的執行緒屬性，例如執行緒識別、環境異動和目前的權限集，以及使用者定義的執行緒屬性，例如具名位置。  
  
 與直接以 CLR 為目標的程式不同，工作流程程式是在執行緒無從驗證的環境中執行之活動的階層式範圍樹狀結構。 這意味標準的 TLS 機制無法直接用於決定哪些內容位於指定的工作項目範圍內。 例如，兩個平行的執行分支也許會使用不同的交易，而排程器也許會在相同的 CLR 執行緒上交錯執行。  
  
 工作流程執行屬性會提供將內容特定屬性加入至活動環境的機制。 這個機制可讓活動宣告哪些屬性在其子樹狀範圍中，而且也會提供設定和破壞 TLS 的攔截程序，以和 CLR 物件適當地互通。  
  
## <a name="creating-and-using-workflow-execution-properties"></a>建立與使用工作流程執行屬性  
 工作流程執行屬性通常會實作 <xref:System.Activities.IExecutionProperty> 介面，但是著重於傳訊功能的屬性可能會實作 <xref:System.ServiceModel.Activities.ISendMessageCallback> 和 <xref:System.ServiceModel.Activities.IReceiveMessageCallback>。 若要建立工作流程執行屬性，請建立實作 <xref:System.Activities.IExecutionProperty> 介面的類別，並實作成員 <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> 和 <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>。 這些成員可讓執行屬性在包含該屬性之活動 (包括任何子活動) 工作的每次 Pulse 期間，正確的設定與終止執行緒區域儲存區。 在本範例中，會建立設定 `ConsoleColorProperty` 的 `Console.ForegroundColor`。  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 活動作者可以在活動的執行覆寫中註冊此屬性，以使用此屬性。 在此範例中會定義 `ConsoleColorScope` 活動，此活動會 註冊 `ConsoleColorProperty`，方法是將其加入至目前 <xref:System.Activities.NativeActivityContext.Properties%2A> 的 <xref:System.Activities.NativeActivityContext> 集合。  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 當活動的主體開始工作的 Pulse 時，會呼叫該屬性的 <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> 方法，而當工作的 Pulse 完成時，則會呼叫 <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>。 在本範例中，會建立使用有三個分支的 <xref:System.Activities.Statements.Parallel> 活動之工作流程。 前兩個分支使用 `ConsoleColorScope` 活動，第三個分支則不使用。 三個分支均包含兩個 <xref:System.Activities.Statements.WriteLine> 活動及一個 <xref:System.Activities.Statements.Delay> 活動。 當 <xref:System.Activities.Statements.Parallel> 活動執行時，包含在分支中的活動會交錯執行，但是當每個子活動執行時，`ConsoleColorProperty` 會套用正確的主控台色彩。  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =   
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =   
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 叫用工作流程時，會將下列輸出寫入至主控台視窗。  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> 雖然未顯示在上述輸出中，但主控台視窗中的每一行文字均會以指定的色彩顯示。  
  
 自訂活動作者可以使用工作流程執行屬性，而這些屬性也可以提供活動的處理機制 (例如 <xref:System.ServiceModel.Activities.CorrelationScope> 和 <xref:System.Activities.Statements.TransactionScope> 活動)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
