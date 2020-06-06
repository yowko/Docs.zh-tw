---
title: <add> 的 <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850559"
---
# <a name="add-of-filters"></a><span data-ttu-id="74315-102">\<add> 的 \<filters></span><span class="sxs-lookup"><span data-stu-id="74315-102">\<add> of \<filters></span></span>
<span data-ttu-id="74315-103">XPath 篩選條件，指定要記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="74315-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="74315-104">語法</span><span class="sxs-lookup"><span data-stu-id="74315-104">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74315-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="74315-105">Attributes and Elements</span></span>  
 <span data-ttu-id="74315-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="74315-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74315-107">屬性</span><span class="sxs-lookup"><span data-stu-id="74315-107">Attributes</span></span>  
  
|<span data-ttu-id="74315-108">屬性</span><span class="sxs-lookup"><span data-stu-id="74315-108">Attribute</span></span>|<span data-ttu-id="74315-109">描述</span><span class="sxs-lookup"><span data-stu-id="74315-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74315-110">filter</span><span class="sxs-lookup"><span data-stu-id="74315-110">filter</span></span>|<span data-ttu-id="74315-111">字串，指定查詢由 XPath 1.0 運算式定義的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="74315-111">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="74315-112">如需詳細資訊，請參閱 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 。</span><span class="sxs-lookup"><span data-stu-id="74315-112">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74315-113">子元素</span><span class="sxs-lookup"><span data-stu-id="74315-113">Child Elements</span></span>  
 <span data-ttu-id="74315-114">無。</span><span class="sxs-lookup"><span data-stu-id="74315-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74315-115">父項目</span><span class="sxs-lookup"><span data-stu-id="74315-115">Parent Elements</span></span>  
  
|<span data-ttu-id="74315-116">元素</span><span class="sxs-lookup"><span data-stu-id="74315-116">Element</span></span>|<span data-ttu-id="74315-117">描述</span><span class="sxs-lookup"><span data-stu-id="74315-117">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="74315-118">包含 XPath 篩選條件的集合，這些篩選條件可用於控制藥記錄的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="74315-118">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74315-119">備註</span><span class="sxs-lookup"><span data-stu-id="74315-119">Remarks</span></span>  
 <span data-ttu-id="74315-120">篩選條件只會於套用傳輸層，指定方式是將 `logMessagesAtTransportLevel` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="74315-120">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="74315-121">服務等級和格式錯誤訊息記錄不受篩選條件的影響。</span><span class="sxs-lookup"><span data-stu-id="74315-121">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="74315-122">若要將篩選條件加入至集合，請使用 `add` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="74315-122">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="74315-123">當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="74315-123">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="74315-124">如果沒有定義篩選條件，所有訊息都會通過。</span><span class="sxs-lookup"><span data-stu-id="74315-124">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="74315-125">篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。</span><span class="sxs-lookup"><span data-stu-id="74315-125">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="74315-126">語法不正確的篩選條件會造成組態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74315-126">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="74315-127">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="74315-127">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74315-128">範例</span><span class="sxs-lookup"><span data-stu-id="74315-128">Example</span></span>  
 <span data-ttu-id="74315-129">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="74315-129">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74315-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74315-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="74315-131">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="74315-131">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
