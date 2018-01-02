---
title: "&lt;網路&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d3e99a10403a735383ee5e1a78c1f85ac7fd8281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetworkgt-element-network-settings"></a>&lt;網路&gt;項目 （網路設定）
設定外部簡易郵件傳輸通訊協定 (SMTP) 伺服器的網路選項。  
  
 \<configuration>  
\<system.net >  
\<mailSettings >  
\<smtp >  
\<網路 >  
  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`clientDomain`|指定要用於初始 SMTP 通訊協定的要求連接到 SMTP 郵件伺服器的用戶端網域名稱。 預設值是本機電腦傳送要求的本機主機名稱。|  
|`defaultCredentials`|指定是否可用於存取 SMTP 交易的 SMTP 郵件伺服器的預設使用者認證。 預設值是 `false`。|  
|`enableSsl`|指定存取 SMTP 郵件伺服器是否使用 SSL。 預設值是 `false`。|  
|`host`|指定要用於 SMTP 交易的 SMTP 郵件伺服器的主機名稱。 這個屬性沒有預設值。|  
|`password`|指定要用於驗證的 SMTP 郵件伺服器的密碼。 這個屬性沒有預設值。|  
|`port`|指定要用於連接到 SMTP 郵件伺服器的連接埠號碼。 預設值為 25。|  
|`targetName`|指定要用於 SMTP 交易的擴充的保護時，用於驗證服務提供者名稱 (SPN)。 這個屬性沒有預設值。|  
|`userName`|指定要用來驗證的 SMTP 郵件伺服器的使用者名稱。 這個屬性沒有預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<smtp > 項目 （網路設定）](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|設定簡易郵件傳輸通訊協定 (SMTP) 郵件傳送選項。|  
  
## <a name="remarks"></a>備註  
 某些 SMTP 伺服器需要您進行自我驗證至伺服器，才能使用。 如果您想要驗證您的身份使用預設網路認證在主機上，設定`defaultCredentials`屬性`true`。 <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>屬性可以用來取得目前的值`defaultCredentials`適用的組態檔中的屬性。  
  
 您也可以使用基本驗證 （使用者名稱和密碼） 來驗證您自己的 SMTP 伺服器。 若要使用此選項，您必須指定有效的使用者名稱和指定的 SMTP 伺服器的密碼。  
  
> [!NOTE]
>  基本驗證會傳送`userName`和`password`伺服器未加密的值。 監視網路流量的任何人都可以檢視您的認證，並使用它們來連接到伺服器。 您應該考慮使用更安全的驗證機制，例如 Kerberos 或 NT LAN Manager (NTLM)。如果`defaultCredentials`是`true`，將會使用 Kerberos 或 NTLM，如果伺服器支援這些通訊協定。  
  
 基本驗證和預設網路認證選項互斥。如果您設定`defaultCredentials`至`true`使用者名稱和密碼，會使用預設網路認證，並指定基本驗證資料會被忽略。  
  
 基本驗證，如果您指定`userName`，您也應該指定`password`驗證您自己的郵件伺服器。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>屬性可以用來取得目前的值`userName`適用的組態檔中的屬性。 <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>屬性可以用來取得目前的值`password`適用的組態檔中的屬性。 A`password`屬性不通常會輸入基於安全性的組態檔中。  
  
 `clientDomain`屬性變更為 SMTP 伺服器的起始 SMTP 通訊協定要求中使用的用戶端網域名稱。 `clientDomain`屬性可以設為本機電腦的完整網域名稱，而不是預設會使用 localhost 名稱。 這會提供更高的相容性與 SMTP 通訊協定標準。 預設值是本機電腦傳送要求的本機主機名稱。 <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>屬性可以用來取得目前的值`clientDomain`適用的組態檔中的屬性。  
  
 `targetName`屬性用於驗證擴充的保護時。 預設值是表單的"SMTPSVC /\<主機 >"其中\<主機 > 是 SMTP 郵件伺服器主機名稱。 <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>屬性可以用來取得目前的值`targetName`適用的組態檔中的屬性。  
  
 `enableSsl`屬性會指定存取 SMTP 郵件伺服器是否使用 SSL。 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類別只支援 SMTP 服務延伸模組安全 smtp 透過傳輸層安全性 RFC 3207 中所定義。 在此模式中，在 SMTP 工作階段開始在未加密的通道，然後 STARTTLS 命令發給用戶端切換至使用 SSL 的安全通訊的伺服器。 請參閱 RFC 3207 發佈根據網際網路工程任務推動小組 (IETF) 如需詳細資訊。  
  
 連接的替代方法是 SSL 工作階段最前面位置建立之前命令會傳送任何通訊協定。 這種連線方法有時稱為 SMTPS，而且根據預設會使用連接埠 465。 目前不支援這種替代的連線方法，使用 SSL。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>屬性可以用來取得目前的值`enableSsl`適用的組態檔中的屬性。  
  
## <a name="example"></a>範例  
 下列範例會指定適當的 SMTP 參數使用預設網路認證傳送電子郵件。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
