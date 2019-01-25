---
title: 設定訊息記錄
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: f57385b930ce533de3ff12b0dbd363690f04082d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636010"
---
# <a name="configuring-message-logging"></a><span data-ttu-id="ede8a-102">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="ede8a-102">Configuring Message Logging</span></span>
<span data-ttu-id="ede8a-103">本主題描述如何針對不同的案例設定訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-103">This topic describes how you can configure message logging for different scenarios.</span></span>  
  
## <a name="enabling-message-logging"></a><span data-ttu-id="ede8a-104">啟用訊息記錄</span><span class="sxs-lookup"><span data-stu-id="ede8a-104">Enabling Message Logging</span></span>  
 <span data-ttu-id="ede8a-105">根據預設，Windows Communication Foundation (WCF) 不會記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-105">Windows Communication Foundation (WCF) does not log messages by default.</span></span> <span data-ttu-id="ede8a-106">若要啟動訊息記錄，您必須將追蹤接聽項加入至 `System.ServiceModel.MessageLogging` 追蹤來源，並在組態檔中設定 `<messagelogging>` 項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="ede8a-106">To activate message logging, you must add a trace listener to the `System.ServiceModel.MessageLogging` trace source and set attributes for the `<messagelogging>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="ede8a-107">下列範例示範如何啟用記錄並指定其他選項。</span><span class="sxs-lookup"><span data-stu-id="ede8a-107">The following example shows how to enable logging and specify additional options.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
         <add name="messages"  
              type="System.Diagnostics.XmlWriterTraceListener"  
              initializeData="c:\logs\messages.svclog" />  
        </listeners>  
    </source>  
  </sources>  
