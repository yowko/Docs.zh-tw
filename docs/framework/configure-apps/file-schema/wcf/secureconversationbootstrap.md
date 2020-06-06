---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: b3187cb51b6fd32797c9ad401c704d5f16c6f7e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399916"
---
# \<secureConversationBootstrap>
指定用於啟始安全對話服務的預設值。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationBootstrap>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
                             authenticationMode="AuthenticationMode"
                             defaultAlgorithmSuite="SecurityAlgorithmSuite"
                             includeTimestamp="Boolean"
                             requireDerivedKeys="Boolean"
                             keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
                             messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
                             messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
                             requireDerivedKeys="Boolean"
                             requireSecurityContextCancellation="Boolean"
                             requireSignatureConfirmation="Boolean"
                             securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
                             includeTimestamp="Boolean" />
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|選擇性。 布林值，指定序列化權杖是否可以用在回覆上。 預設值是 `false`。 使用雙重繫結時，設定將預設為 `true`，並忽略所做的任何設定。|  
|`authenticationMode`|指定啟動器和回應程式之間使用的 SOAP 驗證模式。<br /><br /> 預設為 sspiNegotiated。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.Configuration.AuthenticationMode>。|  
|`defaultAlgorithmSuite`|安全性演算法套件會定義各種不同的演算法，例如標準化、摘要式、KeyWrap、簽章、加密和 KeyDerivation 演算法。 每個安全性演算法套件會定義這些不同參數的值。 訊息安全性是使用這些演算法達成的。<br /><br /> 當使用另一個平台，且該平台選擇一組和預設值不同的演算法時，則使用這個屬性。 在修改這個設定時，您應該了解相關演算法的優點和缺點。 此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。 預設值為 `Basic256`。|  
|`includeTimestamp`|布林值，指定每個訊息是否包含時間戳記。 預設值為 `true`。|  
|`keyEntropyMode`|指定保護訊息安全之金鑰的計算方法。 金鑰可僅根據用戶端金鑰資料、僅根據服務金鑰資料，或兩者的組合。 有效值為：<br /><br /> -ClientEntropy：工作階段金鑰是以用戶端提供的金鑰內容為基礎。<br />-ServerEntropy：工作階段金鑰是根據服務提供的金鑰材料。<br />-CombinedEntropy：工作階段金鑰是以用戶端和服務提供的金鑰資料為基礎。<br /><br /> 預設為 CombinedEntropy。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。|  
|`messageProtectionOrder`|設定順序，訊息層級安全性演算法會以這個順序套用至訊息。 有效值如下：<br /><br /> -SignBeforeEncrypt：先簽署，然後加密。<br />-SignBeforeEncryptAndEncryptSignature：簽署、加密和加密簽章。<br />-EncryptBeforeSign：先加密，然後簽署。<br /><br /> 使用相互憑證搭配 WS-Security 1.1 時，SignBeforeEncryptAndEncryptSignature 是預設值。  SignBeforeEncrypt 是 WS-Security 1.0 的預設值。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.Security.MessageProtectionOrder>。|  
|`messageSecurityVersion`|設定使用的 WS-Security 版本。 有效值如下：<br /><br /> - WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> 預設為 WSSecurityXXX2005。 此屬性的型別為 <xref:System.ServiceModel.MessageSecurityVersion>。|  
|`requireDerivedKeys`|布林值，指定是否可以從原始的證明金鑰衍生金鑰。 預設值為 `true`。|  
|`requireSecurityContextCancellation`|布林值，指定當不再需要安全性內容時是否應取消及終止它。 預設值為 `true`。|  
|`requireSignatureConfirmation`|布林值，指定是否啟用 WS-Security 簽章確認。 設定為 `true` 時，回應程式會確認訊息簽章。 預設值為 `false`。<br /><br /> 簽章確認是用來確認服務的回應完全感知要求。|  
|`securityHeaderLayout`|指定安全性標頭中的項目順序。 有效值為：<br /><br /> Strict. 會根據「使用前宣告」的一般原則，將項目加入至安全性標頭中。<br />嚴格. 會依據符合 WSS: SOAP 訊息安全性的任何順序，將項目加入至安全性標頭中。<br />- LaxWithTimestampFirst. 會依據符合 WSS: SOAP 訊息安全性的任何順序，將項目加入至安全性標頭中，例外的是安全性標頭中的第一個項目必須是 wsse:Timestamp 項目。<br />- LaxWithTimestampLast. 會依據符合 WSS: SOAP 訊息安全性的任何順序，將項目加入至安全性標頭中，例外的是安全性標頭中的最後一個項目必須是 wsse:Timestamp 項目。<br /><br /> 預設為 Strict。<br /><br /> 此項目的型別為 <xref:System.ServiceModel.Channels.SecurityHeaderLayout>。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|指定目前發行的權杖。 此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>。|  
|[\<localClientSettings>](localclientsettings-element.md)|指定此繫結之本機用戶端的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>。|  
|[\<localServiceSettings>](localservicesettings-element.md)|指定此繫結之本機服務的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|指定自訂繫結的安全性選項。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自訂繫結安全性](../../../wcf/samples/custom-binding-security.md)
