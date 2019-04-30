---
title: 從 .NET 遠端處理移轉到 WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c6bc16e97a87461be7b2c4877777329a0005a497
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955229"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="bdbd5-102">從 .NET 遠端處理移轉到 WCF</span><span class="sxs-lookup"><span data-stu-id="bdbd5-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="bdbd5-103">此文章說明如何將使用 .NET 遠端處理的應用程式移轉為使用 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="bdbd5-104">此文章會先比較這這些產品的類似概念，再說明如何在 WCF 中完成幾個常見的遠端處理案例。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="bdbd5-105">.NET 遠端處理是僅為了回溯相容性所支援的舊版產品。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="bdbd5-106">此產品由於無法在用戶端與伺服器之間維護個別的信任層級，因此會因為跨受信任與未受信任的環境而不安全。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="bdbd5-107">例如，您絕不能將 .NET 遠端處理端點公開給網際網路或未受信任的用戶端。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="bdbd5-108">建議將現有的遠端處理應用程式移轉至更新且更安全的技術。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="bdbd5-109">如果應用程式的設計只使用 HTTP 並且符合 REST 規範，則建議使用 ASP.NET Web API。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="bdbd5-110">如需詳細資訊，請參閱＜ASP.NET Web API＞。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="bdbd5-111">如果應用程式是以 SOAP 為基礎，或需要非 Http 通訊協定 (例如 TCP)，則建議使用 WCF。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="bdbd5-112">比較 .NET 遠端處理與 WCF</span><span class="sxs-lookup"><span data-stu-id="bdbd5-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="bdbd5-113">本節將 .NET 遠端處理的基本建置組塊與其 WCF 對應項進行比較。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="bdbd5-114">我們稍後將使用這些建置組塊，在 WCF 中建立一些常見的用戶端和伺服器案例。下表摘要說明 .NET 遠端處理和 WCF 之間的主要相似性和差異。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="bdbd5-115">.NET 遠端處理</span><span class="sxs-lookup"><span data-stu-id="bdbd5-115">.NET Remoting</span></span>|<span data-ttu-id="bdbd5-116">WCF</span><span class="sxs-lookup"><span data-stu-id="bdbd5-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="bdbd5-117">伺服器類型</span><span class="sxs-lookup"><span data-stu-id="bdbd5-117">Server type</span></span>|<span data-ttu-id="bdbd5-118">子類別 MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="bdbd5-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="bdbd5-119">以 [ServiceContract] 屬性標記</span><span class="sxs-lookup"><span data-stu-id="bdbd5-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="bdbd5-120">服務作業</span><span class="sxs-lookup"><span data-stu-id="bdbd5-120">Service operations</span></span>|<span data-ttu-id="bdbd5-121">伺服器類型的公用方法</span><span class="sxs-lookup"><span data-stu-id="bdbd5-121">Public methods on server type</span></span>|<span data-ttu-id="bdbd5-122">以 [OperationContract] 屬性標記</span><span class="sxs-lookup"><span data-stu-id="bdbd5-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="bdbd5-123">序列化</span><span class="sxs-lookup"><span data-stu-id="bdbd5-123">Serialization</span></span>|<span data-ttu-id="bdbd5-124">ISerializable 或 [Serializable]</span><span class="sxs-lookup"><span data-stu-id="bdbd5-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="bdbd5-125">DataContractSerializer 或 XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="bdbd5-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="bdbd5-126">已傳遞的物件</span><span class="sxs-lookup"><span data-stu-id="bdbd5-126">Objects passed</span></span>|<span data-ttu-id="bdbd5-127">傳值或傳址</span><span class="sxs-lookup"><span data-stu-id="bdbd5-127">By-value or by-reference</span></span>|<span data-ttu-id="bdbd5-128">僅限傳值</span><span class="sxs-lookup"><span data-stu-id="bdbd5-128">By-value only</span></span>|  
|<span data-ttu-id="bdbd5-129">錯誤/例外狀況</span><span class="sxs-lookup"><span data-stu-id="bdbd5-129">Errors/exceptions</span></span>|<span data-ttu-id="bdbd5-130">任何可序列化的例外狀況</span><span class="sxs-lookup"><span data-stu-id="bdbd5-130">Any serializable exception</span></span>|<span data-ttu-id="bdbd5-131">FaultContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="bdbd5-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="bdbd5-132">用戶端 Proxy 物件</span><span class="sxs-lookup"><span data-stu-id="bdbd5-132">Client proxy objects</span></span>|<span data-ttu-id="bdbd5-133">強型別 Transparent Proxy 是從 MarshalByRefObjects 自動建立</span><span class="sxs-lookup"><span data-stu-id="bdbd5-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="bdbd5-134">產生強型別的 proxy 是視需要使用 ChannelFactory\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="bdbd5-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="bdbd5-135">所需的平台</span><span class="sxs-lookup"><span data-stu-id="bdbd5-135">Platform required</span></span>|<span data-ttu-id="bdbd5-136">用戶端和伺服器都必須使用 Microsoft 作業系統與 .NET</span><span class="sxs-lookup"><span data-stu-id="bdbd5-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="bdbd5-137">跨平台</span><span class="sxs-lookup"><span data-stu-id="bdbd5-137">Cross-platform</span></span>|  
|<span data-ttu-id="bdbd5-138">訊息格式</span><span class="sxs-lookup"><span data-stu-id="bdbd5-138">Message format</span></span>|<span data-ttu-id="bdbd5-139">Private</span><span class="sxs-lookup"><span data-stu-id="bdbd5-139">Private</span></span>|<span data-ttu-id="bdbd5-140">業界標準 (SOAP、WS-\* 等)</span><span class="sxs-lookup"><span data-stu-id="bdbd5-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="bdbd5-141">伺服器實作比較</span><span class="sxs-lookup"><span data-stu-id="bdbd5-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="bdbd5-142">在 .NET 遠端處理中建立伺服器</span><span class="sxs-lookup"><span data-stu-id="bdbd5-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="bdbd5-143">.NET 遠端處理伺服器類型必須衍生自 MarshalByRefObject 並定義用戶端可呼叫的方法 (如下所示)：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="bdbd5-144">此伺服器類型的公用方法會變成用戶端可用的公用合約。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="bdbd5-145">伺服器的公用介面與其實作之間沒有區隔 (一種類型處理兩者)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="bdbd5-146">定義伺服器類型之後，便可將類型提供給用戶端，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="bdbd5-147">有許多方法可將遠端處理類型當做伺服器來提供，包括使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="bdbd5-148">這只是其中一個範例。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="bdbd5-149">在 WCF 中建立伺服器</span><span class="sxs-lookup"><span data-stu-id="bdbd5-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="bdbd5-150">在 WCF 中的對應步驟包含建立兩種類型：公用「服務合約」與具體實作。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="bdbd5-151">第一種類型會宣告為以 [ServiceContract] 標記的介面。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="bdbd5-152">提供給用戶端的的方法會以 [OperationContract] 標記：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="bdbd5-153">伺服器的實作會在個別的具體類別中定義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="bdbd5-154">定義這些類型之後，便可將 WCF 伺服器提供給用戶端，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="bdbd5-155">TCP 會用於這兩個範例中，以盡可能保持這兩個範例類似。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="bdbd5-156">如需使用 HTTP 的範例，請參閱本主題稍後的案例逐步解說。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="bdbd5-157">設定及裝載 WCF 服務的方法有許多種。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="bdbd5-158">這只是其中一個範例，稱為「自我裝載」。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="bdbd5-159">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-159">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="bdbd5-160">如何：定義服務合約</span><span class="sxs-lookup"><span data-stu-id="bdbd5-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="bdbd5-161">使用設定檔設定服務</span><span class="sxs-lookup"><span data-stu-id="bdbd5-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="bdbd5-162">裝載服務</span><span class="sxs-lookup"><span data-stu-id="bdbd5-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="bdbd5-163">用戶端實作比較</span><span class="sxs-lookup"><span data-stu-id="bdbd5-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="bdbd5-164">在 .NET 遠端處理中建立用戶端</span><span class="sxs-lookup"><span data-stu-id="bdbd5-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="bdbd5-165">提供 .NET 遠端處理伺服器物件之後，用戶端便可使用這個物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="bdbd5-166">從 Activator.GetObject() 傳回的 RemotingServer 執行個體稱為 "Transparent Proxy"。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="bdbd5-167">它會針對用戶端上的 RemotingServer 類型實作公用 API，但所有方法都會呼叫在不同處理序或電腦中執行的伺服器物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="bdbd5-168">在 WCF 中建立用戶端</span><span class="sxs-lookup"><span data-stu-id="bdbd5-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="bdbd5-169">在 WCF 中的對應步驟包含使用通道處理站明確建立 Proxy。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="bdbd5-170">如同遠端處理，Proxy 物件可用來叫用伺服器上的作業，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="bdbd5-171">此範例顯示如何在通道層級進行程式設計，因為它最類似遠端處理範例。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="bdbd5-172">也可**加入服務參考**產生程式碼以簡化用戶端程式設計的 Visual Studio 中的方法。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="bdbd5-173">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-173">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="bdbd5-174">用戶端通道層級的程式設計</span><span class="sxs-lookup"><span data-stu-id="bdbd5-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="bdbd5-175">如何：新增、 更新或移除服務參考</span><span class="sxs-lookup"><span data-stu-id="bdbd5-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="bdbd5-176">序列化使用方式</span><span class="sxs-lookup"><span data-stu-id="bdbd5-176">Serialization Usage</span></span>  
 <span data-ttu-id="bdbd5-177">雖然 .NET 遠端處理與 WCF 都是使用序列化在用戶端與伺服器之間傳送物件，但是它們在下列幾個重要方面有所不同：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="bdbd5-178">它們使用不同的序列化程式與慣例，來指出要序列化的項目。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="bdbd5-179">.NET 遠端處理支援「傳址」序列化，允許在某個階層上存取方法或屬性，以在另一個階層上執行程式碼，也就是跨安全性界限。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="bdbd5-180">此功能有安全性弱點，這也是為什麼絕不能將遠端處理端點公開給未受信任的用戶端的主要原因之一。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="bdbd5-181">遠端處理所使用的序列化必須選擇退出 (明確排除不要序列化的項目)，而 WCF 序列化必須選擇加入 (明確標記要序列化的成員)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="bdbd5-182">.NET 遠端處理的序列化</span><span class="sxs-lookup"><span data-stu-id="bdbd5-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="bdbd5-183">.NET 遠端處理支援以兩種方式在用戶端與伺服器之間序列化及還原序列化物件：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="bdbd5-184">*依值*– 跨階層界限序列化物件的值，並在另一個階層上建立該物件的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="bdbd5-185">對新執行個體的方法或屬性所做的任何呼叫只會在本機執行，並不會影響原始物件或階層。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="bdbd5-186">*傳址*– 跨階層界限序列化特殊 「 物件參考 」。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="bdbd5-187">當某個階層與該物件的方法或屬性互動時，它會回到原始階層與原始物件通訊。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="bdbd5-188">傳址物件流向可為任一方向 (從伺服器到用戶端，或從用戶端到伺服器)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="bdbd5-189">遠端處理的傳值類型是以 [Serializable] 屬性標記或實作 ISerializable，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="bdbd5-190">傳址類型衍生自 MarshalByRefObject 類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="bdbd5-191">請務必了解遠端處理之傳址物件的含意。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="bdbd5-192">如果其中一個階層 (用戶端或伺服器) 將傳址物件傳送至另一個階層，則會回到擁有該物件的階層上執行所有方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="bdbd5-193">例如，當用戶端對伺服器所傳回的傳址物件呼叫方法時，會在伺服器上執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="bdbd5-194">同樣地，當伺服器對用戶端所提供的傳址物件呼叫方法時，也會回到用戶端執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="bdbd5-195">因此，建議只在完全信任的環境中使用 .NET 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="bdbd5-196">將公用 .NET 遠端處理端點公開給未受信任的用戶端，會使遠端處理伺服器容易受到攻擊。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="bdbd5-197">WCF 中的序列化</span><span class="sxs-lookup"><span data-stu-id="bdbd5-197">Serialization in WCF</span></span>  
 <span data-ttu-id="bdbd5-198">WCF 只支援傳值序列化。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="bdbd5-199">若要定義在用戶端和伺服器之間交換的類型，最常見的方法如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="bdbd5-200">[DataContract] 屬性將此類型識別為可在用戶端與伺服器之間序列化及還原序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="bdbd5-201">[DataMember] 屬性識別要序列化的個別屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="bdbd5-202">當 WCF 跨階層傳送物件時，它只會序列化值，並在另一個階層上建立新的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="bdbd5-203">與物件值的任何互動只會在本機進行，而不會和 .NET 遠端處理傳址物件一樣與另一個階層通訊。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="bdbd5-204">如需詳細資訊，請參閱 <<c0> [ 序列化和還原序列化](./feature-details/serialization-and-deserialization.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-204">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="bdbd5-205">例外狀況處理功能</span><span class="sxs-lookup"><span data-stu-id="bdbd5-205">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="bdbd5-206">.NET 遠端處理中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="bdbd5-206">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="bdbd5-207">遠端處理伺服器所擲回的例外狀況和其他任何例外狀況一樣，會序列化、傳送至用戶端，然後在用戶端本機擲回。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-207">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="bdbd5-208">您可以將例外狀況類型分為子類別並標記為 [Serializable]，來建立自訂例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-208">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="bdbd5-209">大多數的架構例外狀況已透過這種方式標記，以允許大部分的例外狀況由伺服器擲回、序列化，並在用戶端上重新擲回。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-209">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="bdbd5-210">雖然這種設計在開發期間很方便，但可能會將伺服器端資訊不慎洩漏給用戶端。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-210">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="bdbd5-211">這就是遠端處理只能在完全信任的環境中使用的原因之一。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-211">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="bdbd5-212">WCF 中的例外狀況與錯誤</span><span class="sxs-lookup"><span data-stu-id="bdbd5-212">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="bdbd5-213">WCF 不允許將任意例外狀況類型從伺服器傳回至用戶端，因為這樣做可能會導致不慎洩漏資訊。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-213">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="bdbd5-214">如果服務作業擲回未預期的例外狀況，則會導致在用戶端上擲回一般目的 FaultException。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-214">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="bdbd5-215">這個例外狀況不會傳達有關發生問題之原因和位置的任何資訊，這對於某些應用程式而言便已足夠。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-215">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="bdbd5-216">如果應用程式必須對用戶端傳達更豐富的錯誤資訊，則可以透過定義錯誤合約來達成目的。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-216">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="bdbd5-217">若要這樣做，請先建立要傳達錯誤資訊的 [DataContract] 類型。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-217">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="bdbd5-218">指定每個服務作業所要使用的錯誤合約。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-218">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="bdbd5-219">伺服器會擲回 FaultException 來報告錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-219">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="bdbd5-220">此外，當用戶端對伺服器提出要求時，它會攔截錯誤，就像是攔截一般例外狀況一樣。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-220">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 <span data-ttu-id="bdbd5-221">如需錯誤合約的詳細資訊，請參閱 <xref:System.ServiceModel.FaultException>。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-221">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="bdbd5-222">安全性考量</span><span class="sxs-lookup"><span data-stu-id="bdbd5-222">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="bdbd5-223">.NET 遠端處理中的安全性</span><span class="sxs-lookup"><span data-stu-id="bdbd5-223">Security in .NET Remoting</span></span>  
 <span data-ttu-id="bdbd5-224">某些 .NET 遠端處理通道支援安全性功能，例如通道層 (IPC 和 TCP) 的驗證和加密。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-224">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="bdbd5-225">HTTP 通道需要 Internet Information Service (IIS) 來進行驗證與加密。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-225">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="bdbd5-226">儘管有此支援，您還是應該將 .NET 遠端處理視為不安全的通訊協定，並只在完全信任的環境中使用。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-226">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="bdbd5-227">絕對不要將公用遠端處理端點公開給網際網路或未受信任的用戶端。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-227">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="bdbd5-228">WCF 的安全性</span><span class="sxs-lookup"><span data-stu-id="bdbd5-228">Security in WCF</span></span>  
 <span data-ttu-id="bdbd5-229">WCF 的設計將安全性納入考量，部分是為了解決 .NET 遠端處理中所發現的安全性弱點類型。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-229">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="bdbd5-230">WCF 在傳輸與訊息層級提供安全性，並提供驗證、授權、加密等許多選項。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-230">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="bdbd5-231">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-231">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="bdbd5-232">安全性</span><span class="sxs-lookup"><span data-stu-id="bdbd5-232">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="bdbd5-233">WCF 安全性指引</span><span class="sxs-lookup"><span data-stu-id="bdbd5-233">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="bdbd5-234">移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="bdbd5-234">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="bdbd5-235">為什麼要從遠端處理移轉至 WCF？</span><span class="sxs-lookup"><span data-stu-id="bdbd5-235">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="bdbd5-236">**.NET 遠端處理是舊版產品。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-236">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="bdbd5-237">中所述[.NET 遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)，它會被視為舊版產品，並不建議用於新的開發。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-237">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="bdbd5-238">建議針對新的和現有的應用程式使用 WCF 或 ASP.NET Web API。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-238">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="bdbd5-239">**WCF 會使用跨平台標準。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-239">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="bdbd5-240">WCF 的設計將跨平台互通性納入考量，並支援許多業界標準 (SOAP、WS-Security、WS-Trust 等)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-240">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="bdbd5-241">WCF 服務可以與在非 Windows 作業系統上執行的用戶端互通。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-241">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="bdbd5-242">遠端處理的設計主要是針對在 Windows 作業系統上使用 .NET Framework 執行伺服器和用戶端應用程式的環境。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-242">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
- <span data-ttu-id="bdbd5-243">**WCF 具有內建的安全性。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-243">**WCF has built-in security.**</span></span> <span data-ttu-id="bdbd5-244">WCF 的設計將安全性納入考量，並提供驗證、傳輸層級安全性、訊息層級安全性等許多選項。遠端處理的設計是為了讓應用程式輕鬆地互通，而不是為了確保在未受信任環境中的安全性。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-244">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="bdbd5-245">WCF 的設計是為了在受信任和未受信任的環境中都能夠正常運作。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-245">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="bdbd5-246">移轉建議</span><span class="sxs-lookup"><span data-stu-id="bdbd5-246">Migration Recommendations</span></span>  
 <span data-ttu-id="bdbd5-247">以下是從 .NET 遠端處理移轉至 WCF 的建議步驟：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-247">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="bdbd5-248">**建立服務合約。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-248">**Create the service contract.**</span></span> <span data-ttu-id="bdbd5-249">定義您的服務介面類型並以 [ServiceContract] 屬性標記。將用戶端可使用 [OperationContract] 呼叫的所有方法都加以標記。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-249">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="bdbd5-250">**建立資料合約。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-250">**Create the data contract.**</span></span> <span data-ttu-id="bdbd5-251">定義要在伺服器與用戶端之間交換的資料類型，並以 [DataContract] 屬性標記這些類型。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-251">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="bdbd5-252">將用戶端可搭配 [DataMember] 使用之所有欄位和屬性都加以標記。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-252">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="bdbd5-253">**建立錯誤合約 （選擇性）。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-253">**Create the fault contract (optional).**</span></span> <span data-ttu-id="bdbd5-254">建立遇到錯誤時，要在伺服器與用戶端之間交換的類型。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-254">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="bdbd5-255">以 [DataContract] 和 [DataMember] 標記這些類型，使這些類型可序列化。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-255">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="bdbd5-256">針對已標記為 [OperationContract] 的所有服務作業，您也應該將它們標記為 [FaultContract]，以指出這些服務作業可能傳回的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-256">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="bdbd5-257">**設定及裝載服務。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-257">**Configure and host the service.**</span></span> <span data-ttu-id="bdbd5-258">建立服務合約之後，下一個步驟是設定繫結，以公開端點上的服務。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-258">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="bdbd5-259">如需詳細資訊，請參閱[端點：位址、 繫結和合約](./feature-details/endpoints-addresses-bindings-and-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-259">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="bdbd5-260">將遠端處理應用程式移轉至 WCF 之後，還必須移除與 .NET 遠端處理的相依性。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-260">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="bdbd5-261">如此可確保移除應用程式中的任何遠端處理安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-261">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="bdbd5-262">這些步驟包括：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-262">These steps include the following:</span></span>  
  
- <span data-ttu-id="bdbd5-263">**停用 MarshalByRefObject。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-263">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="bdbd5-264">MarshalByRefObject 類型只適用於遠端處理，而且不會由 WCF 使用。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-264">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="bdbd5-265">任何具有子類別 MarshalByRefObject 的應用程式類型都應予以移除或變更。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-265">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="bdbd5-266">**停止使用 [Serializable] 與 ISerializable。**</span><span class="sxs-lookup"><span data-stu-id="bdbd5-266">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="bdbd5-267">[Serializable] 屬性與 ISerializable 介面原本是為了在信任的環境中序列化類型所設計，而且由遠端處理使用。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-267">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="bdbd5-268">WCF 序列化必須以 [DataContract] 與 [DataMember] 來標記類型。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-268">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="bdbd5-269">應用程式所使用的資料類型應該修改為使用 [DataContract]，而不是使用 ISerializable 或 [Serializable]。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-269">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="bdbd5-270">移轉案例</span><span class="sxs-lookup"><span data-stu-id="bdbd5-270">Migration Scenarios</span></span>  
 <span data-ttu-id="bdbd5-271">現在我們來看看如何在 WCF 中完成下列常見的遠端處理案例：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-271">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="bdbd5-272">伺服器以傳值方式將物件傳回至用戶端</span><span class="sxs-lookup"><span data-stu-id="bdbd5-272">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="bdbd5-273">伺服器以傳址方式將物件傳回至用戶端</span><span class="sxs-lookup"><span data-stu-id="bdbd5-273">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="bdbd5-274">用戶端以傳值方式將物件傳送至伺服器</span><span class="sxs-lookup"><span data-stu-id="bdbd5-274">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdbd5-275">在 WCF 中不允許以傳址方式將物件從用戶端傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-275">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="bdbd5-276">閱讀這些案例時，請假設 .NET 遠端處理的基準介面如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-276">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="bdbd5-277">.NET 遠端處理實作在這裡並不重要，因為我們只想要說明如何使用 WCF 來實作對應功能。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-277">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="bdbd5-278">案例 1:服務傳值方式傳回物件</span><span class="sxs-lookup"><span data-stu-id="bdbd5-278">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="bdbd5-279">這個案例示範伺服器如何以傳值方式將物件傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-279">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="bdbd5-280">WCF 一律會以傳值方式從伺服器傳回物件，因此下列步驟只會說明如何建置一般 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-280">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="bdbd5-281">一開始請定義 WCF 服務的公用介面並以 [ServiceContract] 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-281">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="bdbd5-282">我們會使用 [OperationContract] 來識別用戶端將呼叫的伺服器端方法。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-282">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. <span data-ttu-id="bdbd5-283">下一個步驟是建立此服務的資料合約。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-283">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="bdbd5-284">若要執行此作業，請建立以 [DataContract] 屬性標記的類別 (而不是介面)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-284">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="bdbd5-285">我們想要顯示給用戶端與伺服器的個別屬性或欄位都會以 [DataMember] 標記。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-285">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="bdbd5-286">如果我們想要允許衍生類型，則必須使用 [KnownType] 屬性加以識別。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-286">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="bdbd5-287">WCF 唯一可讓此服務序列化或還原序列化的類型是服務介面中的類型或「已知類型」。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-287">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="bdbd5-288">嘗試交換不在這個清單中的其他任何類型都會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-288">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. <span data-ttu-id="bdbd5-289">接下來，我們將提供服務介面的實作。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-289">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. <span data-ttu-id="bdbd5-290">若要執行 WCF 服務，我們需要宣告一個端點，這個端點會使用特定 WCF 繫結在特定 URL 上公開該服務介面。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-290">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="bdbd5-291">將下列區段加入到伺服器專案的 web.config 檔案通常可達成目的。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-291">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. <span data-ttu-id="bdbd5-292">接著會使用下列程式碼來啟動 WCF 服務：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-292">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="bdbd5-293">當啟動這個 ServiceHost 時，它會使用 web.config 檔案來建立適當的合約、繫結與端點。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-293">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="bdbd5-294">如需有關組態檔的詳細資訊，請參閱 <<c0> [ 設定服務使用組態檔](./configuring-services-using-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-294">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="bdbd5-295">這種啟動伺服器的方式稱為自我裝載。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-295">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="bdbd5-296">若要深入了解裝載 WCF 服務的其他選擇，請參閱[裝載的服務](./hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-296">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="bdbd5-297">用戶端專案的 app.config 必須宣告服務端點的相符繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-297">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="bdbd5-298">若要這樣做的 Visual Studio 中的最簡單方式是使用**加入服務參考**，它將會自動更新 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-298">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="bdbd5-299">您也可以手動加入這些相同的變更。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-299">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="bdbd5-300">如需使用詳細資訊**加入服務參考**，請參閱[How to:新增、 更新或移除服務參考](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-300">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="bdbd5-301">現在我們可以從用戶端呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-301">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="bdbd5-302">若要執行此作業，請建立該服務的通道處理站，針對通道要求通道處理站，然後在該通道上直接呼叫所需的方法。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-302">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="bdbd5-303">我們可以這樣做的原因，是因為通道會實作服務的介面並為我們處理基礎要求/回覆邏輯。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-303">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="bdbd5-304">從該方法呼叫傳回的值是伺服器回應的已還原序列化複本。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-304">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="bdbd5-305">WCF 一律會以傳值方式將物件從伺服器傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-305">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="bdbd5-306">這些物件是伺服器所傳送之資料的已還原序列化複本。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-306">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="bdbd5-307">用戶端可以對這些本機複本呼叫方法，而不會有透過回呼叫用伺服器程式碼的任何危險。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-307">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="bdbd5-308">案例 2:伺服器傳址方式傳回物件</span><span class="sxs-lookup"><span data-stu-id="bdbd5-308">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="bdbd5-309">這個案例示範伺服器如何以傳址方式將物件提供給用戶端。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-309">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="bdbd5-310">在 .NET 遠端處理中，所有衍生自以傳址方式序列化之 MarshalByRefObject 的類型都將自動處理。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-310">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="bdbd5-311">這個案例的範例是讓多個用戶端具有獨立工作階段的伺服器端物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-311">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="bdbd5-312">如前所述，WCF 服務所傳回的物件一律為傳值物件，因此沒有傳址物件的直接對應項，但這個物件可能取得與使用 <xref:System.ServiceModel.EndpointAddress10> 物件之傳址語意類似的結果。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-312">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="bdbd5-313">這是可序列化的傳值物件，可供用戶端用來取得伺服器上的工作階段傳址物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-313">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="bdbd5-314">如此一來，便可讓多個用戶端具有獨立工作階段的伺服器端物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-314">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="bdbd5-315">首先，我們需要定義對應到工作階段物件本身的 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-315">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    >  <span data-ttu-id="bdbd5-316">請注意，工作階段物件是以 [ServiceContract] 標記，因此是一般 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-316">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="bdbd5-317">設定 SessionMode 屬性表示它將會是工作階段服務。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-317">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="bdbd5-318">在 WCF 中，工作階段是將兩個端點之間傳送的多個訊息相互關聯的方式。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-318">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="bdbd5-319">這表示一旦用戶端取得此服務的連接，便會在用戶端與伺服器之間建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-319">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="bdbd5-320">用戶端會針對這個工作階段內的所有互動，使用伺服器端物件的唯一執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-320">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="bdbd5-321">接下來，我們需要提供此服務介面的實作。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-321">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="bdbd5-322">我們透過以 [ServiceBehavior] 標記並設定 InstanceContextMode，來告知 WCF 將要為每個工作階段使用此類型的唯一執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-322">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. <span data-ttu-id="bdbd5-323">現在我們需要設法取得此工作階段物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-323">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="bdbd5-324">若要執行此作業，請建立傳回 EndpointAddress10 物件的另一個 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-324">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="bdbd5-325">這是端點的可序列化形式，可供用戶端用來建立工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-325">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="bdbd5-326">此外，我們會實作此 WCF 服務：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-326">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="bdbd5-327">此實作會維護單一通道處理站來建立工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-327">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="bdbd5-328">呼叫 GetInstanceAddress() 時，它會建立通道，並建立有效指向與這個通道關聯之遠端位址的 EndpointAddress10 物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-328">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="bdbd5-329">EndpointAddress10 是能夠以傳值方式傳回至用戶端的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-329">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="bdbd5-330">我們需要執行下列兩個動作，來修改伺服器的組態檔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-330">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="bdbd5-331">宣告\<用戶端 > 區段，其中說明工作階段物件端點。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-331">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="bdbd5-332">由於在這種情況下伺服器也會當做用戶端，因此必須執行這個動作。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-332">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="bdbd5-333">宣告處理站與工作階段物件的端點。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-333">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="bdbd5-334">這樣才能讓用戶端與服務端點通訊，以取得 EndpointAddress10 並建立工作階段通道。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-334">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="bdbd5-335">接著我們可以啟動這些服務：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-335">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="bdbd5-336">我們藉由在用戶端之專案的 app.config 檔案中宣告這些相同的端點，來設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-336">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. <span data-ttu-id="bdbd5-337">若要建立及使用這個工作階段物件，用戶端必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bdbd5-337">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="bdbd5-338">建立 ISessionBoundFactory 服務的通道。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-338">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="bdbd5-339">使用該通道叫用服務，以取得 EndpointAddress10。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-339">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="bdbd5-340">使用 EndpointAddress10 建立通道，以取得工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-340">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="bdbd5-341">與工作階段物件互動，以示範它在多個呼叫會保持相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-341">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="bdbd5-342">WCF 一律會以傳值方式傳回物件，但是可透過使用 EndpointAddress10 來支援傳址語意的對應項。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-342">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="bdbd5-343">這可讓用戶端要求工作階段 WCF 服務執行個體，在這之後，便可像任何其他 WCF 服務一樣與其互動。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-343">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="bdbd5-344">案例 3:用戶端會傳送伺服器的傳值執行個體</span><span class="sxs-lookup"><span data-stu-id="bdbd5-344">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="bdbd5-345">這個案例示範用戶端如何以傳值方式將非基本物件執行個體傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-345">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="bdbd5-346">由於 WCF 只會以傳值方式傳送物件，因此這個案例會示範一般 WCF 使用方式。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-346">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="bdbd5-347">使用案例 1 中的相同 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-347">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="bdbd5-348">使用用戶端來建立新的傳值物件 (客戶)，建立要與 ICustomerService 服務通訊的通道，然後將物件傳送至通道。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-348">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     <span data-ttu-id="bdbd5-349">客戶物件會序列化並傳送至伺服器，再於其中還原序列化為該物件的新複本。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-349">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bdbd5-350">這個程式碼也會說明如何傳送衍生類型 (PremiumCustomer)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-350">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="bdbd5-351">服務介面必須有 Customer 物件，但 Customer 類別上的 [KnownType] 屬性表示也允許 PremiumCustomer。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-351">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="bdbd5-352">WCF 對於透過這個服務介面序列化或還原序列化其他任何類型所做的任何嘗試都將會失敗。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-352">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="bdbd5-353">一般 WCF 交換資料的方式是傳值。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-353">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="bdbd5-354">如此可確保在其中一個資料物件上叫用方法的作業只會在本機執行，而不會在另一個階層上叫用程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-354">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="bdbd5-355">雖然您可以傳回的傳址物件類似*從*伺服器，不可能將傳址物件傳遞的用戶端*至*伺服器。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-355">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="bdbd5-356">如果需要在用戶端與伺服器之間來回溝通，可透過雙工服務在 WCF 中達成。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-356">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="bdbd5-357">如需詳細資訊，請參閱 <<c0> [ 雙工服務](./feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-357">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="bdbd5-358">總結</span><span class="sxs-lookup"><span data-stu-id="bdbd5-358">Summary</span></span>  
 <span data-ttu-id="bdbd5-359">.NET 遠端處理是只能在完全信任的環境中使用的通訊架構。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-359">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="bdbd5-360">它是只為了回溯相容性所支援的舊版產品。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-360">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="bdbd5-361">不應該用來建置新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-361">It should not be used to build new applications.</span></span> <span data-ttu-id="bdbd5-362">相反地，WCF 的設計將安全性納入考量，建議針對新的與現有的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-362">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="bdbd5-363">Microsoft 建議將現有的遠端處理應用程式移轉為改用 WCF 或 ASP.NET Web API。</span><span class="sxs-lookup"><span data-stu-id="bdbd5-363">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
