---
title: 使用 NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 5090cfdfeb068acda1e1092e408f3cd747c574c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121013"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="39819-102">使用 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="39819-102">Using the NetHttpBinding</span></span>
<xref:System.ServiceModel.NetHttpBinding> <span data-ttu-id="39819-103">是專為使用 HTTP 或 WebSocket 服務而設計的繫結，並使用預設的二進位編碼。</span><span class="sxs-lookup"><span data-stu-id="39819-103">is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <xref:System.ServiceModel.NetHttpBinding> <span data-ttu-id="39819-104">會偵測是否有使用與要求-回覆合約還是雙工合約，並改變行為來比對-它會使用 HTTP 要求-回覆合約和 WebSockets 雙工合約。</span><span class="sxs-lookup"><span data-stu-id="39819-104">will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="39819-105">使用 <xref:System.ServiceModel.Channels.WebSocketTransportUsage> 設定即可覆寫這個行為：</span><span class="sxs-lookup"><span data-stu-id="39819-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> <span data-ttu-id="39819-106">-這會強制使用 WebSockets，甚至用於要求-回覆合約。</span><span class="sxs-lookup"><span data-stu-id="39819-106">- This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> <span data-ttu-id="39819-107">-這可避免使用 WebSockets。</span><span class="sxs-lookup"><span data-stu-id="39819-107">- This prevents WebSockets from being used.</span></span> <span data-ttu-id="39819-108">嘗試將這個設定用於雙工合約會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39819-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> <span data-ttu-id="39819-109">-這是預設值和行為方式如上所述。</span><span class="sxs-lookup"><span data-stu-id="39819-109">- This is the default value and behaves as described above.</span></span>  
  
 <xref:System.ServiceModel.NetHttpBinding> <span data-ttu-id="39819-110">在 HTTP 模式和 WebSocket 模式支援可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="39819-110">supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="39819-111">在 WebSocket 模式中，工作階段是由傳輸提供。</span><span class="sxs-lookup"><span data-stu-id="39819-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="39819-112">當使用 <xref:System.ServiceModel.NetHttpBinding> 且繫結的 TransferMode 設為 TransferMode.Streamed 時，大量資料流可能會造成死結與呼叫逾時。</span><span class="sxs-lookup"><span data-stu-id="39819-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="39819-113">為了解決此問題，請傳送較小的訊息或使用 TransferMode.Buffered。</span><span class="sxs-lookup"><span data-stu-id="39819-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="39819-114">設定服務以使用 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="39819-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="39819-115">可以將 <xref:System.ServiceModel.NetHttpBinding> 設定成和任何其他繫結程序一樣。</span><span class="sxs-lookup"><span data-stu-id="39819-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="39819-116">下列組態檔片段說明如何使用 <xref:System.ServiceModel.NetHttpBinding> 來設定 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="39819-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 <span data-ttu-id="39819-117">下列程式碼片段示範如何在程式碼中加入 <xref:System.ServiceModel.NetHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="39819-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="39819-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39819-118">See also</span></span>

- [<span data-ttu-id="39819-119">設定服務的繫結</span><span class="sxs-lookup"><span data-stu-id="39819-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="39819-120">繫結</span><span class="sxs-lookup"><span data-stu-id="39819-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="39819-121">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="39819-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="39819-122">雙工服務</span><span class="sxs-lookup"><span data-stu-id="39819-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
