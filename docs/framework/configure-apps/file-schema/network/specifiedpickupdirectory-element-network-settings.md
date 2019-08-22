---
title: <specifiedPickupDirectory> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: b2e31dee4f5aff2bf6cedf5c4e9ca235695b0a53
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659088"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a>\<specifiedPickupDirectory > 元素 (網路設定)
設定簡單郵件傳輸通訊協定 (SMTP) 伺服器的本機目錄。  
  
 \<configuration>  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<specifiedPickupDirectory>  
  
## <a name="syntax"></a>語法  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|應用程式儲存電子郵件以供 SMTP 伺服器稍後處理的目錄。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<smtp > 元素 (網路設定)](smtp-element-network-settings.md)|設定簡單郵件傳輸通訊協定 (SMTP) 郵件傳送選項。|  
  
## <a name="remarks"></a>備註  
 `specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器處理。  
  
## <a name="example"></a>範例  
 下列範例會將 c:\maildrop 指定為郵件收取目錄。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
