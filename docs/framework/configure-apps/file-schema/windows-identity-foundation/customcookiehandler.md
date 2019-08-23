---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942789"
---
# <a name="customcookiehandler"></a>\<customCookieHandler>
設定自訂 cookie 處理常式類型。 只有當`mode` `<cookieHandler>`元素的屬性是 "Custom" 時, 才會出現此元素。 自訂類型必須衍生<xref:System.IdentityModel.Services.CookieHandler>自類別。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
\<customCookieHandler>  
  
## <a name="syntax"></a>語法  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|型別|指定衍生<xref:System.IdentityModel.Services.CookieHandler>自類別的自訂類型。 如需如何指定屬性的`type`詳細資訊, 請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<xref:System.IdentityModel.Services.CookieHandler> 設定用來讀取<xref:System.IdentityModel.Services.SessionAuthenticationModule>和寫入 cookie 的。|  
  
## <a name="remarks"></a>備註  
 當您藉由將專案的`mode`屬性`<cookieHandler>`設定為 "custom" 來指定自訂 cookie 處理常式時, 您必須包含參考 cookie 處理常式類型的`<customCookieHandler>`子項目, 以指定自訂 cookie 處理常式的類型。 當屬性設定為 "分塊" `mode`或 "Default" 時, 無法指定此元素。 自訂 cookie 處理常式必須衍生<xref:System.IdentityModel.Services.CookieHandler>自類別。  
  
 `<customCookieHandler>`元素是<xref:System.IdentityModel.Configuration.CustomTypeElement>由類別表示。  
  
## <a name="example"></a>範例  
 下列範例會將 SAM 設定為使用類型`MyNamespace.MyCustomCookieHandler`的自訂 cookie 處理常式。  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.CookieHandler>
