---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f9daea7d6b78e2f6790050b35dde62db6058c60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
設定使用的組態為基礎的簽發者名稱登錄的受信任簽發者憑證的清單 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
\<trustedIssuers >  
  
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
 無  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|將憑證加入至受信任簽發者的集合。 使用指定的憑證`thumbprint`屬性。 這個屬性是必要，應該包含憑證指紋的 ASN.1 編碼格式。 `name`屬性是選擇性的而且可用來指定憑證的易記名稱。|  
|`<clear>`|清除集合中的受信任簽發者的所有憑證。|  
|`<remove thumbprint=xs:string>`|從受信任簽發者的集合中移除憑證。 使用指定的憑證`thumbprint`屬性。 這是必要屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|設定簽發者名稱登錄。 **重要事項：** `type`屬性`<issuerNameRegistry>`元素必須參考<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。|  
  
## <a name="remarks"></a>備註  
 Windows Identity Foundation (WIF) 提供的單一實作<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別，根據預設，<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。 設定簽發者名稱登錄會維護從組態載入的受信任簽發者清單。 清單會將每個簽發者名稱關聯才能驗證權杖簽發者所產生的簽章的 X.509 憑證。 受信任簽發者憑證的清單下，會指定`<trustedIssuers>`項目。 在清單中的每個項目將與需要驗證的語彙基元的簽發者所產生的簽章的 X.509 憑證關聯的助憶鍵簽發者名稱。 受信任的憑證會指定使用 ASN.1 編碼的憑證指紋的格式，而且會加入集合，使用`<add>`項目。 您可以清除，或從清單中移除簽發者 （憑證），使用`<clear>`和`<remove>`項目。  
  
 `type`屬性`<issuerNameRegistry>`元素必須參考<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。  
  
## <a name="example"></a>範例  
 下列 XML 會示範如何指定基礎設定簽發者名稱登錄。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
