---
title: "JSON 序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 706cea8ed07fae680987e58b118b0a87951a059b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="json-serialization"></a><span data-ttu-id="5dc07-102">JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="5dc07-102">JSON Serialization</span></span>
<span data-ttu-id="5dc07-103">這個範例示範如何使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 以序列化與還原序列化使用 JavaScript Object Notation (JSON) 格式的資料。</span><span class="sxs-lookup"><span data-stu-id="5dc07-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="5dc07-104">這個序列化引擎會將 JSON 資料轉換為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別的執行個體，以及轉換回 JSON 資料。</span><span class="sxs-lookup"><span data-stu-id="5dc07-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="5dc07-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 與 <xref:System.Runtime.Serialization.DataContractSerializer> 支援相同的型別。</span><span class="sxs-lookup"><span data-stu-id="5dc07-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="5dc07-106">當撰寫 Asynchronous JavaScript and XML (AJAX) 型 Web 應用程式時，JSON 資料格式特別有用。</span><span class="sxs-lookup"><span data-stu-id="5dc07-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="5dc07-107">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的 AJAX 支援已針對透過 ScriptManager 控制項來搭配 ASP.NET AJAX 使用完成最佳化。</span><span class="sxs-lookup"><span data-stu-id="5dc07-107">AJAX support in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="5dc07-108">如需如何使用的範例[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]與 ASP.NET AJAX，請參閱[AJAX 範例](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)。</span><span class="sxs-lookup"><span data-stu-id="5dc07-108">For examples of how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dc07-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="5dc07-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5dc07-110">此範例會使用 `Person` 資料合約以示範序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="5dc07-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  
  
```  
[DataContract]  
    class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
```  
  
 <span data-ttu-id="5dc07-111">若要將 `Person` 型別的執行個體序列化為 JSON，請先建立 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>，然後使用 `WriteObject` 方法將 JSON 資料寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="5dc07-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  
  
```  
Person p = new Person();  
//Set up Person object...  
MemoryStream stream1 = new MemoryStream();  
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
ser.WriteObject(stream1, p);  
```  
  
 <span data-ttu-id="5dc07-112">這個記憶體資料流包含有效的 JSON 資料。</span><span class="sxs-lookup"><span data-stu-id="5dc07-112">The memory stream contains valid JSON data.</span></span>  
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="5dc07-113">此範例會示範從 JSON 資料還原序列化為物件。</span><span class="sxs-lookup"><span data-stu-id="5dc07-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="5dc07-114">接下來，您要倒轉資料流並呼叫 `ReadObject`。</span><span class="sxs-lookup"><span data-stu-id="5dc07-114">You then rewind the stream and call `ReadObject`.</span></span>  
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 <span data-ttu-id="5dc07-115">檢查 `p2` 物件，便可顯示 JSON 資料是否已正確地還原序列化。</span><span class="sxs-lookup"><span data-stu-id="5dc07-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5dc07-116">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5dc07-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5dc07-117">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5dc07-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5dc07-118">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="5dc07-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5dc07-119">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5dc07-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5dc07-120">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5dc07-120">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="5dc07-121">中所述，建置此方案 JsonSerialization.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5dc07-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="5dc07-122">執行產生的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="5dc07-122">Run the resulting console application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc07-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dc07-123">See Also</span></span>
