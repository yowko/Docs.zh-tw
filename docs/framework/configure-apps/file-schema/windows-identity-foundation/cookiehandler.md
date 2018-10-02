---
title: '&lt;cookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 99bf6edb4e4f631eba292990c65c1f0c8553d8c0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046444"
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
會設定<xref:System.IdentityModel.Services.CookieHandler>， <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 會使用來讀取和寫入 cookie。  
  
 \<system.identityModel.services >  
\<Federationconfiguration> >  
\<cookieHandler >  
  
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
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|指定寫入的任何 cookie 的基底名稱。 預設值為"FedAuth"。|  
|路徑|指定寫入的任何 cookie 的路徑值。 預設值為"HttpRuntime.AppDomainAppVirtualPath 」。|  
|模式|其中一個<xref:System.IdentityModel.Services.CookieHandlerMode>指定 SAM 所使用的 cookie 處理常式類型的值。 可以使用下列值：<br /><br /> -"Default"，"Chunked"相同。<br />-「 區塊 」 — 使用的執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別。 此 cookie 處理常式可確保個別 cookie 不會超過設定的最大大小。 這是可能 「 區塊處理 」 邏輯 cookie cookie 上連線的數目。<br />-「 自訂 」 — 使用一個衍生自的自訂類別的執行個體<xref:System.IdentityModel.Services.CookieHandler>。 在衍生的類別由參考`<customCookieHandler>`子項目。<br /><br /> 預設值為"Default"。|  
|persistentSessionLifetime|指定持續性工作階段的存留期。 如果是零，永遠使用暫時性工作階段。 預設值是"0:0:0 」，其指定的暫時性工作階段。 最大值是"365:0:0 」，其指定為 365 天的工作階段。 應該指定的值，根據下列限制： `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`，其中最左邊的值會指定天、 中間值 （如果有的話） 會指定小時，而最右邊的值 （如果有的話） 會指定分鐘。|  
|RequireSsl|指定是否為任何撰寫的 cookie 發出"Secure"旗標。 如果此值設定時，登入工作階段 cookie 只可透過 HTTPS。 預設為 "true"。|  
|hideFromScript|控制是否"HttpOnly 」 旗標，就會發出任何寫入的 cookie。 某些網頁瀏覽器會接受這個旗標，保留用戶端指令碼存取 cookie 值。 預設為 "true"。|  
|網域|寫入的任何 cookie 網域值。 預設值為 ""。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Chunkedcookiehandler> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。 這個項目只會出現如果`mode`屬性的`<cookieHandler>`項目是 「 預設 」 或 「 區塊 」。|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|設定自訂 cookie 處理常式型別。 必須有此項目如果`mode`屬性的`<cookieHandler>`項目是 「 自訂 」。 它不能存在的任何其他值`mode`屬性。 自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>備註  
 <xref:System.IdentityModel.Services.CookieHandler>負責讀取和寫入未經處理的 cookie 在 HTTP 通訊協定層級。 您可以設定其中一個<xref:System.IdentityModel.Services.ChunkedCookieHandler>或自訂 cookie 處理常式衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。  
  
 若要設定區塊的 cookie 處理常式，將模式屬性設定為"Chunked"或"Default"。 預設區塊大小為 2000 個位元組，但您可以選擇性地指定不同的區塊大小包含`<chunkedCookieHandler>`子項目。  
  
 若要設定自訂 cookie 處理常式，將模式屬性設定為 「 自訂 」。 您也必須指定`<customCookieHandler>`子項目會參考您的自訂處理常式的類型。  
  
 `<cookieHandler>`項目由<xref:System.IdentityModel.Services.CookieHandlerElement>類別。 已在組態中指定的 cookie 處理常式是可從<xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A>的屬性<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件，在設定<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性。  
  
## <a name="example"></a>範例  
 下列 XML 會說明`<cookieHandler>`項目。 在此範例中，因為`mode`屬性未指定，SAM 將使用預設的 cookie 處理常式。 這是執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別。 因為`<chunkedCookieHandler>`子項目未指定，將使用預設區塊大小。 不需要 HTTPS，因為`requireSsl`屬性設定`false`。  
  
> [!WARNING]
>  在此範例中，HTTPS 不是需要撰寫工作階段 cookie。 這是因為`requireSsl`屬性`<cookieHandler>`元素設定為`false`。 此設定不會建議用於大部分的生產環境，因為它可能會有安全性風險。  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
