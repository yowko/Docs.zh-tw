---
title: HOW TO：啟用訊息重新執行偵測
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: a7bdfc244b0ff1c2ed625235df7e74ced026c542
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343606"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="7ff86-102">HOW TO：啟用訊息重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="7ff86-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="7ff86-103">當攻擊者複製兩方之間的訊息資料流，並且對其中一方或多方重新執行資料流時，即表示發生重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="7ff86-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="7ff86-104">除非緩解攻擊，否則受到攻擊的電腦會將資料流當成合法訊息來處理，導致發生一連串負面的影響，例如項目的重複排序。</span><span class="sxs-lookup"><span data-stu-id="7ff86-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="7ff86-105">如需有關訊息重新執行偵測的詳細資訊，請參閱[訊息重新執行偵測](https://go.microsoft.com/fwlink/?LinkId=88536)。</span><span class="sxs-lookup"><span data-stu-id="7ff86-105">For more information about message replay detection, see [Message Replay Detection](https://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="7ff86-106">下列程序示範您可以使用來控制使用 Windows Communication Foundation (WCF) 的重新執行偵測的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="7ff86-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="7ff86-107">若要透過程式碼在用戶端上控制重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="7ff86-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="7ff86-108">建立用於 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的 <xref:System.ServiceModel.Channels.CustomBinding>。</span><span class="sxs-lookup"><span data-stu-id="7ff86-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="7ff86-109">如需詳細資訊，請參閱[如何：建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。</span><span class="sxs-lookup"><span data-stu-id="7ff86-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="7ff86-110">下列範例會使用 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> (使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> 類別的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 來建立)。</span><span class="sxs-lookup"><span data-stu-id="7ff86-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="7ff86-111">請使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> 屬性將參照傳回 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> 類別，並在必要時設定下列任何一個屬性：</span><span class="sxs-lookup"><span data-stu-id="7ff86-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  `DetectReplay`<span data-ttu-id="7ff86-112">。</span><span class="sxs-lookup"><span data-stu-id="7ff86-112">.</span></span> <span data-ttu-id="7ff86-113">布林值 (Boolean)。</span><span class="sxs-lookup"><span data-stu-id="7ff86-113">A Boolean value.</span></span> <span data-ttu-id="7ff86-114">它將控制用戶端是否應該偵測來自伺服器的重新執行。</span><span class="sxs-lookup"><span data-stu-id="7ff86-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="7ff86-115">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7ff86-115">The default is `true`.</span></span>  
  
    2.  `MaxClockSkew`<span data-ttu-id="7ff86-116">。</span><span class="sxs-lookup"><span data-stu-id="7ff86-116">.</span></span> <span data-ttu-id="7ff86-117"><xref:System.TimeSpan> 值。</span><span class="sxs-lookup"><span data-stu-id="7ff86-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="7ff86-118">控制在用戶端與伺服器之間重新執行機制可容許的時間誤差。</span><span class="sxs-lookup"><span data-stu-id="7ff86-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="7ff86-119">安全性機制會檢查傳送的時間戳記並判斷它是否已經傳送出去太久了。</span><span class="sxs-lookup"><span data-stu-id="7ff86-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="7ff86-120">預設值是 5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="7ff86-120">The default is 5 minutes.</span></span>  
  
    3.  `ReplayWindow`<span data-ttu-id="7ff86-121">。</span><span class="sxs-lookup"><span data-stu-id="7ff86-121">.</span></span> <span data-ttu-id="7ff86-122">`TimeSpan` 值。</span><span class="sxs-lookup"><span data-stu-id="7ff86-122">A `TimeSpan` value.</span></span> <span data-ttu-id="7ff86-123">它會控制訊息在經由伺服器傳送出去 (透過媒介) 並在抵達用戶端之前，可以在網路中存留的時間長短。</span><span class="sxs-lookup"><span data-stu-id="7ff86-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="7ff86-124">用戶端會追蹤於最近 `ReplayWindow` 傳送的訊息簽章，以利進行重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="7ff86-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  `ReplayCacheSize`<span data-ttu-id="7ff86-125">。</span><span class="sxs-lookup"><span data-stu-id="7ff86-125">.</span></span> <span data-ttu-id="7ff86-126">整數值。</span><span class="sxs-lookup"><span data-stu-id="7ff86-126">An integer value.</span></span> <span data-ttu-id="7ff86-127">用戶端會將訊息簽章儲存到快取中。</span><span class="sxs-lookup"><span data-stu-id="7ff86-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="7ff86-128">這項設定將指定快取可以儲存的簽章數量。</span><span class="sxs-lookup"><span data-stu-id="7ff86-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="7ff86-129">如果最近一次重新執行視窗中傳送的訊息數量到達快取上限，則會等到最早的快取簽章抵達時間限制才會開始接受新的訊息。</span><span class="sxs-lookup"><span data-stu-id="7ff86-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="7ff86-130">預設值為 500000。</span><span class="sxs-lookup"><span data-stu-id="7ff86-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="7ff86-131">若要透過程式碼在服務上控制重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="7ff86-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="7ff86-132">建立用於 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的 <xref:System.ServiceModel.Channels.CustomBinding>。</span><span class="sxs-lookup"><span data-stu-id="7ff86-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="7ff86-133">請使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> 屬性將參照傳回 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 類別，然後如先前所述設定屬性。</span><span class="sxs-lookup"><span data-stu-id="7ff86-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="7ff86-134">若要透過組態來控制用戶端或服務的重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="7ff86-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="7ff86-135">建立[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="7ff86-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="7ff86-136">建立 `<security>` 項目。</span><span class="sxs-lookup"><span data-stu-id="7ff86-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="7ff86-137">建立[ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)或是[ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)。</span><span class="sxs-lookup"><span data-stu-id="7ff86-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="7ff86-138">必要時設定 `detectReplays`、`maxClockSkew`、`replayWindow`，和 `replayCacheSize` 的屬性值。</span><span class="sxs-lookup"><span data-stu-id="7ff86-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="7ff86-139">下列範例將同時設定 `<localServiceSettings>`和`<localClientSettings>` 項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ff86-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="7ff86-140">範例</span><span class="sxs-lookup"><span data-stu-id="7ff86-140">Example</span></span>  
 <span data-ttu-id="7ff86-141">下列範例將使用 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 方法來建立 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>，並設定繫結的重新執行屬性。</span><span class="sxs-lookup"><span data-stu-id="7ff86-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="7ff86-142">重新執行範圍：只有在訊息安全性</span><span class="sxs-lookup"><span data-stu-id="7ff86-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="7ff86-143">請注意，下列程序僅適用訊息安全性模式。</span><span class="sxs-lookup"><span data-stu-id="7ff86-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="7ff86-144">在 [傳輸] 與 [使用訊息認證的傳輸] 模式中，傳輸機制會偵測重新執行。</span><span class="sxs-lookup"><span data-stu-id="7ff86-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="7ff86-145">安全對話提示</span><span class="sxs-lookup"><span data-stu-id="7ff86-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="7ff86-146">針對可啟用安全對話的繫結，您可以同時對應用程式通道，以及安全對話啟動安裝繫結調整這些設定。</span><span class="sxs-lookup"><span data-stu-id="7ff86-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="7ff86-147">例如，您可以關閉應用程式通道的重新執行，但卻針對可建立安全對話的啟動安裝繫結加以啟用。</span><span class="sxs-lookup"><span data-stu-id="7ff86-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="7ff86-148">如果您並未使用安全對話工作階段，重新執行偵測將無法保證在伺服器陣列案例以及處理序回收期間偵測重新執行。</span><span class="sxs-lookup"><span data-stu-id="7ff86-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="7ff86-149">此情況適用下列系統提供的繫結：</span><span class="sxs-lookup"><span data-stu-id="7ff86-149">This applies to the following system-provided bindings:</span></span>  
  
-   <xref:System.ServiceModel.BasicHttpBinding><span data-ttu-id="7ff86-150">。</span><span class="sxs-lookup"><span data-stu-id="7ff86-150">.</span></span>  
  
-   <xref:System.ServiceModel.WSHttpBinding> <span data-ttu-id="7ff86-151">具有<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A>屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="7ff86-151">with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ff86-152">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7ff86-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7ff86-153">要編譯程式碼時，必須有下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="7ff86-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="7ff86-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ff86-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="7ff86-155">安全對話與安全工作階段</span><span class="sxs-lookup"><span data-stu-id="7ff86-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="7ff86-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="7ff86-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="7ff86-157">HOW TO：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="7ff86-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
