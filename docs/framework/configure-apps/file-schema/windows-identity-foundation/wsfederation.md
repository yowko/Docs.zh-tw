---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152459"
---
# <a name="wsfederation"></a>\<ws聯邦>
為<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 提供配置。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型.服務>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<聯合配置>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws聯邦>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|authenticationType|指定驗證類型的 URI。 設置 WS-聯合登錄請求 wauth 參數。 選擇性。 預設值為空字串，它指定請求中不包括 wauth 參數。|  
|新鮮|所需的驗證要求最長使用期限，以分鐘為單位。 設定 WS-Federation 登入要求 wfresh 參數。 選擇性。 預設值為 0。 選擇性。 **警告：** 在下一個版本 .NET Framework 4.5`freshness`中，屬性將的類型`xs:string`，其預設值將為`null`。|  
|首頁王國|用於身份驗證的標識提供程式 （IdP） 的主要領域。 設定 WS-Federation 登入要求 whr 參數。 選擇性。 預設值為空字串，它指定請求中不包括 whr 參數。|  
|簽發者|預期權杖頒發器的 URI。 設置 WS-聯合登錄請求和需要登出請求的基本 URL。|  
|持久性 CookieOn 被動重定向|指定是否在身份驗證時發出持久性 Cookie。 選擇性。 預設值為"false"，未發出 Cookie。|  
|被動重定向啟用|指定是否啟用 WSFAM 自動將未經授權的請求重定向到 STS。 選擇性。 預設值為"true"，未經授權的請求將自動重定向。|  
|原則|指定要在登錄請求上使用的相關策略的位置的 URL。 預設值是空字串。 設定 WS-Federation 登入要求 wp 參數。 選擇性。 預設值為空字串，它指定請求中不包括 wp 參數。|  
|realm|請求域的 URI。 （標識安全權杖服務 （STS） 的依賴方 （RP） 的 URI。佈建要求 wtrealm WS-聯合登錄請求參數。 必要。|  
|答覆|識別信賴憑證者 (RP) 應用程式要用來接收 Security Token Service (STS) 回覆之位址的 URL。 設置 WS-聯合登錄請求 wreply 參數。 選擇性。 預設值為空字串，它指定請求中不包括 wreply 參數。|  
|要求|權杖頒發請求。 設定 WS-Federation 登入要求 wreq 參數。 選擇性。 預設值為空字串，它指定 wreq 參數不包括在請求中。 不包括請求中的 wreq 或 wreqptr 參數意味著 STS 知道要發出哪種權杖。|  
|請求Ptr|URL，指定語彙基元發佈要求的位置。 佈建要求 wreqptr 參數。 選擇性。 預設值為空字串，它指定請求中不包括 wreqptr 參數。 不包括請求中的 wreq 或 wreqptr 參數意味著 STS 知道要發出哪種權杖。|  
|需要 Https|指定與安全權杖服務 （STS） 的通信是否必須使用 HTTPS 協定。 選擇性。 預設值為"true"，必須使用 HTTPS。|  
|resource|用來向 Security Token Service (STS) 識別所存取之資源 (信賴憑證者 (RP)) 的 URI。 選擇性。 設置 WS-聯合登錄請求 wres 參數。 選擇性。 預設值為空字串，它指定請求中不包括 wres 參數。 **注意：wrs**是一個舊參數。 指定要`realm`改用 wtrealm 參數的屬性。|  
|符號在查詢字串|提供擴充點，用於在 WS-聯合登錄請求 URL 中指定應用程式定義的查詢參數。 選擇性。 預設值為空字串，它指定請求中不應包含其他參數。 參數使用以下形式指定為查詢字串片段：`"param1=value1&param2=value2&param3=value3"`等。 **注：** 在設定檔中，必須使用其實體引用指定查詢字串中的"&"字元`&`。|  
|登出查詢字串|提供擴充點，用於在 WS-聯合登錄請求 URL 中指定應用程式定義的查詢參數。 選擇性。 預設值為空字串，它指定請求中不應包含其他參數。 參數使用以下形式指定為查詢字串片段：`"param1=value1&param2=value2&param3=value3"`等。 **注：** 在設定檔中，必須使用其實體引用指定查詢字串中的"&"字元`&`。|  
|符號退出回復|指定在通過 WS-聯合協定進行被動登出期間，安全權杖服務 （STS） 應重定向用戶端的 URL。 在 WS-聯合登出請求上設置 wreply 參數。 選擇性。 預設值為空字串，它指定請求中不應包含其他參數。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<聯合配置>](federationconfiguration.md)|包含配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 和 （SAM）<xref:System.IdentityModel.Services.SessionAuthenticationModule>的設置。|  
  
## <a name="remarks"></a>備註  
 可以使用 該`<wsFederation>`元素為 WSFAM 配置預設 WS-聯合參數設置和預設行為。 在元素集下`<wsFederation>`定義的 WS-聯合參數設置，<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>該屬性公開了等效屬性。 對於 WSFAM 發出的每個請求，這些屬性保持不變。 通過在請求處理期間為 WSFAM 公開的事件添加事件處理常式，可以動態更改 WS-聯合參數;例如，事件<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>。 有關詳細資訊，請參閱<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>類的文檔。  
  
 元素`<wsFederation>`由類<xref:System.IdentityModel.Services.Configuration.WSFederationElement>表示。 設定物件本身由類<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>表示。 在通過<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration><xref:System.IdentityModel.Services.Configuration.FederationConfiguration><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性訪問的物件上設置單個實例，並為 WSFAM 提供配置。  
  
## <a name="example"></a>範例  
 以下 XML 顯示了`<wsFederation>`指定 WSFAM 設置的元素。  
  
> [!WARNING]
> 在此示例中，WSFAM 不需要使用 HTTPS。 這是因為`requireHttps``<wsFederation>`元素上的屬性被設置`false`。 對於大多數生產環境，不建議此設置，因為它可能會帶來安全風險。  
  
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
