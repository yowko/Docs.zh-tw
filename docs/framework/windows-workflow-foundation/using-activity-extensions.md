---
title: "使用活動延伸模組 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 使用活動延伸模組
活動可以與工作流程應用程式延伸模組互動，好讓主機提供未明確在工作流程中模組化的其他功能。本主題將說明如何建立及使用延伸模組來計算此活動所執行的次數。  
  
### 若要使用活動延伸模組來計算執行次數  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。選取 \[**新增**\]、\[**專案**\]。選取 \[**Visual C\#**\] 節點底下的 \[**工作流程**\]。從範本清單中選取 \[**工作流程主控台應用程式**\]。將專案命名為 `Extensions`。按一下 \[**確定**\]，建立專案。  
  
2.  在 Program.cs 檔案中為 **System.Collections.Generic** 命名空間加入 `using` 陳述式。  
  
    ```  
    using System.Collections.Generic;  
  
    ```  
  
3.  在 Program.cs 檔案中，建立名為 **ExecutionCountExtension** 的新類別。下列程式碼會建立一個工作流程延伸模組，此延伸模組會在呼叫其 **Register** 方法時追蹤執行個體識別碼。  
  
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
  
4.  建立一個活動來取用 **ExecutionCountExtension**。下列程式碼會定義一個活動，此活動會從執行階段擷取 **ExecutionCountExtension** 物件，並在執行活動時呼叫其 **Register** 方法。  
  
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
  
5.  在 program.cs 檔案的 **Main** 方法中實作此活動。下列程式碼包含的方法可產生兩個不同的工作流程、執行每一個工作流程數次，並顯示延伸模組中所包含的結果資料。  
  
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