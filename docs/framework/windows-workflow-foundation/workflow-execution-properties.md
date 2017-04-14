---
title: "工作流程執行屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 工作流程執行屬性
CLR 會透過執行緒區域儲存區 \(TLS\) 維護每個執行緒的執行內容。這個執行內容會管理已知的執行緒作業，如執行緒識別、環境交易和目前的權限集，以及如具名位置等使用者定義的執行緒屬性。  
  
 與直接以 CLR 為目標的程式不同，工作流程程式是在執行緒無從驗證的環境中執行之活動的階層式範圍樹狀結構。這意味標準的 TLS 機制無法直接用於決定哪些內容位於指定的工作項目範圍內。例如，兩個平行的執行分支也許會使用不同的交易，而排程器也許會在相同的 CLR 執行緒上交錯執行。  
  
 工作流程執行屬性會提供將內容特定屬性加入至活動環境的機制。這個機制可讓活動宣告哪些屬性在其子樹狀結構範圍中，以及提供設定和破壞 TLS 的攔截程序來與 CLR 物件適當地互通。  
  
## 建立與使用工作流程執行屬性  
 工作流程執行屬性通常會實作 <xref:System.Activities.IExecutionProperty>介面，雖然著重於傳訊功能的屬性可能會實作 <xref:> System.ServiceModel.Activities.ISendMessageCallback?qualifyHint=False&autoUpgrade=True 和 <xref:> System.ServiceModel.Activities.IReceiveMessageCallback?qualifyHint=False&autoUpgrade=True。若要建立工作流程執行屬性，請建立實作 <xref:System.Activities.IExecutionProperty> 介面的類別，並實作成員 <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> 和 <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>。這些成員可讓執行屬性在包含該屬性之活動 \(包括任何子活動\) 工作的每次 Pulse 期間，正確的設定與終止執行緒區域儲存區。在本範例中，會建立設定 `Console.ForegroundColor` 的 `ConsoleColorProperty`。  
  
> [!NOTE]
>  本主題中的下列範例程式碼以[執行屬性](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md)為基礎。  
  
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
  
 活動作者可以在活動的執行覆寫中註冊此屬性，以使用此屬性。在此範例中會定義 `ConsoleColorScope` 活動，此活動會 註冊 `ConsoleColorProperty`，方法是將其加入至目前 <xref:System.Activities.NativeActivityContext> 的 <xref:System.Activities.NativeActivityContext.Properties%2A> 集合。  
  
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
  
 活動主體啟動工作的 Pulse 時，會呼叫該屬性的 <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> 方法，而當工作的 Pulse 完成時，則會呼叫 <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>。在本範例中，會建立使用有三個分支的 <xref:System.Activities.Statements.Parallel> 活動之工作流程。前兩個分支使用 `ConsoleColorScope` 活動，第三個分支則不使用。三個分支均包含兩個 <xref:System.Activities.Statements.WriteLine> 活動及一個 <xref:System.Activities.Statements.Delay> 活動。執行 <xref:System.Activities.Statements.Parallel> 活動時，會交錯執行包含在分支中的活動，但執行每個子活動時，`ConsoleColorProperty` 會套用正確的主控台色彩。  
  
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
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  雖然未顯示在上述輸出中，但主控台視窗中的每一行文字均會以指定的色彩顯示。  
  
 自訂活動作者可以使用工作流程執行屬性，而這些屬性也可以提供活動的處理機制 \(例如 <xref:System.ServiceModel.Activities.CorrelationScope> 和 <xref:System.Activities.Statements.TransactionScope> 活動\)。  
  
## 請參閱  
 <xref:System.Activities.IExecutionProperty>   
 <xref:System.Activities.IPropertyRegistrationCallback>   
 <xref:System.Activities.RegistrationContext>