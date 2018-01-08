---
title: "HOW TO：序列化及還原序列化 JSON 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 994ccb677d1376eff5b889a0a4ddfe072557bdea
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>HOW TO：序列化及還原序列化 JSON 資料
JSON (JavaScript 物件標記法) 是一種有效率的資料編碼格式，可以在用戶端瀏覽器與啟用 AJAX 的 Web 服務之間啟用快速的小量資料交換作業。  
  
 本主題示範如何將 .NET 型別物件序列化為 JSON 編碼資料，然後透過 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>，將 JSON 格式的資料還原序列化為 .NET 型別執行個體。 這個範例會使用資料合約來示範使用者定義之 `Person` 型別的序列化與還原序列化。  
  
 一般來說，當您在啟用 AJAX 的端點上所公開的服務作業中使用資料合約類型時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會自動處理 JSON 序列化和還原序列化。 但是，在某些情況下您可能需要直接使用 JSON 資料，而本主題就是要示範這種情況。  
  
> [!NOTE]
>  如果在伺服器的傳出回覆序列化期間發生錯誤，或是因為某些原因導致回覆作業擲回例外狀況，該錯誤可能不會被當成錯誤傳回用戶端。  
  
 本主題根據[JSON 序列化](../../../../docs/framework/wcf/samples/json-serialization.md)範例。  
  
### <a name="to-define-the-data-contract-for-a-person"></a>若要定義 Person 的資料合約  
  
1.  將 `Person` 附加到類別，並將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性附加到要序列化的成員中，以定義 <xref:System.Runtime.Serialization.DataMemberAttribute> 的資料合約。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]資料合約，請參閱[設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)。  
  
    ```csharp  
    [DataContract]  
    internal class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
    ```  
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>若要將型別 Person 的執行個體序列化為 JSON  
  
1.  建立 `Person` 型別的執行個體。  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  使用 `Person`，將 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 物件序列化為記憶體資料流。  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 方法，將 JSON 資料寫入資料流。  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  顯示 JSON 輸出。  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>若要從 JSON 還原序列化型別 Person 的執行個體  
  
1.  使用 `Person` 的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> 方法，將 JSON 編碼的資料還原序列化為 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 的新執行個體。  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  顯示結果。  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>範例  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  對於具有多個同名成員的資料合約，JSON 序列化程式會擲回序列化例外狀況，如下列範例程式碼所示。  
  
```csharp  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}

[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [獨立 JSON 序列化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [JSON 和其他資料傳輸格式的支援](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
