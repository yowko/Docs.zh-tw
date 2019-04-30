---
title: HOW TO：建立自訂執行個體存放區
ms.date: 03/30/2017
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
ms.openlocfilehash: cacee7d95a543525ba031de0cc0636d05fc72fc8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945635"
---
# <a name="how-to-create-a-custom-instance-store"></a><span data-ttu-id="a4f78-102">HOW TO：建立自訂執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="a4f78-102">How to: Create a Custom Instance Store</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a4f78-103">包含 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>，這是使用 SQL Server 來保存工作流程資料的執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-103">contains <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, an instance store that uses SQL Server to persist workflow data.</span></span> <span data-ttu-id="a4f78-104">如果您的應用程式需要將工作流程資料保存在另一個媒體中，例如不同的資料庫或檔案系統，您可以實作自訂的執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-104">If your application is required to persist workflow data to another medium, such as a different database or a file system, you can implement a custom instance store.</span></span> <span data-ttu-id="a4f78-105">擴充抽象的 <xref:System.Runtime.DurableInstancing.InstanceStore> 類別，並實作進行實作所需的方法，即可建立自訂執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-105">A custom instance store is created by extending the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class and implementing the methods that are required for the implementation.</span></span> <span data-ttu-id="a4f78-106">自訂執行個體存放區的完整實作，請參閱[公司購買程序](./samples/corporate-purchase-process.md)範例。</span><span class="sxs-lookup"><span data-stu-id="a4f78-106">For a complete implementation of a custom instance store, see the [Corporate Purchase Process](./samples/corporate-purchase-process.md) sample.</span></span>

## <a name="implementing-the-begintrycommand-method"></a><span data-ttu-id="a4f78-107">實作 BeginTryCommand 方法</span><span class="sxs-lookup"><span data-stu-id="a4f78-107">Implementing the BeginTryCommand method</span></span>

<span data-ttu-id="a4f78-108">持續性引擎會將 <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> 傳送至執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-108">The <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> is sent to the instance store by the persistence engine.</span></span> <span data-ttu-id="a4f78-109">`command` 參數的型別會表示所執行的命令；此參數可以是下列其中一種型別：</span><span class="sxs-lookup"><span data-stu-id="a4f78-109">The type of the `command` parameter indicates which command is being executed; this parameter can be of the following types:</span></span>

- <span data-ttu-id="a4f78-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>：工作流程時要保存至儲存媒體，持續性引擎會傳送此命令至執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be persisted to the storage medium.</span></span> <span data-ttu-id="a4f78-111">工作流程持續性資料已提供給在<xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> 參數之 `command` 成員中的方法。</span><span class="sxs-lookup"><span data-stu-id="a4f78-111">The workflow persistence data is provided to the method in the <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> member of the `command` parameter.</span></span>

- <span data-ttu-id="a4f78-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>：要從儲存媒體載入工作流程時，持續性引擎會傳送此命令至執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be loaded from the storage medium.</span></span> <span data-ttu-id="a4f78-113">所要載入之工作流程的執行個體 ID 會提供給 `instanceId` 參數的 <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> 屬性的 `context` 參數中的方法。</span><span class="sxs-lookup"><span data-stu-id="a4f78-113">The instance ID of the workflow to be loaded is provided to the method in the `instanceId` parameter of the <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> property of the `context` parameter.</span></span>

- <span data-ttu-id="a4f78-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>：此命令的執行個體存放區時持續性引擎會傳送<xref:System.ServiceModel.Activities.WorkflowServiceHost>必須註冊為鎖定擁有者。</span><span class="sxs-lookup"><span data-stu-id="a4f78-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when a <xref:System.ServiceModel.Activities.WorkflowServiceHost> must be registered as a lock owner.</span></span> <span data-ttu-id="a4f78-115">應使用 <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> 參數的 `context` 方法，將目前工作流程的執行個體 ID 提供給執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-115">The instance ID of the current workflow should be provided to the instance store using <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> method of the `context` parameter.</span></span>

     <span data-ttu-id="a4f78-116">下列程式碼片段示範如何實作 CreateWorkflowOwner 命令，以指派明確的鎖定擁有人。</span><span class="sxs-lookup"><span data-stu-id="a4f78-116">The following code snippet demonstrates how to implement the CreateWorkflowOwner command to assign an explicit lock owner.</span></span>

    ```csharp
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");
    ...
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()
    {
        InstanceOwnerMetadata =
        {
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },
        }
    };
    InstanceHandle ownerHandle = store.CreateInstanceHandle();
    store.DefaultInstanceOwner = store.Execute(
                                   ownerHandle,
                                   createCommand,
                                   TimeSpan.FromSeconds(30)).InstanceOwner;
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });
    ```

