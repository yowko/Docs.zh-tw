---
title: DataContractResolver
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aefe0bc0e0be17c2585499e4c943b43672907dfc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="datacontractresolver"></a><span data-ttu-id="4484a-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="4484a-102">DataContractResolver</span></span>
<span data-ttu-id="4484a-103">此範例示範如何使用 <xref:System.Runtime.Serialization.DataContractResolver> 類別來自訂序列化和還原序列化程序。</span><span class="sxs-lookup"><span data-stu-id="4484a-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="4484a-104">此範例會示範如何使用 DataContractResolver，在序列化和還原序列化期間來回對應 CLR 型別與 xsi:type 表示。</span><span class="sxs-lookup"><span data-stu-id="4484a-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="4484a-105">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="4484a-105">Sample Details</span></span>  
 <span data-ttu-id="4484a-106">此範例會定義下列 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="4484a-106">The sample defines the following CLR types.</span></span>  
  
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
  
 <span data-ttu-id="4484a-107">此範例會載入組件、擷取其中每個型別，然後序列化和還原序列化這些型別。</span><span class="sxs-lookup"><span data-stu-id="4484a-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="4484a-108">系統會將 <xref:System.Runtime.Serialization.DataContractResolver> 衍生類別的執行個體傳遞給 <xref:System.Runtime.Serialization.DataContractResolver> 建構函式，藉以將 <xref:System.Runtime.Serialization.DataContractSerializer> 插入序列化程序中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4484a-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>  
  
```csharp  
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));  
```  
  
 <span data-ttu-id="4484a-109">然後，此範例會序列化這些 CLR 型別，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="4484a-109">The sample then serializes the CLR types as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="4484a-110">然後，此範例會還原序列化這些 xsi:type，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="4484a-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="4484a-111">因為自訂 <xref:System.Runtime.Serialization.DataContractResolver> 已傳入 <xref:System.Runtime.Serialization.DataContractSerializer> 建構函式，所以系統會在序列化期間呼叫 <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>，以便將 CLR 型別對應至對等的 `xsi:type`。</span><span class="sxs-lookup"><span data-stu-id="4484a-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="4484a-112">同樣地，系統會在還原序列化期間呼叫 <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>，以便將 `xsi:type` 對應至對等的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="4484a-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="4484a-113">在此範例中，<xref:System.Runtime.Serialization.DataContractResolver> 定義的方式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4484a-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>  
  
 <span data-ttu-id="4484a-114">下列程式碼範例是從 <xref:System.Runtime.Serialization.DataContractResolver> 衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="4484a-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>  
  
```  
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
  
 <span data-ttu-id="4484a-115">在此範例中，類型專案會產生包含此範例中使用之所有類型的組件。</span><span class="sxs-lookup"><span data-stu-id="4484a-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="4484a-116">使用此專案加入、移除或修改即將序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="4484a-116">Use this project to add, remove or modify the types that will be serialized.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4484a-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="4484a-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="4484a-118">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 DCRSample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="4484a-118">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the DCRSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4484a-119">若要執行方案，請按 F5</span><span class="sxs-lookup"><span data-stu-id="4484a-119">To run the solution, press F5</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4484a-120">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4484a-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4484a-121">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4484a-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4484a-122">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="4484a-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4484a-123">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4484a-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="4484a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4484a-124">See Also</span></span>  
 [<span data-ttu-id="4484a-125">使用資料合約解析程式</span><span class="sxs-lookup"><span data-stu-id="4484a-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
