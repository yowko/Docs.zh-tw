---
title: 如何：使用 DataContractJsonSerializer
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 5e521621dd3ec8e82a860590e66c1c4da95fd3b8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180213"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="babdc-102">如何：使用 DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="babdc-102">How to: use DataContractJsonSerializer</span></span>
<span data-ttu-id="babdc-103">JSON (JavaScript 物件標記法) 是一種有效率的資料編碼格式，可以在用戶端瀏覽器與啟用 AJAX 的 Web 服務之間啟用快速的小量資料交換作業。</span><span class="sxs-lookup"><span data-stu-id="babdc-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="babdc-104">本文示範如何將 .NET 類型物件序列化為 JSON 編碼資料，然後將 JSON 格式的資料還原序列化回 .NET 類型的實例。</span><span class="sxs-lookup"><span data-stu-id="babdc-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="babdc-105">這個範例會使用資料合約來示範使用者定義的 `Person` 類型的序列化和還原序列化，並使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。</span><span class="sxs-lookup"><span data-stu-id="babdc-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="babdc-106">一般來說，當您在服務作業中使用資料合約型別，而這些類型是在已啟用 AJAX 的端點上公開時，Windows Communication Foundation （WCF）會自動處理 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="babdc-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="babdc-107">不過，在某些情況下，您可能需要直接使用 JSON 資料。</span><span class="sxs-lookup"><span data-stu-id="babdc-107">However, in some cases you may need to work with JSON data directly.</span></span>

> [!NOTE]
> <span data-ttu-id="babdc-108">本文是關於 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。</span><span class="sxs-lookup"><span data-stu-id="babdc-108">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="babdc-109">對於涉及序列化和還原序列化 JSON 的大部分案例，我們建議您在 system.string[命名空間](../../../standard/serialization/system-text-json-overview.md)中的工具。</span><span class="sxs-lookup"><span data-stu-id="babdc-109">For most scenarios that involve serializing and deserializing JSON, we recommend the tools in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span> 
  
 <span data-ttu-id="babdc-110">本文是以[DataContractJsonSerializer 範例](../samples/json-serialization.md)為基礎。</span><span class="sxs-lookup"><span data-stu-id="babdc-110">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="babdc-111">若要定義人員類型的資料合約</span><span class="sxs-lookup"><span data-stu-id="babdc-111">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="babdc-112">將 `Person` 附加到類別，並將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性附加到要序列化的成員中，以定義 <xref:System.Runtime.Serialization.DataMemberAttribute> 的資料合約。</span><span class="sxs-lookup"><span data-stu-id="babdc-112">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="babdc-113">如需資料合約的詳細資訊，請參閱[設計服務合約](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="babdc-113">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="babdc-114">若要將型別 Person 的執行個體序列化為 JSON</span><span class="sxs-lookup"><span data-stu-id="babdc-114">To serialize an instance of type Person to JSON</span></span>  
  
> [!NOTE]
> <span data-ttu-id="babdc-115">如果在序列化伺服器上的傳出回復期間發生錯誤，或基於其他原因，則可能不會將它當做錯誤傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="babdc-115">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  

1. <span data-ttu-id="babdc-116">建立 `Person` 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="babdc-116">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="babdc-117">使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>，將 `Person` 物件序列化為記憶體資料流程。</span><span class="sxs-lookup"><span data-stu-id="babdc-117">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="babdc-118">使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 方法，將 JSON 資料寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="babdc-118">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="babdc-119">顯示 JSON 輸出。</span><span class="sxs-lookup"><span data-stu-id="babdc-119">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="babdc-120">若要從 JSON 還原序列化型別 Person 的執行個體</span><span class="sxs-lookup"><span data-stu-id="babdc-120">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="babdc-121">使用 `Person` 的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> 方法，將 JSON 編碼的資料還原序列化為 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="babdc-121">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="babdc-122">顯示結果。</span><span class="sxs-lookup"><span data-stu-id="babdc-122">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="babdc-123">範例</span><span class="sxs-lookup"><span data-stu-id="babdc-123">Example</span></span>  
  
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
> <span data-ttu-id="babdc-124">對於具有多個同名成員的資料合約，JSON 序列化程式會擲回序列化例外狀況，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="babdc-124">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="babdc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="babdc-125">See also</span></span>

- [<span data-ttu-id="babdc-126">.NET 中的 JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="babdc-126">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)

