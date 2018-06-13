---
title: '&lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
ms.openlocfilehash: 3a5a0844da401607b2049069e7195fa996c62fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365536"
---
# <a name="ltwebhttpbindinggt"></a>&lt;webHttpBinding&gt;
定義用來設定 Windows Communication Foundation (WCF) Web 服務回應 HTTP 要求，而非 SOAP 訊息的端點繫結項目。  
  
\<system.ServiceModel>  
\<繫結 >  
\<webHttpBinding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<webHttpBinding>  
  <binding   
    allowCookies="Boolean"  
    bypassProxyOnLocal="Boolean"  
    closeTimeout="TimeSpan"  
    hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
    maxBufferPoolSize="integer"  
    maxBufferSize="integer"  
    maxReceivedMessageSize="Integer"  
    name="string"  
    openTimeout="TimeSpan"   
    proxyAddress="URI"  
    receiveTimeout="TimeSpan"  
    sendTimeout="TimeSpan"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
    useDefaultWebProxy="Boolean" 
    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding">  
  <security mode="None/Transport/TransportCredentialOnly">  
    <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
               proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
               realm="string" />  
  </security>  
  <readerQuotas maxArrayLength="Integer" 
                maxBytesPerRead="Integer" 
                maxDepth="Integer" 
                maxNameTableCharCount="Integer" 
                maxStringContentLength="Integer" />  
  </binding>  
</webHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|allowCookies|布林值，表示用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。 預設為 false。<br /><br /> 當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。 如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。|  
|bypassProxyOnLocal|布林值，指出本機位址是否略過 Proxy 伺服器。 預設為 `false`。|  
|closeTimeout|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|hostnameComparisonMode|指定用於剖析 URI 的 HTTP 主機名稱比較模式。 這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。 預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。|  
|maxBufferPoolSize|指定此繫結之緩衝區集區大小上限的整數。 預設為 524,288 個位元組 (512 * 1024)。 Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。 每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。 有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區， 因此可以避免建立及終結緩衝區的負荷。|  
|maxBufferSize|整數，指定配置供從通道接收訊息之訊息緩衝區管理員使用的最大記憶體量。 預設值為 524,288 (0x80000) 位元組。|  
|maxReceivedMessageSize|正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。 超出此限制之訊息的寄件者將會收到錯誤。 收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。 預設值為 65536。 **注意：** 只增加此值不是不足以在 ASP.NET 相容模式。 您也應該增加的值`httpRuntime`(請參閱[httpRuntime 元素 （ASP.NET 設定結構描述）](http://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369))。|  
|name|包含繫結之組態名稱的字串。 這個值應該是唯一的，因為它會當做繫結的識別使用。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|openTimeout|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|proxyAddress|指定 HTTP Proxy 位址的 URI。 如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。 預設為 `null`。|  
|receiveTimeout|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|sendTimeout|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|transferMode.|<xref:System.ServiceModel.TransferMode> 值，指出以繫結設定的服務使用訊息傳輸的資料流處理模式或緩衝處理模式 (或兩者)。 預設為 `Buffered`。|  
|useDefaultWebProxy|布林值，指定是否使用系統自動設定的 HTTP Proxy。 預設為 `true`。|  
|writeEncoding|指定用於訊息文字的字元編碼。 有效值包括以下的值：<br /><br /> UnicodeFffeTextEncoding：Unicode BigEndian 編碼方式。<br /><br /> Utf16TextEncoding：16 位元編碼方式。<br /><br /> Utf8TextEncoding：8 位元編碼方式。<br /><br /> 預設為 Utf8TextEncoding。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|定義 POX 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。 此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|定義繫結的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## <a name="remarks"></a>備註  
 WCF Web 程式設計模型可讓開發人員公開 WCF Web 服務透過 HTTP 要求，使用"plain old XML"(POX) 樣式傳訊而非 SOAP 為基礎的傳訊。 必須使用設定的服務端點使用 HTTP 要求與服務通訊的用戶端， [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)具有\<WebHttpBehavior > 附加到它。  
  
 支援在 WCF 中對於新聞訂閱和 ASP。同時建置在 Web 程式撰寫模型之上 AJAX 整合。 如需有關模型的詳細資訊，請參閱[WCF Web HTTP 程式設計模型](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 [WCF Web HTTP 程式設計模型](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結來設定 Windows Communication Foundation 服務和用戶端](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)
