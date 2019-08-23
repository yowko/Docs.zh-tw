---
title: <add> 的 <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926691"
---
# <a name="add-of-filters"></a><span data-ttu-id="2a103-102">\<新增篩選的\<> ></span><span class="sxs-lookup"><span data-stu-id="2a103-102">\<add> of \<filters></span></span>
<span data-ttu-id="2a103-103">XPath 篩選條件，指定要記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="2a103-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="2a103-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a103-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a103-105">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="2a103-105">\<diagnostic></span></span>  
<span data-ttu-id="2a103-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="2a103-106">\<messageLogging></span></span>  
<span data-ttu-id="2a103-107">\<filters></span><span class="sxs-lookup"><span data-stu-id="2a103-107">\<filters></span></span>  
<span data-ttu-id="2a103-108">\<add></span><span class="sxs-lookup"><span data-stu-id="2a103-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a103-109">語法</span><span class="sxs-lookup"><span data-stu-id="2a103-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a103-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a103-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a103-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2a103-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a103-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2a103-112">Attributes</span></span>  
  
|<span data-ttu-id="2a103-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2a103-113">Attribute</span></span>|<span data-ttu-id="2a103-114">描述</span><span class="sxs-lookup"><span data-stu-id="2a103-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a103-115">篩選</span><span class="sxs-lookup"><span data-stu-id="2a103-115">filter</span></span>|<span data-ttu-id="2a103-116">字串，指定查詢由 XPath 1.0 運算式定義的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="2a103-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="2a103-117">如需詳細資訊，請參閱 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。</span><span class="sxs-lookup"><span data-stu-id="2a103-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a103-118">子元素</span><span class="sxs-lookup"><span data-stu-id="2a103-118">Child Elements</span></span>  
 <span data-ttu-id="2a103-119">無。</span><span class="sxs-lookup"><span data-stu-id="2a103-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a103-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2a103-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2a103-121">項目</span><span class="sxs-lookup"><span data-stu-id="2a103-121">Element</span></span>|<span data-ttu-id="2a103-122">描述</span><span class="sxs-lookup"><span data-stu-id="2a103-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a103-123">\<filters></span><span class="sxs-lookup"><span data-stu-id="2a103-123">\<filters></span></span>](filters.md)|<span data-ttu-id="2a103-124">包含 XPath 篩選條件的集合，這些篩選條件可用於控制藥記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="2a103-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a103-125">備註</span><span class="sxs-lookup"><span data-stu-id="2a103-125">Remarks</span></span>  
 <span data-ttu-id="2a103-126">篩選條件只會於套用傳輸層，指定方式是將 `logMessagesAtTransportLevel` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="2a103-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="2a103-127">服務等級和格式錯誤訊息記錄不受篩選條件的影響。</span><span class="sxs-lookup"><span data-stu-id="2a103-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="2a103-128">若要將篩選條件加入至集合，請使用 `add` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2a103-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="2a103-129">當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="2a103-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="2a103-130">如果沒有定義篩選條件，所有訊息都會通過。</span><span class="sxs-lookup"><span data-stu-id="2a103-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="2a103-131">篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。</span><span class="sxs-lookup"><span data-stu-id="2a103-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="2a103-132">語法不正確的篩選條件會造成組態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2a103-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="2a103-133">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="2a103-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a103-134">範例</span><span class="sxs-lookup"><span data-stu-id="2a103-134">Example</span></span>  
 <span data-ttu-id="2a103-135">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="2a103-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a103-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a103-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="2a103-137">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="2a103-137">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="2a103-138">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="2a103-138">\<messageLogging></span></span>](messagelogging.md)
