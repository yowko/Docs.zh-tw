---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152576"
---
# \<serviceTokenResolver>
註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。 服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
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
|type|指定服務權杖解析程式的類型。 可能是 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 類型或衍生自類別的類型 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。 如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂類型參考]。 必要。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 服務權杖解析程式可以用來解析傳入權杖和訊息上的加密權杖。 它是用來抓取用來解密傳入權杖的金鑰。 您必須指定 `type` 屬性。 指定的型別可以是 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 或衍生自類別的自訂型別 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。  
  
 某些權杖處理常式可讓您在設定中指定服務權杖解析程式設定。 個別權杖處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。  
  
> [!NOTE]
> 將專案指定為專案的 `<serviceTokenResolver>` 子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。 元素上的設定會覆寫專案上的專案 `<securityTokenHandlerConfiguration>` `<identityConfiguration>` 。  
  
## <a name="example"></a>範例  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
