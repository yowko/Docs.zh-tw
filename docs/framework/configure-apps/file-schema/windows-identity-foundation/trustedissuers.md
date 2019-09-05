---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251750"
---
# <a name="trustedissuers"></a>\<trustedIssuers>
設定以設定為基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>) 所使用的受信任簽發者憑證清單。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerNameRegistry >** ](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<s >**  
  
## <a name="syntax"></a>語法  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 None  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|將憑證新增至受信任簽發者的集合。 憑證是以`thumbprint`屬性指定。 此為必要屬性, 且應包含憑證指紋的 asn.1 編碼形式。 屬性`name`是選擇性的, 可以用來指定憑證的易記名稱。|  
|`<clear>`|清除受信任簽發者集合中的所有憑證。|  
|`<remove thumbprint=xs:string>`|從受信任簽發者的集合中移除憑證。 憑證是以`thumbprint`屬性指定。 這是必要屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|設定簽發者名稱登錄。 **重要：** `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>元素的`type`屬性必須`<trustedIssuers>`參考類別, 專案才會是有效的。|  
  
## <a name="remarks"></a>備註  
 Windows Identity Foundation (WIF) 提供<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>的單一實作為類別。 設定簽發者名稱登錄會維護從設定載入之受信任簽發者的清單。 此清單會將每個簽發者名稱與 x.509 憑證建立關聯, 以驗證簽發者所產生之權杖的簽章。 受信任簽發者憑證的清單是在`<trustedIssuers>`元素下指定。 清單中的每個元素會將助憶鍵簽發者名稱與 x.509 憑證產生關聯, 以驗證該簽發者所產生之權杖的簽章。 受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定, 並使用`<add>`元素來新增集合。 您可以使用`<clear>`和`<remove>`元素, 從清單中清除或移除簽發者 (憑證)。  
  
 `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>元素的`type`屬性必須`<trustedIssuers>`參考類別, 專案才會是有效的。  
  
## <a name="example"></a>範例  
 下列 XML 顯示如何指定以設定為基礎的簽發者名稱登錄。  
  
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
