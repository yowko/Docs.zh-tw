---
title: '&lt;wsFederation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e4779baa24e172affad2ed5e04451ad791d7cdf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltwsfederationgt"></a>&lt;wsFederation&gt;
提供組態<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM)。  
  
\<system.identityModel.services >  
\<federationConfiguration >  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|authenticationType|URI，指定驗證類型。 WS-同盟登入要求 wauth 參數設定。 選擇項。 預設為空字串，指定 wauth 參數不包含在要求中。|  
|有效期限|所需最長使用期限的驗證要求，以分鐘為單位。 WS-同盟登入要求 wfresh 參數設定。 選擇項。 預設值是零。 選擇項。 **警告：**下一版的.NET Framework 4.5、`freshness`屬性都屬於類型`xs:string`和其預設值為`null`。|  
|homeRealm|要用於驗證的身分識別提供者 (IP) 主領域。 WS-同盟登入要求 whr 參數設定。 選擇項。 預設為空字串，指定 whr 參數不包含在要求中。|  
|issuer|預期的權杖簽發者的 URI。 設定基底 URL 的 WS-同盟登入要求和所需的登出要求。|  
|persistentCookiesOnPassiveRedirects|指定是否要針對驗證，來發出永續性 cookie。 選擇項。 預設值為"false"，不會發行 cookie。|  
|passiveRedirectEnabled|指定是否啟用 WSFAM 自動未經授權的要求重新導向至 STS。 選擇項。 預設值為"true"，未經授權的要求會自動重新導向。|  
|原則|指定的登入要求上使用相關的原則位置的 URL。 預設為空字串。 WS-同盟登入要求 wp 參數設定。 選擇項。 預設為空字串，指定 wp 參數不包含在要求中。|  
|realm|要求領域的 URI。 (可識別信賴憑證者的合作對象 (RP) 的安全性權杖服務 (STS) URI)。設定要求 wtrealm WS-同盟登入要求的參數。 必要項。|  
|回覆|URL 識別的信賴憑證者的合作對象 (RP) 應用程式想要從安全性權杖服務 (STS) 都會收到回覆地址。 WS-同盟登入要求 wreply 參數設定。 選擇項。 預設為空字串，指定 wreply 參數不包含在要求中。|  
|要求|權杖發佈要求。 WS-同盟登入要求 wreq 參數設定。 選擇項。 預設為空字串，指定 wreq 參數不包含在要求中。 不包括在要求中的 wreq 或 wreqptr 參數表示 STS 知道要發出的權杖類型。|  
|requestPtr|指定權杖發佈要求的位置的 URL。 設定要求的 wreqptr 參數。 選擇項。 預設為空字串，指定 wreqptr 參數不包含在要求中。 不包括在要求中的 wreq 或 wreqptr 參數表示 STS 知道要發出的權杖類型。|  
|requireHttps|指定與安全性權杖服務 (STS) 的通訊是否必須使用 HTTPS 通訊協定。 選擇項。 預設值為"true"，則必須使用 HTTPS。|  
|資源|URI 為識別所存取之資源的信賴憑證者的合作對象 (RP)，以安全性權杖服務 (STS)。 選擇項。 WS-同盟登入要求 wres 參數設定。 選擇項。 預設為空字串，指定 wres 參數不包含在要求中。 **注意：** wres 是傳統的參數。 指定`realm`改為使用 wtrealm 參數的屬性。|  
|signInQueryString|提供擴充點，以便在 WS-同盟登入要求 URL 中指定應用程式定義查詢參數。 選擇項。 預設為空字串，指定應該在要求中包含其他任何參數。 參數會指定為使用下列形式的查詢字串片段： `"param1=value1&param2=value2&param3=value3"` ，依此類推。 **注意：**組態檔中 ' （& s) 」 必須使用其實體參考，來指定查詢字串中的字元`&`。|  
|signOutQueryString|提供擴充點，以便在 WS-同盟登入要求 URL 中指定應用程式定義查詢參數。 選擇項。 預設為空字串，指定應該在要求中包含其他任何參數。 參數會指定為使用下列形式的查詢字串片段： `"param1=value1&param2=value2&param3=value3"` ，依此類推。 **注意：**組態檔中 ' （& s) 」 必須使用其實體參考，來指定查詢字串中的字元`&`。|  
|signOutReply|在被動登出透過 WS-同盟通訊協定中指定的用戶端應該重新導向安全性權杖服務 (STS) 的 URL。 在 WS-同盟登出要求上設定 wreply 的參數。 選擇項。 預設為空字串，指定應該在要求中包含其他任何參數。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>備註  
 您可以使用`<wsFederation>`WSFAM 設定預設的 WS-同盟參數設定和預設行為的項目。 定義在 WS-同盟參數設定`<wsFederation>`元素設定對等所公開的屬性<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>類別。 這些屬性保持不變 WSFAM 所發出的每個要求。 您可以將 WSFAM; 所公開的事件的事件處理常式加入處理要求期間，動態變更 WS-同盟參數例如，<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>事件。 如需詳細資訊，請參閱文件<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>類別。  
  
 `<wsFederation>`項目由<xref:System.IdentityModel.Services.Configuration.WSFederationElement>類別。 組態物件本身由<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>類別。 單一<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>執行個體上設定<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件透過存取<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性，並提供 WSFAM 的組態。  
  
## <a name="example"></a>範例  
 下列 XML 會說明`<wsFederation>`指定 WSFAM 的設定項目。  
  
> [!WARNING]
>  在此範例中，WSFAM 不需要使用 HTTPS。 這是因為`requireHttps`屬性`<wsFederation>`元素設定`false`。 這項設定不會建議針對大部分的實際執行環境，因為它可能會有安全性風險。  
  
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
