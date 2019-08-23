---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918879"
---
# <a name="filters"></a><span data-ttu-id="e9b9b-101">\<filters></span><span class="sxs-lookup"><span data-stu-id="e9b9b-101">\<filters></span></span>

<span data-ttu-id="e9b9b-102">`filters` 項目含有 XPath 篩選條件的集合，用於控制記錄何種訊息。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-102">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="e9b9b-103">篩選條件只會於套用傳輸層，指定方式是將 `logMessagesAtTransportLevel` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-103">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="e9b9b-104">服務等級和格式錯誤訊息記錄不受篩選條件的影響。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-104">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="e9b9b-105">若要將篩選條件加入至集合，請使用 `add` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-105">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="e9b9b-106">當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-106">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="e9b9b-107">如果沒有定義篩選條件，所有訊息都會通過。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-107">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="e9b9b-108">篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-108">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="e9b9b-109">語法不正確的篩選條件會造成組態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-109">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="e9b9b-110">下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="e9b9b-110">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9b9b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9b9b-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="e9b9b-112">設定訊息記錄</span><span class="sxs-lookup"><span data-stu-id="e9b9b-112">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="e9b9b-113">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="e9b9b-113">\<messageLogging></span></span>](messagelogging.md)
