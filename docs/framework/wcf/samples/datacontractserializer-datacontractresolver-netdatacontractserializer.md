---
title: 使用 DataContractSerializer 及 DataContractResolver 提供 NetDataContractSerializer 的功能
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 481d9d7f30f9c2137ec91a87c9743dcb0a97baf7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816799"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="f319f-102">使用 DataContractSerializer 及 DataContractResolver 提供 NetDataContractSerializer 的功能</span><span class="sxs-lookup"><span data-stu-id="f319f-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="f319f-103">此範例示範如何搭配適當的 <xref:System.Runtime.Serialization.DataContractSerializer> 使用 <xref:System.Runtime.Serialization.DataContractResolver> 以提供與 <xref:System.Runtime.Serialization.NetDataContractSerializer> 相同的功能。</span><span class="sxs-lookup"><span data-stu-id="f319f-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f319f-104">此範例示範如何建立適當的 <xref:System.Runtime.Serialization.DataContractResolver>，以及如何將其加入至 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="f319f-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="f319f-105">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="f319f-105">Sample details</span></span>
 <span data-ttu-id="f319f-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> 與 <xref:System.Runtime.Serialization.DataContractSerializer> 有一項重要的差異：<xref:System.Runtime.Serialization.NetDataContractSerializer> 在已序列化的 XML 中包含 CLR 型別資訊，而 <xref:System.Runtime.Serialization.DataContractSerializer> 則否。</span><span class="sxs-lookup"><span data-stu-id="f319f-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="f319f-107">因此，只有當序列化和還原序列化兩端共用相同的 CLR 型別時，才能使用 <xref:System.Runtime.Serialization.NetDataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="f319f-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="f319f-108">不過，建議您使用 <xref:System.Runtime.Serialization.DataContractSerializer>，因為其效能比 <xref:System.Runtime.Serialization.NetDataContractSerializer> 更好。</span><span class="sxs-lookup"><span data-stu-id="f319f-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f319f-109">您可以在 <xref:System.Runtime.Serialization.DataContractSerializer> 中變更已序列化的資訊，只要在其中加入 <xref:System.Runtime.Serialization.DataContractResolver> 即可。</span><span class="sxs-lookup"><span data-stu-id="f319f-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="f319f-110">此範例包含兩個專案。</span><span class="sxs-lookup"><span data-stu-id="f319f-110">This sample consists of two projects.</span></span> <span data-ttu-id="f319f-111">第一個專案使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> 來序列化物件。</span><span class="sxs-lookup"><span data-stu-id="f319f-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="f319f-112">第二個專案搭配 <xref:System.Runtime.Serialization.DataContractSerializer> 使用 <xref:System.Runtime.Serialization.DataContractResolver>，以提供與第一個專案相同的功能。</span><span class="sxs-lookup"><span data-stu-id="f319f-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="f319f-113">下列程式碼範例示範名稱為 <xref:System.Runtime.Serialization.DataContractResolver>，且已加入至 DCSwithDCR 專案之 `MyDataContractResolver` 中的自訂 <xref:System.Runtime.Serialization.DataContractSerializer> 實作。</span><span class="sxs-lookup"><span data-stu-id="f319f-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        if (type == null)
        {
            type = Type.GetType(typeName + ", " + typeNamespace);
        }
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="f319f-114">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="f319f-114">To use this sample</span></span>

1.  <span data-ttu-id="f319f-115">使用 Visual Studio 2012，請開啟 DCRSample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="f319f-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2.  <span data-ttu-id="f319f-116">以滑鼠右鍵按一下方案檔，然後選擇 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="f319f-116">Right-click the solution file and choose **Properties**.</span></span>

3.  <span data-ttu-id="f319f-117">在 [**方案屬性頁**] 對話方塊底下**通用屬性**，**啟始專案**，選取**多個啟始專案：**。</span><span class="sxs-lookup"><span data-stu-id="f319f-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4.  <span data-ttu-id="f319f-118">旁**DCSwithDCR**專案，然後選取**開始**從**動作**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f319f-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5.  <span data-ttu-id="f319f-119">旁**NetDCS**專案，然後選取**開始**從**動作**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f319f-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6.  <span data-ttu-id="f319f-120">按一下 **確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f319f-120">Click **OK** to close the dialog.</span></span>

7.  <span data-ttu-id="f319f-121">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="f319f-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8.  <span data-ttu-id="f319f-122">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="f319f-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="f319f-123">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f319f-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f319f-124">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f319f-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f319f-125">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="f319f-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f319f-126">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f319f-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
