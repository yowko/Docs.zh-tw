---
title: DataContract Surrogate
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 5729943f455d4669f047eb2d86fb7292824c0f2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645414"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="0f36f-102">DataContract Surrogate</span><span class="sxs-lookup"><span data-stu-id="0f36f-102">DataContract Surrogate</span></span>
<span data-ttu-id="0f36f-103">這個範例示範如何使用資料合約 Surrogate 類別來自訂像是序列化 (Serialization)、還原序列化 (Deserialization)、結構描述匯出以及結構描述匯入等程序。</span><span class="sxs-lookup"><span data-stu-id="0f36f-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="0f36f-104">此範例示範如何在用戶端和伺服器的案例，其中資料會序列化並傳送 Windows Communication Foundation (WCF) 用戶端與服務之間使用代理。</span><span class="sxs-lookup"><span data-stu-id="0f36f-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f36f-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="0f36f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0f36f-106">此範例使用下列服務合約：</span><span class="sxs-lookup"><span data-stu-id="0f36f-106">The sample uses the following service contract:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 <span data-ttu-id="0f36f-107">`AddEmployee` 作業允許使用者新增新進員工的資料，而 `GetEmployee` 作業則支援根據名字搜尋員工。</span><span class="sxs-lookup"><span data-stu-id="0f36f-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="0f36f-108">這些作業使用下列資料型別：</span><span class="sxs-lookup"><span data-stu-id="0f36f-108">These operations use the following data type:</span></span>  
  
