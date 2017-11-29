---
title: '&lt;customCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: df95e8d47d6a19e4fd488fa14bc771bc2c2b56b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcustomcookiehandlergt"></a>&lt;customCookieHandler&gt;
設定自訂的 cookie 處理常式型別。 這個項目可能只會存在於如果`mode`屬性`<cookieHandler>`項目是 「 自訂 」。 自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<Requiressl >  
\<customCookieHandler >  
  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|指定自訂型別衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。 如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<Requiressl >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|設定<xref:System.IdentityModel.Services.CookieHandler>，<xref:System.IdentityModel.Services.SessionAuthenticationModule>用來讀取和寫入 cookie。|  
  
## <a name="remarks"></a>備註  
 當您指定自訂 cookie 處理常式設定`mode`屬性`<cookieHandler>`項目為"Custom"，您必須指定自訂 cookie 處理常式的類型包括`<customCookieHandler>`參考 cookie 處理常式類型的子元素。 此元素不能指定何時`mode`屬性設為"Chunked"或"Default"。 自訂的 cookie 處理常式必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。  
  
 `<customCookieHandler>`項目由<xref:System.IdentityModel.Configuration.CustomTypeElement>類別。  
  
## <a name="example"></a>範例  
 下列範例會設定使用自訂的 cookie 處理常式類型的 SAM `MyNamespace.MyCustomCookieHandler`。  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Services.CookieHandler>
