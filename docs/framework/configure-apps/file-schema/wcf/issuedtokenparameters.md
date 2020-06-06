---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397947"
---
# \<issuedTokenParameters>
指定在聯合安全性案例中發行之安全性權杖的參數。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|defaultMessageSecurityVersion|指定繫結必須支援的安全性規格版本 (WS-Security、WS-Trust、WS-Secure Conversation 和 WS-Security Policy)。 這個值的型別為 <xref:System.ServiceModel.MessageSecurityVersion>。|  
|inclusionMode|指定權杖內含需求。 此屬性的型別為 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>。|  
|keySize|指定權杖金鑰大小的整數。 預設值為 256。|  
|keyType|指定金鑰型別之 <xref:System.IdentityModel.Tokens.SecurityKeyType> 的有效值。 預設值為 `SymmetricKey`。|  
|tokenType|指定權杖型別的字串。 預設值為「http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML」。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|指定額外要求參數的組態項目集合。|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|指定必要宣告型別的集合。<br /><br /> 在聯合案例中，服務會聲明對傳入認證的需求。 例如，傳入認證必須處理特定的一組宣告型別。 這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|指定發行目前權杖之端點的組態項目。|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|指定權杖簽發者中繼資料之端點位址的組態項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|指定用於啟始安全對話服務的預設值。|  
|[\<security>](security-of-custombinding.md)|指定自訂繫結的安全性選項。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自訂繫結安全性](../../../wcf/samples/custom-binding-security.md)
- [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)
- [聯合與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [自訂繫結的安全性功能](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [聯合與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
