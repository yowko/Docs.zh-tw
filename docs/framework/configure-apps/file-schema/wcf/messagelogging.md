---
title: '&lt;messageLogging&gt;'
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: e137070b71cf8a481eef3ea16260c135e29b4932
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750683"
---
# <a name="ltmessagelogginggt"></a><span data-ttu-id="d1a23-102">&lt;messageLogging&gt;</span><span class="sxs-lookup"><span data-stu-id="d1a23-102">&lt;messageLogging&gt;</span></span>
<span data-ttu-id="d1a23-103">這個項目會定義 Windows Communication Foundation (WCF) 的訊息記錄功能設定。</span><span class="sxs-lookup"><span data-stu-id="d1a23-103">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="d1a23-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d1a23-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1a23-105">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="d1a23-105">\<diagnostic></span></span>  
<span data-ttu-id="d1a23-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="d1a23-106">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a23-107">語法</span><span class="sxs-lookup"><span data-stu-id="d1a23-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
                            <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1a23-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1a23-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1a23-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1a23-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1a23-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d1a23-110">Attributes</span></span>  
  
|<span data-ttu-id="d1a23-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d1a23-111">Attribute</span></span>|<span data-ttu-id="d1a23-112">描述</span><span class="sxs-lookup"><span data-stu-id="d1a23-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="d1a23-113">布林值，指定是否記錄整個訊息 (訊息標頭和本文)。</span><span class="sxs-lookup"><span data-stu-id="d1a23-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="d1a23-114">預設為 `false`，意指只會記錄訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="d1a23-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="d1a23-115">這個設定會影響所有的訊息記錄層級 (服務、傳輸和格式錯誤)。</span><span class="sxs-lookup"><span data-stu-id="d1a23-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="d1a23-116">布林值，指定是否記錄格式錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="d1a23-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="d1a23-117">格式錯誤的訊息不會計入 `maxMessagesToLog`。</span><span class="sxs-lookup"><span data-stu-id="d1a23-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="d1a23-118">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d1a23-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="d1a23-119">布林值，指定是否在服務層級追蹤訊息 (在加密和傳輸相關轉換之前)。</span><span class="sxs-lookup"><span data-stu-id="d1a23-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="d1a23-120">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d1a23-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="d1a23-121">布林值，指定是否在傳輸層級追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="d1a23-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="d1a23-122">在組態檔中指定的任何篩選條件都會套用，且只會追蹤符合篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="d1a23-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="d1a23-123">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d1a23-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="d1a23-124">正整數，指定要記錄的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="d1a23-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="d1a23-125">預設值為 1000。</span><span class="sxs-lookup"><span data-stu-id="d1a23-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="d1a23-126">正整數，指定要記錄之訊息的大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="d1a23-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="d1a23-127">大於限制的訊息將不會記錄。</span><span class="sxs-lookup"><span data-stu-id="d1a23-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="d1a23-128">這個設定會影響所有的追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="d1a23-128">This setting affects all trace levels.</span></span> <span data-ttu-id="d1a23-129">預設為 262144(0x4000)。</span><span class="sxs-lookup"><span data-stu-id="d1a23-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1a23-130">子項目</span><span class="sxs-lookup"><span data-stu-id="d1a23-130">Child Elements</span></span>  
  
|<span data-ttu-id="d1a23-131">項目</span><span class="sxs-lookup"><span data-stu-id="d1a23-131">Element</span></span>|<span data-ttu-id="d1a23-132">描述</span><span class="sxs-lookup"><span data-stu-id="d1a23-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1a23-133">篩選條件</span><span class="sxs-lookup"><span data-stu-id="d1a23-133">filters</span></span>|<span data-ttu-id="d1a23-134">`filters` 項目含有 XPath 篩選條件的集合。</span><span class="sxs-lookup"><span data-stu-id="d1a23-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="d1a23-135">當啟用傳輸訊息記錄時 (`logMessagesAtTransportLevel` 是 `true`)，將只記錄符合篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="d1a23-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="d1a23-136">篩選條件只會在傳輸層套用。</span><span class="sxs-lookup"><span data-stu-id="d1a23-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="d1a23-137">服務等級和格式錯誤訊息記錄不受篩選條件的影響。</span><span class="sxs-lookup"><span data-stu-id="d1a23-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="d1a23-138">`filter` 這個項目的唯一屬性為 XpathFilter。</span><span class="sxs-lookup"><span data-stu-id="d1a23-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1a23-139">父項目</span><span class="sxs-lookup"><span data-stu-id="d1a23-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d1a23-140">項目</span><span class="sxs-lookup"><span data-stu-id="d1a23-140">Element</span></span>|<span data-ttu-id="d1a23-141">描述</span><span class="sxs-lookup"><span data-stu-id="d1a23-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1a23-142">診斷</span><span class="sxs-lookup"><span data-stu-id="d1a23-142">diagnostics</span></span>|<span data-ttu-id="d1a23-143">為系統管理員定義執行階段檢查和控制的 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="d1a23-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1a23-144">備註</span><span class="sxs-lookup"><span data-stu-id="d1a23-144">Remarks</span></span>  
 <span data-ttu-id="d1a23-145">訊息會記錄在堆疊中的三個不同層級：服務、傳輸和格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="d1a23-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="d1a23-146">每個層級可個別啟動。</span><span class="sxs-lookup"><span data-stu-id="d1a23-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="d1a23-147">可以加入 XPath 篩選條件，以記錄傳輸和服務層級的特定訊息。</span><span class="sxs-lookup"><span data-stu-id="d1a23-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="d1a23-148">如果沒有定義篩選條件，便會記錄所有的訊息。</span><span class="sxs-lookup"><span data-stu-id="d1a23-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="d1a23-149">篩選條件只會套用於訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="d1a23-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="d1a23-150">本文會被忽略。</span><span class="sxs-lookup"><span data-stu-id="d1a23-150">The body is ignored.</span></span> <span data-ttu-id="d1a23-151">WCF 會忽略訊息本文，以增進效能。</span><span class="sxs-lookup"><span data-stu-id="d1a23-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="d1a23-152">如果您希望根據本文的內容進行篩選，可以使用執行這項工作的篩選條件來建立自訂接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d1a23-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="d1a23-153">您必須建立追蹤接聽程式，以啟動訊息追蹤。</span><span class="sxs-lookup"><span data-stu-id="d1a23-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="d1a23-154">接聽程式本身可以是與 <xref:System.Diagnostics> 追蹤架構搭配使用的任何接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d1a23-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="d1a23-155">下列範例示範如何建立這類接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d1a23-155">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
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
  
## <a name="example"></a><span data-ttu-id="d1a23-156">範例</span><span class="sxs-lookup"><span data-stu-id="d1a23-156">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1a23-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1a23-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [<span data-ttu-id="d1a23-158">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="d1a23-158">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
