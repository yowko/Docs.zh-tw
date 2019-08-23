---
title: HOW TO：序列化及還原序列化 JSON 資料
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0bebdbb3d74d58db093c4ec1e0e88138c7080335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947902"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>作法：序列化和還原序列化 JSON 資料
JSON (JavaScript 物件標記法) 是一種有效率的資料編碼格式，可以在用戶端瀏覽器與啟用 AJAX 的 Web 服務之間啟用快速的小量資料交換作業。  
  
 本文示範如何將 .NET 類型物件序列化為 JSON 編碼資料, 然後將 JSON 格式的資料還原序列化回 .NET 類型的實例。 這個範例會使用資料合約來示範使用者自訂`Person`類型的序列化和還原序列化, 並使用。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
 一般來說, 當您在服務作業中使用資料合約型別, 而這些類型是在已啟用 AJAX 的端點上公開時, Windows Communication Foundation (WCF) 會自動處理 JSON 序列化和還原序列化。 不過, 在某些情況下, 您可能需要直接使用 JSON 資料。   
  
> [!NOTE]
> 如果在序列化伺服器上的傳出回復期間發生錯誤, 或基於其他原因, 則可能不會將它當做錯誤傳回給用戶端。  
  
 本文是以[JSON 序列化](../samples/json-serialization.md)範例為基礎。  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>若要定義人員類型的資料合約 
  
1. 將 `Person` 附加到類別，並將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性附加到要序列化的成員中，以定義 <xref:System.Runtime.Serialization.DataMemberAttribute> 的資料合約。 如需資料合約的詳細資訊, 請參閱[設計服務合約](../designing-service-contracts.md)。  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>若要將型別 Person 的執行個體序列化為 JSON  
  
1. 建立 `Person` 型別的執行個體。  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. 使用,<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>將物件序列化為記憶體資料流程。 `Person`  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. 使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 方法，將 JSON 資料寫入資料流。  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. 顯示 JSON 輸出。  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>若要從 JSON 還原序列化型別 Person 的執行個體  
  
1. 使用 `Person` 的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> 方法，將 JSON 編碼的資料還原序列化為 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 的新執行個體。  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. 顯示結果。  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>範例  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    // Create User object.  
    var user = new User("Bob", 42);  
  
    // Create a stream to serialize the object to.  
    var ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    var ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    var deserializedUser = new User();  
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
> 對於具有多個同名成員的資料合約，JSON 序列化程式會擲回序列化例外狀況，如下列範例程式碼所示。  
  
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
  
## <a name="see-also"></a>另請參閱

- [獨立 JSON 序列化](stand-alone-json-serialization.md)
- [JSON 和其他資料傳輸格式的支援](support-for-json-and-other-data-transfer-formats.md)
