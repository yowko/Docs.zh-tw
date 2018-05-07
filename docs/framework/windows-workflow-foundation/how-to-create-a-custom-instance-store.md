---
title: HOW TO：建立自訂執行個體存放區
ms.date: 03/30/2017
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
ms.openlocfilehash: 96f713765178011b9122afcb31e4721e9184d1d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-instance-store"></a>HOW TO：建立自訂執行個體存放區
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 包含 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>，這是使用 SQL Server 來保存工作流程資料的執行個體存放區。 如果您的應用程式需要將工作流程資料保存在另一個媒體中，例如不同的資料庫或檔案系統，您可以實作自訂的執行個體存放區。 擴充抽象的 <xref:System.Runtime.DurableInstancing.InstanceStore> 類別，並實作進行實作所需的方法，即可建立自訂執行個體存放區。 自訂執行個體存放區的完整實作，請參閱[公司購買程序](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)範例。  
  
## <a name="implementing-the-begintrycommand-method"></a>實作 BeginTryCommand 方法  
 持續性引擎會將 <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> 傳送至執行個體存放區。 `command` 參數的型別會表示所執行的命令；此參數可以是下列其中一種型別：  
  
-   <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>：需要將工作流程保存至儲存媒體中時，持續性引擎會將此命令傳送至執行個體存放區。 工作流程持續性資料已提供給在<xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> 參數之 `command` 成員中的方法。  
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowCommand>：需要從儲存媒體載入工作流程時，持續性引擎會將此命令傳送至執行個體存放區。 所要載入之工作流程的執行個體 ID 會提供給 `instanceId` 參數的 <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> 屬性的 `context` 參數中的方法。  
  
-   <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>：必須將 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 登錄為鎖定擁有人時，持續性引擎會將此命令傳送至執行個體存放區。 應使用 <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> 參數的 `context` 方法，將目前工作流程的執行個體 ID 提供給執行個體存放區。  
  
     下列程式碼片段示範如何實作 CreateWorkflowOwner 命令，以指派明確的鎖定擁有人。  
  
    ```  
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
  
-   <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>：可以從執行個體存放區中移除鎖定擁有人的執行個體 ID 時，持續性引擎會將此命令傳送至執行個體存放區。 就像使用 <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand> 一樣，應由應用程式提供鎖定擁有人的 ID。  
  
     下列程式碼片段示範如何使用 <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand> 來解除鎖定。  
  
    ```  
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
  
     當子執行個體執行時，應在 Try/Catch 區塊中叫用上述方法。  
  
    ```  
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
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>：需要使用工作流程的執行個體索引鍵載入工作流程執行個體時，持續性引擎會將此命令傳送至執行個體存放區。 可以使用命令的 <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> 參數來判斷執行個體索引鍵的 ID。  
  
-   <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>：持續性引擎會將這個命令傳送至執行個體存放區，以擷取持續工作流程的啟動參數，進而建立可以載入工作流程的工作流程主機。 在找到可以啟動的執行個體時，引擎會傳送此命令，以回應向主機發出 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> 的執行個體存放區。 應輪詢執行個體存放區，以判斷是否有可啟動的工作流程。  
  
-   <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>：持續性引擎會傳送這個命令至執行個體存放區，以載入可執行的工作流程執行個體。 在找到可以執行的執行個體時，引擎會傳送此命令，以回應向主機發出 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> 的執行個體存放區。 執行個體存放區應輪詢可以執行的工作流程。 下列程式碼片段示範如何在執行個體存放區中輪詢可執行或啟動的工作流程。  
  
    ```  
    public void PollForEvents()  
    {  
        InstanceOwner[] storeOwners = this.GetInstanceOwners();  
  
        foreach (InstanceOwner owner in storeOwners)  
        {  
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))  
            {  
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))  
                {  
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivable);  
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
                   bool hasActivable = GetActivableEvents(this.StoreId, owner.InstanceOwnerId);  
                   if (hasActivable)  
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
  
     在上面的程式碼片段中，執行個體存放區會查詢可用的事件，並檢查每一個事件以判斷其是否為<xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> 事件。 如果找到此類事件，會呼叫 <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A>，以通知主機傳送命令至執行個體存放區。  下列程式碼片段示範如何實作此命令的處理常式。  
  
    ```  
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
  
     在上面的程式碼片段中，執行個體存放區會搜尋可執行的執行個體。 如果找到執行個體，就會將它繫結到執行內容並載入。  
  
## <a name="using-a-custom-instance-store"></a>使用自訂執行個體存放區  
 若要實作自訂執行個體存放區，請將該執行個體存放區的執行個體指派至 <xref:System.Activities.WorkflowApplication.InstanceStore%2A>，並且實作 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>方法。  請參閱[How to： 建立和執行長時間執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)教學課程的細節。  
  
## <a name="a-sample-instance-store"></a>執行個體存放區範例  
 下列程式碼範例是完整的執行個體存放區實作，取自[公司購買程序](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)範例。 此執行個體存放區會使用 XML 將工作流程資料保存至檔案。  
  
```  
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
