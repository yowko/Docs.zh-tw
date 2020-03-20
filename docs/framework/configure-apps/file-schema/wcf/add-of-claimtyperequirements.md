---
title: <add> 的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153083"
---
# <a name="add-of-claimtyperequirements"></a>\<添加\<索賠類型需求>>
指定必須在聯合認證中出現的必要及選擇性宣告型別。 例如，服務說明傳入認證必須處理特定的一組宣告型別。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<自訂綁定>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<已發出權杖參數>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<索賠類型要求>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|claimType|定義宣告型別的 URI。 例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。 宣告型別是信用卡的 URI。|  
|isOptional|布林值，指定此宣告是否為選擇性宣告。 若此為必要宣告，請將此屬性設為 `false`。<br /><br /> 若服務要求某些資訊，但並非必要，便可使用此屬性。 例如，如果要求使用者輸入其名字、姓氏和位址，但確定該電話號碼是可選的。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<索賠類型要求>](claimtyperequirements-element.md)|指定必要宣告型別的集合。<br /><br /> 在聯合案例中，服務會聲明對傳入認證的需求。 例如，傳入認證必須處理特定的一組宣告型別。 這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。|  
  
## <a name="remarks"></a>備註  
 在聯合案例中，服務會聲明對傳入認證的需求。 例如，傳入認證必須處理特定的一組宣告型別。 這項需求會顯示在安全性原則中。 當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。  
  
## <a name="example"></a>範例  
 下列組態會將兩項宣告型別需求新增至安全性繫結程序。  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<索賠類型要求>](claimtyperequirements-element.md)
- [綁定](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<自訂綁定>](custombinding.md)
- [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自訂繫結安全性](../../../wcf/samples/custom-binding-security.md)
