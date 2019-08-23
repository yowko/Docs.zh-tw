---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923101"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver>
註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。 服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<serviceTokenResolver>  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|型別|指定服務權杖解析程式的類型。 <xref:System.IdentityModel.Selectors.SecurityTokenResolver>可能是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類型或衍生自類別的類型。 如需如何指定屬性的`type`詳細資訊, 請參閱 [自訂類型參考]。 必要項。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 服務權杖解析程式可以用來解析傳入權杖和訊息上的加密權杖。 它是用來抓取用來解密傳入權杖的金鑰。 您必須指定`type`屬性。 指定的型別可以是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>或衍生<xref:System.IdentityModel.Selectors.SecurityTokenResolver>自類別的自訂型別。  
  
 某些權杖處理常式可讓您在設定中指定服務權杖解析程式設定。 個別權杖處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。  
  
> [!NOTE]
> 將專案指定為[ \<identityConfiguration >](identityconfiguration.md)專案的子項目已被取代, 但仍支援回溯相容性。 `<serviceTokenResolver>` 元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。  
  
## <a name="example"></a>範例  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
