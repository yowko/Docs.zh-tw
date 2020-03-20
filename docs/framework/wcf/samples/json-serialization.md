---
title: 資料合同Jon序列化器樣品
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144626"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="ede10-102">資料合同Jon序列化器樣品</span><span class="sxs-lookup"><span data-stu-id="ede10-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="ede10-103">此示例用於<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。</span><span class="sxs-lookup"><span data-stu-id="ede10-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="ede10-104">對於大多數涉及序列化和反序列化 JSON 的方案，我們建議[在系統中使用 API。](../../../standard/serialization/system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="ede10-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="ede10-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 與 <xref:System.Runtime.Serialization.DataContractSerializer> 支援相同的型別。</span><span class="sxs-lookup"><span data-stu-id="ede10-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="ede10-106">當撰寫 Asynchronous JavaScript and XML (AJAX) 型 Web 應用程式時，JSON 資料格式特別有用。</span><span class="sxs-lookup"><span data-stu-id="ede10-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="ede10-107">Windows 通信基礎 （WCF） 中的 AJAX 支援經過優化，可通過腳本管理器控制項與ASP.NET AJAX 一起使用。</span><span class="sxs-lookup"><span data-stu-id="ede10-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="ede10-108">有關如何將 Windows 通信基礎 （WCF） 與 ASP.NET AJAX 一起使用的示例，請參閱[AJAX 示例](ajax.md)。</span><span class="sxs-lookup"><span data-stu-id="ede10-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="ede10-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ede10-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="ede10-110">此範例會使用 `Person` 資料合約以示範序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ede10-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="ede10-111">若要將 `Person` 型別的執行個體序列化為 JSON，請先建立 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>，然後使用 `WriteObject` 方法將 JSON 資料寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="ede10-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="ede10-112">這個記憶體資料流包含有效的 JSON 資料。</span><span class="sxs-lookup"><span data-stu-id="ede10-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="ede10-113">此範例會示範從 JSON 資料還原序列化為物件。</span><span class="sxs-lookup"><span data-stu-id="ede10-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="ede10-114">接下來，您要倒轉資料流並呼叫 `ReadObject`。</span><span class="sxs-lookup"><span data-stu-id="ede10-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="ede10-115">檢查 `p2` 物件，便可顯示 JSON 資料是否已正確地還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ede10-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ede10-116">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ede10-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ede10-117">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ede10-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ede10-118">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="ede10-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ede10-119">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ede10-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ede10-120">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ede10-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="ede10-121">生成解決方案 Json 序列化.sln，如[構建 Windows 通信基礎示例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="ede10-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="ede10-122">執行產生的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ede10-122">Run the resulting console application.</span></span>  