- <span data-ttu-id="a4f78-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>：可以從執行個體存放區中移除鎖定擁有者的執行個體識別碼時，持續性引擎會傳送此命令至執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when the instance ID of a lock owner can be removed from the instance store.</span></span> <span data-ttu-id="a4f78-118">就像使用 <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand> 一樣，應由應用程式提供鎖定擁有人的 ID。</span><span class="sxs-lookup"><span data-stu-id="a4f78-118">As with <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, the ID of the lock owner should be provided by the application.</span></span>

     <span data-ttu-id="a4f78-119">下列程式碼片段示範如何使用 <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand> 來解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="a4f78-119">The following code snippet demonstrates how to release a lock using <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span></span>

    ```csharp
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)
    {
        handle.Free();
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);
        try
        {
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.
            Thread.Sleep(10000);
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));
        }
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }
        catch (Exception ex) { Log.Inform(ex.Message); }
        finally
        {
            handle.Free();
            store.DefaultInstanceOwner = null;
        }
    }
    ```

     <span data-ttu-id="a4f78-120">當子執行個體執行時，應在 Try/Catch 區塊中叫用上述方法。</span><span class="sxs-lookup"><span data-stu-id="a4f78-120">The above method should be called in a Try/Catch block when a child instance is run.</span></span>

    ```csharp
    try
    {
        childInstance.Run();
    }
    catch (Exception)
    {
        throw ;
    }
    finally
    {
        FreeHandleAndDeleteOwner(store, ownerHandle);
    }
    ```

- <span data-ttu-id="a4f78-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>：使用工作流程的執行個體索引鍵載入工作流程執行個體時，持續性引擎會傳送此命令至執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: The persistence engine sends this command to the instance store when a workflow instance is to be loaded using the workflow’s instance key.</span></span> <span data-ttu-id="a4f78-122">可以使用命令的 <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> 參數來判斷執行個體索引鍵的 ID。</span><span class="sxs-lookup"><span data-stu-id="a4f78-122">The ID of the instance key can be determined by using the <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parameter of the command.</span></span>

- <span data-ttu-id="a4f78-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>：持續性引擎會將此命令傳送至執行個體存放區，才能建立可以載入工作流程的工作流程主機擷取持續性工作流程的啟動參數。</span><span class="sxs-lookup"><span data-stu-id="a4f78-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: The persistence engine sends this command to the instance store to retrieve activation parameters for persisted workflows in order to create a workflow host that can then load workflows.</span></span> <span data-ttu-id="a4f78-124">在找到可以啟動的執行個體時，引擎會傳送此命令，以回應向主機發出 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> 的執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-124">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> to the host when it locates an instance that can be activated.</span></span> <span data-ttu-id="a4f78-125">應輪詢執行個體存放區，以判斷是否有可啟動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a4f78-125">The instance store should be polled to determine if there are workflows that can be activated.</span></span>

