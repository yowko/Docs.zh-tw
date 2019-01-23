---
title: 工作流程執行屬性
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 96f5057986e256f485f60221d1c6ad3d2494be55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566719"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="ca465-102">工作流程執行屬性</span><span class="sxs-lookup"><span data-stu-id="ca465-102">Workflow Execution Properties</span></span>
<span data-ttu-id="ca465-103">CLR 會透過執行緒區域儲存區 (TLS) 維護每個執行緒的執行內容。</span><span class="sxs-lookup"><span data-stu-id="ca465-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="ca465-104">這個執行內容會管理眾所周知的執行緒屬性，例如執行緒識別、環境交易和目前的權限集，以及使用者定義的執行緒屬性，例如具名位置。</span><span class="sxs-lookup"><span data-stu-id="ca465-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="ca465-105">與直接以 CLR 為目標的程式不同，工作流程程式是在執行緒無從驗證的環境中執行之活動的階層式範圍樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ca465-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="ca465-106">這意味標準的 TLS 機制無法直接用於決定哪些內容位於指定的工作項目範圍內。</span><span class="sxs-lookup"><span data-stu-id="ca465-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="ca465-107">例如，兩個平行的執行分支也許會使用不同的交易，而排程器也許會在相同的 CLR 執行緒上交錯執行。</span><span class="sxs-lookup"><span data-stu-id="ca465-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="ca465-108">工作流程執行屬性會提供將內容特定屬性加入至活動環境的機制。</span><span class="sxs-lookup"><span data-stu-id="ca465-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="ca465-109">這個機制可讓活動宣告哪些屬性在其子樹狀結構範圍中，而且也會提供設定和破壞 TLS 的攔截程序，以和 CLR 物件適當地互通。</span><span class="sxs-lookup"><span data-stu-id="ca465-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="ca465-110">建立與使用工作流程執行屬性</span><span class="sxs-lookup"><span data-stu-id="ca465-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="ca465-111">工作流程執行屬性通常會實作 <xref:System.Activities.IExecutionProperty> 介面，但是著重於傳訊功能的屬性可能會實作 <xref:System.ServiceModel.Activities.ISendMessageCallback> 和 <xref:System.ServiceModel.Activities.IReceiveMessageCallback>。</span><span class="sxs-lookup"><span data-stu-id="ca465-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="ca465-112">若要建立工作流程執行屬性，請建立實作 <xref:System.Activities.IExecutionProperty> 介面的類別，並實作成員 <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> 和 <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>。</span><span class="sxs-lookup"><span data-stu-id="ca465-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="ca465-113">這些成員可讓執行屬性在包含該屬性之活動 (包括任何子活動) 工作的每次 Pulse 期間，正確的設定與終止執行緒區域儲存區。</span><span class="sxs-lookup"><span data-stu-id="ca465-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="ca465-114">在本範例中，會建立設定 `ConsoleColorProperty` 的 `Console.ForegroundColor`。</span><span class="sxs-lookup"><span data-stu-id="ca465-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="ca465-115">活動作者可以在活動的執行覆寫中註冊此屬性，以使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="ca465-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="ca465-116">在此範例中會定義 `ConsoleColorScope` 活動，此活動會 註冊 `ConsoleColorProperty`，方法是將其加入至目前 <xref:System.Activities.NativeActivityContext.Properties%2A> 的 <xref:System.Activities.NativeActivityContext> 集合。</span><span class="sxs-lookup"><span data-stu-id="ca465-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="ca465-117">當活動的主體開始工作的 Pulse 時，會呼叫該屬性的 <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> 方法，而當工作的 Pulse 完成時，則會呼叫 <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>。</span><span class="sxs-lookup"><span data-stu-id="ca465-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="ca465-118">在本範例中，會建立使用有三個分支的 <xref:System.Activities.Statements.Parallel> 活動之工作流程。</span><span class="sxs-lookup"><span data-stu-id="ca465-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="ca465-119">前兩個分支使用 `ConsoleColorScope` 活動，第三個分支則不使用。</span><span class="sxs-lookup"><span data-stu-id="ca465-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="ca465-120">三個分支均包含兩個 <xref:System.Activities.Statements.WriteLine> 活動及一個 <xref:System.Activities.Statements.Delay> 活動。</span><span class="sxs-lookup"><span data-stu-id="ca465-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="ca465-121">當 <xref:System.Activities.Statements.Parallel> 活動執行時，包含在分支中的活動會交錯執行，但是當每個子活動執行時，`ConsoleColorProperty` 會套用正確的主控台色彩。</span><span class="sxs-lookup"><span data-stu-id="ca465-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="ca465-122">叫用工作流程時，會將下列輸出寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="ca465-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="ca465-123">雖然未顯示在上述輸出中，但主控台視窗中的每一行文字均會以指定的色彩顯示。</span><span class="sxs-lookup"><span data-stu-id="ca465-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="ca465-124">自訂活動作者可以使用工作流程執行屬性，而這些屬性也可以提供活動的處理機制 (例如 <xref:System.ServiceModel.Activities.CorrelationScope> 和 <xref:System.Activities.Statements.TransactionScope> 活動)。</span><span class="sxs-lookup"><span data-stu-id="ca465-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca465-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca465-125">See also</span></span>
- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
