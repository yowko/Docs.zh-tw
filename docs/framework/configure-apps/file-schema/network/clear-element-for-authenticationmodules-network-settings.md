---
title: authenticationModules 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: 12ac146926103b40073d34f48895b0645c8a8ed2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659471"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a>\<清除 Authenticationmodules 專案的 > 元素 (網路設定)
清除應用程式中的所有驗證模組。  
  
 \<configuration>  
\<system.net>  
\<authenticationModules>  
\<清除 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|指定用來驗證網路要求的模組。|  
  
## <a name="remarks"></a>備註  
 `clear`元素會移除先前在設定檔或設定階層中較高層級定義的所有驗證模組。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會移除所有已設定的驗證模組。  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [網路設定結構描述](index.md)