- <span data-ttu-id="a4f78-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>：持續性引擎會將此命令傳送至載入可執行工作流程執行個體的執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: The persistence engine sends this command to the instance store to load runnable workflow instances.</span></span> <span data-ttu-id="a4f78-127">在找到可以執行的執行個體時，引擎會傳送此命令，以回應向主機發出 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> 的執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-127">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> to the host when it locates an instance that can be run.</span></span> <span data-ttu-id="a4f78-128">執行個體存放區應輪詢可以執行的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a4f78-128">The instance store should poll for workflows that can be run.</span></span> <span data-ttu-id="a4f78-129">下列程式碼片段示範如何在執行個體存放區中輪詢可執行或啟動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a4f78-129">The following code snippet demonstrates polling an instance store for workflows that can be run or activated.</span></span>

    ```csharp
    public void PollForEvents()
    {
        InstanceOwner[] storeOwners = this.GetInstanceOwners();

        foreach (InstanceOwner owner in storeOwners)
        {
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))
            {
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))
                {
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivatable);
                    if (hasRunnable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))
                {
                   bool hasActivatable = GetActivatableEvents(this.StoreId, owner.InstanceOwnerId);
                   if (hasActivatable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
            }
        }
    }
    ```

     <span data-ttu-id="a4f78-130">在上面的程式碼片段中，執行個體存放區會查詢可用的事件，並檢查每一個事件以判斷其是否為<xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> 事件。</span><span class="sxs-lookup"><span data-stu-id="a4f78-130">In the above code snippet, the instance store queries the events available and examines each one to determine if it is a <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> event.</span></span> <span data-ttu-id="a4f78-131">如果找到此類事件，會呼叫 <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A>，以通知主機傳送命令至執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f78-131">If one is found, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> is called to signal the host to send a command to the instance store.</span></span> <span data-ttu-id="a4f78-132">下列程式碼片段示範如何實作此命令的處理常式。</span><span class="sxs-lookup"><span data-stu-id="a4f78-132">The following code snippet demonstrates an implementation of a handler for this command.</span></span>

    ```csharp
    If (command is TryLoadRunnableWorkflowCommand)
    {
        Owner owner;
        CheckOwner(context, command.Name, out owner);
        // Checking instance.Owner is like an InstanceLockQueryResult.
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));

        XName ownerService = null;
        InstanceValue value;
        Instance runnableInstance = default(Instance);
        bool foundRunnableInstance = false;

        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);
        if (value != null && value.Value is XName)
        {
            ownerService = (XName)value.Value;
        }

        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)
        {
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)
            {
                continue;
            }

            if (ownerService != null)
            {
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);
                if (value == null || ((XName)value.Value) != ownerService)
                {
                    continue;
                }
            }

            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);
            if (value != null && value.Value != null && value.Value is string)
            {
                continue;
            }

            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")
            {
                runnableInstance = instance.Value;
                foundRunnableInstance = true;
            }

            if (!foundRunnableInstance)
            {
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)
                {
                    runnableInstance = instance.Value;
                    foundRunnableInstance = true;
                }
            }

            if (foundRunnableInstance)
            {
                runnableInstance.LockVersion++;
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;
                MemoryStore.instances[instance.Key] = runnableInstance;
                context.BindInstance(instance.Key);
                context.BindAcquiredLock(runnableInstance.LockVersion);

                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)
                {
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)
                {
                    if (keyEntry.Value.Completed)
                    {
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                    else
                    {
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                }
            }

            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);
            break;
        }
    }
    ```

    <span data-ttu-id="a4f78-133">在上面的程式碼片段中，執行個體存放區會搜尋可執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4f78-133">In the above code snippet, the instance store searches for runnable instances.</span></span> <span data-ttu-id="a4f78-134">如果找到執行個體，就會將它繫結到執行內容並載入。</span><span class="sxs-lookup"><span data-stu-id="a4f78-134">If an instance is found, it is bound to the execution context and loaded.</span></span>

## <a name="using-a-custom-instance-store"></a><span data-ttu-id="a4f78-135">使用自訂執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="a4f78-135">Using a custom instance store</span></span>

<span data-ttu-id="a4f78-136">若要實作自訂執行個體存放區，請將該執行個體存放區的執行個體指派至 <xref:System.Activities.WorkflowApplication.InstanceStore%2A>，並且實作 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a4f78-136">To implement a custom instance store, assign an instance of the instance store to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, and implement the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> method.</span></span> <span data-ttu-id="a4f78-137">請參閱[How to:建立並執行 a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md)教學課程，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a4f78-137">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) tutorial for specifics.</span></span>

## <a name="a-sample-instance-store"></a><span data-ttu-id="a4f78-138">執行個體存放區範例</span><span class="sxs-lookup"><span data-stu-id="a4f78-138">A sample instance store</span></span>

