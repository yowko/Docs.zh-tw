---
title: 與 POX 應用程式的互通性
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 7522233723b6b91d5a7b27d3f82ca328e29ce3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494195"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="66aae-102">與 POX 應用程式的互通性</span><span class="sxs-lookup"><span data-stu-id="66aae-102">Interoperability with POX Applications</span></span>
<span data-ttu-id="66aae-103">"Plain Old XML"(POX) 應用程式交換僅包含 XML 應用程式資料不是在 SOAP envelope 內包含的原始 HTTP 訊息來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="66aae-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="66aae-104">使用 POX 訊息的用戶端和服務，可以提供 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="66aae-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="66aae-105">在服務上，WCF 可以用於實作公開端點，如網頁瀏覽器的用戶端的服務和傳送和接收 POX 訊息的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="66aae-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="66aae-106">在用戶端，WCF 程式設計模型可用來實作與 POX 式服務通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="66aae-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66aae-107">本文件原本是針對 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 而撰寫。</span><span class="sxs-lookup"><span data-stu-id="66aae-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]<span data-ttu-id="66aae-108"> 3.5 具有可使用 POX 應用程式的內建支援。</span><span class="sxs-lookup"><span data-stu-id="66aae-108"> 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="66aae-109">如需詳細資訊，請參閱有關[WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="66aae-109">For more information about see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span></span>  
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="66aae-110">使用 WCF 的 POX 程式撰寫</span><span class="sxs-lookup"><span data-stu-id="66aae-110">POX Programming with WCF</span></span>  
 <span data-ttu-id="66aae-111">使用 POX 訊息使用透過 HTTP 通訊的 WCF 服務[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="66aae-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="66aae-112">此自訂繫結包含兩個項目：</span><span class="sxs-lookup"><span data-stu-id="66aae-112">This custom binding contains two elements:</span></span>  
  
-   <span data-ttu-id="66aae-113">[ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)和</span><span class="sxs-lookup"><span data-stu-id="66aae-113">The [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) and</span></span>  
  
-   <span data-ttu-id="66aae-114">[ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)。</span><span class="sxs-lookup"><span data-stu-id="66aae-114">The [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
 <span data-ttu-id="66aae-115">WCF 文字訊息編碼器特別設定為使用的標準<xref:System.ServiceModel.Channels.MessageVersion.None%2A>使其可以處理 XML 訊息承載不會到達包裝在 SOAP envelope 中的值。</span><span class="sxs-lookup"><span data-stu-id="66aae-115">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>  
  
 <span data-ttu-id="66aae-116">使用 POX 訊息透過 HTTP 通訊的 WCF 用戶端使用類似的繫結 （如下列命令式程式碼所示）。</span><span class="sxs-lookup"><span data-stu-id="66aae-116">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 <span data-ttu-id="66aae-117">由於 POX 用戶端必須指定它們傳送訊息所至的 URI，因此它們通常必須在項目上將 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 屬性設定為 <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A>，以便將 `true` 設定為手動定址模式。</span><span class="sxs-lookup"><span data-stu-id="66aae-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="66aae-118">這樣做使應用程式程式碼可以明確將訊息定址，而且不需要在每次應用程式傳送訊息至不同的 HTTP URI 時都建立新的 <xref:System.ServiceModel.ChannelFactory>。</span><span class="sxs-lookup"><span data-stu-id="66aae-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>  
  
 <span data-ttu-id="66aae-119">由於 POX 訊息不使用 SOA 標頭傳送重要的通訊協定資訊，因此 POX 用戶端和服務經常必須管理基礎 HTTP 要求的片段以傳送或接收訊息。</span><span class="sxs-lookup"><span data-stu-id="66aae-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="66aae-120">WCF 程式設計模型透過兩個類別中提出 HTTP 標頭和狀態碼等 HTTP 特定通訊協定資訊：</span><span class="sxs-lookup"><span data-stu-id="66aae-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>  
  
-   <span data-ttu-id="66aae-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>，包含有關 HTTP 要求的資訊，例如 HTTP 方法和要求標頭。</span><span class="sxs-lookup"><span data-stu-id="66aae-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>  
  
-   <span data-ttu-id="66aae-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>，包含有關 HTTP 回應的資訊，例如 HTTP 狀態代碼、狀態說明與任何 HTTP 回應標頭。</span><span class="sxs-lookup"><span data-stu-id="66aae-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>  
  
 <span data-ttu-id="66aae-123">下列程式碼範例示範如何建立定址至 HTTP GET 要求訊息http://localhost:8100/customers。</span><span class="sxs-lookup"><span data-stu-id="66aae-123">The following code example shows how to create an HTTP GET request message that is addressed to http://localhost:8100/customers.</span></span>  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 <span data-ttu-id="66aae-124">首先呼叫 <xref:System.ServiceModel.Channels.Message> 來建立空白的要求 <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>。</span><span class="sxs-lookup"><span data-stu-id="66aae-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="66aae-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> 可用於指示不需要 SOAP 封套，並且傳遞 <xref:System.String.Empty> 參數做為動作。</span><span class="sxs-lookup"><span data-stu-id="66aae-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="66aae-126">然後，將 <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> 標頭設定為所需的 URI 以便將要求訊息定址。</span><span class="sxs-lookup"><span data-stu-id="66aae-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="66aae-127">接著，建立 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>，並且將 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> 設定為 HTTP 動詞 GET 方法，以及將 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> 設定為 `true`，以指示不應在傳出 HTTP 要求訊息的本文中傳送任何資料。</span><span class="sxs-lookup"><span data-stu-id="66aae-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="66aae-128">最後將要求屬性新增至要求訊息的 <xref:System.ServiceModel.Channels.Message.Properties%2A> 集合中，因此可影響 HTTP 傳輸如何傳送要求。</span><span class="sxs-lookup"><span data-stu-id="66aae-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="66aae-129">然後準備好透過 <xref:System.ServiceModel.Channels.IRequestChannel> 的適當執行個體傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="66aae-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>  
  
 <span data-ttu-id="66aae-130">可在服務上使用類似的技巧，以擷取來自傳入訊息的 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> 並建構回應。</span><span class="sxs-lookup"><span data-stu-id="66aae-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
