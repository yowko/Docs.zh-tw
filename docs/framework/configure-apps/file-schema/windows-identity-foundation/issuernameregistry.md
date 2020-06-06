---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251958"
---
# \<issuerNameRegistry>
設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|衍生自類別的類型 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 如需如何指定自訂的詳細資訊 `type` ，請參閱 [自訂類型參考]。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|當屬性指定以設定為 `type` 基礎的簽發者名稱登錄（ <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別）時， [\<trustedIssuers>](trustedissuers.md) 必須指定元素。 [\<trustedIssuers>](trustedissuers.md)元素可以接受 `<add>` 、或專案 `<clear>` `<remove>` 做為子專案。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 所有簽發者權杖都會使用簽發者名稱登錄來進行驗證。 這是衍生自類別的物件 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。 簽發者名稱登錄是用來建立助憶鍵名稱與密碼編譯資料的關聯性，以驗證對應簽發者所產生之權杖的簽章。 簽發者名稱登錄會維護信賴憑證者（RP）應用程式所信任的 issuer 清單。 簽發者名稱登錄的類型是使用屬性所指定 `type` 。 `<issuerNameRegistry>`元素可以有一個或多個子專案，以提供指定之類型的設定。 您可以藉由覆寫方法來提供處理這些子專案的邏輯 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> 。  
  
 WIF 提供一個現成的簽發者名稱登錄類型，也就是 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別。 此類別會使用設定中指定的一組受信任的簽發者憑證。 它需要子設定元素，在此專案 `<trustedIssuers>` 下，會在此專案中設定受信任簽發者憑證的集合。 受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定，並使用、或專案從集合中加入或 `<add>` 移除 `<clear>` `<remove>` 。  
  
 `<issuerNameRegistry>`元素是由 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> 類別表示。  
  
> [!NOTE]
> 將專案指定為專案的 `<issuerNameRegistry>` 子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。 元素上的設定會覆寫專案上的專案 `<securityTokenHandlerConfiguration>` `<identityConfiguration>` 。  
  
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
