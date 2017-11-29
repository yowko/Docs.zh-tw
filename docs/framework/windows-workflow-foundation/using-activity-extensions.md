---
title: "使用活動延伸模組"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7ff4f441df437dc5785b6df77c16923a1a1c9906
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-activity-extensions"></a>使用活動延伸模組
活動可以與工作流程應用程式延伸模組互動，好讓主機提供未明確在工作流程中模組化的其他功能。  本主題將說明如何建立及使用延伸模組來計算此活動所執行的次數。  
  
### <a name="to-use-an-activity-extension-to-count-executions"></a>若要使用活動延伸模組來計算執行次數  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。 選取**新**，**專案**。 在下**Visual C#**節點中，選取**工作流程**。  選取**工作流程主控台應用程式**從範本清單。 將專案命名為 `Extensions`。 按一下**確定**建立專案。  
  
2.  新增`using`Program.cs 檔案中的陳述式**System.Collections.Generic**命名空間。  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
3.  在 Program.cs 檔案中，建立新的類別，名為**ExecutionCountExtension**。 下列程式碼會建立追蹤執行個體識別碼的工作流程延伸模組時其**註冊**方法呼叫。  
  
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
  
4.  建立一個活動來取用**ExecutionCountExtension**。 下列程式碼會定義一個活動，擷取**ExecutionCountExtension**物件的執行階段和呼叫其**註冊**活動執行時的方法。  
  
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
  
5.  實作中的活動**Main** program.cs 檔案的方法。 下列程式碼包含的方法可產生兩個不同的工作流程、執行每一個工作流程數次，並顯示延伸模組中所包含的結果資料。  
  
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
