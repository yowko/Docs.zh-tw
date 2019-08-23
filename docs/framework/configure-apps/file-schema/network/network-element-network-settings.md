---
title: <network> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: ee60b990bc749dbb9c5d0e7426c57e9392ddf9d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920978"
---
# <a name="network-element-network-settings"></a>\<網路 > 元素 (網路設定)
設定外部簡易郵件傳輸通訊協定 (SMTP) 伺服器的網路選項。  
  
 \<configuration>  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<network>  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`clientDomain`|指定要在初始 SMTP 通訊協定要求中用來連接 SMTP 郵件伺服器的用戶端功能變數名稱。 預設值是傳送要求的本機電腦的 localhost 名稱。|  
|`defaultCredentials`|指定是否應該使用預設的使用者認證來存取 smtp 交易的 SMTP 郵件伺服器。 預設值為 `false`。|  
|`enableSsl`|指定是否使用 SSL 來存取 SMTP 郵件伺服器。 預設值為 `false`。|  
|`host`|指定要用於 SMTP 交易的 SMTP 郵件伺服器的主機名稱。 這個屬性沒有預設值。|  
|`password`|指定要用於 SMTP 郵件伺服器驗證的密碼。 這個屬性沒有預設值。|  
|`port`|指定要用來連接 SMTP 郵件伺服器的通訊埠編號。 預設值為 25。|  
|`targetName`|指定使用 SMTP 交易的擴充保護時, 用於驗證的服務提供者名稱 (SPN)。 這個屬性沒有預設值。|  
|`userName`|指定要用於 SMTP 郵件伺服器驗證的使用者名稱。 這個屬性沒有預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<smtp > 元素 (網路設定)](smtp-element-network-settings.md)|設定簡單郵件傳輸通訊協定 (SMTP) 郵件傳送選項。|  
  
## <a name="remarks"></a>備註  
 某些 SMTP 伺服器需要您先向伺服器驗證, 才能使用。 如果您想要使用主機上的預設網路認證來驗證自己, 請將`defaultCredentials`屬性設定`true`為。 屬性可以用來從適用的`defaultCredentials`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>  
  
 您也可以使用基本驗證 (使用者名稱和密碼) 向 SMTP 伺服器驗證您自己的身分。 若要使用此選項, 您必須為指定的 SMTP 伺服器指定有效的使用者名稱和密碼。  
  
> [!NOTE]
> 基本驗證會`userName`將`password`和值傳送到未加密的伺服器。 監視網路流量的任何人都可以看到您的認證, 並使用它們來連接到伺服器。 您應該考慮使用更安全的驗證機制, 例如 Kerberos 或 NT LAN Manager (NTLM)。如果`defaultCredentials` 為`true`, 則如果伺服器支援這些通訊協定, 則會使用 Kerberos 或 NTLM。  
  
 [基本驗證] 和 [預設網路認證] 選項互斥。如果您將`defaultCredentials`設定`true`為, 並指定使用者名稱和密碼, 則會使用預設網路認證, 而且會忽略基本驗證資料。  
  
 若為 [基本驗證] `userName`, 如果您指定, 您`password`也應該指定, 以對郵件伺服器進行自我驗證。  
  
 屬性可以用來從適用的`userName`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> 屬性可以用來從適用的`password`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> 基於安全考慮, 通常不會在設定檔中輸入屬性。`password`  
  
 `clientDomain`屬性會將初始 smtp 通訊協定要求中所使用的用戶端功能變數名稱變更為 SMTP 伺服器。 `clientDomain`屬性可以設定為本機電腦的完整功能變數名稱, 而不是預設使用的 localhost 名稱。 這可提供更高的 SMTP 通訊協定標準合規性。 預設值是傳送要求的本機電腦的 localhost 名稱。 屬性可以用來從適用的`clientDomain`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>  
  
 當`targetName`使用擴充保護時, 會使用屬性來進行驗證。 預設值的格式為 "SMTPSVC/\<host >", 其中\<host > 是 SMTP 郵件伺服器的主機名稱。 屬性可以用來從適用的`targetName`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>  
  
 `enableSsl`屬性會指定是否使用 SSL 來存取 SMTP 郵件伺服器。 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類別僅支援透過傳輸層安全性 (如 RFC 3207 中所定義) 的 Secure smtp 的 smtp 服務延伸。 在此模式中, SMTP 會話會在未加密的通道上開始, 然後用戶端會將 STARTTLS 命令發行至伺服器, 以切換至使用 SSL 的安全通訊。 如需詳細資訊, 請參閱網際網路工程任務推動小組 (IETF) 所發佈的 RFC 3207。  
  
 替代連接方法是在傳送任何通訊協定命令之前, 先建立 SSL 會話的前方。 此連接方法有時稱為 SMTPS, 而且預設會使用埠465。 目前不支援使用 SSL 的替代連接方法。  
  
 屬性可以用來從適用的`enableSsl`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>範例  
 下列範例會指定適當的 SMTP 參數, 以使用預設網路認證來傳送電子郵件。  
  
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
