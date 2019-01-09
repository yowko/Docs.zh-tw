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
# <a name="ltaddgt-of-ltfiltersgt"></a>&lt;filters&gt; 的 &lt;add&gt;
XPath 篩選條件，指定要記錄的訊息類型。  
  
 \<system.ServiceModel>  
\<診斷 >  
\<messageLogging >  
\<篩選條件 >  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|篩選|字串，指定查詢由 XPath 1.0 運算式定義的 XML 文件。 如需詳細資訊，請參閱<xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<篩選條件 >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|包含 XPath 篩選條件的集合，這些篩選條件可用於控制藥記錄的訊息類型。|  
  
## <a name="remarks"></a>備註  
 篩選條件只會於套用傳輸層，指定方式是將 `logMessagesAtTransportLevel` 設定為 `true`。 服務等級和格式錯誤訊息記錄不受篩選條件的影響。  
  
 若要將篩選條件加入至集合，請使用 `add` 關鍵字。 當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。 如果沒有定義篩選條件，所有訊息都會通過。  
  
 篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。 語法不正確的篩選條件會造成組態例外狀況。  
  
 下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [設定訊息記錄](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [設定訊息記錄](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
