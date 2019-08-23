---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 548c4884ecd2f4b9a71fcc9d6647a9e258b183c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934240"
---
# <a name="reliablesession"></a><span data-ttu-id="8a9b6-101">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="8a9b6-101">\<reliableSession></span></span>
<span data-ttu-id="8a9b6-102">定義 WS-Reliable 訊息設定。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-102">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="8a9b6-103">將這個項目新增至自訂繫結時，產生的通道可支援確實傳送一次保證。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-103">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="8a9b6-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8a9b6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8a9b6-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8a9b6-105">\<bindings></span></span>  
<span data-ttu-id="8a9b6-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8a9b6-106">\<customBinding></span></span>  
<span data-ttu-id="8a9b6-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="8a9b6-107">\<binding></span></span>  
<span data-ttu-id="8a9b6-108">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="8a9b6-108">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a9b6-109">語法</span><span class="sxs-lookup"><span data-stu-id="8a9b6-109">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a9b6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8a9b6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8a9b6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a9b6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8a9b6-112">Attributes</span></span>  
  
|<span data-ttu-id="8a9b6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8a9b6-113">Attribute</span></span>|<span data-ttu-id="8a9b6-114">描述</span><span class="sxs-lookup"><span data-stu-id="8a9b6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a9b6-115">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="8a9b6-115">acknowledgementInterval</span></span>|<span data-ttu-id="8a9b6-116"><xref:System.TimeSpan>，其中包含通道要等待的最大時間間隔；經過這個間隔以後，通道會針對直到該時間點前收到的訊息傳送認可。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-116">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="8a9b6-117">預設值為 00:00:0.2。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-117">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="8a9b6-118">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="8a9b6-118">flowControlEnabled</span></span>|<span data-ttu-id="8a9b6-119">布林值，指出是否已啟動進階流程控制 (適用於 WS-Reliable 訊息之流程控制的 Microsoft 特定實作)。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-119">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="8a9b6-120">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-120">The default is `true`.</span></span>|  
|<span data-ttu-id="8a9b6-121">inactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="8a9b6-121">inactivityTimeout</span></span>|<span data-ttu-id="8a9b6-122"><xref:System.TimeSpan>，指定將通道判定為失敗之前可允許另一個通訊方不傳送任何訊息的最長期間。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-122">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="8a9b6-123">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-123">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="8a9b6-124">通道上的活動是定義為接收應用程式或基礎結構訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-124">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="8a9b6-125">這個屬性會控制讓非作用中工作階段保持運作的最大時間量。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-125">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="8a9b6-126">如果經過更長的一段時間且無任何活動，工作階段會由基礎結構和通道錯誤中止。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-126">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="8a9b6-127">**注意：** 應用程式不需要定期傳送訊息來維持連線狀態。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-127">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="8a9b6-128">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="8a9b6-128">maxPendingChannels</span></span>|<span data-ttu-id="8a9b6-129">整數，指定可以在接聽程式上等待接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-129">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="8a9b6-130">這個值應介於 1 到 16384 之間 (含 1 和 16384)。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-130">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="8a9b6-131">預設值為 4。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-131">The default is 4.</span></span><br /><br /> <span data-ttu-id="8a9b6-132">通道在等待接受時會暫止。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-132">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="8a9b6-133">一旦到達該限制，便不會建立通道。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-133">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="8a9b6-134">通道反而會處於暫止模式，直到這個數字藉由接受暫止通道下降為止。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-134">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="8a9b6-135">這是一項原廠限制。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-135">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="8a9b6-136">如果到達臨界值，而且遠端應用程式嘗試建立新的可靠工作階段，則要求會被拒絕，提示這個要求的開啟作業也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-136">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="8a9b6-137">這項限制不適用於暫止傳出通道的數目。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-137">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="8a9b6-138">maxRetryCount</span><span class="sxs-lookup"><span data-stu-id="8a9b6-138">maxRetryCount</span></span>|<span data-ttu-id="8a9b6-139">整數，藉由針對可靠通道的基礎通道呼叫 Send，指定可靠通道嘗試重新傳輸其未收到認可之訊息的次數上限。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-139">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="8a9b6-140">這個值應大於零。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-140">This value should be greater than zero.</span></span> <span data-ttu-id="8a9b6-141">預設值為 8。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-141">The default is 8.</span></span><br /><br /> <span data-ttu-id="8a9b6-142">這個值應為大於零的整數。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-142">This value should be an integer greater than zero.</span></span> <span data-ttu-id="8a9b6-143">如果在最後一次重新傳輸後仍未收到認可，則通道會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-143">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="8a9b6-144">如果收件者已認可該處的訊息傳遞，則訊息會視為要傳輸的訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-144">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="8a9b6-145">如果在特定一段時間內沒有收到已傳輸之訊息的認可，則基礎結構會自動重新傳輸該訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-145">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="8a9b6-146">基礎結構會嘗試重新傳送該訊息達這個屬性所指定的最多次數。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-146">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="8a9b6-147">如果在最後一次重新傳輸後仍未收到認可，則通道會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-147">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="8a9b6-148">基礎結構會使用指數倒退演算法，根據計算出來的平均來回時間決定何時重新傳輸。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-148">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="8a9b6-149">經過之後就重新傳輸訊息的時間起初從 1 秒開始，延遲時間也會隨著每次嘗試重新傳輸而加倍，因此第一次重新傳輸嘗試到最後一次重新傳輸嘗試之間會經過約 8.5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-149">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="8a9b6-150">第一次嘗試重新傳輸的時間會根據計算出來的來回時間調整，這些嘗試所花費的時間也會因此而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-150">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="8a9b6-151">如此便可讓重新傳輸時間透過動態的方式適應多變的網路狀況。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-151">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="8a9b6-152">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="8a9b6-152">maxTransferWindowSize</span></span>|<span data-ttu-id="8a9b6-153">指定緩衝區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-153">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="8a9b6-154">有效值為 1 到 4096 (含 1 和 4096)。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-154">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="8a9b6-155">在用戶端上，這個屬性會定義可靠通道用來保留收件者尚未認可之訊息的緩衝區大小上限。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-155">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="8a9b6-156">配額是以訊息做為單位計算。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-156">The unit of the quota is a message.</span></span> <span data-ttu-id="8a9b6-157">如果緩衝區已滿，則會封鎖其他 SEND 作業。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-157">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="8a9b6-158">在接收者上，這個屬性會定義通道用來存放尚未分派到應用程式之傳入訊息的最大緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-158">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="8a9b6-159">如果緩衝區已滿，接收者會在沒有通知的情況下捨棄其他訊息，而且需要用戶端重新傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-159">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="8a9b6-160">排序</span><span class="sxs-lookup"><span data-stu-id="8a9b6-160">ordered</span></span>|<span data-ttu-id="8a9b6-161">布林值，指定是否保證訊息以傳送時的順序到達。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-161">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="8a9b6-162">如果這個設定為 `false`，則訊息可以不按照順序到達。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-162">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="8a9b6-163">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-163">The default is `true`.</span></span>|  
|<span data-ttu-id="8a9b6-164">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="8a9b6-164">reliableMessagingVersion</span></span>|<span data-ttu-id="8a9b6-165"><xref:System.ServiceModel.ReliableMessagingVersion> 中的有效值，指定要使用的 WS-ReliableMessaging 版本。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-165">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a9b6-166">子元素</span><span class="sxs-lookup"><span data-stu-id="8a9b6-166">Child Elements</span></span>  
 <span data-ttu-id="8a9b6-167">無</span><span class="sxs-lookup"><span data-stu-id="8a9b6-167">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a9b6-168">父項目</span><span class="sxs-lookup"><span data-stu-id="8a9b6-168">Parent Elements</span></span>  
  
