---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 57a1513f6de7f7bd9ea441b6cbc3db6a06d76fc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940267"
---
# <a name="wsfederation"></a>\<wsFederation>
<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>提供 (WSFAM) 的設定。  
  
\<system.identityModel.services>  
\<federationConfiguration>  
\<wsFederation>  
  
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
  
|屬性|說明|  
|---------------|-----------------|  
|authenticationType|指定驗證類型的 URI。 設定 WS-同盟登入要求 wauth 參數。 選擇性。 預設值為空字串, 指定 wauth 參數不包含在要求中。|  
|常|驗證要求的所需最長使用期限 (以分鐘為單位)。 設定 WS-同盟登入要求 wfresh 參數。 選擇性。 預設值是零。 選擇性。 **警告：** 在下一版的 .NET Framework 4.5 中, `freshness`屬性的類型`xs:string`會是, 而其預設值將`null`是。|  
|homeRealm|要用於驗證的識別提供者 (IdP) 的主領域。 設定 WS-同盟登入要求中的參數。 選擇性。 預設值為空字串, 指定要求中未包含「瓦的」參數。|  
|issuer|預定權杖簽發者的 URI。 設定 WS-同盟登入要求和登出要求的基底 URL。|  
|persistentCookiesOnPassiveRedirects|指定是否在驗證時發出持續性 cookie。 選擇性。 預設值為 "false", 不會發出 cookie。|  
|passiveRedirectEnabled|指定是否啟用 WSFAM, 以將未經授權的要求自動重新導向至 STS。 選擇性。 預設值為 "true", 未授權的要求會自動重新導向。|  
|原則|URL, 指定要用於登入要求的相關原則位置。 預設值是空字串。 設定 WS-同盟登入要求 wp 參數。 選擇性。 預設值為空字串, 指定 wp 參數不包含在要求中。|  
|realm|要求領域的 URI。 (識別 Security Token Service (STS) 信賴憑證者 (RP) 的 URI。)設定要求 wtrealm WS-同盟登入要求參數。 必要項。|  
|件|識別信賴憑證者 (RP) 應用程式想要從安全性權杖服務 (STS) 接收回複之位址的 URL。 設定 WS-同盟登入要求 wreply 參數。 選擇性。 預設值為空字串, 指定 wreply 參數不包含在要求中。|  
|要求|權杖發佈要求。 設定 WS-同盟登入要求 wreq 參數。 選擇性。 預設值為空字串, 指定 wreq 參數不包含在要求中。 不包含 wreq 或要求中的 wreqptr 參數表示 STS 知道要發出的權杖種類。|  
|requestPtr|指定權杖發行要求位置的 URL。 設定要求 wreqptr 參數。 選擇性。 預設值為空字串, 指定 wreqptr 參數不包含在要求中。 不包含 wreq 或要求中的 wreqptr 參數表示 STS 知道要發出的權杖種類。|  
|requireHttps|指定與 Security Token Service (STS) 的通訊是否必須使用 HTTPS 通訊協定。 選擇性。 預設值為 "true", 必須使用 HTTPS。|  
|資源|URI, 識別要存取的資源 (信賴憑證者 (RP)) 至 Security Token Service (STS)。 選擇性。 設定 WS-同盟登入要求 wres 參數。 選擇性。 預設值為空字串, 指定 wres 參數不包含在要求中。 **注意:** wres 是舊版參數。 請指定`realm`要改用 wtrealm 參數的屬性。|  
|signInQueryString|提供擴充點, 以在 WS-同盟登入要求 URL 中指定應用程式定義的查詢參數。 選擇性。 預設值為空字串, 指定不應在要求中包含任何其他參數。 參數會使用下列格式指定為查詢字串片段: `"param1=value1&param2=value2&param3=value3"`等等。 **注意：** 在設定檔中, `&`查詢字串中的 ' & "字元必須使用其實體參考來指定。|  
|signOutQueryString|提供擴充點, 以在 WS-同盟登入要求 URL 中指定應用程式定義的查詢參數。 選擇性。 預設值為空字串, 指定不應在要求中包含任何其他參數。 參數會使用下列格式指定為查詢字串片段: `"param1=value1&param2=value2&param3=value3"`等等。 **注意：** 在設定檔中, `&`查詢字串中的 ' & "字元必須使用其實體參考來指定。|  
|signOutReply|指定在透過 WS-同盟通訊協定進行被動式登出期間, Security Token Service (STS) 應將用戶端重新導向至的 URL。 在 WS-同盟登出要求上設定 wreply 參數。 選擇性。 預設值為空字串, 指定不應在要求中包含任何其他參數。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule>和 (SAM) 的設定。|  
  
## <a name="remarks"></a>備註  
 您可以使用`<wsFederation>`元素來設定預設的 WS-同盟參數設定和 WSFAM 的預設行為。 在元素底下定義的 WS-同盟`<wsFederation>`參數設定會設定類別所<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>公開的對等屬性。 針對 WSFAM 所發出的每個要求, 這些屬性會維持不變。 您可以為 WSFAM 所公開的事件新增事件處理常式, 以動態方式在要求處理期間變更 WS-同盟參數;例如, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>事件。 如需詳細資訊, 請參閱<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>類別的檔。  
  
 `<wsFederation>`元素是<xref:System.IdentityModel.Services.Configuration.WSFederationElement>由類別表示。 設定物件本身是以<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>類別表示。 會在<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>透過<xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性存取的物件上設定單一實例,並提供WSFAM的設定。<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>範例  
 下列 XML 顯示`<wsFederation>`的元素會指定 WSFAM 的設定。  
  
> [!WARNING]
>  在此範例中, 不需要 WSFAM 就能使用 HTTPS。 這是因為已`requireHttps`設定`<wsFederation>` `false`元素上的屬性。 在大部分的生產環境中, 不建議使用此設定, 因為這可能會有安全性風險。  
  
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

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
