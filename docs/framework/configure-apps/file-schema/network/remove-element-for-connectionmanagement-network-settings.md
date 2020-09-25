---
title: connectionManagement 的 <remove> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 46157482d7ceb42b352c68dc9b0eab4f7688bc5c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176171"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a>connectionManagement 的 \<remove> 項目 (網路設定)

從連接管理清單中移除 IP 位址或 DNS 名稱。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntax  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**Attribute**|**說明**|  
|-------------------|---------------------|  
|`address`|IP 位址或 DNS 名稱。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|指定連接至網路主機的連線數目上限。|  
  
## <a name="remarks"></a>備註  

 `remove`元素會移除指定之伺服器的連接管理清單專案。  
  
 屬性的值 `address` 應為有效的 IP 位址或主機名稱。  
  
## <a name="configuration-files"></a>組態檔  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  

 下列範例會移除伺服器的任何連接管理清單專案 `www.adventure-works.com` ，然後將應用程式設定為使用四個與伺服器的連線 `www.contoso.com` ，以及兩個連接到所有其他伺服器的連線。  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [網路設定結構描述](index.md)
