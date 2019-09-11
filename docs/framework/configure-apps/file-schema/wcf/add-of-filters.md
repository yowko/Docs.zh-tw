---
title: <add> 的 <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850559"
---
# <a name="add-of-filters"></a><span data-ttu-id="d80e4-102">\<新增篩選的\<> ></span><span class="sxs-lookup"><span data-stu-id="d80e4-102">\<add> of \<filters></span></span>
<span data-ttu-id="d80e4-103">XPath 篩選條件，指定要記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d80e4-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
<span data-ttu-id="d80e4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d80e4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d80e4-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d80e4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d80e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<診斷 >** ](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="d80e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="d80e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<messageLogging >** ](messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="d80e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)</span></span>\
<span data-ttu-id="d80e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<篩選 >** ](filters.md)</span><span class="sxs-lookup"><span data-stu-id="d80e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)</span></span>\
<span data-ttu-id="d80e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="d80e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80e4-110">語法</span><span class="sxs-lookup"><span data-stu-id="d80e4-110">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d80e4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d80e4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d80e4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d80e4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d80e4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d80e4-113">Attributes</span></span>  
  
|<span data-ttu-id="d80e4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d80e4-114">Attribute</span></span>|<span data-ttu-id="d80e4-115">描述</span><span class="sxs-lookup"><span data-stu-id="d80e4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d80e4-116">篩選</span><span class="sxs-lookup"><span data-stu-id="d80e4-116">filter</span></span>|<span data-ttu-id="d80e4-117">字串，指定查詢由 XPath 1.0 運算式定義的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="d80e4-117">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="d80e4-118">如需詳細資訊，請參閱 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。</span><span class="sxs-lookup"><span data-stu-id="d80e4-118">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d80e4-119">子元素</span><span class="sxs-lookup"><span data-stu-id="d80e4-119">Child Elements</span></span>  
 <span data-ttu-id="d80e4-120">無。</span><span class="sxs-lookup"><span data-stu-id="d80e4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d80e4-121">父項目</span><span class="sxs-lookup"><span data-stu-id="d80e4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d80e4-122">項目</span><span class="sxs-lookup"><span data-stu-id="d80e4-122">Element</span></span>|<span data-ttu-id="d80e4-123">說明</span><span class="sxs-lookup"><span data-stu-id="d80e4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d80e4-124">\<filters></span><span class="sxs-lookup"><span data-stu-id="d80e4-124">\<filters></span></span>](filters.md)|<span data-ttu-id="d80e4-125">包含 XPath 篩選條件的集合，這些篩選條件可用於控制藥記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d80e4-125">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d80e4-126">備註</span><span class="sxs-lookup"><span data-stu-id="d80e4-126">Remarks</span></span>  
 <span data-ttu-id="d80e4-127">篩選條件只會於套用傳輸層，指定方式是將 `logMessagesAtTransportLevel` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d80e4-127">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="d80e4-128">服務等級和格式錯誤訊息記錄不受篩選條件的影響。</span><span class="sxs-lookup"><span data-stu-id="d80e4-128">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="d80e4-129">若要將篩選條件加入至集合，請使用 `add` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d80e4-129">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="d80e4-130">當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="d80e4-130">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="d80e4-131">如果沒有定義篩選條件，所有訊息都會通過。</span><span class="sxs-lookup"><span data-stu-id="d80e4-131">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="d80e4-132">篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。</span><span class="sxs-lookup"><span data-stu-id="d80e4-132">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="d80e4-133">語法不正確的篩選條件會造成組態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d80e4-133">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="d80e4-134">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="d80e4-134">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d80e4-135">範例</span><span class="sxs-lookup"><span data-stu-id="d80e4-135">Example</span></span>  
 <span data-ttu-id="d80e4-136">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="d80e4-136">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d80e4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d80e4-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="d80e4-138">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="d80e4-138">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="d80e4-139">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="d80e4-139">\<messageLogging></span></span>](messagelogging.md)
