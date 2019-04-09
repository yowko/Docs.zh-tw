---
title: 通道處理站和快取
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 3914ba74337bd959558348c191a897c79a32da52
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106453"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="757e8-102">通道處理站和快取</span><span class="sxs-lookup"><span data-stu-id="757e8-102">Channel Factory and Caching</span></span>
<span data-ttu-id="757e8-103">WCF 用戶端應用程式會使用 <xref:System.ServiceModel.ChannelFactory%601> 類別來建立與 WCF 服務的通訊通道。</span><span class="sxs-lookup"><span data-stu-id="757e8-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="757e8-104">建立 <xref:System.ServiceModel.ChannelFactory%601> 執行個體會產生額外負荷，因為這涉及到下列作業：</span><span class="sxs-lookup"><span data-stu-id="757e8-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
-   <span data-ttu-id="757e8-105">建構 <xref:System.ServiceModel.Description.ContractDescription> 樹狀</span><span class="sxs-lookup"><span data-stu-id="757e8-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
-   <span data-ttu-id="757e8-106">反映所有必要的 CLR 型別</span><span class="sxs-lookup"><span data-stu-id="757e8-106">Reflecting all of the required CLR types</span></span>  
  
-   <span data-ttu-id="757e8-107">建構通道堆疊</span><span class="sxs-lookup"><span data-stu-id="757e8-107">Constructing the channel stack</span></span>  
  
-   <span data-ttu-id="757e8-108">處置資源</span><span class="sxs-lookup"><span data-stu-id="757e8-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="757e8-109">為了盡量減少這種負荷，WCF 可以在您使用 WCF 用戶端 Proxy 時快取通道處理站。</span><span class="sxs-lookup"><span data-stu-id="757e8-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="757e8-110">直接使用 <xref:System.ServiceModel.ChannelFactory%601> 類別時，您可以直接控制通道處理站的建立作業。</span><span class="sxs-lookup"><span data-stu-id="757e8-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="757e8-111">WCF 用戶端 proxy 產生含有[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)衍生自<xref:System.ServiceModel.ClientBase%601>。</span><span class="sxs-lookup"><span data-stu-id="757e8-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <xref:System.ServiceModel.ClientBase%601> <span data-ttu-id="757e8-112">定義靜態<xref:System.ServiceModel.ClientBase%601.CacheSetting%2A>定義通道處理站快取行為的屬性。</span><span class="sxs-lookup"><span data-stu-id="757e8-112">defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="757e8-113">快取設定會針對特定類型來設定。</span><span class="sxs-lookup"><span data-stu-id="757e8-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="757e8-114">例如，設定`ClientBase<ITest>.CacheSettings`其中一個下面定義的值將會影響只有那些 proxy/ClientBase 型別的`ITest`。</span><span class="sxs-lookup"><span data-stu-id="757e8-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="757e8-115">第一個 Proxy/ClientBase 執行個體一經建立，特定 <xref:System.ServiceModel.ClientBase%601> 的快取設定就會是不可變的。</span><span class="sxs-lookup"><span data-stu-id="757e8-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="757e8-116">指定快取行為</span><span class="sxs-lookup"><span data-stu-id="757e8-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="757e8-117">快取行為是藉由將 <xref:System.ServiceModel.ClientBase%601.CacheSetting> 屬性設定為下列其中一個值所指定。</span><span class="sxs-lookup"><span data-stu-id="757e8-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="757e8-118">快取設定值</span><span class="sxs-lookup"><span data-stu-id="757e8-118">Cache Setting Value</span></span>|<span data-ttu-id="757e8-119">描述</span><span class="sxs-lookup"><span data-stu-id="757e8-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="757e8-120">應用程式定義域內 <xref:System.ServiceModel.ClientBase%601> 的所有執行個體都可以參與快取。</span><span class="sxs-lookup"><span data-stu-id="757e8-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="757e8-121">開發人員已經確定對快取沒有不利的安全性影響。</span><span class="sxs-lookup"><span data-stu-id="757e8-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="757e8-122">快取將不會關閉即使 「 安全性敏感 」 屬性<xref:System.ServiceModel.ClientBase%601>存取。</span><span class="sxs-lookup"><span data-stu-id="757e8-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="757e8-123">「 安全性敏感 」 屬性<xref:System.ServiceModel.ClientBase%601>都<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>，<xref:System.ServiceModel.ClientBase%601.Endpoint%2A>和<xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>。</span><span class="sxs-lookup"><span data-stu-id="757e8-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="757e8-124">只有從定義於組態檔之端點建立的 <xref:System.ServiceModel.ClientBase%601> 執行個體才會在應用程式定義域中參與快取。</span><span class="sxs-lookup"><span data-stu-id="757e8-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="757e8-125">任何以程式設計方式在應用程式定義域內建立的 <xref:System.ServiceModel.ClientBase%601> 執行個體都不會參與快取。</span><span class="sxs-lookup"><span data-stu-id="757e8-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="757e8-126">此外，將會停用快取執行個體<xref:System.ServiceModel.ClientBase%601>之後的任何 「 安全性敏感 」 屬性存取。</span><span class="sxs-lookup"><span data-stu-id="757e8-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="757e8-127">在相關應用程式定義域內，特定類型之所有 <xref:System.ServiceModel.ClientBase%601> 執行個體的快取都會關閉。</span><span class="sxs-lookup"><span data-stu-id="757e8-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="757e8-128">下列程式碼片段說明如何使用 <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="757e8-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))   
         {   
            // ...  
            proxy.Test(msg);   
            // ...  
         }   
      }   
   }   
}  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }  
```  
  
 <span data-ttu-id="757e8-129">在上述程式碼中，`TestClient` 的所有執行個體都將使用相同的通道處理站。</span><span class="sxs-lookup"><span data-stu-id="757e8-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.Default;   
      int i = 1;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            if (i == 4)   
            {   
               ServiceEndpoint endpoint = proxy.Endpoint;   
               ... // use endpoint in some way   
            }   
            proxy.Test(msg);   
         }   
         i++;   
   }   
}   
  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="757e8-130">在上述範例中，除了執行個體 #4 以外，`TestClient` 的所有執行個體都會使用相同的通道處理站。</span><span class="sxs-lookup"><span data-stu-id="757e8-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="757e8-131">執行個體 #4 會使用專門針對其用途建立的通道處理站。</span><span class="sxs-lookup"><span data-stu-id="757e8-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="757e8-132">這個設定適用於特定端點需要的安全性設定與通道處理站類型 (在本例中為 `ITest`) 相同之其他端點所需安全性設定有所不同時的情節。</span><span class="sxs-lookup"><span data-stu-id="757e8-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            proxy.Test(msg);   
         }           
      }   
   }  
}  
  
// Generated by SvcUtil.exe   
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="757e8-133">在上述範例中，`TestClient` 的所有執行個體都會使用不同的通道處理站。</span><span class="sxs-lookup"><span data-stu-id="757e8-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="757e8-134">當每個端點各有不同的安全性需求，而進行快取沒有意義時，這種方式非常有用。</span><span class="sxs-lookup"><span data-stu-id="757e8-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757e8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="757e8-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="757e8-136">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="757e8-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="757e8-137">用戶端</span><span class="sxs-lookup"><span data-stu-id="757e8-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="757e8-138">使用 WCF 用戶端存取服務</span><span class="sxs-lookup"><span data-stu-id="757e8-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="757e8-139">HOW TO：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="757e8-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
