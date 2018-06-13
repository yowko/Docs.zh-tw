---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 64a7cba7b1bbc55a4504e3af4784fcb2a84f0fa1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807224"
---
# <a name="httpcookiesession"></a><span data-ttu-id="b34e2-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="b34e2-102">HttpCookieSession</span></span>
<span data-ttu-id="b34e2-103">這個範例會示範如何建置自訂通訊協定通道，以便在工作階段管理使用 HTTP Cookie。</span><span class="sxs-lookup"><span data-stu-id="b34e2-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="b34e2-104">這個通道可以啟用 Windows Communication Foundation (WCF) 服務和 ASMX 用戶端或 WCF 用戶端與 ASMX 服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="b34e2-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="b34e2-105">當用戶端在工作階段架構 ASMX Web 服務中呼叫 Web 方法時，[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 引擎會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b34e2-105">When a client calls a Web method in an ASMX Web service that is session-based, the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] engine does the following:</span></span>  
  
-   <span data-ttu-id="b34e2-106">產生唯一 ID (工作階段 ID)。</span><span class="sxs-lookup"><span data-stu-id="b34e2-106">Generates a unique ID (session ID).</span></span>  
  
-   <span data-ttu-id="b34e2-107">產生工作階段物件，並使該物件與唯一 ID 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b34e2-107">Generates the session object and associates it with the unique ID.</span></span>  
  
-   <span data-ttu-id="b34e2-108">將唯一 ID 新增至 Set-Cookie HTTP 回應標頭，並傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="b34e2-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
-   <span data-ttu-id="b34e2-109">根據傳送至用戶端的工作階段 ID，識別後續呼叫上的用戶端。</span><span class="sxs-lookup"><span data-stu-id="b34e2-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="b34e2-110">用戶端會在傳送至伺服器的後續要求中，加入這個工作階段 ID。</span><span class="sxs-lookup"><span data-stu-id="b34e2-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="b34e2-111">伺服器則會使用來自用戶端的工作階段 ID，為目前的 HTTP 內容載入適當的工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="b34e2-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b34e2-112">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b34e2-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b34e2-113">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b34e2-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b34e2-114">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="b34e2-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b34e2-115">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b34e2-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="b34e2-116">HttpCookieSession 通道訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="b34e2-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="b34e2-117">這個範例會對類似 ASMX 的案例啟用工作階段。</span><span class="sxs-lookup"><span data-stu-id="b34e2-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="b34e2-118">在通道堆疊的底部，將會提供支援 <xref:System.ServiceModel.Channels.IRequestChannel> 和 <xref:System.ServiceModel.Channels.IReplyChannel> 的 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="b34e2-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="b34e2-119">通道的工作就是要對通道堆疊的較高層級提供工作階段。</span><span class="sxs-lookup"><span data-stu-id="b34e2-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="b34e2-120">這個範例會實作兩個支援工作階段的通道 (<xref:System.ServiceModel.Channels.IRequestSessionChannel> 和 <xref:System.ServiceModel.Channels.IReplySessionChannel>)。</span><span class="sxs-lookup"><span data-stu-id="b34e2-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="b34e2-121">服務通道</span><span class="sxs-lookup"><span data-stu-id="b34e2-121">Service Channel</span></span>  
 <span data-ttu-id="b34e2-122">範例會在 `HttpCookieReplySessionChannelListener` 類別中提供服務通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="b34e2-123">這個類別會實作 <xref:System.ServiceModel.Channels.IChannelListener> 介面，並將通道堆疊中較低的 <xref:System.ServiceModel.Channels.IReplyChannel> 通道轉換為 <xref:System.ServiceModel.Channels.IReplySessionChannel>。</span><span class="sxs-lookup"><span data-stu-id="b34e2-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="b34e2-124">這個處理序可以分成下列幾個部分：</span><span class="sxs-lookup"><span data-stu-id="b34e2-124">This process can be divided into the following parts:</span></span>  
  
-   <span data-ttu-id="b34e2-125">通道接聽程式開啟時，會接受來自內部接聽程式的內部通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="b34e2-126">因為內部接聽程式為資料包 (Datagram) 接聽程式，而且所接受通道的時間範圍會少於接聽程式的時間範圍，因此我們可以關閉內部接聽程式而只保留內部通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   <span data-ttu-id="b34e2-127">完成開啟的處理序時，我們會設定訊息迴圈以接收來自內部通道的訊息。</span><span class="sxs-lookup"><span data-stu-id="b34e2-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   <span data-ttu-id="b34e2-128">訊息抵達時，服務通道會檢查工作階段識別碼，並將信號分離至適當的工作階段通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="b34e2-129">通道接聽程式所維護的字典，會將工作階段識別碼對應至工作階段通道執行個體。</span><span class="sxs-lookup"><span data-stu-id="b34e2-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="b34e2-130">`HttpCookieReplySessionChannel` 類別會實作 <xref:System.ServiceModel.Channels.IReplySessionChannel>。</span><span class="sxs-lookup"><span data-stu-id="b34e2-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="b34e2-131">通道堆疊的較高層級會呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 方法，以讀取此工作階段的要求。</span><span class="sxs-lookup"><span data-stu-id="b34e2-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="b34e2-132">每個工作階段通道都有由服務通道所填入 (Populate) 的私用訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="b34e2-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="b34e2-133">在某人呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 方法而且訊息佇列中沒有任何訊息的情況下，通道會先等待指定的時間量，然後才自行關機。</span><span class="sxs-lookup"><span data-stu-id="b34e2-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="b34e2-134">這會清除為非 WCF 用戶端建立的工作階段通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="b34e2-135">我們會使用 `channelMapping` 來追蹤 `ReplySessionChannels`，而在所有已接受的通道關閉之前，不會關閉基礎 `innerChannel`。</span><span class="sxs-lookup"><span data-stu-id="b34e2-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="b34e2-136">使用這個方法時，`HttpCookieReplySessionChannel` 存在的時間會超過 `HttpCookieReplySessionChannelListener` 的存留期。</span><span class="sxs-lookup"><span data-stu-id="b34e2-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="b34e2-137">我們也不用擔心接聽程式會在執行時進行記憶體回收，因為接受的通道會透過 `OnClosed` 回呼參考其接聽程式。</span><span class="sxs-lookup"><span data-stu-id="b34e2-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="b34e2-138">用戶端通道</span><span class="sxs-lookup"><span data-stu-id="b34e2-138">Client channel</span></span>  
 <span data-ttu-id="b34e2-139">對應的用戶端通道位於 `HttpCookieSessionChannelFactory` 類別中。</span><span class="sxs-lookup"><span data-stu-id="b34e2-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="b34e2-140">在通道建立期間，通道處理站會使用 `HttpCookieRequestSessionChannel` 包裝內部要求。</span><span class="sxs-lookup"><span data-stu-id="b34e2-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="b34e2-141">`HttpCookieRequestSessionChannel` 類別則會將呼叫轉寄至基礎要求通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="b34e2-142">當用戶端關閉 Proxy 時，`HttpCookieRequestSessionChannel` 會將訊息傳送至服務，指出通道正在關閉。</span><span class="sxs-lookup"><span data-stu-id="b34e2-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="b34e2-143">因此，服務通道堆疊可順利關閉使用中的工作階段通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="b34e2-144">繫結和繫結項目</span><span class="sxs-lookup"><span data-stu-id="b34e2-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="b34e2-145">建立服務與用戶端通道之後, 的下一個步驟是將它們整合到 WCF 執行階段。</span><span class="sxs-lookup"><span data-stu-id="b34e2-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="b34e2-146">通道會透過繫結和繫結項目公開至 WCF。</span><span class="sxs-lookup"><span data-stu-id="b34e2-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="b34e2-147">繫結是由一個或多個繫結元素所組成。</span><span class="sxs-lookup"><span data-stu-id="b34e2-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="b34e2-148">WCF 提供數種具有系統定義的繫結。例如，BasicHttpBinding 或 WSHttpBinding。</span><span class="sxs-lookup"><span data-stu-id="b34e2-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="b34e2-149">`HttpCookieSessionBindingElement` 類別含有繫結項目的實作。</span><span class="sxs-lookup"><span data-stu-id="b34e2-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="b34e2-150">該類別會覆寫通道接聽程式和通道處理站的建立方法，以執行必要的通道接聽程式或通道處理站執行個體化 (Instantiation)。</span><span class="sxs-lookup"><span data-stu-id="b34e2-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="b34e2-151">範例會在服務描述中使用原則判斷提示。</span><span class="sxs-lookup"><span data-stu-id="b34e2-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="b34e2-152">這可讓範例將其通道需求發行至使用服務的其他用戶端。</span><span class="sxs-lookup"><span data-stu-id="b34e2-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="b34e2-153">例如，這個繫結項目會發行原則判斷提示，讓可能的用戶端清楚繫結項目可支援工作階段。</span><span class="sxs-lookup"><span data-stu-id="b34e2-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="b34e2-154">由於範例會啟用繫結項目組態中的 `ExchangeTerminateMessage` 屬性，因此會新增必要的判斷提示，表示該服務支援額外的訊息交換動作以終止工作階段對話。</span><span class="sxs-lookup"><span data-stu-id="b34e2-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="b34e2-155">接著，用戶端就可以使用此動作。</span><span class="sxs-lookup"><span data-stu-id="b34e2-155">Clients can then use this action.</span></span> <span data-ttu-id="b34e2-156">下列 WSDL 程式碼會顯示從 `HttpCookieSessionBindingElement` 建立的原則判斷提示。</span><span class="sxs-lookup"><span data-stu-id="b34e2-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="b34e2-157">`HttpCookieSessionBinding` 類別是系統提供的繫結，會使用先前描述的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="b34e2-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="b34e2-158">將通道新增至組態系統</span><span class="sxs-lookup"><span data-stu-id="b34e2-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="b34e2-159">此範例提供了兩個類別，這兩個類別會透過組態來公開範例通道。</span><span class="sxs-lookup"><span data-stu-id="b34e2-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="b34e2-160">第一個類別為 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 的 `HttpCookieSessionBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="b34e2-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="b34e2-161">大量實作會委派至衍生自 `HttpCookieSessionBindingConfigurationElement` 的 <xref:System.ServiceModel.Configuration.StandardBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="b34e2-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="b34e2-162">`HttpCookieSessionBindingConfigurationElement` 的屬性會對應至 `HttpCookieSessionBindingElement` 上的屬性。</span><span class="sxs-lookup"><span data-stu-id="b34e2-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="b34e2-163">繫結項目延伸區段</span><span class="sxs-lookup"><span data-stu-id="b34e2-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="b34e2-164">區段 `HttpCookieSessionBindingElementSection` 是 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>，它會將 `HttpCookieSessionBindingElement` 公開至組態系統。</span><span class="sxs-lookup"><span data-stu-id="b34e2-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="b34e2-165">透過一些覆寫，會定義組態區段名稱、繫結項目的型別，以及如何建立繫結項目。</span><span class="sxs-lookup"><span data-stu-id="b34e2-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="b34e2-166">然後您可以在組態檔中登錄延伸區段，如同下列所示：</span><span class="sxs-lookup"><span data-stu-id="b34e2-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="b34e2-167">測試程式碼</span><span class="sxs-lookup"><span data-stu-id="b34e2-167">Test Code</span></span>  
 <span data-ttu-id="b34e2-168">您可以在用戶端和服務目錄中，找到使用此範例傳輸的測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="b34e2-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="b34e2-169">它包含兩個測試，一項測試會使用的繫結`allowCookies`設`true`用戶端上。</span><span class="sxs-lookup"><span data-stu-id="b34e2-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="b34e2-170">第二個測試則會在繫結上啟用明確關閉 (使用終止訊息交換)。</span><span class="sxs-lookup"><span data-stu-id="b34e2-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="b34e2-171">當您執行範例時，您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b34e2-171">When you run the sample, you should see the following output:</span></span>  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b34e2-172">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="b34e2-172">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b34e2-173">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="b34e2-173">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="b34e2-174">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b34e2-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="b34e2-175">若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b34e2-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="b34e2-176">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b34e2-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b34e2-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b34e2-177">See Also</span></span>
