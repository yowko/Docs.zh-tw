---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 9991430f09cb6a63d0a3cdde24a4ff03d3dd746d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165048"
---
# \<issuerNameRegistry>

設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a>Syntax  
  
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

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|衍生自類別的型別 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 如需如何指定自訂的詳細資訊 `type` ，請參閱 [自訂類型參考]。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|當屬性指定以設定為 `type` 基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別) 時， [\<trustedIssuers>](trustedissuers.md) 必須指定元素。 專案 [\<trustedIssuers>](trustedissuers.md) 可以將 `<add>` 、 `<clear>` 或元素做 `<remove>` 為子項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  

 所有簽發者權杖都會使用簽發者名稱登錄進行驗證。 這是衍生自類別的物件 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 簽發者名稱登錄用來將助憶鍵名稱與所需的密碼編譯內容產生關聯，以驗證對應的簽發者所產生的權杖簽章。 簽發者名稱登錄會維護信賴憑證者 (RP) 應用程式信任的簽發者清單。 簽發者名稱登錄的類型是使用屬性來指定 `type` 。 `<issuerNameRegistry>`元素可以有一或多個子專案，以提供指定類型的設定。 您可以藉由覆寫方法，提供處理這些子項目的邏輯 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> 。  
  
 WIF 會提供一種現成的單一簽發者名稱登錄類型，也就是 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別。 此類別會使用設定中指定的一組受信任的簽發者憑證。 它需要子設定元素，在此專案中， `<trustedIssuers>` 會設定信任的簽發者憑證集合。 受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定，並使用、或專案在集合中加入或 `<add>` 移除 `<clear>` `<remove>` 。  
  
 `<issuerNameRegistry>`元素是由 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> 類別表示。  
  
> [!NOTE]
> 將 `<issuerNameRegistry>` 元素指定為專案的子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。 元素上的設定會覆 `<securityTokenHandlerConfiguration>` 寫元素上的設定 `<identityConfiguration>` 。  
  
## <a name="example"></a>範例  

 下列 XML 說明如何指定以設定為基礎的簽發者名稱登錄。  
  
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
