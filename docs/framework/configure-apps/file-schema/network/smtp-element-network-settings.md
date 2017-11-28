---
title: "&lt;smtp&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17b4050c43354da7e7ba6c3ea13a0c7621faf0a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsmtpgt-element-network-settings"></a>&lt;smtp&gt;項目 （網路設定）
設定傳送電子郵件的傳遞格式、傳遞方法和寄件地址。  
  
 \<configuration>  
\<system.net >  
\<mailSettings >  
\<smtp >  
  
## <a name="syntax"></a>語法  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`deliveryFormat`|指定外送電子郵件的傳遞格式。 可接受的值為 SevenBit 和 International。|  
|`deliveryMethod`|指定電子郵件的傳遞方法。 可接受的值為網路、 pickupDirectoryFromIis 和 specifiedPickupDirectory。|  
|`from`|指定外送電子郵件的寄件地址。|  
  
### <a name="child-elements"></a>子元素  
  
|屬性|說明|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|設定簡易郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。|  
|`network`|設定外部的 SMTP 伺服器的網路選項。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**說明**|  
|-----------------|---------------------|  
|[\<mailSettings> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|設定郵件傳送選項。|  
  
## <a name="example"></a>範例  
 下列範例會指定適當的 SMTP 參數使用預設網路認證傳送電子郵件。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
