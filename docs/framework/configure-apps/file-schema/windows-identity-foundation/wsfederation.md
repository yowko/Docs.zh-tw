---
title: "&lt;wsFederation&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;wsFederation&gt;
提供設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\)。  
  
## 語法  
  
```  
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
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|識別碼|URI，指定將驗證類型。  WS\-同盟登入要求 wauth 參數設定。  選擇項。  預設為空字串，指定在要求中不包含 wauth 參數。|  
|短有效期限|您想要最長使用期限的驗證要求，以分鐘為單位。  WS\-同盟登入要求 wfresh 參數設定。  選擇項。  預設值是零。  選擇項。 **Warning:**  在下一版。NET Framework 4.5， `freshness`屬性即為型別`xs:string` ，其預設值會是`null`。|  
|homeRealm|要用於驗證的身份識別提供者 \(IP\) 的主領域。  WS\-同盟登入要求 whr 參數設定。  選擇項。  預設為空字串，指定 whr 參數不包含在要求中。|  
|issuer|預期的語彙基元發出者 URI。  設定基底 URL 的 WS\-同盟登入要求和教具借出所需的要求。|  
|persistentCookiesOnPassiveRedirects|指定持續性的 cookie 是否會發出驗證。  選擇項。  預設值為"false"，不會發出 cookie。|  
|passiveRedirectEnabled|指定是否啟用 WSFAM 會自動將未經授權的要求重新導向到 STS。  選擇項。  預設值為"true"，未經授權的要求會自動重新導向。|  
|policy|指定的位置相關的原則，若要使用的登入要求的 URL。  預設為空字串。  WS\-同盟登入要求 wp 參數設定。  選擇項。  預設為空字串，指定 wp 參數不包含在要求中。|  
|realm|URI，屬於提出要求的領域。  \(用來識別為安全性權杖服務 \(STS\) 的信賴憑證者 \(RP\) URI\)。要求 wtrealm WS\-同盟登入要求參數設定。  必要項。|  
|回覆|識別要接收其回覆從安全性權杖服務 \(STS\) 信賴憑證者的合作對象 \(RP\) 應用程式想要的地址的 URL。  WS\-同盟登入要求 wreply 參數設定。  選擇項。  預設為空字串，指定在要求中不包含 wreply 參數。|  
|要求|語彙基元發佈要求。  WS\-同盟登入要求 wreq 參數設定。  選擇項。  預設為空字串，指定在要求中不包含 wreq 參數。  不包含在要求中的 \[wreq 或 wreqptr 參數隱含了 STS 知道哪一種來發出權杖。|  
|requestPtr|可指定位置的語彙基元發佈要求的 URL。  要求的 wreqptr 參數設定。  選擇項。  預設為空字串，指定在要求中不包含 wreqptr 參數。  不包含在要求中的 \[wreq 或 wreqptr 參數隱含了 STS 知道哪一種來發出權杖。|  
|requireHttps|指定是否與安全性權杖服務 \(STS\) 通訊必須使用 HTTPS 通訊協定。  選擇項。  預設值為"true"，必須使用 HTTPS。|  
|Resource \- 資源|URI，識別所存取的資源信賴憑證者 \(RP\)，為安全性權杖服務 \(STS\)。  選擇項。  WS\-同盟登入要求 wres 參數設定。  選擇項。  預設為空字串，指定在要求中不包含 wres 參數。 **Note:**  wres 是傳統的參數。  指定`realm`改為使用 wtrealm 參數的屬性。|  
|signInQueryString|提供的擴充點的 WS\-同盟登入要求 URL 中指定應用程式所定義的查詢參數。  選擇項。  預設為空字串，指定無其他參數應包含在要求中。  參數會指定為使用下列形式的查詢字串片段： `“param1=value1&param2=value2&param3=value3”` ，以此類推。 **Note:**  在組態檔中 ' &"查詢字串中的字元必須使用其實體參考，來指定`&`。|  
|signOutQueryString|提供的擴充點的 WS\-同盟登入要求 URL 中指定應用程式所定義的查詢參數。  選擇項。  預設為空字串，指定無其他參數應包含在要求中。  參數會指定為使用下列形式的查詢字串片段： `“param1=value1&param2=value2&param3=value3”` ，以此類推。 **Note:**  在組態檔中 ' &"查詢字串中的字元必須使用其實體參考，來指定`&`。|  
|signOutReply|在重新導向的 URL 用戶端應該是由安全性權杖服務 \(STS\) 時指定被動教具借出透過 WS\-同盟通訊協定。  將 wreply 參數設定的 WS\-同盟教具借出要求。  選擇項。  預設為空字串，指定無其他參數應包含在要求中。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。|  
  
## 備註  
 您可以使用`<wsFederation>`元素來設定為 WSFAM 的 WS\-同盟參數的預設設定，以及預設的行為。  WS\-同盟參數設定定義在`<wsFederation>`項目集合對等的屬性所公開的<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>類別。  這些屬性會維持相同的每個由 WSFAM 所發出的要求。  您可以藉由新增 WSFAM ； 所公開的事件的事件處理常式處理要求期間以動態方式變更 WS\-同盟參數 例如， <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>事件。  如需詳細資訊，請參閱 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> 類別的文件。  
  
 `<wsFederation>`項目會以<xref:System.IdentityModel.Services.Configuration.WSFederationElement>類別。  組態物件本身由<xref:System.IdentityModel.Services.Configuration.WSFederationConfiguration>類別。  會有一個<xref:System.IdentityModel.Services.Configuration.WSFederationConfiguration>執行個體上設定<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件，便會透過<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>屬性，並提供 WSFAM 的設定。  
  
## 範例  
 下列 XML 顯示`<wsFederation>` WSFAM 的設定值的指定項目。  
  
> [!WARNING]
>  在這個範例中，WSFAM 不是需要使用 HTTPS。  這是因為`requireHttps`在`<wsFederation>`項目設定`false`。  這項設定不會建議大多數實際執行環境，因為它不會帶來安全性風險。  
  
```  
<wsFederation passiveRedirectEnabled="true"   
  issuer="http://localhost:15839/wsFederationSTS/Issue"   
  realm="http://localhost:50969/"   
  reply="http://localhost:50969/"   
  requireHttps="false"   
  signOutReply="http://localhost:50969/SignedOutPage.html"   
  signOutQueryString="Param1=value2&Param2=value2"   
  persistentCookiesOnPassiveRedirects="true" />  
  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>