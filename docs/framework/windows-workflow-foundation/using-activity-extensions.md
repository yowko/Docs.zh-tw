---
title: 使用活動延伸模組
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768954"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="5ce8e-102">使用活動延伸模組</span><span class="sxs-lookup"><span data-stu-id="5ce8e-102">Using Activity Extensions</span></span>
<span data-ttu-id="5ce8e-103">活動可以與工作流程應用程式延伸模組互動，好讓主機提供未明確在工作流程中模組化的其他功能。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="5ce8e-104">本主題將說明如何建立及使用延伸模組來計算此活動所執行的次數。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="5ce8e-105">若要使用活動延伸模組來計算執行次數</span><span class="sxs-lookup"><span data-stu-id="5ce8e-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="5ce8e-106">開啟 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="5ce8e-107">選取 **新**，**專案**。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-107">Select **New**, **Project**.</span></span> <span data-ttu-id="5ce8e-108">底下**Visual C#** 節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="5ce8e-109">選取 **工作流程主控台應用程式**從範本清單。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="5ce8e-110">將專案命名為 `Extensions`。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-110">Name the project `Extensions`.</span></span> <span data-ttu-id="5ce8e-111">按一下 [確定] 建立專案。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="5ce8e-112">新增`using`陳述式中的 Program.cs 檔案**System.Collections.Generic**命名空間。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="5ce8e-113">在 Program.cs 檔案中，建立新的類別，名為**ExecutionCountExtension**。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="5ce8e-114">下列程式碼會建立追蹤的執行個體識別碼的工作流程延伸模組時其**註冊**呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```
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

4. <span data-ttu-id="5ce8e-115">建立一個活動來取用**ExecutionCountExtension**。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="5ce8e-116">下列程式碼定義一個活動，擷取**ExecutionCountExtension**物件的執行階段，並呼叫其**註冊**活動執行時的方法。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```
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

5. <span data-ttu-id="5ce8e-117">實作中的活動**Main** program.cs 檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="5ce8e-118">下列程式碼包含的方法可產生兩個不同的工作流程、執行每一個工作流程數次，並顯示延伸模組中所包含的結果資料。</span><span class="sxs-lookup"><span data-stu-id="5ce8e-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```
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
