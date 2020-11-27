---
title: 使用活動延伸模組
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 3a9cabda9fe92b2ea4e708da8f853f3029328775
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293282"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="2b9b8-102">使用活動延伸模組</span><span class="sxs-lookup"><span data-stu-id="2b9b8-102">Using Activity Extensions</span></span>

<span data-ttu-id="2b9b8-103">活動可以與工作流程應用程式延伸模組互動，好讓主機提供未明確在工作流程中模組化的其他功能。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="2b9b8-104">本主題將說明如何建立及使用延伸模組來計算此活動所執行的次數。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="2b9b8-105">若要使用活動延伸模組來計算執行次數</span><span class="sxs-lookup"><span data-stu-id="2b9b8-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="2b9b8-106">開啟 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="2b9b8-107">選取 [ **新增**]、[ **專案**]。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-107">Select **New**, **Project**.</span></span> <span data-ttu-id="2b9b8-108">在 [ **Visual c #** ] 節點底下，選取 [ **工作流程**]。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="2b9b8-109">從範本清單中選取 [ **工作流程主控台應用程式** ]。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="2b9b8-110">將專案命名為 `Extensions`。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-110">Name the project `Extensions`.</span></span> <span data-ttu-id="2b9b8-111">按一下 [確定]  以建立專案。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="2b9b8-112">`using`在 Program.cs 檔案中，為 system.string 命名空間 **System.Collections.Generic** 加入語句。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```csharp
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="2b9b8-113">在 Program.cs 檔案中，建立名為 **ExecutionCountExtension** 的新類別。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="2b9b8-114">下列程式碼會建立工作流程延伸模組，以在呼叫其 **Register** 方法時追蹤實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```csharp
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. <span data-ttu-id="2b9b8-115">建立使用 **ExecutionCountExtension** 的活動。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="2b9b8-116">下列程式碼會定義一個活動，此活動會從執行時間抓取 **ExecutionCountExtension** 物件，並在活動執行時呼叫其 **Register** 方法。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```csharp
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. <span data-ttu-id="2b9b8-117">在 program.cs 檔案的 **Main** 方法中，執行活動。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="2b9b8-118">下列程式碼包含的方法可產生兩個不同的工作流程、執行每一個工作流程數次，並顯示延伸模組中所包含的結果資料。</span><span class="sxs-lookup"><span data-stu-id="2b9b8-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```csharp
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
