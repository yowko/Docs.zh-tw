---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 1c044f7346fabc77d7744f42c5bfd3d86d72402e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988349"
---
# <a name="cookiehandler"></a>\<cookieHandler>
<xref:System.IdentityModel.Services.CookieHandler> 設定(SAM)用來讀取<xref:System.IdentityModel.Services.SessionAuthenticationModule>和寫入 cookie 的。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|NAME|指定任何寫入 cookie 的基底名稱。 預設值為 "FedAuth"。|  
|路徑|指定任何寫入 cookie 的路徑值。 預設值為 "HttpRuntime. AppDomainAppVirtualPath"。|  
|模式|其中一個值, 指定 SAM 所使用的 cookie 處理常式種類。 <xref:System.IdentityModel.Services.CookieHandlerMode> 可能會使用下列值:<br /><br /> -「預設」-與「區塊」相同。<br />-「區塊」-使用<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別的實例。 此 cookie 處理常式可確保個別 cookie 不會超過設定的大小上限。 這是因為可能會將一個邏輯 cookie 「區塊化」到多個網路上的 cookie。<br />-「自訂」—使用衍生自之<xref:System.IdentityModel.Services.CookieHandler>自訂類別的實例。 衍生類別是由`<customCookieHandler>`子項目所參考。<br /><br /> 預設值為 "Default"。|  
|persistentSessionLifetime|指定持續性會話的存留期。 如果為零, 則一律使用暫時性會話。 預設值為 "0:0:0", 指定暫時性會話。 最大值為 "365:0:0", 指定365天的會話。 應該根據下列限制來指定值: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, 其中最左邊的值會指定 days、中間值 (如果有的話) 指定小時, 而最右邊的值 (如果有的話) 會指定分鐘。|  
|requireSsl|指定是否針對任何寫入的 cookie 發出 "Secure" 旗標。 如果設定此值, 登入會話 cookie 只會透過 HTTPS 提供。 預設為 "true"。|  
|hideFromScript|控制是否針對任何寫入的 cookie 發出 "HttpOnly" 旗標。 某些網頁瀏覽器會藉由保留用戶端腳本來存取 cookie 值, 以接受此旗標。 預設為 "true"。|  
|網域|任何寫入 cookie 的網域值。 預設值為 ""。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|<xref:System.IdentityModel.Services.ChunkedCookieHandler>設定。 只有當`mode` `<cookieHandler>`元素的屬性為「預設」或「區塊」時, 才會出現此元素。|  
|[\<customCookieHandler>](customcookiehandler.md)|設定自訂 cookie 處理常式類型。 如果`mode` `<cookieHandler>`元素的屬性為 "Custom", 則必須要有此元素。 它不能存在於`mode`屬性的任何其他值。 自訂類型必須衍生<xref:System.IdentityModel.Services.CookieHandler>自類別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule>和 (SAM) 的設定。|  
  
## <a name="remarks"></a>備註  
 <xref:System.IdentityModel.Services.CookieHandler>負責讀取及寫入 HTTP 通訊協定層級的原始 cookie。 您可以設定<xref:System.IdentityModel.Services.ChunkedCookieHandler> <xref:System.IdentityModel.Services.CookieHandler>從類別衍生的或自訂 cookie 處理常式。  
  
 若要設定區塊 cookie 處理常式, 請將 mode 屬性設為 "分塊" 或 "Default"。 預設的區塊大小是2000個位元組, 但是您可以選擇性地指定不同的區塊大小, `<chunkedCookieHandler>`方法是包含子項目。  
  
 若要設定自訂的 cookie 處理常式, 請將 mode 屬性設為 "Custom"。 您也必須指定`<customCookieHandler>`參考自訂處理常式類型的子項目。  
  
 `<cookieHandler>`元素是<xref:System.IdentityModel.Services.CookieHandlerElement>由類別表示。 在設定中指定的 cookie 處理常式, 可從<xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性上<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件集的屬性取得。  
  
## <a name="example"></a>範例  
 下列 XML 會顯示`<cookieHandler>`元素。 在此範例中, 因為`mode`未指定屬性, 所以 SAM 會使用預設的 cookie 處理常式。 這是<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別的實例。 由於未指定子項目, 因此會使用預設的區塊大小。 `<chunkedCookieHandler>` 不需要 HTTPS, `requireSsl`因為已設定`false`屬性。  
  
> [!WARNING]
> 在此範例中, 不需要 HTTPS 來寫入會話 cookie。 這是因為`<cookieHandler>`元素`requireSsl`上的屬性設定為。 `false` 在大部分的生產環境中, 不建議使用此設定, 因為這可能會有安全性風險。  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
