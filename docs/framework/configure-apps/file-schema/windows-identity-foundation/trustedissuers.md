---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: c390cecc265b27dfa8d9d0a892f5930c982f7054
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261003"
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
設定使用的組態為基礎的簽發者名稱登錄的受信任簽發者憑證的清單 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<Securitytokenhandlerconfiguration> >  
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
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|將憑證加入至受信任簽發者的集合。 使用指定的憑證`thumbprint`屬性。 這個屬性是必要的而且應該包含憑證指紋的 ASN.1 編碼形式。 `name`屬性是選擇性的而且可用來指定憑證的易記名稱。|  
|`<clear>`|清除集合中的受信任簽發者的所有憑證。|  
|`<remove thumbprint=xs:string>`|從受信任簽發者的集合中移除憑證。 使用指定的憑證`thumbprint`屬性。 這是必要屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|設定簽發者名稱登錄。 **重要事項︰** `type`屬性`<issuerNameRegistry>`項目必須參考<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。|  
  
## <a name="remarks"></a>備註  
 Windows Identity Foundation (WIF) 提供的單一實作<xref:System.IdentityModel.Tokens.IssuerNameRegistry>根據預設，類別<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。 設定簽發者名稱登錄會維護從組態載入信任的簽發者清單。 清單會將每個簽發者名稱關聯才能驗證簽發者所產生之權杖的簽章的 X.509 憑證。 受信任的簽發者憑證的清單下，會指定`<trustedIssuers>`項目。 在清單中的每個項目關聯，才能驗證該簽發者所產生之權杖的簽章的 X.509 憑證的助憶鍵簽發者名稱。 受信任的憑證使用 ASN.1 編碼的憑證指紋的格式指定，而且會藉由新增集合`<add>`項目。 您可以清除，或從清單中移除簽發者 （憑證），使用`<clear>`和`<remove>`項目。  
  
 `type`的屬性`<issuerNameRegistry>`元素必須參照<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。  
  
## <a name="example"></a>範例  
 下列 XML 程式碼顯示如何指定組態的簽發者名稱登錄。  
  
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
