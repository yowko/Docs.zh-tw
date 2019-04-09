---
title: DataContract Surrogate
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 663f168ebbba2238be814791fd0d75e211a469ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196420"
---
# <a name="datacontract-surrogate"></a>DataContract Surrogate
這個範例示範如何使用資料合約 Surrogate 類別來自訂像是序列化 (Serialization)、還原序列化 (Deserialization)、結構描述匯出以及結構描述匯入等程序。 此範例示範如何在用戶端和伺服器的案例，其中資料會序列化並傳送 Windows Communication Foundation (WCF) 用戶端與服務之間使用代理。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此範例使用下列服務合約：  
  
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
  
 `AddEmployee` 作業允許使用者新增新進員工的資料，而 `GetEmployee` 作業則支援根據名字搜尋員工。  
  
 這些作業使用下列資料型別：  
  
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
  
 在 `Employee` 型別中，由於 `Person` 類別 (如下列範例程式碼所示) 不是有效的資料合約類別，因此 <xref:System.Runtime.Serialization.DataContractSerializer> 無法加以序列化。  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 您可以將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至 `Person` 類別，但是不一定可行。 例如，`Person` 類別可能是在您無法控制的其他組件中定義的。  
  
 在這個限制下，有一種方法可以序列化 `Person` 類別，即是使用標示為 <xref:System.Runtime.Serialization.DataContractAttribute> 的另一個類別來替代它，然後將必要的資料整個複製到新類別。 這麼做的目的是要將 `Person` 類別對 <xref:System.Runtime.Serialization.DataContractSerializer> 顯示為 DataContract。 請注意，這只是序列化非資料合約類別的其中一種方法。  
  
 此範例邏輯上是使用名為 `Person` 的不同類別來取代 `PersonSurrogated` 類別。  
  
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
  
 但實際上是使用資料合約 Surrogate 來達成這項取代。 資料合約 Surrogate 是實作 <xref:System.Runtime.Serialization.IDataContractSurrogate> 的類別。 在這個範例中，`AllowNonSerializableTypesSurrogate` 類別會實作這個介面。  
  
 在介面實作中，第一項工作就是建立從 `Person` 到 `PersonSurrogated` 的型別對應。 序列化階段與結構描述匯出階段都會用到這個型別對應。 這種對應可以藉由實作 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> 方法來達成。  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> 方法會在序列化期間，將 `Person` 執行個體對應至 `PersonSurrogated` 執行個體，如下列範例程式碼所示。  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> 方法會提供反向對應以進行還原序列化，如下列範例程式碼所示。  
  
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
  
 為了在結構描述匯入期間將 `PersonSurrogated` 資料合約對應至現有 `Person` 類別，範例會實作 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> 方法，如下列範例程式碼所示。  
  
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
  
 下列範例程式碼會完成 <xref:System.Runtime.Serialization.IDataContractSurrogate> 介面的實作。  
  
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
  
 在這個範例中，`AllowNonSerializableTypesAttribute` 屬性在 ServiceModel 中啟用了 Surrogate。 依上述 `IPersonnelDataService` 服務合約看來，開發人員或許會想要在他們的服務合約上套用這個屬性， 因為這個屬性會實作 `IContractBehavior`，並在 `ApplyClientBehavior` 和 `ApplyDispatchBehavior` 方法中設定作業上的 Surrogate。  
  
 但對本例而言，這個屬性並非必要，它只是在範例中做示範之用。 使用者也可以選擇使用程式碼或組態，透過手動方式新增類似的 `IContractBehavior`、`IEndpointBehavior` 或 `IOperationBehavior` 來啟用 Surrogate。  
  
 `IContractBehavior` 實作會尋找使用 DataContract 的作業，而尋找的方式是檢查這些作業是否註冊了行為 `DataContractSerializerOperationBehavior`。 如果沒有，就會在該行為上設定 `DataContractSurrogate` 屬性。 下列範例程式碼示範如何做到這點。 在這個作業行為上設定 Surrogate，就可以啟用 Surrogate 來進行序列化和還原序列化。  
  
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
  
 此外，還必須執行其他步驟，才能將 Surrogate 插入以供中繼資料產生期間使用。 有一個機制可以用來達到這個目的，即提供 `IWsdlExportExtension`，而這也是本範例所示範的。 另一個方法則是直接修改 `WsdlExporter`。  
  
 `AllowNonSerializableTypesAttribute`屬性會實作`IWsdlExportExtension`和`IContractBehavior`。 延伸模組可以是`IContractBehavior`或`IEndpointBehavior`在此情況下。 `IWsdlExportExtension.ExportContract` 方法實作會將此延伸新增至 DataContract 結構描述產生期間所使用的 `XsdDataContractExporter`，以啟用 Surrogate。 下列程式碼片段示範如何執行這項操作。  
  
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
  
 當您執行範例時，用戶端會在呼叫 AddEmployee 之後接著呼叫 GetEmployee，以檢查第一項呼叫是否成功。 GetEmployee 作業要求的結果會顯示在用戶端主控台視窗中。 GetEmployee 作業必須成功找到員工，並列印 「 找到 」。  
  
> [!NOTE]
>  這個範例示範如何插入 Surrogate 以進行序列化、還原序列化和中繼資料產生作業， 但是不示範如何插入 Surrogate，以從中繼資料產生程式碼。 若要查看如何使用 「 代理 」 插入用戶端程式碼產生的範例，請參閱[自訂 WSDL 發行物](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)範例。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 版本，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
