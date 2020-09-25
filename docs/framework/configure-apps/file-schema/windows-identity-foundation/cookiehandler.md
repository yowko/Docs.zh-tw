---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 5f5b432830a61adab324b2b6cd2ebe6eeccca7f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189834"
---
# \<cookieHandler>

設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 用來讀取和寫入 cookie 的。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cookieHandler>**  
  
## <a name="syntax"></a>Syntax  
  
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
|path|指定任何寫入 cookie 的路徑值。 預設值為 "HttpRuntime. AppDomainAppVirtualPath"。|  
|mode|其中一個 <xref:System.IdentityModel.Services.CookieHandlerMode> 值，這個值會指定 SAM 所使用的 cookie 處理常式種類。 您可以使用下列值：<br /><br /> -「預設」，與「區塊」相同。<br />-「區塊」-使用類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 此 cookie 處理常式可確保個別的 cookie 不會超過設定的大小上限。 它會藉由在網路上將一個邏輯 cookie 「區塊化」為數個 cookie 來完成此操作。<br />-"Custom"-使用衍生自之自訂類別的實例 <xref:System.IdentityModel.Services.CookieHandler> 。 子項目會參考衍生類別 `<customCookieHandler>` 。<br /><br /> 預設值為 "Default"。|  
|persistentSessionLifetime|指定持續性會話的存留期。 如果是零，則永遠使用暫時性工作階段。 預設值為 "0:0:0"，指定暫時性會話。 最大值為 "365:0:0"，其指定的會話為365天。 您應該根據下列限制來指定此值： `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />` ，其中最左邊的值指定天數、中間值 (（如果有的話）) 指定時，以及最右邊的 (值（如果有的話）) 指定分鐘數。|  
|requireSsl|指定是否針對任何寫入的 cookie 發出 "Secure" 旗標。 如果設定此值，登入會話 cookie 將只能透過 HTTPS 來使用。 預設為 "true"。|  
|hideFromScript|控制是否針對任何寫入的 cookie 發出 "HttpOnly" 旗標。 某些網頁瀏覽器會藉由讓用戶端腳本存取 cookie 值，來接受此旗標。 預設為 "true"。|  
|網域|任何寫入之 cookie 的定義域值。 預設值為 ""。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 只有當專案的 `mode` 屬性 `<cookieHandler>` 是 "Default" 或 "區塊" 時，才會出現這個元素。|  
|[\<customCookieHandler>](customcookiehandler.md)|設定自訂的 cookie 處理常式類型。 如果 `mode` 元素的屬性是「自訂」，則必須有這個元素 `<cookieHandler>` 。 屬性的任何其他值都不能有此值 `mode` 。 自訂類型必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 的設定。|  
  
## <a name="remarks"></a>備註  

 <xref:System.IdentityModel.Services.CookieHandler>負責在 HTTP 通訊協定層級讀取和寫入原始 cookie。 您可以設定衍生自 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 類別的或自訂 cookie 處理常式 <xref:System.IdentityModel.Services.CookieHandler> 。  
  
 若要設定區塊 cookie 處理常式，請將模式屬性設定為「區塊」或「預設」。 預設區塊大小為2000個位元組，但您可以選擇性地包含子項目來指定不同的區塊大小 `<chunkedCookieHandler>` 。  
  
 若要設定自訂的 cookie 處理常式，請將 [模式] 屬性設定為 [自訂]。 您也必須指定 `<customCookieHandler>` 參考自訂處理常式類型的子項目。  
  
 `<cookieHandler>`元素是由 <xref:System.IdentityModel.Services.CookieHandlerElement> 類別表示。 在設定中指定的 cookie 處理常式，可從 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> 屬性（property）上的物件（property）屬性（property）中取得 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> 。  
  
## <a name="example"></a>範例  

 下列 XML 會顯示 `<cookieHandler>` 元素。 在此範例中，因為 `mode` 未指定屬性，所以 SAM 將會使用預設的 cookie 處理常式。 這是類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 因為 `<chunkedCookieHandler>` 未指定子項目，所以會使用預設的區塊大小。 因為已設定屬性，所以不需要 HTTPS `requireSsl` `false` 。  
  
> [!WARNING]
> 在此範例中，不需要 HTTPS 來寫入會話 cookie。 這是因為 `requireSsl` 元素上的屬性 `<cookieHandler>` 設定為 `false` 。 這項設定不建議用於大部分的生產環境，因為這可能會帶來安全性風險。  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