|<span data-ttu-id="8a9b6-169">項目</span><span class="sxs-lookup"><span data-stu-id="8a9b6-169">Element</span></span>|<span data-ttu-id="8a9b6-170">說明</span><span class="sxs-lookup"><span data-stu-id="8a9b6-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a9b6-171">\<binding></span><span class="sxs-lookup"><span data-stu-id="8a9b6-171">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="8a9b6-172">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-172">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a9b6-173">備註</span><span class="sxs-lookup"><span data-stu-id="8a9b6-173">Remarks</span></span>  
 <span data-ttu-id="8a9b6-174">可靠的工作階段會提供可靠傳訊和工作階段功能。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-174">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="8a9b6-175">可靠的傳訊失敗時會重試通訊，而且允許指定傳遞保證，例如訊息依序到達。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-175">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="8a9b6-176">工作階段會保持呼叫之間的用戶端狀態。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-176">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="8a9b6-177">這個項目還會選擇性地提供排序式的訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-177">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="8a9b6-178">這個實作的工作階段可以跨 SOAP 和傳輸媒介。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-178">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="8a9b6-179">每個繫結項目都代表傳送或接收訊息時的一個處理步驟。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-179">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="8a9b6-180">繫結項目會在執行階段建立通道處理站和接聽程式，它們是在傳送和接收訊息時所需要之傳出和傳入通道堆疊的必要建置項目。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-180">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="8a9b6-181">`reliableSession` 在堆疊中提供選擇性的層級，而透過該層級可以在端點之間建立可靠工作階段，並設定這個工作階段的行為。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-181">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="8a9b6-182">如需詳細資訊, 請參閱[可靠會話](../../../wcf/feature-details/reliable-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-182">For more information, see [Reliable Sessions](../../../wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a9b6-183">範例</span><span class="sxs-lookup"><span data-stu-id="8a9b6-183">Example</span></span>  
 <span data-ttu-id="8a9b6-184">以下範例將示範如何使用各種傳輸和訊息編碼項目來設定自訂繫結，尤其是啟用可靠的工作階段，因為這麼做可保持用戶端狀態並指定依序傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-184">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="8a9b6-185">這個功能是在用戶端和服務的應用程式組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-185">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="8a9b6-186">該範例會顯示服務組態。</span><span class="sxs-lookup"><span data-stu-id="8a9b6-186">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="8a9b6-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a9b6-187">See also</span></span>

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="8a9b6-188">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="8a9b6-188">Reliable Sessions</span></span>](../../../wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="8a9b6-189">繫結</span><span class="sxs-lookup"><span data-stu-id="8a9b6-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8a9b6-190">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="8a9b6-190">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8a9b6-191">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="8a9b6-191">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8a9b6-192">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8a9b6-192">\<customBinding></span></span>](custombinding.md)
