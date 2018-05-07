---
title: 使用資料合約解析程式
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 467977374e9e2b4a369be7ce467ced1b0dca1195
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-data-contract-resolver"></a>使用資料合約解析程式
資料合約解析程式可讓您動態設定已知型別。 在序列化或還原序列化資料合約未預期的型別時，就會需要已知型別。 如需已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。 已知型別通常會以靜態方式指定。 這表示，實作作業時，您必須知道此作業可能會接收的所有可能型別。 不過，這項條件在某些情況中並不成立，此時，能夠以動態方式指定已知型別就很重要。  
  
## <a name="creating-a-data-contract-resolver"></a>建立資料合約解析程式  
 建立資料合約解析程式需要實作兩個方法：<xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> 與 <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>。 這兩個方法會分別實作序列化與還原序列化期間使用的回呼。 <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> 方法會在序列化期間叫用，此方法會取得資料合約型別，並且對應到 `xsi:type` 名稱與命名空間。 <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> 方法會在還原序列化期間叫用，此方法會取得 `xsi:type` 名稱與命名空間，並且解析為資料合約型別。 這兩個方法都有 `knownTypeResolver` 參數，可以使用您實作中預設的已知型別解析程式。  
  
 下列範例顯示如何實作 <xref:System.Runtime.Serialization.DataContractResolver> 的對應，處理衍生自 `Customer` 資料合約型別，命名為 `Person` 的資料合約型別。  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 一旦定義了 <xref:System.Runtime.Serialization.DataContractResolver>，只要傳遞至 <xref:System.Runtime.Serialization.DataContractSerializer> 建構函式即可使用，如下列範例所示。  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 您可以在 <xref:System.Runtime.Serialization.DataContractSerializer> 或 <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> 方法的呼叫中指定 <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A>，如下列範例所示。  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 您也可以在 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 上進行設定，如下列範例所示。  
  
```  
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 您可以透過實作可套用至服務的屬性，以宣告方式指定資料合約解析程式。  如需詳細資訊，請參閱[KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)範例。 這個範例會實作稱為"KnownAssembly"的屬性，將加上自訂資料合約解析程式服務的行為。  
  
## <a name="see-also"></a>另請參閱  
 [資料合約已知類型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [DataContractSerializer 範例](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
