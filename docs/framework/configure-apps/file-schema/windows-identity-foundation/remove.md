---
title: '&lt;remove&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0c8fd5a9a5c4d6007ff0f67132b97b0aa5d98256
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltremovegt"></a>&lt;remove&gt;
從權杖處理常式集合中移除指定的安全性權杖處理常式。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<移除 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|要移除的語彙基元處理常式的 CLR 型別名稱。 如需有關如何指定`type`屬性，請參閱[自訂型別參考](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。 必要項。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定註冊的端點的安全性權杖處理常式的集合。|  
  
## <a name="example"></a>範例  
 下列 XML 程式碼將示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設工作階段權杖處理常式項目。 XML 取自`ClaimsAwareWebFarm`範例。  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
