---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
設定使用的組態為基礎的簽發者名稱登錄的受信任簽發者憑證的清單 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|將憑證加入至受信任簽發者的集合。 使用指定的憑證`thumbprint`屬性。 這個屬性是必要，應該包含憑證指紋的 ASN.1 編碼格式。 `name`屬性是選擇性的而且可用來指定憑證的易記名稱。|  
|`<clear>`|清除集合中的受信任簽發者的所有憑證。|  
|`<remove thumbprint=xs:string>`|從受信任簽發者的集合中移除憑證。 使用指定的憑證`thumbprint`屬性。 這是必要屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
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
