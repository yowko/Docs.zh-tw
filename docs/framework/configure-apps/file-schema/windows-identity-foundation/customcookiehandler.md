---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: a8ee23ac6facaea18cd7f1820616cb9b16afa336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189847"
---
# \<customCookieHandler>

設定自訂的 cookie 處理常式類型。 如果 `mode` 元素的屬性 `<cookieHandler>` 是 "Custom"，則這個元素可能只有存在。 自訂類型必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|指定衍生自類別的自訂型別 <xref:System.IdentityModel.Services.CookieHandler> 。 如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考](../windows-workflow-foundation/index.md)。|  
  
### <a name="child-elements"></a>子元素  

 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 用來讀取和寫入 cookie 的。|  
  
## <a name="remarks"></a>備註  

 當您將專案的屬性設定為 [自訂] 來指定自訂的 cookie 處理常式時 `mode` `<cookieHandler>` ，您必須加入 `<customCookieHandler>` 參考 cookie 處理常式類型的子專案，以指定自訂 cookie 處理常式的類型。 當屬性設定為「區塊」或「預設」時，無法指定此元素 `mode` 。 自訂 cookie 處理常式必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。  
  
 `<customCookieHandler>`元素是由 <xref:System.IdentityModel.Configuration.CustomTypeElement> 類別表示。  
  
## <a name="example"></a>範例  

 下列範例會將 SAM 設定為使用類型的自訂 cookie 處理常式 `MyNamespace.MyCustomCookieHandler` 。  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.CookieHandler>
