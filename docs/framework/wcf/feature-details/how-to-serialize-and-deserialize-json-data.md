---
title: HOW TO：序列化及還原序列化 JSON 資料
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 7edce66a23021fa03a6f98b3b847a5b671c17124
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336950"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="68571-102">HOW TO：序列化和還原序列化 JSON 資料</span><span class="sxs-lookup"><span data-stu-id="68571-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="68571-103">JSON (JavaScript 物件標記法) 是一種有效率的資料編碼格式，可以在用戶端瀏覽器與啟用 AJAX 的 Web 服務之間啟用快速的小量資料交換作業。</span><span class="sxs-lookup"><span data-stu-id="68571-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="68571-104">這篇文章會示範如何將.NET 型別物件序列化為 JSON 編碼資料，然後以 JSON 格式的資料還原序列化的.NET 型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="68571-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="68571-105">此範例會使用資料合約以示範序列化與還原序列化的使用者定義`Person`型別，並使用<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。</span><span class="sxs-lookup"><span data-stu-id="68571-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="68571-106">一般來說，JSON 序列化和還原序列化會自動處理由 Windows Communication Foundation (WCF) 啟用 AJAX 的端點上所公開的服務作業中使用資料合約型別時。</span><span class="sxs-lookup"><span data-stu-id="68571-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="68571-107">不過，在某些情況下，您可能需要直接處理 JSON 資料。</span><span class="sxs-lookup"><span data-stu-id="68571-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
>  <span data-ttu-id="68571-108">如果在伺服器上，或因其他原因的傳出回覆序列化期間發生錯誤，它可能不會被傳回至用戶端為錯誤。</span><span class="sxs-lookup"><span data-stu-id="68571-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="68571-109">這篇文章根據[JSON 序列化](../samples/json-serialization.md)範例。</span><span class="sxs-lookup"><span data-stu-id="68571-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="68571-110">若要定義 Person 類型的資料合約</span><span class="sxs-lookup"><span data-stu-id="68571-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="68571-111">將 `Person` 附加到類別，並將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性附加到要序列化的成員中，以定義 <xref:System.Runtime.Serialization.DataMemberAttribute> 的資料合約。</span><span class="sxs-lookup"><span data-stu-id="68571-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="68571-112">如需有關資料合約的詳細資訊，請參閱[設計服務合約](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="68571-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="68571-113">若要將型別 Person 的執行個體序列化為 JSON</span><span class="sxs-lookup"><span data-stu-id="68571-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="68571-114">建立 `Person` 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68571-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="68571-115">序列化`Person`要使用的記憶體資料流物件<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。</span><span class="sxs-lookup"><span data-stu-id="68571-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="68571-116">使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 方法，將 JSON 資料寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="68571-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="68571-117">顯示 JSON 輸出。</span><span class="sxs-lookup"><span data-stu-id="68571-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="68571-118">若要從 JSON 還原序列化型別 Person 的執行個體</span><span class="sxs-lookup"><span data-stu-id="68571-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="68571-119">使用 `Person` 的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> 方法，將 JSON 編碼的資料還原序列化為 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="68571-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="68571-120">顯示結果。</span><span class="sxs-lookup"><span data-stu-id="68571-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="68571-121">範例</span><span class="sxs-lookup"><span data-stu-id="68571-121">Example</span></span>  
  
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
>  <span data-ttu-id="68571-122">對於具有多個同名成員的資料合約，JSON 序列化程式會擲回序列化例外狀況，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="68571-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68571-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68571-123">See also</span></span>

- [<span data-ttu-id="68571-124">獨立 JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="68571-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="68571-125">支援 JSON 和其他資料傳輸格式</span><span class="sxs-lookup"><span data-stu-id="68571-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
