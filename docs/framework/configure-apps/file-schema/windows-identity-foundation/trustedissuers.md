---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 08cddd19f40f039f86e100cc7ee6a78633502eb2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185557"
---
# \<trustedIssuers>

設定以設定為基礎的簽發者名稱登錄 () 所使用的受信任簽發者憑證清單 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|將憑證加入至受信任簽發者的集合。 憑證是以 `thumbprint` 屬性指定。 這個屬性是必要的，而且應該包含憑證指紋的 asn.1 編碼形式。 `name`屬性是選擇性的，可以用來指定憑證的易記名稱。|  
|`<clear>`|清除受信任簽發者集合中的所有憑證。|  
|`<remove thumbprint=xs:string>`|從受信任簽發者的集合中移除憑證。 憑證是以 `thumbprint` 屬性指定。 這是必要屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|設定簽發者名稱登錄。 **重要事項：**  專案的 `type` 屬性 `<issuerNameRegistry>` 必須參考 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別， `<trustedIssuers>` 元素才能有效。|  
  
## <a name="remarks"></a>備註  

 Windows Identity Foundation (WIF) 提供類別的單一實作為類別 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。 設定簽發者名稱登錄會維護從設定載入的受信任簽發者清單。 此清單會將每個簽發者名稱與驗證簽發者所產生之權杖簽章所需的 x.509 憑證產生關聯。 受信任的簽發者憑證清單是在元素下指定 `<trustedIssuers>` 。 清單中的每個專案會將助記者名稱與 x.509 憑證產生關聯，以驗證該簽發者所產生之權杖的簽章。 受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定，並使用元素加入集合 `<add>` 。 您可以使用和元素，從清單中清除或移除簽發者 (憑證) `<clear>` `<remove>` 。  
  
 專案的 `type` 屬性 `<issuerNameRegistry>` 必須參考 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別， `<trustedIssuers>` 元素才能有效。  
  
## <a name="example"></a>範例  

 下列 XML 說明如何指定以設定為基礎的簽發者名稱登錄。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
