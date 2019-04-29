---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768910"
---
# <a name="messagelogging"></a><span data-ttu-id="d020f-101">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="d020f-101">\<messageLogging></span></span>
<span data-ttu-id="d020f-102">這個項目會定義 Windows Communication Foundation (WCF) 的訊息記錄功能設定。</span><span class="sxs-lookup"><span data-stu-id="d020f-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="d020f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d020f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d020f-104">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="d020f-104">\<diagnostic></span></span>  
<span data-ttu-id="d020f-105">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="d020f-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d020f-106">語法</span><span class="sxs-lookup"><span data-stu-id="d020f-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d020f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d020f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d020f-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d020f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d020f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d020f-109">Attributes</span></span>  
  
|<span data-ttu-id="d020f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d020f-110">Attribute</span></span>|<span data-ttu-id="d020f-111">描述</span><span class="sxs-lookup"><span data-stu-id="d020f-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="d020f-112">布林值，指定是否記錄整個訊息 (訊息標頭和本文)。</span><span class="sxs-lookup"><span data-stu-id="d020f-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="d020f-113">預設為 `false`，意指只會記錄訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="d020f-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="d020f-114">這個設定會影響所有的訊息記錄層級 (服務、傳輸和格式錯誤)。</span><span class="sxs-lookup"><span data-stu-id="d020f-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="d020f-115">布林值，指定是否記錄格式錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="d020f-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="d020f-116">格式錯誤的訊息不會計入 `maxMessagesToLog`。</span><span class="sxs-lookup"><span data-stu-id="d020f-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="d020f-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d020f-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="d020f-118">布林值，指定是否在服務層級追蹤訊息 (在加密和傳輸相關轉換之前)。</span><span class="sxs-lookup"><span data-stu-id="d020f-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="d020f-119">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d020f-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="d020f-120">布林值，指定是否在傳輸層級追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="d020f-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="d020f-121">在組態檔中指定的任何篩選條件都會套用，且只會追蹤符合篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="d020f-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="d020f-122">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d020f-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="d020f-123">正整數，指定要記錄的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="d020f-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="d020f-124">預設值為 1000。</span><span class="sxs-lookup"><span data-stu-id="d020f-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="d020f-125">正整數，指定要記錄之訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="d020f-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="d020f-126">大於限制的訊息將不會記錄。</span><span class="sxs-lookup"><span data-stu-id="d020f-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="d020f-127">這個設定會影響所有的追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="d020f-127">This setting affects all trace levels.</span></span> <span data-ttu-id="d020f-128">預設為 262144(0x4000)。</span><span class="sxs-lookup"><span data-stu-id="d020f-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d020f-129">子元素</span><span class="sxs-lookup"><span data-stu-id="d020f-129">Child Elements</span></span>  
  
|<span data-ttu-id="d020f-130">項目</span><span class="sxs-lookup"><span data-stu-id="d020f-130">Element</span></span>|<span data-ttu-id="d020f-131">描述</span><span class="sxs-lookup"><span data-stu-id="d020f-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d020f-132">篩選條件</span><span class="sxs-lookup"><span data-stu-id="d020f-132">filters</span></span>|<span data-ttu-id="d020f-133">`filters` 項目含有 XPath 篩選條件的集合。</span><span class="sxs-lookup"><span data-stu-id="d020f-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="d020f-134">當啟用傳輸訊息記錄時 (`logMessagesAtTransportLevel` 是 `true`)，將只記錄符合篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="d020f-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="d020f-135">篩選條件只會在傳輸層套用。</span><span class="sxs-lookup"><span data-stu-id="d020f-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="d020f-136">服務等級和格式錯誤訊息記錄不受篩選條件的影響。</span><span class="sxs-lookup"><span data-stu-id="d020f-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="d020f-137">`filter` 這個項目的唯一屬性為 XpathFilter。</span><span class="sxs-lookup"><span data-stu-id="d020f-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="d020f-138">父項目</span><span class="sxs-lookup"><span data-stu-id="d020f-138">Parent Elements</span></span>  
  
|<span data-ttu-id="d020f-139">項目</span><span class="sxs-lookup"><span data-stu-id="d020f-139">Element</span></span>|<span data-ttu-id="d020f-140">描述</span><span class="sxs-lookup"><span data-stu-id="d020f-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d020f-141">診斷</span><span class="sxs-lookup"><span data-stu-id="d020f-141">diagnostics</span></span>|<span data-ttu-id="d020f-142">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="d020f-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d020f-143">備註</span><span class="sxs-lookup"><span data-stu-id="d020f-143">Remarks</span></span>  
 <span data-ttu-id="d020f-144">訊息會記錄在堆疊中的三個不同層級：服務、傳輸和格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="d020f-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="d020f-145">每個層級可個別啟動。</span><span class="sxs-lookup"><span data-stu-id="d020f-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="d020f-146">可以加入 XPath 篩選條件，以記錄傳輸和服務層級的特定訊息。</span><span class="sxs-lookup"><span data-stu-id="d020f-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="d020f-147">如果沒有定義篩選條件，便會記錄所有的訊息。</span><span class="sxs-lookup"><span data-stu-id="d020f-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="d020f-148">篩選條件只會套用於訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="d020f-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="d020f-149">本文會被忽略。</span><span class="sxs-lookup"><span data-stu-id="d020f-149">The body is ignored.</span></span> <span data-ttu-id="d020f-150">WCF 會忽略訊息本文，以增進效能。</span><span class="sxs-lookup"><span data-stu-id="d020f-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="d020f-151">如果您希望根據本文的內容進行篩選，可以使用執行這項工作的篩選條件來建立自訂接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d020f-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="d020f-152">您必須建立追蹤接聽程式，以啟動訊息追蹤。</span><span class="sxs-lookup"><span data-stu-id="d020f-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="d020f-153">接聽程式本身可以是與 <xref:System.Diagnostics> 追蹤架構搭配使用的任何接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d020f-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="d020f-154">下列範例示範如何建立這類接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d020f-154">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="d020f-155">範例</span><span class="sxs-lookup"><span data-stu-id="d020f-155">Example</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="d020f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d020f-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="d020f-157">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="d020f-157">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
