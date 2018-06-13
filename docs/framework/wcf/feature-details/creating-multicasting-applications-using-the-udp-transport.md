---
title: 使用 UDP 傳輸建立多點傳送應用程式
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 84b36029416a66ef03768aed7d0c789a41eed8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490421"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="a2b1c-102">使用 UDP 傳輸建立多點傳送應用程式</span><span class="sxs-lookup"><span data-stu-id="a2b1c-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="a2b1c-103">多點傳送應用程式會在同一時間將小量訊息發送給大量的收件人，而無需建立點對點連接。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="a2b1c-104">這類應用程式著重速度勝於可靠性。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="a2b1c-105">換句話說，及時發送資料要比確保任何特定訊息實際送達來得更重要。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="a2b1c-106">WCF 現在支援使用 <xref:System.ServiceModel.UdpBinding> 撰寫多點傳送應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="a2b1c-107">這種傳輸適用於服務需要將出小量訊息同時傳送給許多用戶端的情節。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="a2b1c-108">股票行情指示器應用程式是這類服務的範例。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="a2b1c-109">實作多點傳送應用程式</span><span class="sxs-lookup"><span data-stu-id="a2b1c-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="a2b1c-110">若要實作多點傳送應用程式，請定義服務合約，並為每個需要回應多點傳送訊息的軟體元件實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="a2b1c-111">例如，股票行情指示器應用程式可能定義下列服務合約：</span><span class="sxs-lookup"><span data-stu-id="a2b1c-111">For example, a stock ticker application might define a service contract:</span></span>  
  
```  
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="a2b1c-112">每個想要接收多點傳送訊息的應用程式都必須裝載公開此介面的服務。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="a2b1c-113">例如，下列示範如何接收多點傳送訊息的程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="a2b1c-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```  
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="a2b1c-114">應用程式會指定所有服務都將接聽的 UDP 位址。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="a2b1c-115">建立新的 <xref:System.ServiceModel.ServiceHost>，並使用 <xref:System.ServiceModel.UdpBinding> 公開服務端點。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="a2b1c-116">然後 <xref:System.ServiceModel.ServiceHost> 會開啟，並開始接聽傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="a2b1c-117">在這種類型的情節中，實際發送多點傳送訊息的是用戶端。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="a2b1c-118">每個正在接聽正確 UDP 位址的服務都會接收多點傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="a2b1c-119">下列是發送多點傳送訊息之用戶端的範例：</span><span class="sxs-lookup"><span data-stu-id="a2b1c-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
```  
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory 
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine(String.Format("sent stock info at {0}", DateTime.Now));
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="a2b1c-120">這個程式碼會產生股票資訊，然後使用服務合約 IStockTicker 發送多點傳送訊息以呼叫接聽正確 UDP 位址的服務。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="a2b1c-121">UDP 和可靠傳訊</span><span class="sxs-lookup"><span data-stu-id="a2b1c-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="a2b1c-122">因為 UDP 通訊協定的性質屬於輕量型，所以 UDP 繫結不支援可靠傳訊。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="a2b1c-123">如果您需要確認遠端端點已收到訊息，請使用支援可靠傳訊的運輸，例如 HTTP 或 TCP。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="a2b1c-124">如需有關可信賴傳訊，請參閱 http://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="a2b1c-124">For more information about reliable messaging see http://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="a2b1c-125">雙向多點傳送訊息</span><span class="sxs-lookup"><span data-stu-id="a2b1c-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="a2b1c-126">雖然多點傳送訊息通常為單向，但 UdpBinding 確實可支援要求/回覆訊息交換。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="a2b1c-127">使用 UDP 傳輸傳送的訊息會同時包含寄件者和收件者位址。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="a2b1c-128">使用寄件者位址時必須多加小心，因為它可能會在傳送途中遭到惡意變更。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="a2b1c-129">可以使用下列程式碼來檢查位址：</span><span class="sxs-lookup"><span data-stu-id="a2b1c-129">The address can be checked using the following code:</span></span>  
  
```  
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="a2b1c-130">這個程式碼會檢查寄件者位址的第一個位元組以查看其中是否包含 0xE0，這表示該位址是多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="a2b1c-131">安全性考量</span><span class="sxs-lookup"><span data-stu-id="a2b1c-131">Security Considerations</span></span>  
 <span data-ttu-id="a2b1c-132">接聽多點傳送訊息時，會將 ICMP 封包傳送至路由器，以通知路由器您正在多點傳送位址上進行接聽。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="a2b1c-133">本機子網路上具有使用權限的任何人都可以接聽這些類型的封包，並判斷您是在哪一個多點傳送位址和連接埠上進行接聽。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="a2b1c-134">不要將寄件者的 IP 位址用於任何安全性目的。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="a2b1c-135">這項資訊可以偽冒，並且可能導致應用程式將回應傳送到錯誤的電腦。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="a2b1c-136">減輕這種威脅的一種方法，就是啟用訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="a2b1c-137">您也可以使用網路層級 IPSec (網際網路通訊協定安全性) 和/或 NAP (網路存取保護)。</span><span class="sxs-lookup"><span data-stu-id="a2b1c-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
