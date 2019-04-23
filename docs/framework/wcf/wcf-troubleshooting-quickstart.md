---
title: WCF 疑難排解快速入門
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 4327e8bb07cb03a91f7384f7fe82bc2e47f6fcb9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319998"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="6d92c-102">WCF 疑難排解快速入門</span><span class="sxs-lookup"><span data-stu-id="6d92c-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="6d92c-103">本主題列出客戶在開發 WCF 用戶端和服務時會碰到的幾個已知問題。</span><span class="sxs-lookup"><span data-stu-id="6d92c-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="6d92c-104">如果您遇到的問題不在此清單中，建議您為您的服務設定追蹤。</span><span class="sxs-lookup"><span data-stu-id="6d92c-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="6d92c-105">這會產生一個追蹤檔案，您可以使用追蹤檔案檢視器檢視這個檔案，並取得服務中可能會發生之例外狀況的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6d92c-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="6d92c-106">如需有關如何設定追蹤的詳細資訊，請參閱：[設定追蹤](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-106">For more information on configuring tracing, see: [Configuring Tracing](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="6d92c-107">如需有關追蹤檔案檢視器的詳細資訊，請參閱：[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="6d92c-108">安裝 Windows 7 和 IIS 之後，當我嘗試瀏覽至 WCF 服務時得到下列錯誤訊息：HTTP 錯誤 404.3 – 找不到</span><span class="sxs-lookup"><span data-stu-id="6d92c-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     <span data-ttu-id="6d92c-109">HTTP 錯誤 404.3 – 找不到。由於延伸組態的緣故，無法提供您要求的網頁。</span><span class="sxs-lookup"><span data-stu-id="6d92c-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="6d92c-110">若網頁是指令碼，請加入處理常式。</span><span class="sxs-lookup"><span data-stu-id="6d92c-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="6d92c-111">如應下載檔案，請加入 MIME 對應。</span><span class="sxs-lookup"><span data-stu-id="6d92c-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="6d92c-112">詳細的錯誤 InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="6d92c-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="6d92c-113">如果我的用戶端在第一個要求之後閒置一陣子，有時我會在第二個要求收到 MessageSecurityException。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3. [<span data-ttu-id="6d92c-114">我的服務在與大約 10 個用戶端互動之後，開始拒絕新的用戶端。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4. [<span data-ttu-id="6d92c-115">我可以從 WCF 應用程式的組態檔以外的地方載入我的服務組態嗎？</span><span class="sxs-lookup"><span data-stu-id="6d92c-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5. [<span data-ttu-id="6d92c-116">我的服務和用戶端運作良好，但是當用戶端在另一台電腦上時，它們就無法運作。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6. [<span data-ttu-id="6d92c-117">當我擲回 FaultException\<例外狀況 > 其中型別是例外狀況，我一定會收到一般的 FaultException 型別，用戶端上並不是泛型類型。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7. [<span data-ttu-id="6d92c-118">當回覆未包含任何資料時，單向和要求與回覆作業似乎會以大約相同的速度傳回。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8. [<span data-ttu-id="6d92c-119">我使用 X.509 憑證搭配我的服務，然後得到 System.Security.Cryptography.CryptographicException。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [<span data-ttu-id="6d92c-120">我將作業的第一個參數從大寫變更為小寫；現在我的用戶端擲回了例外狀況。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [<span data-ttu-id="6d92c-121">我正在使用我的其中一種追蹤工具，而我得到 EndpointNotFoundException。這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [<span data-ttu-id="6d92c-122">從 WCF SOAP 應用程式呼叫 WCF Web HTTP 應用程式時，服務就會傳回下列錯誤：405 不允許的方法</span><span class="sxs-lookup"><span data-stu-id="6d92c-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [<span data-ttu-id="6d92c-123">什麼是基底位址？它與端點位址如何產生關聯？</span><span class="sxs-lookup"><span data-stu-id="6d92c-123">What is the base address? How does it relate to an endpoint address?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="6d92c-124">安裝 Windows 7 和 IIS 之後，當我嘗試瀏覽至 WCF 服務時得到下列錯誤訊息：HTTP 錯誤 404.3 – 找不到</span><span class="sxs-lookup"><span data-stu-id="6d92c-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="6d92c-125">完整的錯誤訊息是：</span><span class="sxs-lookup"><span data-stu-id="6d92c-125">The full error message is:</span></span>  
  
 <span data-ttu-id="6d92c-126">HTTP 錯誤 404.3 – 找不到。由於延伸組態的緣故，無法提供您要求的網頁。</span><span class="sxs-lookup"><span data-stu-id="6d92c-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="6d92c-127">若網頁是指令碼，請加入處理常式。</span><span class="sxs-lookup"><span data-stu-id="6d92c-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="6d92c-128">如應下載檔案，請加入 MIME 對應。</span><span class="sxs-lookup"><span data-stu-id="6d92c-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="6d92c-129">詳細的錯誤 InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="6d92c-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="6d92c-130">在控制台中未明確設定 「 Windows Communication Foundation HTTP 啟動 」，就會發生此錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="6d92c-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="6d92c-131">若要設定此項目，請移至控制台，按一下視窗左下角的 [程式]。</span><span class="sxs-lookup"><span data-stu-id="6d92c-131">To set this go to the Control Panel, click Programs in the lower left hand corner of the window.</span></span> <span data-ttu-id="6d92c-132">按一下 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="6d92c-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="6d92c-133">展開 [Microsoft .NET Framework 3.5.1]，並選取 [Windows Communication Foundation Http 啟動]。</span><span class="sxs-lookup"><span data-stu-id="6d92c-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="6d92c-134">如果我的用戶端在第一個要求之後閒置一陣子，有時我會在第二個要求收到 MessageSecurityException。</span><span class="sxs-lookup"><span data-stu-id="6d92c-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="6d92c-135">這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-135">What is happening?</span></span>  
 <span data-ttu-id="6d92c-136">第二個要求可能會失敗，主要是基於兩個：（1） 工作階段已逾時或者 （2） 的裝載服務的 Web 伺服器就會回收。</span><span class="sxs-lookup"><span data-stu-id="6d92c-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="6d92c-137">第一種情況中，在服務逾時之前工作階段都是有效的。當服務未在服務繫結中指定的時間內收到來自用戶端的要求時 (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>)，服務會終止安全性工作階段。</span><span class="sxs-lookup"><span data-stu-id="6d92c-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="6d92c-138">後續的用戶端訊息會造成 <xref:System.ServiceModel.Security.MessageSecurityException>。</span><span class="sxs-lookup"><span data-stu-id="6d92c-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="6d92c-139">用戶端必須以此服務重新建立安全工作階段，以傳送未來的訊息或使用可設定狀態的安全性內容權杖。</span><span class="sxs-lookup"><span data-stu-id="6d92c-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="6d92c-140">可設定狀態的安全性內容權杖也允許安全工作階段存留已回收的 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6d92c-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="6d92c-141">如需使用安全工作階段的可設定狀態的安全性內容權杖的詳細資訊，請參閱[How to:建立安全性內容權杖的安全工作階段](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="6d92c-142">或者，您可以停用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="6d92c-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="6d92c-143">當您使用[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)繫結，您可以設定`establishSecurityContext`屬性設`false`停用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="6d92c-143">When you use the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="6d92c-144">如果要為其他繫結停用安全工作階段，必須建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="6d92c-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="6d92c-145">如需有關建立自訂繫結的詳細資訊，請參閱[How to:建立自訂繫結使用 SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="6d92c-146">在您套用其中任何一種選項之前，必須瞭解您應用程式的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="6d92c-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="6d92c-147">我的服務在與大約 10 個用戶端互動之後，開始拒絕新的用戶端。</span><span class="sxs-lookup"><span data-stu-id="6d92c-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="6d92c-148">這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-148">What is happening?</span></span>  
 <span data-ttu-id="6d92c-149">根據預設，服務同時只能有 10 個工作階段。</span><span class="sxs-lookup"><span data-stu-id="6d92c-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="6d92c-150">因此，如果服務繫結使用工作階段，服務會接受新用戶端連線直到到達該數目，然後拒絕新用戶端連線，直到其中一個目前工作階段結束為止。</span><span class="sxs-lookup"><span data-stu-id="6d92c-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="6d92c-151">您可以使用許多種方法來支援多個用戶端。</span><span class="sxs-lookup"><span data-stu-id="6d92c-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="6d92c-152">如果您的服務不需要工作階段，請勿使用工作階段繫結</span><span class="sxs-lookup"><span data-stu-id="6d92c-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="6d92c-153">(如需詳細資訊，請參閱 <<c0> [ 使用工作階段的](../../../docs/framework/wcf/using-sessions.md)。)另一種選擇是將 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> 屬性的值變更為適合您情況的數目，以增加工作階段限制。</span><span class="sxs-lookup"><span data-stu-id="6d92c-153">(For more information, see [Using Sessions](../../../docs/framework/wcf/using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="6d92c-154">我可以從 WCF 應用程式的組態檔以外的地方載入我的服務組態嗎？</span><span class="sxs-lookup"><span data-stu-id="6d92c-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="6d92c-155">可以，不過您必須建立覆寫 <xref:System.ServiceModel.ServiceHost> 方法的自訂 <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> 類別。</span><span class="sxs-lookup"><span data-stu-id="6d92c-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="6d92c-156">在該方法中，您可以呼叫基底先載入組態 (如果您也想要載入標準組態資訊)，但您也可以完全取代組態載入系統。</span><span class="sxs-lookup"><span data-stu-id="6d92c-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="6d92c-157">請注意，如果您要從與應用程式組態檔不同的組態檔載入組態，必須自行剖析組態檔並載入組態。</span><span class="sxs-lookup"><span data-stu-id="6d92c-157">Note that if you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="6d92c-158">下列程式碼範例將示範如何覆寫 <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> 方法，以及直接設定端點。</span><span class="sxs-lookup"><span data-stu-id="6d92c-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="6d92c-159">我的服務和用戶端運作良好，但是當用戶端在另一台電腦上時，它們就無法運作。</span><span class="sxs-lookup"><span data-stu-id="6d92c-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="6d92c-160">發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="6d92c-160">What’s happening?</span></span>  
 <span data-ttu-id="6d92c-161">根據例外狀況，可能有幾個問題：</span><span class="sxs-lookup"><span data-stu-id="6d92c-161">Depending upon the exception, there may be several issues:</span></span>  
  
-   <span data-ttu-id="6d92c-162">您可能需要將用戶端端點位址變更為主機名稱而非 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="6d92c-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
-   <span data-ttu-id="6d92c-163">您可能需要對應用程式開放連接埠。</span><span class="sxs-lookup"><span data-stu-id="6d92c-163">You might need to open the port to the application.</span></span> <span data-ttu-id="6d92c-164">如需詳細資料，請參閱 SDK 範例的 [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) 。</span><span class="sxs-lookup"><span data-stu-id="6d92c-164">For details, see [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
-   <span data-ttu-id="6d92c-165">如需其他可能的問題，請參閱範例主題[執行 Windows Communication Foundation 範例](./samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-165">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
-   <span data-ttu-id="6d92c-166">如果您的用戶端是使用 Windows 認證，且例外狀況為 <xref:System.ServiceModel.Security.SecurityNegotiationException>，請設定 Kerberos 如下。</span><span class="sxs-lookup"><span data-stu-id="6d92c-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1.  <span data-ttu-id="6d92c-167">將身分識別認證新增至用戶端的 App.config 檔案中的端點項目：</span><span class="sxs-lookup"><span data-stu-id="6d92c-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2.  <span data-ttu-id="6d92c-168">在 System 或 NetworkService 帳戶下執行自我主控的服務。</span><span class="sxs-lookup"><span data-stu-id="6d92c-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="6d92c-169">您可以執行這個命令，在 System 帳戶下建立命令視窗：</span><span class="sxs-lookup"><span data-stu-id="6d92c-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  <span data-ttu-id="6d92c-170">在網際網路資訊服務 (IIS) 下主控服務，根據預設，它會使用服務主要名稱 (SPN) 帳戶。</span><span class="sxs-lookup"><span data-stu-id="6d92c-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4.  <span data-ttu-id="6d92c-171">使用 SetSPN 向網域註冊新的 SPN。</span><span class="sxs-lookup"><span data-stu-id="6d92c-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="6d92c-172">請注意，您必須是網域系統管理員才能執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="6d92c-172">Note that you will need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="6d92c-173">如需有關 Kerberos 通訊協定的詳細資訊，請參閱 < [Security Concepts Used in WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md)和：</span><span class="sxs-lookup"><span data-stu-id="6d92c-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
-   [<span data-ttu-id="6d92c-174">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="6d92c-174">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [<span data-ttu-id="6d92c-175">使用 Http.sys 登錄 Kerberos 服務主要名稱</span><span class="sxs-lookup"><span data-stu-id="6d92c-175">Registering Kerberos Service Principal Names by Using Http.sys</span></span>](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [<span data-ttu-id="6d92c-176">Kerberos 說明</span><span class="sxs-lookup"><span data-stu-id="6d92c-176">Kerberos Explained</span></span>](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="6d92c-177">當我擲回 FaultException\<例外狀況 > 其中型別是例外狀況，我一定會收到一般的 FaultException 型別，用戶端上並不是泛型類型。</span><span class="sxs-lookup"><span data-stu-id="6d92c-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="6d92c-178">發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="6d92c-178">What’s happening?</span></span>  
 <span data-ttu-id="6d92c-179">強烈建議您建議自己的自訂錯誤資料型別，並宣告為您的錯誤合約中的詳細型別。</span><span class="sxs-lookup"><span data-stu-id="6d92c-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="6d92c-180">原因是使用系統提供的例外狀況類型：</span><span class="sxs-lookup"><span data-stu-id="6d92c-180">The reason is that using system-provided exception types:</span></span>  
  
-   <span data-ttu-id="6d92c-181">建立類型依存性，移除服務導向應用程式的其中一個最大的強度。</span><span class="sxs-lookup"><span data-stu-id="6d92c-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
-   <span data-ttu-id="6d92c-182">無法依存以標準方式序列化的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d92c-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="6d92c-183">有些 (例如 <xref:System.Security.SecurityException>) 可能完全不能序列化。</span><span class="sxs-lookup"><span data-stu-id="6d92c-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
-   <span data-ttu-id="6d92c-184">對用戶端公開內部實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6d92c-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="6d92c-185">如需詳細資訊，請參閱 <<c0> [ 指定及處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-185">For more information, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="6d92c-186">然而，如果您是對應用程式進行偵錯，可以使用 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 類別來序列化例外狀況資訊，並傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="6d92c-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="6d92c-187">當回覆未包含任何資料時，單向和要求與回覆作業似乎會以大約相同的速度傳回。</span><span class="sxs-lookup"><span data-stu-id="6d92c-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="6d92c-188">這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-188">What's happening?</span></span>  
 <span data-ttu-id="6d92c-189">將作業指定為單向只是表示作業合約接受輸入訊息，而沒有傳回輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="6d92c-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="6d92c-190">在 WCF 中，所有的用戶端叫用時，傳回的輸出資料寫入網路或擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d92c-190">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="6d92c-191">單向作業的運作方式相同，如果找不到服務可以擲回，或如果服務尚未準備好從網路接受資料便會封鎖。</span><span class="sxs-lookup"><span data-stu-id="6d92c-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="6d92c-192">通常在 WCF 中，這會導致單向呼叫比要求與回覆; 更快速地傳回給用戶端但是任何減慢傳出資料傳送透過網路的條件會減慢單向作業以及要求-回覆作業。</span><span class="sxs-lookup"><span data-stu-id="6d92c-192">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="6d92c-193">如需詳細資訊，請參閱 <<c0> [ 單向服務](../../../docs/framework/wcf/feature-details/one-way-services.md)並[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-193">For more information, see [One-Way Services](../../../docs/framework/wcf/feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="6d92c-194">我使用 X.509 憑證搭配我的服務，然後得到 System.Security.Cryptography.CryptographicException。</span><span class="sxs-lookup"><span data-stu-id="6d92c-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="6d92c-195">發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="6d92c-195">What’s happening?</span></span>  
 <span data-ttu-id="6d92c-196">這常常發生在變更用來執行 IIS 背景工作處理序的使用者帳戶之後。</span><span class="sxs-lookup"><span data-stu-id="6d92c-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="6d92c-197">例如，在 [!INCLUDE[wxp](../../../includes/wxp-md.md)]中，如果您將用於執行 Aspnet_wp.exe 的預設使用者帳戶從 ASPNET 變更為自訂使用者帳戶，您可能會看到這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d92c-197">For example, in [!INCLUDE[wxp](../../../includes/wxp-md.md)], if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="6d92c-198">如果使用私密金鑰，使用它的處理序將會需要有權限才能存取儲存該金鑰的檔案。</span><span class="sxs-lookup"><span data-stu-id="6d92c-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="6d92c-199">如果是這種情況，您必須提供存取權限給處理序的帳戶，檔案才能包含私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="6d92c-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="6d92c-200">例如，如果 IIS 背景工作處理序正在 Bob 帳戶下執行，則您會需要為 Bob 提供含有私密金鑰的檔案的讀取權。</span><span class="sxs-lookup"><span data-stu-id="6d92c-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="6d92c-201">如需如何授與正確的使用者帳戶存取權包含特定的 X.509 憑證的私密金鑰之檔案的詳細資訊，請參閱[How to:讓 WCF 能夠存取 X.509 憑證](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="6d92c-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="6d92c-202">我將作業的第一個參數從大寫變更為小寫；現在我的用戶端擲回了例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d92c-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="6d92c-203">這是為什麼？</span><span class="sxs-lookup"><span data-stu-id="6d92c-203">What's happening?</span></span>  
 <span data-ttu-id="6d92c-204">作業簽章中參數名稱的值是合約的一部分，而且必須區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="6d92c-204">The value of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="6d92c-205">當您需要區分本機參數名稱和描述用戶端應用程式的作業的中繼資料時，請使用 <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6d92c-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="6d92c-206">我正在使用我的其中一種追蹤工具，而我得到 EndpointNotFoundException。</span><span class="sxs-lookup"><span data-stu-id="6d92c-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="6d92c-207">發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="6d92c-207">What’s happening?</span></span>  
 <span data-ttu-id="6d92c-208">如果您使用一種追蹤工具，不是系統提供的 WCF 追蹤機制，而且您會收到<xref:System.ServiceModel.EndpointNotFoundException>表示，位址篩選不符的情況，您需要使用<xref:System.ServiceModel.Description.ClientViaBehavior>追蹤公用程式將訊息導向的類別和已將這些訊息重新導向至服務位址的公用程式。</span><span class="sxs-lookup"><span data-stu-id="6d92c-208">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="6d92c-209"><xref:System.ServiceModel.Description.ClientViaBehavior> 類別會變更 `Via` 位址標頭，以指定與最終接收者不同的下一個網路位址，由 `To` 位址標頭指示。</span><span class="sxs-lookup"><span data-stu-id="6d92c-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="6d92c-210">然而，執行這項操作時，請勿變更端點位址，它是用於建立 `To` 值的。</span><span class="sxs-lookup"><span data-stu-id="6d92c-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="6d92c-211">下列程式碼範例顯示用戶端組態檔範例。</span><span class="sxs-lookup"><span data-stu-id="6d92c-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint   
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="6d92c-212">什麼是基底位址？</span><span class="sxs-lookup"><span data-stu-id="6d92c-212">What is the base address?</span></span> <span data-ttu-id="6d92c-213">它與端點位址如何產生關聯？</span><span class="sxs-lookup"><span data-stu-id="6d92c-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="6d92c-214">基底位址是 <xref:System.ServiceModel.ServiceHost> 類別的根位址。</span><span class="sxs-lookup"><span data-stu-id="6d92c-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="6d92c-215">根據預設，如果您將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 類別新增至服務組態中，會從 HTTP 基底位址擷取主機發行的所有端點的 Web 服務描述語言 (WSDL)，加上提供給中繼資料行為的相對位址，加上 "?wsdl"。</span><span class="sxs-lookup"><span data-stu-id="6d92c-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="6d92c-216">如果您熟悉 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 和 IIS，基底位址就等同虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="6d92c-216">If you are familiar with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="6d92c-217">使用 NetTcpBinding 在服務端點與 MEX 端點之間共用通訊埠</span><span class="sxs-lookup"><span data-stu-id="6d92c-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="6d92c-218">如果您將服務的基底位址指定為 net.tcp://MyServer:8080/MyService，並且加入下列端點：</span><span class="sxs-lookup"><span data-stu-id="6d92c-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="6d92c-219">而且，如果您修改其中一個 NetTcpBinding 設定，如下列組態片段所示：</span><span class="sxs-lookup"><span data-stu-id="6d92c-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="6d92c-220">您會看到類似下列錯誤：未處理的例外狀況：System.ServiceModel.AddressAlreadyInUseException:您可以藉由指定完整的 URL 使用不同的連接埠的 MEX 端點，如下列組態片段所示暫時解決這個錯誤的 IP 端點 0.0.0.0:9000 上已經有接聽程式：</span><span class="sxs-lookup"><span data-stu-id="6d92c-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="6d92c-221">從 WCF SOAP 應用程式呼叫 WCF Web HTTP 應用程式時，服務就會傳回下列錯誤：405 不允許的方法</span><span class="sxs-lookup"><span data-stu-id="6d92c-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="6d92c-222">呼叫 WCF Web HTTP 應用程式 (使用的服務<xref:System.ServiceModel.WebHttpBinding>和<xref:System.ServiceModel.Description.WebHttpBehavior>) 從 WCF 服務可能會產生下列例外狀況：`Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]:遠端伺服器傳回未預期的回應：(405) 方法不允許。 ' 發生這個例外狀況，因為 WCF 覆寫傳出<xref:System.ServiceModel.OperationContext>以傳入<xref:System.ServiceModel.OperationContext>。</span><span class="sxs-lookup"><span data-stu-id="6d92c-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.\` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="6d92c-223">若要解決這個問題，請在 WCF Web HTTP 服務作業中建立 <xref:System.ServiceModel.OperationContextScope> 。</span><span class="sxs-lookup"><span data-stu-id="6d92c-223">To solve this problem create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="6d92c-224">例如: </span><span class="sxs-lookup"><span data-stu-id="6d92c-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d92c-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d92c-225">See also</span></span>

- [<span data-ttu-id="6d92c-226">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="6d92c-226">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