<span data-ttu-id="a4f78-139">下列程式碼範例是完整的執行個體存放區實作，取自[公司購買程序](./samples/corporate-purchase-process.md)範例。</span><span class="sxs-lookup"><span data-stu-id="a4f78-139">The following code sample is a complete instance store implementation, taken from the [Corporate Purchase Process](./samples/corporate-purchase-process.md) sample.</span></span> <span data-ttu-id="a4f78-140">此執行個體存放區會使用 XML 將工作流程資料保存至檔案。</span><span class="sxs-lookup"><span data-stu-id="a4f78-140">This instance store persists workflow data to a file using XML.</span></span>

```csharp
using System;
using System.Activities.DurableInstancing;
using System.Collections.Generic;
using System.IO;
using System.Runtime.DurableInstancing;
using System.Runtime.Serialization;
using System.ServiceModel.Persistence;
using System.Xml;
using System.Xml.Linq;

namespace Microsoft.Samples.WF.PurchaseProcess
{

    public class XmlWorkflowInstanceStore : InstanceStore
    {
        Guid ownerInstanceID;

        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())
        {

        }

        public XmlWorkflowInstanceStore(Guid id)
        {
            ownerInstanceID = id;
        }

        //Synchronous version of the Begin/EndTryCommand functions
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)
        {
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));
        }

        //The persistence engine will send a variety of commands to the configured InstanceStore,
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.
        //This method is where we will handle those commands
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)
        {
            IDictionary<XName, InstanceValue> data = null;

            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle
            if (command is CreateWorkflowOwnerCommand)
            {
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());
            }
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key
            else if (command is SaveWorkflowCommand)
            {
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;
                data = saveCommand.InstanceData;

                Save(data);
            }
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle
            else if (command is LoadWorkflowCommand)
            {
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);

                try
                {
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))
                    {
                        data = LoadInstanceDataFromFile(inputStream);
                        //load the data into the persistence Context
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);
                    }
                }
                catch (Exception exception)
                {
                    throw new PersistenceException(exception.Message);
                }
            }

            return new CompletedAsyncResult<bool>(true, callback, state);
        }

        protected override bool EndTryCommand(IAsyncResult result)
        {
            return CompletedAsyncResult<bool>.End(result);
        }

        //Reads data from xml file and creates a dictionary based off of that.
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)
        {
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();

            NetDataContractSerializer s = new NetDataContractSerializer();

            XmlReader rdr = XmlReader.Create(inputStream);
            XmlDocument doc = new XmlDocument();
            doc.Load(rdr);

            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");
            foreach (XmlElement instanceElement in instances)
            {
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");
                XName key = (XName)DeserializeObject(s, keyElement);

                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");
                object value = DeserializeObject(s, valueElement);
                InstanceValue instVal = new InstanceValue(value);

                data.Add(key, instVal);
            }

            return data;
        }

        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)
        {
            object deserializedObject = null;

            MemoryStream stm = new MemoryStream();
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);
            element.WriteContentTo(wtr);
            wtr.Flush();
            stm.Position = 0;

            deserializedObject = serializer.Deserialize(stm);

            return deserializedObject;
        }

        //Saves the persistence data to an xml file.
        void Save(IDictionary<XName, InstanceValue> instanceData)
        {
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);
            XmlDocument doc = new XmlDocument();
            doc.LoadXml("<InstanceValues/>");

            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)
            {
                XmlElement newInstance = doc.CreateElement("InstanceValue");

                XmlElement newKey = SerializeObject("key", valPair.Key, doc);
                newInstance.AppendChild(newKey);

                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);
                newInstance.AppendChild(newValue);

                doc.DocumentElement.AppendChild(newInstance);
            }
            doc.Save(fileName);
       }

        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)
        {
            NetDataContractSerializer s = new NetDataContractSerializer();
            XmlElement newElement = doc.CreateElement(elementName);
            MemoryStream stm = new MemoryStream();

            s.Serialize(stm, o);
            stm.Position = 0;
            StreamReader rdr = new StreamReader(stm);
            newElement.InnerXml = rdr.ReadToEnd();

            return newElement;
        }
    }
}
```
