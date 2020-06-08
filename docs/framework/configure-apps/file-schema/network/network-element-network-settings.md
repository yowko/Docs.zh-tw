---
title: <network> 項目 (網路設定)
description: <network>網路設定元素會針對 .NET Framework 中的外部 SMTP 伺服器選項設定網路選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: 36857e63871b4672df349934594f0887a042609e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504546"
---
# <a name="network-element-network-settings"></a>\<network> 項目 (網路設定)
設定外部簡易郵件傳輸通訊協定（SMTP）伺服器的網路選項。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a>語法  
  
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
  
|屬性|說明|  
|---------------|-----------------|  
|`clientDomain`|指定要在初始 SMTP 通訊協定要求中用來連接 SMTP 郵件伺服器的用戶端功能變數名稱。 預設值是傳送要求的本機電腦的 localhost 名稱。|  
|`defaultCredentials`|指定是否應該使用預設的使用者認證來存取 smtp 交易的 SMTP 郵件伺服器。 預設值為 `false`。|  
|`enableSsl`|指定是否使用 SSL 來存取 SMTP 郵件伺服器。 預設值為 `false`。|  
|`host`|指定要用於 SMTP 交易的 SMTP 郵件伺服器的主機名稱。 此屬性沒有預設值。|  
|`password`|指定要用於 SMTP 郵件伺服器驗證的密碼。 此屬性沒有預設值。|  
|`port`|指定要用來連接 SMTP 郵件伺服器的通訊埠編號。 預設值為 25。|  
|`targetName`|指定使用 SMTP 交易的擴充保護時，用於驗證的服務提供者名稱（SPN）。 此屬性沒有預設值。|  
|`userName`|指定要用於 SMTP 郵件伺服器驗證的使用者名稱。 此屬性沒有預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[\<smtp>元素（網路設定）](smtp-element-network-settings.md)|設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。|  
  
## <a name="remarks"></a>備註  
 某些 SMTP 伺服器需要您先向伺服器驗證，才能使用。 如果您想要使用主機上的預設網路認證來驗證自己，請將 `defaultCredentials` 屬性設定為 `true` 。 <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `defaultCredentials` 。  
  
 您也可以使用基本驗證（使用者名稱和密碼）向 SMTP 伺服器驗證您自己的身分。 若要使用此選項，您必須為指定的 SMTP 伺服器指定有效的使用者名稱和密碼。  
  
> [!NOTE]
> 基本驗證會將 `userName` 和 `password` 值傳送到未加密的伺服器。 監視網路流量的任何人都可以看到您的認證，並使用它們來連接到伺服器。 您應該考慮使用更安全的驗證機制，例如 Kerberos 或 NT LAN Manager （NTLM）。如果 `defaultCredentials` 為 `true` ，則如果伺服器支援這些通訊協定，則會使用 KERBEROS 或 NTLM。  
  
 [基本驗證] 和 [預設網路認證] 選項互斥。如果您將設定 `defaultCredentials` 為， `true` 並指定使用者名稱和密碼，則會使用預設網路認證，而且會忽略基本驗證資料。  
  
 若為 [基本驗證]，如果您指定 `userName` ，您也應該指定， `password` 以對郵件伺服器進行自我驗證。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `userName` 。 <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `password` 。 基於 `password` 安全考慮，通常不會在設定檔中輸入屬性。  
  
 屬性會將 `clientDomain` 初始 smtp 通訊協定要求中所使用的用戶端功能變數名稱變更為 SMTP 伺服器。 `clientDomain`屬性可以設定為本機電腦的完整功能變數名稱，而不是預設使用的 localhost 名稱。 這可提供更高的 SMTP 通訊協定標準合規性。 預設值是傳送要求的本機電腦的 localhost 名稱。 <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `clientDomain` 。  
  
 `targetName`當使用擴充保護時，會使用屬性來進行驗證。 預設值的格式為 "SMTPSVC/"， \<host> 其中 \<host> 是 SMTP 郵件伺服器的主機名稱。 <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `targetName` 。  
  
 `enableSsl`屬性會指定是否使用 SSL 來存取 SMTP 郵件伺服器。 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類別僅支援透過傳輸層安全性（如 RFC 3207 中所定義）的 SECURE smtp 的 Smtp 服務延伸。 在此模式中，SMTP 會話會在未加密的通道上開始，然後用戶端會將 STARTTLS 命令發行至伺服器，以切換至使用 SSL 的安全通訊。 如需詳細資訊，請參閱網際網路工程任務推動小組（IETF）所發佈的 RFC 3207。  
  
 替代連接方法是在傳送任何通訊協定命令之前，先建立 SSL 會話的前方。 此連接方法有時稱為 SMTPS，而且預設會使用埠465。 目前不支援使用 SSL 的替代連接方法。  
  
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
