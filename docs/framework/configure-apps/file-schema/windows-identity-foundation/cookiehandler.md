---
title: "&lt;cookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;cookieHandler&gt;
設定<xref:System.IdentityModel.Services.CookieHandler> ， <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) 用來讀取和寫入 cookie。  
  
## 語法  
  
```  
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
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|指定的主檔名的寫入任何 cookie。  預設為"FedAuth"。|  
|path|指定寫入任何 cookie 的路徑值。  預設為"HttpRuntime.AppDomainAppVirtualPath"。|  
|mode|其中<xref:System.IdentityModel.Services.CookieHandlerMode>值，指定 cookie SAM 所使用的處理常式的種類。  可能會使用下列值：<br /><br /> -   "預設"—"區塊 」 相同。<br />-   「 區塊 」 — 使用執行個體的<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別。  這個 cookie 處理常式可確保個別的 cookie 不能超過設定的最大大小。  這樣的其優勢區塊可能會 「 處理 」 邏輯剩一塊餅乾成數個 cookie 在線上。<br />-   「 自訂 」 — 會使用衍生自的自訂類別的執行個體<xref:System.IdentityModel.Services.CookieHandler>。  在衍生的類別參考的`<customCookieHandler>`子項目。<br /><br /> 預設為 「 預設 」。|  
|persistentSessionLifetime|指定永續性的工作階段存留的期。  如果是零，會永遠會使用暫時的工作階段。  預設值為"0:0:0"，其指定暫時的工作階段。  最大值為"365:0:0"，其指定為 365 天的工作階段。  根據下列的限制，應該指定值： `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`、 其中最左邊的值會指定天數、 中間的值 \(如果有的話\) 指定時數，而最右邊的值 \(如果有的話\) 指定分鐘。|  
|requireSsl|指定是否為寫入任何 cookie，就會發出 「 保全 」 旗標。  如果這個值設定，登入工作階段 cookie 只能使用在 HTTPS 上。  預設為"true"。|  
|hideFromScript|控制是否為寫入任何 cookie，就會發出 「 你 」 旗標。  某些 web 瀏覽器接受這個旗標，保留用戶端指令碼無法存取的 cookie 值。  預設為"true"。|  
|domain|寫入任何 cookie 網域值。  預設值是""。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<chunkedCookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。  這個項目可能只會顯示如果`mode`屬性的`<cookieHandler>`項目為 「 預設 」 或 「 區塊 」。|  
|[\<customCookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|設定自訂的 cookie 的處理常式型別。  此元素必須存在如果`mode`屬性的`<cookieHandler>`項目是 \[自訂\]。  它就不能有任何其他值的`mode`屬性。  自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。|  
  
## 備註  
 <xref:System.IdentityModel.Services.CookieHandler>負責讀取及寫入未經處理的 cookie，在 HTTP 通訊協定層級。  您可以設定其中一個<xref:System.IdentityModel.Services.ChunkedCookieHandler>或自訂的 cookie 的處理常式會衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。  
  
 若要設定處理常式區塊的 cookie，請設定 mode 屬性來 「 區塊 」 或 \[預設\]。  預設區塊大小是 2000 位元組，但您可能會以選擇性地指定不同的區塊大小，藉以`<chunkedCookieHandler>`子項目。  
  
 若要設定自訂的 cookie 的處理常式，請設定 mode 屬性來 「 自訂 」。  您也必須指定`<customCookieHandler>`所參考的自訂處理常式型別子項目。  
  
 `<cookieHandler>`項目會以<xref:System.IdentityModel.Services.CookieHandlerElement>類別。  組態中指定了該 cookie 處理常式位於<xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A>屬性的<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件上設定<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>屬性。  
  
## 範例  
 下列 XML 顯示`<cookieHandler>`項目。  在這個範例中，因為`mode`屬性沒有指定，則將使用預設的 cookie 處理常式的 SAM。  這是執行個體的<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別。  因為`<chunkedCookieHandler>`子項目沒有指定，則將使用預設的區塊大小。  無法需要 HTTPS，因為`requireSsl`屬性設定`false`。  
  
> [!WARNING]
>  在這個範例中，並不需要 HTTPS 寫入工作階段 cookie。  這是因為`requireSsl`在`<cookieHandler>`元素設為`false`。  這項設定不會建議大多數實際執行環境，因為它不會帶來安全性風險。  
  
```  
<cookieHandler requireSsl="false" />  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Services.CookieHandler>   
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>   
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>