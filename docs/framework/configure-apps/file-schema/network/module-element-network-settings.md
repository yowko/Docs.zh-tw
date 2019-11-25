---
title: <module> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 78f6418160b80096214c6e37268a5a90498d6d4d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089244"
---
# <a name="module-element-network-settings"></a>\<模組 > 元素（網路設定）
將新的 Proxy 模組加入至應用程式。  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**模組 >**

## <a name="syntax"></a>語法  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**說明**|  
|-------------------|---------------------|  
|`type`|完整的類型名稱（以 <xref:System.Type.FullName%2A> 屬性工作表示）和元件名稱（由 <xref:System.Reflection.Assembly.FullName%2A> 屬性工作表示），以逗號分隔，以執行 proxy。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**說明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="remarks"></a>備註  
 `module` 元素會註冊用來執行 <xref:System.Net.IWebProxy> 介面的 proxy 類別。 註冊 Proxy 類別之後，可以使用 `module` 透過支援的 Proxy 要求資訊。  
  
 `type` 屬性的值應該是模組的類別名稱，以及其對應動態連結程式庫（DLL）的名稱。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會註冊自訂 proxy 類別。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
