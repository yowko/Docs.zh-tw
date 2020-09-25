---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 93661af6c907d8cce1a73536a8ebca7bd53c00d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185505"
---
# \<wsFederation>

提供 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 的設定。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederation>**  
  
## <a name="syntax"></a>Syntax  
  
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

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|authenticationType|指定驗證類型的 URI。 設定 WS-同盟登入要求 >wauth 參數。 選擇性。 預設值為空字串，指定 >wauth 參數不包含在要求中。|  
|新鮮|所需的驗證要求最長使用期限，以分鐘為單位。 設定 WS-Federation 登入要求 wfresh 參數。 選擇性。 預設值是零。 選擇性。 **警告：**  在下一版的 .NET Framework 4.5 中， `freshness` 屬性的類型為， `xs:string` 且其預設值為 `null` 。|  
|homeRealm|身分識別提供者的主領域 (IdP) 以用於驗證。 設定 WS-Federation 登入要求 whr 參數。 選擇性。 預設值為空字串，它會指定要求中不包含 [中的瓦] 參數。|  
|簽發者|預定權杖簽發者的 URI。 設定 WS-同盟登入要求和登出要求的基底 URL。|  
|persistentCookiesOnPassiveRedirects|指定是否在驗證時發出持續性 cookie。 選擇性。 預設值是 "false"，不會發出 cookie。|  
|passiveRedirectEnabled|指定是否啟用 WSFAM，以將未經授權的要求自動重新導向至 STS。 選擇性。 預設值為 "true"，系統會自動重新導向未授權的要求。|  
|原則|URL，指定要在登入要求中使用的相關原則的位置。 預設為空字串。 設定 WS-Federation 登入要求 wp 參數。 選擇性。 預設值為空字串，指定 wp 參數不包含在要求中。|  
|realm|要求領域的 URI。  (識別信賴憑證者 (RP) 至安全性權杖服務 (STS) 的 URI。 ) 設定要求 wtrealm WS-同盟登入要求參數。 必要。|  
|答覆|識別信賴憑證者 (RP) 應用程式要用來接收 Security Token Service (STS) 回覆之位址的 URL。 設定 WS-同盟登入要求 wreply 參數。 選擇性。 預設值為空字串，指定 wreply 參數不包含在要求中。|  
|要求|權杖發行要求。 設定 WS-Federation 登入要求 wreq 參數。 選擇性。 預設值為空字串，指定 wreq 參數不包含在要求中。 不在要求中包含 wreq 或 wreqptr 參數表示 STS 知道要發出的權杖種類。|  
|requestPtr|URL，指定語彙基元發佈要求的位置。 設定要求 wreqptr 參數。 選擇性。 預設值為空字串，指定 wreqptr 參數不包含在要求中。 不在要求中包含 wreq 或 wreqptr 參數表示 STS 知道要發出的權杖種類。|  
|requireHttps|指定與安全性權杖服務 (STS) 的通訊是否必須使用 HTTPS 通訊協定。 選擇性。 預設值為 "true"，必須使用 HTTPS。|  
|resource|用來向 Security Token Service (STS) 識別所存取之資源 (信賴憑證者 (RP)) 的 URI。 選擇性。 設定 WS-同盟登入要求 wres 參數。 選擇性。 預設值為空字串，指定 wres 參數不包含在要求中。 **注意：**  wres 是舊版參數。 請指定 `realm` 要改用 wtrealm 參數的屬性。|  
|signInQueryString|提供擴充點，以在 WS-同盟登入要求 URL 中指定應用程式定義的查詢參數。 選擇性。 預設值為空字串，指定要求中不應包含任何其他參數。 參數會使用下列格式指定為查詢字串片段： `"param1=value1&param2=value2&param3=value3"` 等等。 **注意：**  在設定檔中，必須使用實體參考來指定查詢字串中的 ' & "字元 `&` 。|  
|signOutQueryString|提供擴充點，以在 WS-同盟登入要求 URL 中指定應用程式定義的查詢參數。 選擇性。 預設值為空字串，指定要求中不應包含任何其他參數。 參數會使用下列格式指定為查詢字串片段： `"param1=value1&param2=value2&param3=value3"` 等等。 **注意：**  在設定檔中，必須使用實體參考來指定查詢字串中的 ' & "字元 `&` 。|  
|signOutReply|指定由安全性權杖服務將用戶端重新導向至的 URL (STS) 在被動登出期間透過 WS-同盟通訊協定。 設定 WS-同盟登出要求的 wreply 參數。 選擇性。 預設值為空字串，指定要求中不應包含任何其他參數。|  
  
### <a name="child-elements"></a>子元素  

 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 的設定。|  
  
## <a name="remarks"></a>備註  

 您可以使用 `<wsFederation>` 元素來設定預設的 WS-同盟參數設定，以及 WSFAM 的預設行為。 在元素下定義的 WS-同盟參數設定會 `<wsFederation>` 設定類別所公開的對等屬性 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 。 針對 WSFAM 發出的每個要求，這些屬性都會保持不變。 您可以為 WSFAM 所公開的事件新增事件處理常式，以在要求處理期間動態變更 WS-同盟參數;例如， <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> 事件。 如需詳細資訊，請參閱類別的檔 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 。  
  
 `<wsFederation>`元素是由 <xref:System.IdentityModel.Services.Configuration.WSFederationElement> 類別表示。 設定物件本身是以 <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> 類別表示。 在 <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> 透過屬性存取的物件上設定單一實例 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ，並提供 WSFAM 的設定。  
  
## <a name="example"></a>範例  

 下列 XML `<wsFederation>` 會顯示指定 WSFAM 設定的元素。  
  
> [!WARNING]
> 在此範例中，WSFAM 不需要使用 HTTPS。 這是因為 `requireHttps` `<wsFederation>` 已設定元素上的屬性 `false` 。 這項設定不建議用於大部分的生產環境，因為這可能會帶來安全性風險。  
  
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
