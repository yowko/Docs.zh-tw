---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 4eb79cc91ef489501c4c8bb6311f240d855ed053
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399657"
---
# <a name="servicedebug"></a>\<serviceDebug>
指定 Windows Communication Foundation （WCF）服務的偵錯工具和說明資訊功能。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceDebug >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceDebug httpHelpPageBinding="String"
              httpHelpPageBindingConfiguration="String"
              httpHelpPageEnabled="Boolean"
              httpHelpPageUrl="Uri"
              httpsHelpPageBinding="String"
              httpsHelpPageBindingConfiguration="String"
              httpsHelpPageEnabled="Boolean"
              httpsHelpPageUrl="Uri"
              includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|httpHelpPageBinding|字串值，指定當利用 HTTP 存取服務說明頁面時所使用之繫結的型別。<br /><br /> 只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> 時，這些繫結才會受到支援。 此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>。|  
|httpHelpPageBindingConfiguration|字串，這個字串會指定在 `httpHelpPageBinding` 屬性中指定之繫結的名稱，該屬性會參考這個繫結中的其他組態資訊。 必須在 `<bindings>` 區段中定義相同的名稱。|  
|httpHelpPageEnabled|布林值，控制 WCF 是否在`httpHelpPageUrl`屬性指定的位址發行 HTML 說明頁。 預設為 `true`。<br /><br /> 您可以將這個屬性設定為 `false`，以停用 HTML 瀏覽器可見的 HTML 說明頁的發行。<br /><br /> 若要確保 HTML 說明網頁是在由 `httpHelpPageUrl` 屬性控制的位置發行，必須將這個屬性設定為 `true`。 此外，還必須符合下列其中一項條件：<br /><br /> `httpHelpPageUrl` -屬性是支援 HTTP 通訊協定配置的絕對位址。<br />-支援 HTTP 通訊協定配置的服務有基底位址。<br /><br /> 如果將不支援 HTTP 通訊協定配置的絕對位址指派至 `httpHelpPageUrl` 屬性，將會擲回例外狀況，但是其他任何不符合前述條件的情況都會造成沒有例外狀況和沒有 HTML 說明網頁。|  
|httpHelpPageUrl|URI，指定當使用 HTML 瀏覽器檢視端點時，使用者所看到的自訂 HTML 說明檔之相對或絕對 HTTP URL。<br /><br /> 您可以使用這個屬性來啟用從 HTTP/Get 要求 (例如，從 HTML 瀏覽器) 傳回的自訂 HTML 說明檔。 HTML 說明檔的位置解析如下。<br /><br /> 1.如果這個屬性的值是相對位址，HTML 說明檔的位置就是支援 HTTP 要求的服務基底位址的值再加上這個屬性值。<br />2.如果這個屬性的值是絕對位址且支援 HTTP 要求，HTML 說明檔的位置就是這個屬性的值。<br />3.如果這個屬性的值是絕對位址，但不支援 HTTP 要求，便會擲回例外狀況。<br /><br /> 只有當`httpHelpPageEnabled`屬性為`true`時，這個屬性才有效。|  
|httpsHelpPageBinding|字串值，指定當利用 HTTPS 存取服務說明頁面時所使用之繫結的型別。<br /><br /> 只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel> 時，這些繫結才會受到支援。 此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>。|  
|httpsHelpPageBindingConfiguration|字串，這個字串會指定在 `httpsHelpPageBinding` 屬性中指定之繫結的名稱，該屬性會參考這個繫結中的其他組態資訊。 必須在 `<bindings>` 區段中定義相同的名稱。|  
|httpsHelpPageEnabled|布林值，控制 WCF 是否在`httpsHelpPageUrl`屬性指定的位址發行 HTML 說明頁。 預設為 `true`。<br /><br /> 您可以將這個屬性設定為 `false`，以停用 HTML 瀏覽器可見的 HTML 說明頁的發行。<br /><br /> 若要確保 HTML 說明網頁是在由 `httpsHelpPageUrl` 屬性控制的位置發行，必須將這個屬性設定為 `true`。 此外，還必須符合下列其中一項條件：<br /><br /> `httpsHelpPageUrl` -屬性是支援 HTTPS 通訊協定配置的絕對位址。<br />-支援 HTTPS 通訊協定配置的服務有基底位址。<br /><br /> 如果將不支援 HTTPS 通訊協定配置的絕對位址指派至 `httpsHelpPageUrl` 屬性，將會擲回例外狀況，但是其他任何不符合前述條件的情況都會造成沒有例外狀況和沒有 HTML 說明網頁。|  
|httpsHelpPageUrl|URI，指定當使用 HTML 瀏覽器檢視端點時，使用者所看到的自訂 HTML 說明檔的相對或絕對 HTTPS URL。<br /><br /> 您可以使用這個屬性來啟用從 HTTPS/Get 要求 (例如，從 HTML 瀏覽器) 傳回的自訂 HTML 說明檔。 HTML 說明檔的位置解析如下：<br /><br /> -如果這個屬性的值是相對位址，HTML 說明檔的位置就是支援 HTTPS 要求的服務基底位址的值，加上這個屬性值。<br />-如果此屬性的值是絕對位址且支援 HTTPS 要求，HTML 說明檔的位置就是這個屬性的值。<br />-如果此屬性的值是絕對的，但不支援 HTTPS 要求，則會擲回例外狀況。<br /><br /> 只有當`httpHelpPageEnabled`屬性為`true`時，這個屬性才有效。|  
|includeExceptionDetailInFaults|值，指定是否要針對偵錯用途，在傳回給用戶端的 SOAP 錯誤詳細資料中包含 Managed 例外狀況資訊。 預設為 `false`。<br /><br /> 如果您將這個屬性設定為 `true`，就可以讓 Managed 例外狀況資訊的進入用戶端以便偵錯，以及發行可讓使用者在 Web 瀏覽器中瀏覽服務的 HTML 資訊檔案。 **注意**：將 Managed 例外狀況資訊傳回用戶端時，可能會有安全性風險。 這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## <a name="remarks"></a>備註  
 將`includeExceptionDetailInFaults`設定`true`為，可讓服務傳回應用程式代碼所擲回的任何例外狀況，即使例外狀況未使用<xref:System.ServiceModel.FaultContractAttribute>宣告。 當在伺服器擲回非預期例外狀況的案例中偵錯時，這個設定非常有用。 使用這個屬性會傳回未知例外狀況的序列化表單，而且您可以查看例外狀況的詳細資訊。  
  
