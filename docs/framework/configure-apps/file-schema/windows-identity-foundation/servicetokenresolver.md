---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152576"
---
# <a name="servicetokenresolver"></a>\<服務權杖解析器>
註冊權杖處理常式集合中處理常式使用的服務權杖解析器。 服務權杖解析器用於解析傳入權杖和消息上的加密權杖。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式配置>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<服務權杖解析器>**  
  
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
|type|指定服務權杖解析器的類型。 派生自<xref:System.IdentityModel.Selectors.SecurityTokenResolver><xref:System.IdentityModel.Selectors.SecurityTokenResolver>類的類型或類型。 有關如何指定屬性的詳細資訊，`type`請參閱 [自訂類型引用]。 必要。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<安全權杖處理常式配置>](securitytokenhandlerconfiguration.md)|為安全權杖處理常式的集合提供配置。|  
  
## <a name="remarks"></a>備註  
 服務權杖解析器可用於解析傳入權杖和消息上的加密權杖。 它用於檢索應用於解密傳入權杖的金鑰。 必須指定該`type`屬性。 指定的類型可以是 或<xref:System.IdentityModel.Selectors.SecurityTokenResolver>派生自類的<xref:System.IdentityModel.Selectors.SecurityTokenResolver>自訂類型。  
  
 某些權杖處理常式允許您在配置中指定服務權杖解析器設置。 各個權杖處理常式上的設置將覆蓋在安全權杖處理常式集合上指定的設置。  
  
> [!NOTE]
> 將`<serviceTokenResolver>`元素指定為[\<標識配置>](identityconfiguration.md)元素的子項目已被棄用，但仍支援向後相容性。 元素上的`<securityTokenHandlerConfiguration>`設置將覆蓋元素上的`<identityConfiguration>`設置。  
  
## <a name="example"></a>範例  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
