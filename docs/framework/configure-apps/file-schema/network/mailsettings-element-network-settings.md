---
title: <mailSettings> 項目 (網路設定)
description: <mailSettings>Network settings 元素會設定 .NET Framework 中的郵件傳送選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504559"
---
# <a name="mailsettings-element-network-settings"></a>\<mailSettings> 項目 (網路設定)
設定郵件傳送選項。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a>語法  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|屬性|說明|  
|---------------|-----------------|  
|[\<smtp>元素（網路設定）](smtp-element-network-settings.md)|設定簡單郵件傳輸通訊協定選項。|  
  
### <a name="parent-elements"></a>父項目  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[\<system.Net>元素（網路設定）](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="example"></a>範例  
 下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Mail.SmtpClient>
- [網路設定結構描述](index.md)