> [!CAUTION]
> 將 Managed 例外狀況資訊傳回用戶端可能導致安全性風險，因為例外狀況詳細資料會公開未授權的用戶端可使用的內部服務實作相關資訊。 由於涉及安全性問題，因此強烈建議您只在受控制的偵錯狀況下這樣做。 部署應用程式時，`includeExceptionDetailInFaults` 應該要設為 `false`。  
  
 如需與 managed 例外狀況相關之安全性問題的詳細資訊，請參閱[指定和處理合約和服務中的錯誤](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md)。 如需程式碼範例，請參閱[服務的 Debug 行為](../../../wcf/samples/service-debug-behavior.md)。  
  
 您也可以設定 `httpsHelpPageEnabled` 和 `httpsHelpPageUrl` 來啟用或停用說明網頁。 每個服務都可以選擇公開一份說明網頁，其中包含的服務相關資訊可以包括取得服務之 WSDL 的端點。 將 `httpHelpPageEnabled` 設定為 `true`，便可啟用這項功能。 如此就可讓說明網頁傳回至要求服務基底位址的 GET 要求。 您可以藉由設定 `httpHelpPageUrl` 屬性來變更這個位址。 此外，不使用 HTTP 而改用 HTTPS，就可以保護其安全。  
  
 選用的 `httpHelpPageBinding` 和 `httpHelpPageBinding` 屬性可讓您設定用來存取服務網頁的繫結。 如果未指定這些繫結，則會依適當情形，使用預設的繫結 (使用 HTTP 時為 `HttpTransportBindingElement`，使用 HTTPS 時則為 `HttpsTransportBindingElement`) 存取服務說明頁面。 請注意，這些屬性 (Attribute) 無法搭配內建的 WCF 繫結使用。 僅支援具有內部繫結項目的系結，這些元素支援 x： IReplyChannel >。 此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [指定及處理合約與服務中的錯誤](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [處理例外狀況和失敗](../../../wcf/extending/handling-exceptions-and-faults.md)
- [服務偵錯行為](../../../wcf/samples/service-debug-behavior.md)
