---
title: '&lt;wsFederation&gt;'
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 66596bbc7171a33318b835a552b7fb364d6833f7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580392"
---
# <a name="ltwsfederationgt"></a>&lt;wsFederation&gt;
提供組態<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM)。  
  
\<system.identityModel.services >  
\<Federationconfiguration> >  
\<wsFederation >  
  
## <a name="syntax"></a>語法  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|AuthenticationType|URI，指定驗證類型。 設定 WS-同盟登入要求 wauth 參數。 選擇性。 預設為空字串，其指定的 wauth 參數不包含在要求中。|  
|有效期限|想要最長使用期限的驗證要求，以分鐘為單位。 設定 WS-同盟登入要求 wfresh 參數。 選擇性。 預設值是零。 選擇性。 **警告：** 的下一個版本的.NET Framework 4.5`freshness`屬性的類型會是`xs:string`和其預設值為`null`。|  
|homeRealm|要用於驗證身分識別提供者 (IP) 的主領域。 設定 WS-同盟登入要求 whr 參數。 選擇性。 預設為空字串，其指定的 whr 參數不包含在要求中。|  
|issuer|預期的權杖簽發者 URI。 設定基底 URL 的 WS-同盟登入要求和所需的登出要求。|  
|persistentCookiesOnPassiveRedirects|指定是否驗證上發出永續性 cookie。 選擇性。 預設值為"false"，cookies 未發出。|  
|passiveRedirectEnabled|指定是否啟用 WSFAM 會自動將未經授權的要求重新導向至 STS。 選擇性。 預設值為"true"，未經授權的要求會自動重新導向。|  
|原則|指定的位置相關的原則，若要使用的登入要求的 URL。 預設為空字串。 設定 WS-同盟登入要求 wp 參數。 選擇性。 預設為空字串，指定在要求中未包含的 wp 參數。|  
|realm|要求領域的 URI。 (至安全性權杖服務 (STS) 識別的信賴憑證者的合作對象 (RP) URI)。設定要求 wtrealm WS-同盟登入要求參數。 必要。|  
|回覆|識別的信賴憑證者 (rp) 應用程式想要從安全性權杖服務 (STS) 接收回覆的地址的 URL。 設定 WS-同盟登入要求 wreply 參數。 選擇性。 預設為空字串，指定在要求中不包含 wreply 參數。|  
|要求|權杖發佈要求。 設定 WS-同盟登入要求 wreq 參數。 選擇性。 預設為空字串，其指定的 wreq 參數不包含在要求中。 不包含在要求中的 wreq 或 wreqptr 參數，表示 STS 知道要發出的權杖類型。|  
|requestPtr|指定的權杖發佈要求位置的 URL。 設定要求 wreqptr 參數。 選擇性。 預設為空字串，其指定的 wreqptr 參數不包含在要求中。 不包含在要求中的 wreq 或 wreqptr 參數，表示 STS 知道要發出的權杖類型。|  
|requireHttps|指定與安全性權杖服務 (STS) 的通訊是否必須使用 HTTPS 通訊協定。 選擇性。 預設值為"true"，必須使用 HTTPS。|  
|資源|URI，識別所存取資源的信賴憑證者的合作對象 (RP)，為安全性權杖服務 (STS)。 選擇性。 設定 WS-同盟登入要求 wres 參數。 選擇性。 預設為空字串，指定在要求中未包含的 wres 參數。 **注意：** wres 是傳統的參數。 指定`realm`改為使用 wtrealm 參數的屬性。|  
|signInQueryString|提供擴充點，以在 WS-同盟登入要求 URL 中指定應用程式定義查詢參數。 選擇性。 預設為空字串，指定應該在要求中包含任何額外的參數。 參數會指定為查詢字串片段，使用下列格式： `"param1=value1&param2=value2&param3=value3"` ，依此類推。 **注意︰** 組態檔中 ' &"查詢字串中的字元必須使用其實體的參考，來指定`&`。|  
|signOutQueryString|提供擴充點，以在 WS-同盟登入要求 URL 中指定應用程式定義查詢參數。 選擇性。 預設為空字串，指定應該在要求中包含任何額外的參數。 參數會指定為查詢字串片段，使用下列格式： `"param1=value1&param2=value2&param3=value3"` ，依此類推。 **注意︰** 組態檔中 ' &"查詢字串中的字元必須使用其實體的參考，來指定`&`。|  
|signOutReply|在被動登出透過 WS-同盟通訊協定中指定的用戶端應該重新導向安全性權杖服務 (STS) 的 URL。 設定 WS-同盟登出要求 wreply 參數。 選擇性。 預設為空字串，指定應該在要求中包含任何額外的參數。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>備註  
 您可以使用`<wsFederation>`WSFAM 設定預設的 WS-同盟參數設定和預設行為的項目。 WS-同盟參數設定下定義`<wsFederation>`元素設定對等所公開的屬性<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>類別。 這些屬性保持不變，WSFAM 所發出的每個要求。 您可以藉由新增 WSFAM; 所公開之事件的事件處理常式所處理的要求期間，動態變更的 WS-同盟參數比方說，<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>事件。 如需詳細資訊，請參閱文件<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>類別。  
  
 `<wsFederation>`項目由<xref:System.IdentityModel.Services.Configuration.WSFederationElement>類別。 設定物件本身由<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>類別。 單一<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>上設定執行個體<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件，透過存取<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性，並提供 WSFAM 組態。  
  
## <a name="example"></a>範例  
 下列 XML 會說明`<wsFederation>`指定 WSFAM 的設定項目。  
  
> [!WARNING]
>  在此範例中，WSFAM 不是需要使用 HTTPS。 這是因為`requireHttps`屬性`<wsFederation>`項目設定`false`。 此設定不會建議用於大部分的生產環境，因為它可能會有安全性風險。  
  
```xml
<wsFederation passiveRedirectEnabled="true"   
              issuer="http://localhost:15839/wsFederationSTS/Issue"   
              realm="http://localhost:50969/"   
              reply="http://localhost:50969/"   
              requireHttps="false"   
              signOutReply="http://localhost:50969/SignedOutPage.html"   
              signOutQueryString="Param1=value2&Param2=value2"   
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
