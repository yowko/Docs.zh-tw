---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 853dc9817d080e59ac7a792576eda862bd0b1f1d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252032"
---
# \<cookieHandler>
設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）用來讀取和寫入 cookie 的。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cookieHandler>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|指定任何寫入 cookie 的基底名稱。 預設值為 "FedAuth"。|  
|路徑|指定任何寫入 cookie 的路徑值。 預設值為 "HttpRuntime. AppDomainAppVirtualPath"。|  
|mode|其中一個 <xref:System.IdentityModel.Services.CookieHandlerMode> 值，指定 SAM 所使用的 cookie 處理常式種類。 可能會使用下列值：<br /><br /> -「預設」-與「區塊」相同。<br />-「區塊」-使用類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 此 cookie 處理常式可確保個別 cookie 不會超過設定的大小上限。 這是因為可能會將一個邏輯 cookie 「區塊化」到多個網路上的 cookie。<br />-「自訂」—使用衍生自之自訂類別的實例 <xref:System.IdentityModel.Services.CookieHandler> 。 衍生類別是由 `<customCookieHandler>` 子項目所參考。<br /><br /> 預設值為 "Default"。|  
|persistentSessionLifetime|指定持續性會話的存留期。 如果是零，則永遠使用暫時性工作階段。 預設值為 "0:0:0"，指定暫時性會話。 最大值為 "365:0:0"，指定365天的會話。 應該根據下列限制來指定值： `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />` ，其中最左邊的值會指定 days、中間值（如果有的話）指定小時，而最右邊的值（如果有的話）會指定分鐘。|  
|requireSsl|指定是否針對任何寫入的 cookie 發出 "Secure" 旗標。 如果設定此值，登入會話 cookie 只會透過 HTTPS 提供。 預設為 "true"。|  
|hideFromScript|控制是否針對任何寫入的 cookie 發出 "HttpOnly" 旗標。 某些網頁瀏覽器會藉由保留用戶端腳本來存取 cookie 值，以接受此旗標。 預設為 "true"。|  
|網域|任何寫入 cookie 的網域值。 預設值為 ""。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 只有當 `mode` 元素的屬性為「預設」或「區塊」時，才會出現此元素 `<cookieHandler>` 。|  
|[\<customCookieHandler>](customcookiehandler.md)|設定自訂 cookie 處理常式類型。 如果 `mode` 元素的屬性 `<cookieHandler>` 為 "Custom"，則必須要有此元素。 它不能存在於屬性的任何其他值 `mode` 。 自訂類型必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）的設定。|  
  
## <a name="remarks"></a>備註  
 <xref:System.IdentityModel.Services.CookieHandler>負責讀取及寫入 HTTP 通訊協定層級的原始 cookie。 您可以設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 從類別衍生的或自訂 cookie 處理常式 <xref:System.IdentityModel.Services.CookieHandler> 。  
  
 若要設定區塊 cookie 處理常式，請將 mode 屬性設為 "分塊" 或 "Default"。 預設的區塊大小是2000個位元組，但是您可以選擇性地指定不同的區塊大小，方法是包含 `<chunkedCookieHandler>` 子項目。  
  
 若要設定自訂的 cookie 處理常式，請將 mode 屬性設為 "Custom"。 您也必須指定 `<customCookieHandler>` 參考自訂處理常式類型的子項目。  
  
 `<cookieHandler>`元素是由 <xref:System.IdentityModel.Services.CookieHandlerElement> 類別表示。 在設定中指定的 cookie 處理常式，可從 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性上物件集的屬性取得 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> 。  
  
## <a name="example"></a>範例  
 下列 XML 會顯示 `<cookieHandler>` 元素。 在此範例中，因為 `mode` 未指定屬性，所以 SAM 會使用預設的 cookie 處理常式。 這是類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 由於 `<chunkedCookieHandler>` 未指定子項目，因此會使用預設的區塊大小。 不需要 HTTPS，因為 `requireSsl` 已設定屬性 `false` 。  
  
> [!WARNING]
> 在此範例中，不需要 HTTPS 來寫入會話 cookie。 這是因為 `requireSsl` 元素上的屬性 `<cookieHandler>` 設定為 `false` 。 在大部分的生產環境中，不建議使用此設定，因為這可能會有安全性風險。  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
