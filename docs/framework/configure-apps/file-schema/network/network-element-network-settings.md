---
title: <network> 項目 (網路設定)
description: <network>網路設定元素會在 .NET Framework 中設定外部 SMTP 伺服器選項的網路選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: cd142febc0b3aacf1be7978178a6a05d9b9aebbf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190276"
---
# <a name="network-element-network-settings"></a>\<network> 項目 (網路設定)

設定外部 Simple Mail Transport Protocol (SMTP) server 的網路選項。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a>Syntax  
  
```xml  
<network  
  clientDomain="string"
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"
  password="string"  
  port="integer"
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`clientDomain`|指定要在初始 SMTP 通訊協定要求中用來連接到 SMTP 郵件伺服器的用戶端功能變數名稱。 預設值是送出要求的本機電腦的 localhost 名稱。|  
|`defaultCredentials`|指定是否應該使用預設的使用者認證來存取 smtp 郵件伺服器的 SMTP 交易。 預設值是 `false`。|  
|`enableSsl`|指定是否使用 SSL 來存取 SMTP 郵件伺服器。 預設值是 `false`。|  
|`host`|指定要用於 SMTP 交易的 SMTP 郵件伺服器主機名稱。 此屬性沒有預設值。|  
|`password`|指定要用於 SMTP 郵件伺服器驗證的密碼。 此屬性沒有預設值。|  
|`port`|指定要用來連接到 SMTP 郵件伺服器的埠號碼。 預設值為 25。|  
|`targetName`|指定服務提供者名稱 (SPN) ，以在使用 SMTP 交易的延伸保護時用於驗證。 此屬性沒有預設值。|  
|`userName`|指定要用於 SMTP 郵件伺服器驗證的使用者名稱。 此屬性沒有預設值。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<smtp> (網路設定的元素) ](smtp-element-network-settings.md)|設定 Simple Mail Transport Protocol (SMTP) Mail 傳送選項。|  
  
## <a name="remarks"></a>備註  

 某些 SMTP 伺服器會要求您在使用之前先向伺服器驗證。 如果您想要使用主機上的預設網路認證來自行驗證，請將 `defaultCredentials` 屬性設定為 `true` 。 <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `defaultCredentials` 。  
  
 您也可以使用基本驗證 (使用者名稱和密碼) ，向 SMTP 伺服器驗證您自己的身分。 若要使用此選項，您必須為指定的 SMTP 伺服器指定有效的使用者名稱和密碼。  
  
> [!NOTE]
> 基本驗證會將 `userName` 和 `password` 值傳送到未加密的伺服器。 監視網路流量的任何人都可以查看您的認證，並使用它們來連線到伺服器。 您應該考慮使用更安全的驗證機制，例如 Kerberos 或 NT LAN Manager (NTLM。 ) 如果 `defaultCredentials` 是 `true` ，則會使用 KERBEROS 或 ntlm，如果伺服器支援這些通訊協定。  
  
 基本驗證和預設網路認證選項互斥。如果您將設定 `defaultCredentials` 為， `true` 並指定使用者名稱和密碼，則會使用預設的網路認證，而且會忽略基本驗證資料。  
  
 若為基本驗證，則您 `userName` 也應該指定， `password` 以將自己驗證到郵件伺服器。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `userName` 。 <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `password` 。 基於 `password` 安全性考慮，通常不會在設定檔中輸入屬性。  
  
 屬性會將 `clientDomain` 初始 SMTP 通訊協定要求中使用的用戶端功能變數名稱變更為 SMTP 伺服器。 `clientDomain`屬性可以設定為本機電腦的完整功能變數名稱，而不是預設使用的 localhost 名稱。 這可提供較高的 SMTP 通訊協定標準相容性。 預設值是送出要求的本機電腦的 localhost 名稱。 <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `clientDomain` 。  
  
 `targetName`使用擴充保護時，會使用屬性來進行驗證。 預設值的格式為 "SMTPSVC/"， \<host> 其中 \<host> 是 SMTP 郵件伺服器的主機名稱。 <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `targetName` 。  
  
 `enableSsl`屬性會指定是否使用 SSL 來存取 SMTP 郵件伺服器。 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類別僅支援透過傳輸層安全性安全的 Smtp 服務延伸，如 RFC 3207 中所定義。 在此模式中，SMTP 會話會在未加密的通道上開始，然後用戶端會將 STARTTLS 命令發出至伺服器，以切換到使用 SSL 的安全通訊。 如需詳細資訊，請參閱網際網路工程任務推動小組所發佈的 RFC 3207 (IETF) 。  
  
 替代連接方法是在傳送任何通訊協定命令之前，先建立 SSL 會話的位置。 此連接方法有時稱為 SMTPS，預設會使用埠465。 目前不支援使用 SSL 的替代連接方法。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `enableSsl` 。  
  
## <a name="example"></a>範例  

 下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
