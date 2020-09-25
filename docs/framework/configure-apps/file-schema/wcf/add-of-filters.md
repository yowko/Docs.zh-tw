---
title: <add> 的 <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: c1de0605bc8afc502a85d9b2917b975ee45a3d26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201651"
---
# <a name="add-of-filters"></a>\<add> 的 \<filters>

XPath 篩選條件，指定要記錄的訊息類型。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|filter|字串，指定查詢由 XPath 1.0 運算式定義的 XML 文件。 如需詳細資訊，請參閱<xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filters>](filters.md)|包含 XPath 篩選條件的集合，這些篩選條件可用於控制藥記錄的訊息類型。|  
  
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

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [設定訊息記錄](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
