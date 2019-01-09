---
title: '&lt;filters&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: fe9ce8bc2a0efb9e20800189cd9f948d5e6a2232
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150743"
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="3a7d2-102">&lt;filters&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="3a7d2-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="3a7d2-103">XPath 篩選條件，指定要記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="3a7d2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3a7d2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3a7d2-105">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="3a7d2-105">\<diagnostic></span></span>  
<span data-ttu-id="3a7d2-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="3a7d2-106">\<messageLogging></span></span>  
<span data-ttu-id="3a7d2-107">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="3a7d2-107">\<filters></span></span>  
<span data-ttu-id="3a7d2-108">\<add></span><span class="sxs-lookup"><span data-stu-id="3a7d2-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a7d2-109">語法</span><span class="sxs-lookup"><span data-stu-id="3a7d2-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a7d2-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a7d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3a7d2-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a7d2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3a7d2-112">Attributes</span></span>  
  
|<span data-ttu-id="3a7d2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3a7d2-113">Attribute</span></span>|<span data-ttu-id="3a7d2-114">描述</span><span class="sxs-lookup"><span data-stu-id="3a7d2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a7d2-115">篩選</span><span class="sxs-lookup"><span data-stu-id="3a7d2-115">filter</span></span>|<span data-ttu-id="3a7d2-116">字串，指定查詢由 XPath 1.0 運算式定義的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="3a7d2-117">如需詳細資訊，請參閱<xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a7d2-118">子元素</span><span class="sxs-lookup"><span data-stu-id="3a7d2-118">Child Elements</span></span>  
 <span data-ttu-id="3a7d2-119">無。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a7d2-120">父項目</span><span class="sxs-lookup"><span data-stu-id="3a7d2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3a7d2-121">項目</span><span class="sxs-lookup"><span data-stu-id="3a7d2-121">Element</span></span>|<span data-ttu-id="3a7d2-122">描述</span><span class="sxs-lookup"><span data-stu-id="3a7d2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a7d2-123">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="3a7d2-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="3a7d2-124">包含 XPath 篩選條件的集合，這些篩選條件可用於控制藥記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a7d2-125">備註</span><span class="sxs-lookup"><span data-stu-id="3a7d2-125">Remarks</span></span>  
 <span data-ttu-id="3a7d2-126">篩選條件只會於套用傳輸層，指定方式是將 `logMessagesAtTransportLevel` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="3a7d2-127">服務等級和格式錯誤訊息記錄不受篩選條件的影響。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="3a7d2-128">若要將篩選條件加入至集合，請使用 `add` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="3a7d2-129">當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="3a7d2-130">如果沒有定義篩選條件，所有訊息都會通過。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="3a7d2-131">篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="3a7d2-132">語法不正確的篩選條件會造成組態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="3a7d2-133">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a7d2-134">範例</span><span class="sxs-lookup"><span data-stu-id="3a7d2-134">Example</span></span>  
 <span data-ttu-id="3a7d2-135">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="3a7d2-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="3a7d2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a7d2-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="3a7d2-137">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="3a7d2-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="3a7d2-138">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="3a7d2-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="3a7d2-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="3a7d2-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