</system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics>  
    <messageLogging   
         logEntireMessage="true"   
         logMalformedMessages="false"  
         logMessagesAtServiceLevel="true"   
         logMessagesAtTransportLevel="false"  
         maxMessagesToLog="3000"  
         maxSizeOfMessageToLog="2000"/>  
  </diagnostics>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ede8a-108">如需詳細資訊訊息記錄設定的詳細資訊，請參閱 <<c0> [ 追蹤和訊息記錄的建議設定](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="ede8a-108">For more information about message logging settings, see [Recommended Settings for Tracing and Message Logging](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="ede8a-109">您可以使用 `add` 來指定所要使用之接聽項的名稱和型別。</span><span class="sxs-lookup"><span data-stu-id="ede8a-109">You can use `add` to specify the name and type of the listener you want to use.</span></span> <span data-ttu-id="ede8a-110">在範例組態中，我們已將接聽項命名為 "messages"，並且加入標準 .NET Framework 追蹤接聽項 (`System.Diagnostics.XmlWriterTraceListener`) 做為要使用的型別。</span><span class="sxs-lookup"><span data-stu-id="ede8a-110">In the example configuration, the Listener is named "messages" and adds the standard .NET Framework trace listener (`System.Diagnostics.XmlWriterTraceListener`) as the type to use.</span></span> <span data-ttu-id="ede8a-111">如果您要使用 `System.Diagnostics.XmlWriterTraceListener`，就必須在組態檔中指定輸出檔案位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="ede8a-111">If you use `System.Diagnostics.XmlWriterTraceListener`, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="ede8a-112">將 `initializeData` 設定為記錄檔的名稱，即可做到這點。</span><span class="sxs-lookup"><span data-stu-id="ede8a-112">This is done by setting `initializeData` to the name of the log file.</span></span> <span data-ttu-id="ede8a-113">否則，系統會擲回例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="ede8a-113">Otherwise, the system throws an exception.</span></span> <span data-ttu-id="ede8a-114">您也可以實作會將記錄發出到預設檔案的自訂接聽項。</span><span class="sxs-lookup"><span data-stu-id="ede8a-114">You can also implement a custom listener that emits logs to a default file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ede8a-115">由於訊息記錄會存取磁碟空間，因此您應該要限制為特定服務寫入磁碟的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="ede8a-115">Because message logging accesses disk space, you should limit the number of messages that are written to disk for a particular service.</span></span> <span data-ttu-id="ede8a-116">當抵達訊息限制時，便會在資訊層上產生追蹤，並停止所有的訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-116">When the message limit is reached, a trace at the Information level is produced and all message logging activities stop.</span></span>  
  
 <span data-ttu-id="ede8a-117">在記錄層級和選項 (本頁面可能為英文) 一節中，對於記錄層級以及其他選項都有加以討論。</span><span class="sxs-lookup"><span data-stu-id="ede8a-117">The logging level, as well as the additional options, are discussed in the Logging Level and Options section.</span></span>  
  
 <span data-ttu-id="ede8a-118">`switchValue` 的 `source` 屬性只對追蹤有效。</span><span class="sxs-lookup"><span data-stu-id="ede8a-118">The `switchValue` attribute of a `source` is only valid for tracing.</span></span> <span data-ttu-id="ede8a-119">如果您依下面所示指定 `switchValue`的 `System.ServiceModel.MessageLogging` 屬性，該屬性並不會產生作用。</span><span class="sxs-lookup"><span data-stu-id="ede8a-119">If you specify a `switchValue` attribute for the `System.ServiceModel.MessageLogging` trace source as follows, it has no effect.</span></span>  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 <span data-ttu-id="ede8a-120">如果想要停用追蹤來源，您就應該改成使用 `logMessagesAtServiceLevel` 項目的 `logMalformedMessages`、`logMessagesAtTransportLevel` 及 `messageLogging` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ede8a-120">If you want to disable the trace source, you should use the `logMessagesAtServiceLevel`, `logMalformedMessages`, and `logMessagesAtTransportLevel` attributes of the `messageLogging` element instead.</span></span> <span data-ttu-id="ede8a-121">您應該將所有這些屬性都設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ede8a-121">You should set all these attributes to `false`.</span></span> <span data-ttu-id="ede8a-122">使用先前程式碼範例中的組態檔、透過組態編輯器 UI 介面，或是使用 WMI，都可以做到這點。</span><span class="sxs-lookup"><span data-stu-id="ede8a-122">This can be done by using the configuration file in the previous code example, through the Configuration Editor UI interface, or using WMI.</span></span> <span data-ttu-id="ede8a-123">如需有關組態編輯器工具的詳細資訊，請參閱[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="ede8a-123">For more information about the Configuration Editor tool, see [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="ede8a-124">如需有關 WMI 的詳細資訊，請參閱 <<c0> [ 使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ede8a-124">For more information about WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
## <a name="logging-levels-and-options"></a><span data-ttu-id="ede8a-125">記錄層級和選項</span><span class="sxs-lookup"><span data-stu-id="ede8a-125">Logging Levels and Options</span></span>  
 <span data-ttu-id="ede8a-126">對於傳入的訊息，系統會緊接在訊息形成之後、在訊息到達服務層級中的使用者程式碼之前，以及在偵測到格式錯誤的訊息時進行記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-126">For incoming messages, logging happens immediately after the message is formed, immediately before the message gets to user code in the service level, and when malformed messages are detected.</span></span>  
  
 <span data-ttu-id="ede8a-127">對於傳出的訊息，系統會緊接在訊息離開使用者程式碼之後，以及在訊息傳送到網路上之前進行記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-127">For outgoing messages, logging happens immediately after the message leaves user code and immediately before the message goes on the wire.</span></span>  
  
 <span data-ttu-id="ede8a-128">WCF 會記錄在兩個不同的層級、 服務和傳輸的訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-128">WCF logs messages at two different levels, service and transport.</span></span> <span data-ttu-id="ede8a-129">格式錯誤的訊息也會加以記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-129">Malformed messages are also logged.</span></span> <span data-ttu-id="ede8a-130">三個分類彼此獨立，而且可以透過組態來個別啟動。</span><span class="sxs-lookup"><span data-stu-id="ede8a-130">The three categories are independent from each other and can be activated separately in configuration.</span></span>  
  
 <span data-ttu-id="ede8a-131">您可以設定 `logMessagesAtServiceLevel` 項目的 `logMalformedMessages`、`logMessagesAtTransportLevel` 及 `messageLogging` 屬性以控制記錄層級。</span><span class="sxs-lookup"><span data-stu-id="ede8a-131">You can control the logging level by setting the `logMessagesAtServiceLevel`, `logMalformedMessages`, and `logMessagesAtTransportLevel` attributes of the `messageLogging` element.</span></span>  
  
### <a name="service-level"></a><span data-ttu-id="ede8a-132">服務層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-132">Service Level</span></span>  
 <span data-ttu-id="ede8a-133">記錄在這層的是即將進入 (進行接收時) 或離開 (進行傳送時) 使用者程式碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-133">Messages logged at this layer are about to enter (on receiving) or leave (on sending) user code.</span></span> <span data-ttu-id="ede8a-134">如果有定義篩選條件，就只會記錄符合篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-134">If filters have been defined, only messages that match the filters are logged.</span></span> <span data-ttu-id="ede8a-135">否則，便會記錄服務層級中的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-135">Otherwise, all messages at the service level are logged.</span></span> <span data-ttu-id="ede8a-136">基礎結構訊息 (異動、對等通道及安全性) 也會記錄在此層級，除了可信賴傳訊訊息以外。</span><span class="sxs-lookup"><span data-stu-id="ede8a-136">Infrastructure messages (transactions, peer channel, and security) are also logged at this level, except for Reliable Messaging messages.</span></span> <span data-ttu-id="ede8a-137">若是已進行資料流處理的訊息，則只記錄標頭。</span><span class="sxs-lookup"><span data-stu-id="ede8a-137">On streamed messages, only the headers are logged.</span></span> <span data-ttu-id="ede8a-138">此外，安全訊息會以解密形式記錄在此層級。</span><span class="sxs-lookup"><span data-stu-id="ede8a-138">In addition, secure messages are logged decrypted at this level.</span></span>  
  
### <a name="transport-level"></a><span data-ttu-id="ede8a-139">傳輸層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-139">Transport Level</span></span>  
 <span data-ttu-id="ede8a-140">記錄在這層的是要送到網路上傳輸或是在傳輸後而要進行編碼或解碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-140">Messages logged at this layer are ready to be encoded or decoded for or after transportation on the wire.</span></span> <span data-ttu-id="ede8a-141">如果有定義篩選條件，就只會記錄符合篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-141">If filters have been defined, only messages that match the filters are logged.</span></span> <span data-ttu-id="ede8a-142">否則，便會記錄傳輸層級中的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-142">Otherwise, all messages at the transport layer are logged.</span></span> <span data-ttu-id="ede8a-143">所有的基礎結構訊息都會記錄在這層，其中包括可信賴傳訊訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-143">All infrastructure messages are logged at this layer, including reliable messaging messages.</span></span> <span data-ttu-id="ede8a-144">若是已進行資料流處理的訊息，則只記錄標頭。</span><span class="sxs-lookup"><span data-stu-id="ede8a-144">On streamed messages, only the headers are logged.</span></span> <span data-ttu-id="ede8a-145">此外，安全訊息會以加密形式記錄在此層級，除了使用 HTTPS 一類的安全傳輸的情況以外。</span><span class="sxs-lookup"><span data-stu-id="ede8a-145">In addition, secure messages are logged as encrypted at this level, except if a secure transport such as HTTPS is used.</span></span>  
  
### <a name="malformed-level"></a><span data-ttu-id="ede8a-146">格式錯誤層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-146">Malformed Level</span></span>  
 <span data-ttu-id="ede8a-147">格式不正確的訊息是處理的各個階段將會拒絕 WCF 堆疊的訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-147">Malformed messages are messages that are rejected by the WCF stack at any stage of processing.</span></span> <span data-ttu-id="ede8a-148">格式錯誤訊息會依現狀加以記錄：也就是若有加密，便會以加密形式記錄，並包含不正確的 XML 和其他格式。</span><span class="sxs-lookup"><span data-stu-id="ede8a-148">Malformed messages are logged as-is: encrypted if they are so, with non-proper XML, and so on.</span></span> <span data-ttu-id="ede8a-149">`maxSizeOfMessageToLog` 定義了要以 CDATA 形式記錄之訊息的大小。</span><span class="sxs-lookup"><span data-stu-id="ede8a-149">`maxSizeOfMessageToLog` defined the size of the message to be logged as CDATA.</span></span> <span data-ttu-id="ede8a-150">根據預設，`maxSizeOfMessageToLog` 會等於 256 K。</span><span class="sxs-lookup"><span data-stu-id="ede8a-150">By default, `maxSizeOfMessageToLog` is equal to 256K.</span></span> <span data-ttu-id="ede8a-151">如需有關這個屬性的詳細資訊，請參閱其他選項 > 一節。</span><span class="sxs-lookup"><span data-stu-id="ede8a-151">For more information about this attribute, see the Other Options section.</span></span>  
  
### <a name="other-options"></a><span data-ttu-id="ede8a-152">其他選項</span><span class="sxs-lookup"><span data-stu-id="ede8a-152">Other Options</span></span>  
 <span data-ttu-id="ede8a-153">除了記錄層級，使用者也可以指定下列選項：</span><span class="sxs-lookup"><span data-stu-id="ede8a-153">In addition to the logging levels, the user can specify the following options:</span></span>  
  
-   <span data-ttu-id="ede8a-154">記錄整個訊息 (`logEntireMessage`屬性):這個值會指定是否要記錄整個訊息 （訊息標頭和本文）。</span><span class="sxs-lookup"><span data-stu-id="ede8a-154">Log Entire Message (`logEntireMessage` attribute): This value specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="ede8a-155">預設值為 `false`，表示只記錄標頭。</span><span class="sxs-lookup"><span data-stu-id="ede8a-155">The default value is `false`, meaning that only the header is logged.</span></span> <span data-ttu-id="ede8a-156">這項設定會影響到服務和傳輸訊息記錄層級。</span><span class="sxs-lookup"><span data-stu-id="ede8a-156">This setting affects service and transport message logging levels..</span></span>  
  
-   <span data-ttu-id="ede8a-157">要記錄的最大訊息 (`maxMessagesToLog`屬性):這個值會指定要記錄訊息的數目上限。</span><span class="sxs-lookup"><span data-stu-id="ede8a-157">Max messages to log (`maxMessagesToLog` attribute): This value specifies the maximum number of messages to log.</span></span> <span data-ttu-id="ede8a-158">所有的訊息 (服務、傳輸及格式錯誤訊息) 都會計算到此配額內。</span><span class="sxs-lookup"><span data-stu-id="ede8a-158">All messages (service, transport, and malformed messages) are counted towards this quota.</span></span> <span data-ttu-id="ede8a-159">當抵達配額時，便會發出追蹤，而且不再記錄其他訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-159">When the quota is reached, a trace is emitted and no additional message is logged.</span></span> <span data-ttu-id="ede8a-160">預設值為 10000。</span><span class="sxs-lookup"><span data-stu-id="ede8a-160">The default value is 10000.</span></span>  
  
-   <span data-ttu-id="ede8a-161">要記錄訊息的大小上限 (`maxSizeOfMessageToLog`屬性):這個值會指定要記錄以位元組為單位的訊息大小上限。</span><span class="sxs-lookup"><span data-stu-id="ede8a-161">Max size of message to log (`maxSizeOfMessageToLog` attribute): This value specifies the maximum size of messages to log in bytes.</span></span> <span data-ttu-id="ede8a-162">不記錄超過大小限制的訊息，而且也不針對該訊息執行任何其他活動。</span><span class="sxs-lookup"><span data-stu-id="ede8a-162">Messages that exceed the size limit are not logged, and no other activity is performed for that message.</span></span> <span data-ttu-id="ede8a-163">這個設定會影響所有的追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="ede8a-163">This setting affects all trace levels.</span></span> <span data-ttu-id="ede8a-164">如果有開啟 ServiceModel 追蹤，便會在第一個記錄點 (ServiceModelSend\* 或 TransportReceive) 發出警告層級追蹤以通知使用者。</span><span class="sxs-lookup"><span data-stu-id="ede8a-164">If ServiceModel tracing is on, a Warning level trace is emitted at the first logging point (ServiceModelSend\* or TransportReceive) to notify the user.</span></span> <span data-ttu-id="ede8a-165">服務層級和傳輸層級等訊息的預設值是 256 K，而格式錯誤訊息的預設值是 4 K。</span><span class="sxs-lookup"><span data-stu-id="ede8a-165">The default value for service level and transport level messages is 256K, while the default value for malformed messages is 4K.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="ede8a-166">經過計算以便與 `maxSizeOfMessageToLog` 比較的訊息大小，就是進行序列化之前在記憶體中的訊息大小。</span><span class="sxs-lookup"><span data-stu-id="ede8a-166">The message size that is computed to compare against `maxSizeOfMessageToLog` is the message size in memory before serialization.</span></span> <span data-ttu-id="ede8a-167">這個大小可能不同於已記錄之訊息字串的實際長度，而且在許多情況下都會大於實際大小。</span><span class="sxs-lookup"><span data-stu-id="ede8a-167">This size can differ from the actual length of the message string that is being logged, and in many occasions is bigger than the actual size.</span></span> <span data-ttu-id="ede8a-168">如此一來，訊息可能就不會加以記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-168">As a result, messages may not be logged.</span></span> <span data-ttu-id="ede8a-169">您可以將 `maxSizeOfMessageToLog` 屬性指定為超過預期訊息大小的 10%，這樣就可以解決這個情形。</span><span class="sxs-lookup"><span data-stu-id="ede8a-169">You can account for this fact by specifying the `maxSizeOfMessageToLog` attribute to be 10% larger than the expected message size.</span></span> <span data-ttu-id="ede8a-170">此外，如果有記錄格式錯誤訊息，由訊息記錄應用的實際磁碟空間大小最多可為 `maxSizeOfMessageToLog` 所指定值的 5 倍。</span><span class="sxs-lookup"><span data-stu-id="ede8a-170">In addition, if malformed messages are logged, the actual disk space utilized by the message logs can be up to 5 times the size of the value specified by `maxSizeOfMessageToLog`.</span></span>  
  
 <span data-ttu-id="ede8a-171">如果組態檔中未定義追蹤接聽項，則無論指定的記錄層級為何，都不會產生記錄輸出。</span><span class="sxs-lookup"><span data-stu-id="ede8a-171">If no trace listener is defined in the configuration file, no logging output is generated regardless of the specified logging level.</span></span>  
  
 <span data-ttu-id="ede8a-172">包含本節所描述屬性的訊息記錄選項，可以在執行階段使用 Windows Management Instrumentation (WMI) 來加以變更。</span><span class="sxs-lookup"><span data-stu-id="ede8a-172">Message logging options, such as the attributes described in this section, can be changed at runtime using Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="ede8a-173">這可以藉由存取[AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)執行個體，它會公開下列布林值屬性： `LogMessagesAtServiceLevel`， `LogMessagesAtTransportLevel`，和`LogMalformedMessages`。</span><span class="sxs-lookup"><span data-stu-id="ede8a-173">This can be done by accessing the [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, and `LogMalformedMessages`.</span></span> <span data-ttu-id="ede8a-174">因此，如果您為訊息記錄設定一個追蹤接聽項，但在組態中將這些選項設定為 `false`，那麼您可以在稍後應用程式執行時，將選項變更為 `true`。</span><span class="sxs-lookup"><span data-stu-id="ede8a-174">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="ede8a-175">這會在執行階段有效地啟用訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-175">This effectively enables message logging at runtime.</span></span> <span data-ttu-id="ede8a-176">同樣地，如果您在組態檔中啟用訊息記錄，則您可以在執行階段使用 WMI 來停用訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="ede8a-176">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span> <span data-ttu-id="ede8a-177">如需詳細資訊，請參閱 <<c0> [ 使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ede8a-177">For more information, see [Using Windows Management Instrumentation for Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
 <span data-ttu-id="ede8a-178">訊息記錄中的 `source` 欄位會指定要用哪種內容來記錄訊息：何時傳送/接收要求訊息、針對要求-回覆或單向要求、在服務模型或傳輸層，或是在發生格式錯誤訊息的情況下。</span><span class="sxs-lookup"><span data-stu-id="ede8a-178">The `source` field in a message log specifies in which context the message is logged: when sending/receiving a request message, for a request-reply or 1-way request, at service model or transport layer, or in the case of a malformed message.</span></span>  
  
 <span data-ttu-id="ede8a-179">對於格式錯誤的訊息`source`等於`Malformed`。</span><span class="sxs-lookup"><span data-stu-id="ede8a-179">For malformed messages, `source`  is equal to `Malformed`.</span></span> <span data-ttu-id="ede8a-180">否則，便依據內容將來源指定為下列值。</span><span class="sxs-lookup"><span data-stu-id="ede8a-180">Otherwise, source has the following values based on the context.</span></span>  
  
 <span data-ttu-id="ede8a-181">針對要求/回覆</span><span class="sxs-lookup"><span data-stu-id="ede8a-181">For Request/Reply</span></span>  
  
||<span data-ttu-id="ede8a-182">傳送要求</span><span class="sxs-lookup"><span data-stu-id="ede8a-182">Send Request</span></span>|<span data-ttu-id="ede8a-183">接收要求</span><span class="sxs-lookup"><span data-stu-id="ede8a-183">Receive Request</span></span>|<span data-ttu-id="ede8a-184">傳送回覆</span><span class="sxs-lookup"><span data-stu-id="ede8a-184">Send Reply</span></span>|<span data-ttu-id="ede8a-185">接收回覆</span><span class="sxs-lookup"><span data-stu-id="ede8a-185">Receive Reply</span></span>|  
|-|------------------|---------------------|----------------|-------------------|  
|<span data-ttu-id="ede8a-186">服務模型層</span><span class="sxs-lookup"><span data-stu-id="ede8a-186">Service Model layer</span></span>|<span data-ttu-id="ede8a-187">服務</span><span class="sxs-lookup"><span data-stu-id="ede8a-187">Service</span></span><br /><br /> <span data-ttu-id="ede8a-188">層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-188">Level</span></span><br /><br /> <span data-ttu-id="ede8a-189">傳送</span><span class="sxs-lookup"><span data-stu-id="ede8a-189">Send</span></span><br /><br /> <span data-ttu-id="ede8a-190">要求</span><span class="sxs-lookup"><span data-stu-id="ede8a-190">Request</span></span>|<span data-ttu-id="ede8a-191">服務</span><span class="sxs-lookup"><span data-stu-id="ede8a-191">Service</span></span><br /><br /> <span data-ttu-id="ede8a-192">層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-192">Level</span></span><br /><br /> <span data-ttu-id="ede8a-193">接收</span><span class="sxs-lookup"><span data-stu-id="ede8a-193">Receive</span></span><br /><br /> <span data-ttu-id="ede8a-194">要求</span><span class="sxs-lookup"><span data-stu-id="ede8a-194">Request</span></span>|<span data-ttu-id="ede8a-195">服務</span><span class="sxs-lookup"><span data-stu-id="ede8a-195">Service</span></span><br /><br /> <span data-ttu-id="ede8a-196">層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-196">Level</span></span><br /><br /> <span data-ttu-id="ede8a-197">傳送</span><span class="sxs-lookup"><span data-stu-id="ede8a-197">Send</span></span><br /><br /> <span data-ttu-id="ede8a-198">回覆</span><span class="sxs-lookup"><span data-stu-id="ede8a-198">Reply</span></span>|<span data-ttu-id="ede8a-199">服務</span><span class="sxs-lookup"><span data-stu-id="ede8a-199">Service</span></span><br /><br /> <span data-ttu-id="ede8a-200">層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-200">Level</span></span><br /><br /> <span data-ttu-id="ede8a-201">接收</span><span class="sxs-lookup"><span data-stu-id="ede8a-201">Receive</span></span><br /><br /> <span data-ttu-id="ede8a-202">回覆</span><span class="sxs-lookup"><span data-stu-id="ede8a-202">Reply</span></span>|  
|<span data-ttu-id="ede8a-203">傳輸層</span><span class="sxs-lookup"><span data-stu-id="ede8a-203">Transport layer</span></span>|<span data-ttu-id="ede8a-204">Transport</span><span class="sxs-lookup"><span data-stu-id="ede8a-204">Transport</span></span><br /><br /> <span data-ttu-id="ede8a-205">傳送</span><span class="sxs-lookup"><span data-stu-id="ede8a-205">Send</span></span>|<span data-ttu-id="ede8a-206">Transport</span><span class="sxs-lookup"><span data-stu-id="ede8a-206">Transport</span></span><br /><br /> <span data-ttu-id="ede8a-207">接收</span><span class="sxs-lookup"><span data-stu-id="ede8a-207">Receive</span></span>|<span data-ttu-id="ede8a-208">Transport</span><span class="sxs-lookup"><span data-stu-id="ede8a-208">Transport</span></span><br /><br /> <span data-ttu-id="ede8a-209">傳送</span><span class="sxs-lookup"><span data-stu-id="ede8a-209">Send</span></span>|<span data-ttu-id="ede8a-210">Transport</span><span class="sxs-lookup"><span data-stu-id="ede8a-210">Transport</span></span><br /><br /> <span data-ttu-id="ede8a-211">接收</span><span class="sxs-lookup"><span data-stu-id="ede8a-211">Receive</span></span>|  
  
 <span data-ttu-id="ede8a-212">針對單向要求</span><span class="sxs-lookup"><span data-stu-id="ede8a-212">For One-way Request</span></span>  
  
||<span data-ttu-id="ede8a-213">傳送要求</span><span class="sxs-lookup"><span data-stu-id="ede8a-213">Send Request</span></span>|<span data-ttu-id="ede8a-214">接收要求</span><span class="sxs-lookup"><span data-stu-id="ede8a-214">Receive Request</span></span>|  
|-|------------------|---------------------|  
|<span data-ttu-id="ede8a-215">服務模型層</span><span class="sxs-lookup"><span data-stu-id="ede8a-215">Service Model layer</span></span>|<span data-ttu-id="ede8a-216">服務</span><span class="sxs-lookup"><span data-stu-id="ede8a-216">Service</span></span><br /><br /> <span data-ttu-id="ede8a-217">層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-217">Level</span></span><br /><br /> <span data-ttu-id="ede8a-218">傳送</span><span class="sxs-lookup"><span data-stu-id="ede8a-218">Send</span></span><br /><br /> <span data-ttu-id="ede8a-219">資料包</span><span class="sxs-lookup"><span data-stu-id="ede8a-219">Datagram</span></span>|<span data-ttu-id="ede8a-220">服務</span><span class="sxs-lookup"><span data-stu-id="ede8a-220">Service</span></span><br /><br /> <span data-ttu-id="ede8a-221">層級</span><span class="sxs-lookup"><span data-stu-id="ede8a-221">Level</span></span><br /><br /> <span data-ttu-id="ede8a-222">接收</span><span class="sxs-lookup"><span data-stu-id="ede8a-222">Receive</span></span><br /><br /> <span data-ttu-id="ede8a-223">資料包</span><span class="sxs-lookup"><span data-stu-id="ede8a-223">Datagram</span></span>|  
|<span data-ttu-id="ede8a-224">傳輸層</span><span class="sxs-lookup"><span data-stu-id="ede8a-224">Transport layer</span></span>|<span data-ttu-id="ede8a-225">Transport</span><span class="sxs-lookup"><span data-stu-id="ede8a-225">Transport</span></span><br /><br /> <span data-ttu-id="ede8a-226">傳送</span><span class="sxs-lookup"><span data-stu-id="ede8a-226">Send</span></span>|<span data-ttu-id="ede8a-227">Transport</span><span class="sxs-lookup"><span data-stu-id="ede8a-227">Transport</span></span><br /><br /> <span data-ttu-id="ede8a-228">接收</span><span class="sxs-lookup"><span data-stu-id="ede8a-228">Receive</span></span>|  
  
## <a name="message-filters"></a><span data-ttu-id="ede8a-229">訊息篩選條件</span><span class="sxs-lookup"><span data-stu-id="ede8a-229">Message Filters</span></span>  
 <span data-ttu-id="ede8a-230">訊息篩選條件會定義於 `messageLogging` 組態區段的 `diagnostics` 組態項目中。</span><span class="sxs-lookup"><span data-stu-id="ede8a-230">Message filters are defined in the `messageLogging` configuration element of the `diagnostics` configuration section.</span></span> <span data-ttu-id="ede8a-231">訊息篩選條件會套用在服務和傳輸層級上。</span><span class="sxs-lookup"><span data-stu-id="ede8a-231">They are applied at the service and transport level.</span></span> <span data-ttu-id="ede8a-232">當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="ede8a-232">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="ede8a-233">如果沒有定義篩選條件，所有訊息都會通過。</span><span class="sxs-lookup"><span data-stu-id="ede8a-233">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="ede8a-234">篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。</span><span class="sxs-lookup"><span data-stu-id="ede8a-234">Filters support the full XPath syntax and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="ede8a-235">語法不正確的篩選條件會造成組態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ede8a-235">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="ede8a-236">篩選條件也提供使用 `nodeQuota` 屬性的安全性功能，該屬性會限制 XPath DOM 中的節點數目上限，而這些節點可加以檢查來比對篩選條件。</span><span class="sxs-lookup"><span data-stu-id="ede8a-236">Filters also provide a safety feature using the `nodeQuota` attribute, which limits the maximum number of nodes in the XPath DOM that can be examined to match the filter.</span></span>  
  
 <span data-ttu-id="ede8a-237">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="ede8a-237">The following example shows how to configure a filter that records only messages that have a SOAP header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"  
    logMalformedMessages="true"   
    logMessagesAtServiceLevel="true"  
    logMessagesAtTransportLevel="true"  
    maxMessagesToLog="420">  
    <filters>  
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                 /soap:Envelope/soap:Header  
        </add>  
     </filters>  
</messageLogging>  
```  
  
 <span data-ttu-id="ede8a-238">篩選條件無法套用至訊息的本文。</span><span class="sxs-lookup"><span data-stu-id="ede8a-238">Filters cannot be applied to the body of a message.</span></span> <span data-ttu-id="ede8a-239">系統會從篩選條件的清單中移除嘗試操作訊息本文的篩選條件，</span><span class="sxs-lookup"><span data-stu-id="ede8a-239">Filters that attempt to manipulate the body of a message are removed from the list of filters.</span></span> <span data-ttu-id="ede8a-240">而且也會發出事件以表明此點。</span><span class="sxs-lookup"><span data-stu-id="ede8a-240">An event is also emitted that indicates this.</span></span> <span data-ttu-id="ede8a-241">例如，系統會從篩選資料表中移除下列篩選條件。</span><span class="sxs-lookup"><span data-stu-id="ede8a-241">For example, the following filter would be removed from the filter table.</span></span>  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a><span data-ttu-id="ede8a-242">設定自訂接聽項</span><span class="sxs-lookup"><span data-stu-id="ede8a-242">Configuring a Custom Listener</span></span>  
 <span data-ttu-id="ede8a-243">您也可以運用其他選項來設定自訂接聽項。</span><span class="sxs-lookup"><span data-stu-id="ede8a-243">You can also configure a custom listener with additional options.</span></span> <span data-ttu-id="ede8a-244">要在記錄之前從訊息中篩選應用程式特定的 PII 項目時，便可以使用自訂接聽項。</span><span class="sxs-lookup"><span data-stu-id="ede8a-244">A custom listener can be useful in filtering application-specific PII elements from messages before logging.</span></span> <span data-ttu-id="ede8a-245">下列範例示範了自訂接聽項組態。</span><span class="sxs-lookup"><span data-stu-id="ede8a-245">The following example demonstrates a custom listener configuration.</span></span>  
  
```xml  
<system.diagnostics>  
   <sources>  
     <source name="System.ServiceModel.MessageLogging">  
           <listeners>  
             <add name="MyListener"   
                    type="YourCustomListener"  
                    initializeData="c:\logs\messages.svclog"  
                    maxDiskSpace="1000"/>  
           </listeners>  
     </source>  
   </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="ede8a-246">請注意，`type` 屬性應該設定為此型別的限定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="ede8a-246">You should be aware that the `type` attribute should be set to a qualified assembly name of the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede8a-247">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ede8a-247">See also</span></span>
- [<span data-ttu-id="ede8a-248">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="ede8a-248">\<messageLogging></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
- [<span data-ttu-id="ede8a-249">訊息記錄</span><span class="sxs-lookup"><span data-stu-id="ede8a-249">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [<span data-ttu-id="ede8a-250">追蹤與訊息記錄的建議設定</span><span class="sxs-lookup"><span data-stu-id="ede8a-250">Recommended Settings for Tracing and Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
