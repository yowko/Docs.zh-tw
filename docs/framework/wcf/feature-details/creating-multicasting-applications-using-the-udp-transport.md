---
title: 使用 UDP 傳輸建立多點傳送應用程式
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 89ac99ffec614eeebd076f9868568dcf2c7b04fd
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360579"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>使用 UDP 傳輸建立多點傳送應用程式
多點傳送應用程式會在同一時間將小量訊息發送給大量的收件人，而無需建立點對點連接。 這類應用程式著重速度勝於可靠性。 換句話說，及時發送資料要比確保任何特定訊息實際送達來得更重要。 WCF 現在支援使用 <xref:System.ServiceModel.UdpBinding> 撰寫多點傳送應用程式。 這種傳輸適用於服務需要將出小量訊息同時傳送給許多用戶端的情節。 股票行情指示器應用程式是這類服務的範例。  
  
## <a name="implementing-a-multicast-application"></a>實作多點傳送應用程式  
 若要實作多點傳送應用程式，請定義服務合約，並為每個需要回應多點傳送訊息的軟體元件實作服務合約。 例如，股票行情指示器應用程式可能定義下列服務合約：  
  
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
  
 每個想要接收多點傳送訊息的應用程式都必須裝載公開此介面的服務。  例如，下列示範如何接收多點傳送訊息的程式碼範例：  
  
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
  
 應用程式會指定所有服務都將接聽的 UDP 位址。 建立新的 <xref:System.ServiceModel.ServiceHost>，並使用 <xref:System.ServiceModel.UdpBinding> 公開服務端點。 然後 <xref:System.ServiceModel.ServiceHost> 會開啟，並開始接聽傳入的訊息。  
  
 在這種類型的情節中，實際發送多點傳送訊息的是用戶端。 每個正在接聽正確 UDP 位址的服務都會接收多點傳送訊息。 下列是發送多點傳送訊息之用戶端的範例：  
  
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
  
 這個程式碼會產生股票資訊，然後使用服務合約 IStockTicker 發送多點傳送訊息以呼叫接聽正確 UDP 位址的服務。  
  
### <a name="udp-and-reliable-messaging"></a>UDP 和可靠傳訊  
 因為 UDP 通訊協定的性質屬於輕量型，所以 UDP 繫結不支援可靠傳訊。 如果您需要確認遠端端點已收到訊息，請使用支援可靠傳訊的運輸，例如 HTTP 或 TCP。 如需可靠傳訊，請參閱 https://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>雙向多點傳送訊息  
 雖然多點傳送訊息通常為單向，但 UdpBinding 確實可支援要求/回覆訊息交換。 使用 UDP 傳輸傳送的訊息會同時包含寄件者和收件者位址。 使用寄件者位址時必須多加小心，因為它可能會在傳送途中遭到惡意變更。  可以使用下列程式碼來檢查位址：  
  
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
  
 這個程式碼會檢查寄件者位址的第一個位元組以查看其中是否包含 0xE0，這表示該位址是多點傳送位址。  
  
### <a name="security-considerations"></a>安全性考量  
 接聽多點傳送訊息時，會將 ICMP 封包傳送至路由器，以通知路由器您正在多點傳送位址上進行接聽。 本機子網路上具有使用權限的任何人都可以接聽這些類型的封包，並判斷您是在哪一個多點傳送位址和連接埠上進行接聽。  
  
 不要將寄件者的 IP 位址用於任何安全性目的。 這項資訊可以偽冒，並且可能導致應用程式將回應傳送到錯誤的電腦。 減輕這種威脅的一種方法，就是啟用訊息層級安全性。 您也可以使用網路層級 IPSec (網際網路通訊協定安全性) 和/或 NAP (網路存取保護)。