```  
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 <span data-ttu-id="0f36f-109">在 `Employee` 型別中，由於 `Person` 類別 (如下列範例程式碼所示) 不是有效的資料合約類別，因此 <xref:System.Runtime.Serialization.DataContractSerializer> 無法加以序列化。</span><span class="sxs-lookup"><span data-stu-id="0f36f-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="0f36f-110">您可以將 `DataContract` 屬性套用至 `Person` 類別，但是不一定可行。</span><span class="sxs-lookup"><span data-stu-id="0f36f-110">You can apply the `DataContract` attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="0f36f-111">例如，`Person` 類別可能是在您無法控制的其他組件中定義的。</span><span class="sxs-lookup"><span data-stu-id="0f36f-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="0f36f-112">在這個限制下，有一種方法可以序列化 `Person` 類別，即是使用標示為 `DataContractAttribute` 的另一個類別來替代它，然後將必要的資料整個複製到新類別。</span><span class="sxs-lookup"><span data-stu-id="0f36f-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with `DataContractAttribute` and copy over necessary data to the new class.</span></span> <span data-ttu-id="0f36f-113">這麼做的目的是要將 `Person` 類別對 <xref:System.Runtime.Serialization.DataContractSerializer> 顯示為 DataContract。</span><span class="sxs-lookup"><span data-stu-id="0f36f-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="0f36f-114">請注意，這只是序列化非資料合約類別的其中一種方法。</span><span class="sxs-lookup"><span data-stu-id="0f36f-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="0f36f-115">此範例邏輯上是使用名為 `Person` 的不同類別來取代 `PersonSurrogated` 類別。</span><span class="sxs-lookup"><span data-stu-id="0f36f-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```  
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 <span data-ttu-id="0f36f-116">但實際上是使用資料合約 Surrogate 來達成這項取代。</span><span class="sxs-lookup"><span data-stu-id="0f36f-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="0f36f-117">資料合約 Surrogate 是實作 <xref:System.Runtime.Serialization.IDataContractSurrogate> 的類別。</span><span class="sxs-lookup"><span data-stu-id="0f36f-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="0f36f-118">在這個範例中，`AllowNonSerializableTypesSurrogate` 類別會實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="0f36f-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="0f36f-119">在介面實作中，第一項工作就是建立從 `Person` 到 `PersonSurrogated` 的型別對應。</span><span class="sxs-lookup"><span data-stu-id="0f36f-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="0f36f-120">序列化階段與結構描述匯出階段都會用到這個型別對應。</span><span class="sxs-lookup"><span data-stu-id="0f36f-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="0f36f-121">這種對應可以藉由實作 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> 方法來達成。</span><span class="sxs-lookup"><span data-stu-id="0f36f-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```  
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="0f36f-122"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> 方法會在序列化期間，將 `Person` 執行個體對應至 `PersonSurrogated` 執行個體，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0f36f-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```  
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="0f36f-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> 方法會提供反向對應以進行還原序列化，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0f36f-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```  
public object GetDeserializedObject(object obj,   
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="0f36f-124">為了在結構描述匯入期間將 `PersonSurrogated` 資料合約對應至現有 `Person` 類別，範例會實作 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> 方法，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0f36f-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```  
public Type GetReferencedTypeOnImport(string typeName,   
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 <span data-ttu-id="0f36f-125">下列範例程式碼會完成 <xref:System.Runtime.Serialization.IDataContractSurrogate> 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="0f36f-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```  
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,   
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,   
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 <span data-ttu-id="0f36f-126">在這個範例中，`AllowNonSerializableTypesAttribute` 屬性在 ServiceModel 中啟用了 Surrogate。</span><span class="sxs-lookup"><span data-stu-id="0f36f-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="0f36f-127">依上述 `IPersonnelDataService` 服務合約看來，開發人員或許會想要在他們的服務合約上套用這個屬性，</span><span class="sxs-lookup"><span data-stu-id="0f36f-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="0f36f-128">因為這個屬性會實作 `IContractBehavior`，並在 `ApplyClientBehavior` 和 `ApplyDispatchBehavior` 方法中設定作業上的 Surrogate。</span><span class="sxs-lookup"><span data-stu-id="0f36f-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="0f36f-129">但對本例而言，這個屬性並非必要，它只是在範例中做示範之用。</span><span class="sxs-lookup"><span data-stu-id="0f36f-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="0f36f-130">使用者也可以選擇使用程式碼或組態，透過手動方式新增類似的 `IContractBehavior`、`IEndpointBehavior` 或 `IOperationBehavior` 來啟用 Surrogate。</span><span class="sxs-lookup"><span data-stu-id="0f36f-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="0f36f-131">`IContractBehavior` 實作會尋找使用 DataContract 的作業，而尋找的方式是檢查這些作業是否註冊了行為 `DataContractSerializerOperationBehavior`。</span><span class="sxs-lookup"><span data-stu-id="0f36f-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="0f36f-132">如果沒有，就會在該行為上設定 `DataContractSurrogate` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0f36f-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="0f36f-133">下列範例程式碼示範如何做到這點。</span><span class="sxs-lookup"><span data-stu-id="0f36f-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="0f36f-134">在這個作業行為上設定 Surrogate，就可以啟用 Surrogate 來進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f36f-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```  
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 <span data-ttu-id="0f36f-135">此外，還必須執行其他步驟，才能將 Surrogate 插入以供中繼資料產生期間使用。</span><span class="sxs-lookup"><span data-stu-id="0f36f-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="0f36f-136">有一個機制可以用來達到這個目的，即提供 `IWsdlExportExtension`，而這也是本範例所示範的。</span><span class="sxs-lookup"><span data-stu-id="0f36f-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="0f36f-137">另一個方法則是直接修改 `WsdlExporter`。</span><span class="sxs-lookup"><span data-stu-id="0f36f-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="0f36f-138">`AllowNonSerializableTypesAttribute`屬性會實作`IWsdlExportExtension`和`IContractBehavior`。</span><span class="sxs-lookup"><span data-stu-id="0f36f-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="0f36f-139">延伸模組可以是`IContractBehavior`或`IEndpointBehavior`在此情況下。</span><span class="sxs-lookup"><span data-stu-id="0f36f-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="0f36f-140">`IWsdlExportExtension.ExportContract` 方法實作會將此延伸新增至 DataContract 結構描述產生期間所使用的 `XsdDataContractExporter`，以啟用 Surrogate。</span><span class="sxs-lookup"><span data-stu-id="0f36f-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="0f36f-141">下列程式碼片段示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="0f36f-141">The following code snippet shows how to do this.</span></span>  
  
```  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 <span data-ttu-id="0f36f-142">當您執行範例時，用戶端會在呼叫 AddEmployee 之後接著呼叫 GetEmployee，以檢查第一項呼叫是否成功。</span><span class="sxs-lookup"><span data-stu-id="0f36f-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="0f36f-143">GetEmployee 作業要求的結果會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0f36f-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="0f36f-144">GetEmployee 作業必須成功找到員工，並列印 「 找到 」。</span><span class="sxs-lookup"><span data-stu-id="0f36f-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f36f-145">這個範例示範如何插入 Surrogate 以進行序列化、還原序列化和中繼資料產生作業，</span><span class="sxs-lookup"><span data-stu-id="0f36f-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="0f36f-146">但是不示範如何插入 Surrogate，以從中繼資料產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f36f-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="0f36f-147">若要查看如何使用 「 代理 」 插入用戶端程式碼產生的範例，請參閱[自訂 WSDL 發行物](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)範例。</span><span class="sxs-lookup"><span data-stu-id="0f36f-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0f36f-148">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0f36f-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0f36f-149">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0f36f-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0f36f-150">若要建置方案的 C# 版本，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0f36f-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0f36f-151">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0f36f-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f36f-152">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0f36f-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0f36f-153">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0f36f-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0f36f-154">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0f36f-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f36f-155">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0f36f-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a><span data-ttu-id="0f36f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f36f-156">See also</span></span>
