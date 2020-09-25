---
title: <smtp> 項目 (網路設定)
description: <smtp>網路設定元素可設定 .NET Framework 中傳送電子郵件選項的傳遞格式、傳遞方法和寄件者位址。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 58f496b4a07f7d5531df897dd54bb6176111f1c4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178316"
---
# <a name="smtp-element-network-settings"></a>\<smtp> 項目 (網路設定)

設定傳送電子郵件的傳遞格式、傳遞方法和寄件者位址。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a>Syntax  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`deliveryFormat`|指定外寄電子郵件的傳遞格式。 可接受的值為 SevenBit 和 International。|  
|`deliveryMethod`|指定電子郵件的傳遞方法。 可接受的值為 Network、PickupDirectoryFromIis 和 SpecifiedPickupDirectory。|  
|`from`|指定外寄電子郵件的寄件者位址。|  
  
### <a name="child-elements"></a>子元素  
  
|屬性|描述|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|設定簡易郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。|  
|`network`|設定外部 SMTP 伺服器的網路選項。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[\<mailSettings> (網路設定的元素) ](mailsettings-element-network-settings.md)|設定郵件傳送選項。|  
  
## <a name="example"></a>範例  

 下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [網路設定結構描述](index.md)
