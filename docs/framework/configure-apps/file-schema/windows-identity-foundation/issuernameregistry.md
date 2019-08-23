---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942672"
---
# <a name="issuernameregistry"></a>\<issuerNameRegistry>
設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|型別|衍生自<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別的類型。 如需如何指定自訂`type`的詳細資訊, 請參閱 [自訂類型參考]。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|當屬性指定以設定為基礎的簽發者名稱登錄<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (類別) 時, [ \<必須指定 s >](trustedissuers.md)元素。 `type` S > 元素可以接受`<add>`、 `<clear>`或`<remove>`專案做為子專案。 [ \< ](trustedissuers.md)|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 所有簽發者權杖都會使用簽發者名稱登錄來進行驗證。 這是衍生自<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別的物件。 簽發者名稱登錄是用來建立助憶鍵名稱與密碼編譯資料的關聯性, 以驗證對應簽發者所產生之權杖的簽章。 簽發者名稱登錄會維護信賴憑證者 (RP) 應用程式所信任的 issuer 清單。 簽發者名稱登錄的類型是使用`type`屬性所指定。 `<issuerNameRegistry>`元素可以有一個或多個子專案, 以提供指定之類型的設定。 您可以藉由覆寫<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>方法來提供處理這些子專案的邏輯。  
  
 WIF 提供一個現成的簽發者名稱登錄類型, 也就是<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。 此類別會使用設定中指定的一組受信任的簽發者憑證。 它需要子設定元素, `<trustedIssuers>`在此專案下, 會在此專案中設定受信任簽發者憑證的集合。 受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定, 並使用`<add>`、 `<clear>`或`<remove>`專案從集合中加入或移除。  
  
 `<issuerNameRegistry>`元素是<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>由類別表示。  
  
> [!NOTE]
> 將專案指定為[ \<identityConfiguration >](identityconfiguration.md)專案的子項目已被取代, 但仍支援回溯相容性。 `<issuerNameRegistry>` 元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。  
  
## <a name="example"></a>範例  
 下列 XML 顯示如何指定以設定為基礎的簽發者名稱登錄。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
