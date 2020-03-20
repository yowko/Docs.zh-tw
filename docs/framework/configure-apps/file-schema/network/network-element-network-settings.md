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
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154812"
---
# <a name="network-element-network-settings"></a>\<網路>元素（網路設置）
配置外部簡單郵件傳輸協議 （SMTP） 伺服器的網路選項。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<郵件設置>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<斯姆特普>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<網路>**

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
  
|屬性|描述|  
|---------------|-----------------|  
|`clientDomain`|指定要在初始 SMTP 協定請求中用於連接到 SMTP 郵件伺服器的用戶端功能變數名稱。 預設值是發送請求的本地電腦的本地主機名稱稱。|  
|`defaultCredentials`|指定是否應使用預設使用者憑據訪問 SMTP 事務中的 SMTP 郵件伺服器。 預設值是 `false`。|  
|`enableSsl`|指定是否使用 SSL 訪問 SMTP 郵件伺服器。 預設值是 `false`。|  
|`host`|指定用於 SMTP 事務的 SMTP 郵件伺服器的主機名稱。 此屬性沒有預設值。|  
|`password`|指定用於對 SMTP 郵件伺服器進行身份驗證的密碼。 此屬性沒有預設值。|  
|`port`|指定用於連接到 SMTP 郵件伺服器的埠號。 預設值為 25。|  
|`targetName`|指定用於對 SMTP 事務使用擴展保護的服務提供者名稱 （SPN）。 此屬性沒有預設值。|  
|`userName`|指定用於對 SMTP 郵件伺服器進行身份驗證的使用者名。 此屬性沒有預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<smtp>元素（網路設置）](smtp-element-network-settings.md)|配置簡單的郵件傳輸協議 （SMTP） 郵件發送選項。|  
  
## <a name="remarks"></a>備註  
 某些 SMTP 伺服器要求您在使用前向伺服器進行身份驗證。 如果要使用主機上的預設網路憑據進行身份驗證，請將`defaultCredentials`屬性設置為`true`。 該<xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`defaultCredentials`當前值。  
  
 您還可以使用基本驗證（使用者名和密碼）對 SMTP 伺服器進行身份驗證。 要使用此選項，必須為指定的 SMTP 伺服器指定有效的使用者名和密碼。  
  
> [!NOTE]
> 基本驗證將`userName`和`password`值發送到未加密的伺服器。 監視網路流量的任何人都可以查看您的憑據，並使用它們連接到伺服器。 應考慮使用更安全的身份驗證機制，如 Kerberos 或 NT LAN 管理器 （NTLM）。如果是`defaultCredentials``true`，如果伺服器支援這些協定，將使用 Kerberos 或 NTLM。  
  
 基本驗證和預設網路憑據選項是互斥的;如果設置為`defaultCredentials``true`並指定使用者名和密碼，則使用預設網路憑據，並忽略基本驗證資料。  
  
 對於基本驗證，如果指定`userName`了 ，則還應指定`password`以自行對郵件伺服器進行身份驗證。  
  
 該<xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`userName`當前值。 該<xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`password`當前值。 出於`password`安全原因，通常不會在設定檔中輸入屬性。  
  
 該`clientDomain`屬性將初始 SMTP 協定請求中使用的用戶端功能變數名稱更改為 SMTP 伺服器。 該`clientDomain`屬性可以設置為本地電腦的完全限定功能變數名稱，而不是預設情況下使用的本地主機名稱稱。 這提高了 SMTP 協定標準的合規性。 預設值是發送請求的本地電腦的本地主機名稱稱。 該<xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`clientDomain`當前值。  
  
 使用`targetName`擴展保護時，該屬性用於身份驗證。 預設值為"SMTPSVC/\<主機>"的形式，其中\<主機>是 SMTP 郵件伺服器的主機名稱。 該<xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`targetName`當前值。  
  
 該`enableSsl`屬性指定是否使用 SSL 訪問 SMTP 郵件伺服器。 該<xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類僅支援 RFC 3207 中定義的通過傳輸層安全性實現安全 SMTP 的 SMTP 服務擴展。 在此模式下，SMTP 會話從未加密的通道開始，然後用戶端向伺服器發出 STARTTLS 命令，以便使用 SSL 切換到安全通信。 有關詳細資訊，請參閱互聯網工程工作組 （IETF） 發佈的 RFC 3207。  
  
 備用連接方法是在發送任何協定命令之前預先建立 SSL 會話。 此連接方法有時稱為 SMTPS，預設情況下使用埠 465。 當前不支援使用此 SSL 的替代連接方法。  
  
 該<xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`enableSsl`當前值。  
  
## <a name="example"></a>範例  
 下面的示例指定使用預設網路憑據發送電子郵件的相應 SMTP 參數。  
  
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
- [網路設置架構](index.md)
