---
title: 使用活動延伸模組
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 551ce24db8c0adc8225ac94a1d05f998a26873a9
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988626"
---
# <a name="using-activity-extensions"></a>使用活動延伸模組
活動可以與工作流程應用程式延伸模組互動，好讓主機提供未明確在工作流程中模組化的其他功能。  本主題將說明如何建立及使用延伸模組來計算此活動所執行的次數。

### <a name="to-use-an-activity-extension-to-count-executions"></a>若要使用活動延伸模組來計算執行次數

1. 開啟 Visual Studio 2010。 選取 [**新增**]、[**專案**]。 在 [**視覺C#效果**] 節點底下，選取 [**工作流程**]。  從範本清單中選取 [**工作流程主控台應用程式**]。 將專案命名為 `Extensions`。 按一下 \[確定\] 來建立專案。

2. 在 Program.cs 檔案中，為**system.web**命名空間新增語句。`using`

    ```csharp
    using System.Collections.Generic;
    ```

3. 在 Program.cs 檔案中，建立名為**ExecutionCountExtension**的新類別。 下列程式碼會建立工作流程延伸模組，以便在呼叫其**Register**方法時追蹤實例識別碼。

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

4. 建立使用**ExecutionCountExtension**的活動。 下列程式碼定義的活動會從執行時間抓取**ExecutionCountExtension**物件，並在活動執行時呼叫其**Register**方法。

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

5. 在 program.cs 檔案的**Main**方法中，執行活動。 下列程式碼包含的方法可產生兩個不同的工作流程、執行每一個工作流程數次，並顯示延伸模組中所包含的結果資料。

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
