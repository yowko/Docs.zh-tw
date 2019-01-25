---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: ad5436a60b5cd82b44931713d863eaeed791e264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723975"
---
# <a name="datacontractresolver"></a>DataContractResolver
此範例示範如何使用 <xref:System.Runtime.Serialization.DataContractResolver> 類別來自訂序列化和還原序列化程序。 此範例會示範如何使用 DataContractResolver，在序列化和還原序列化期間來回對應 CLR 型別與 xsi:type 表示。

## <a name="sample-details"></a>範例詳細資料
 此範例會定義下列 CLR 型別。

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 此範例會載入組件、擷取其中每個型別，然後序列化和還原序列化這些型別。 系統會將 <xref:System.Runtime.Serialization.DataContractResolver> 衍生類別的執行個體傳遞給 <xref:System.Runtime.Serialization.DataContractResolver> 建構函式，藉以將 <xref:System.Runtime.Serialization.DataContractSerializer> 插入序列化程序中，如下列範例所示。

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 然後，此範例會序列化這些 CLR 型別，如下列程式碼範例所示。

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 然後，此範例會還原序列化這些 xsi:type，如下列程式碼範例所示。

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 因為自訂 <xref:System.Runtime.Serialization.DataContractResolver> 已傳入 <xref:System.Runtime.Serialization.DataContractSerializer> 建構函式，所以系統會在序列化期間呼叫 <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>，以便將 CLR 型別對應至對等的 `xsi:type`。 同樣地，系統會在還原序列化期間呼叫 <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>，以便將 `xsi:type` 對應至對等的 CLR 型別。 在此範例中，<xref:System.Runtime.Serialization.DataContractResolver> 定義的方式如下列範例所示。

 下列程式碼範例是從 <xref:System.Runtime.Serialization.DataContractResolver> 衍生的類別。

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 在此範例中，類型專案會產生包含此範例中使用之所有類型的組件。 使用此專案加入、移除或修改即將序列化的類型。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1.  使用 Visual Studio 2012，請開啟 DCRSample.sln 方案檔案。

2.  若要執行方案，請按 F5

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>另請參閱
- [使用資料合約解析程式](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
