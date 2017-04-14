---
title: "&lt;network&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#network"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<network> 項目"
  - "network 項目"
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;network&gt; 項目 (網路設定)
針對外部 Simple Mail Transport Protocol \(SMTP\) 伺服器設定網路選項。  
  
## 語法  
  
```  
  
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
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`clientDomain`|指定用戶端網域名稱，以便在連接至 SMTP 郵件伺服器的初始 SMTP 通訊協定要求中使用。  預設值是傳送要求之本機電腦的 localhost 名稱。|  
|`defaultCredentials`|指定預設使用者認證是否應該用來存取 SMTP 郵件伺服器以進行 SMTP 交易。  預設值是 `false`。|  
|`enableSsl`|指定是否使用 SSL 存取 SMTP 郵件伺服器。  預設值是 `false`。|  
|`host`|指定要用於 SMTP 交易之 SMTP 郵件伺服器的主機名稱。  這個屬性沒有預設值。|  
|`password`|指定要用於 SMTP 郵件伺服器之驗證的密碼。  這個屬性沒有預設值。|  
|`port`|指定要用來連接至 SMTP 郵件伺服器的連接埠號碼。  預設值為 25。|  
|`targetName`|指定在使用 SMTP 交易的延伸保護時，要用於驗證的服務提供者名稱 \(SPN\)。  這個屬性沒有預設值。|  
|`userName`|指定要用於 SMTP 郵件伺服器之驗證的使用者名稱。  這個屬性沒有預設值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[\<smtp\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|設定 Simple Mail Transport Protocol \(SMTP\) 郵件傳送選項。|  
  
## 備註  
 某些 SMTP 伺服器會要求您先自我驗證才能使用伺服器。  如果您要使用主機上的預設網路認證來進行自我驗證，請將 `defaultCredentials` 屬性設定為 `true`。  <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=fullName> 屬性可用來從適用的組態檔中取得 `defaultCredentials` 屬性的目前值。  
  
 您也可以使用基本驗證 \(使用者名稱和密碼\)，向 SMTP 伺服器自我驗證。  若要使用此選項，您必須針對指定的 SMTP 伺服器指定有效的使用者名稱和密碼。  
  
> [!NOTE]
>  基本驗證會將未加密的 `userName` 和 `password` 值傳送至伺服器。  監視網路流量的任何人，都可以檢視這些認證並使用它們來連接到伺服器。  您必須考慮使用更安全的驗證機制，例如 Kerberos 或 NT LAN Manager \(NTLM\)。如果 `defaultCredentials` 是 `true`，而且伺服器支援 Kerberos 或 NTLM，則會採用這兩種機制。  
  
 基本驗證和預設網路認證選項會互斥 \(Mutually Exclusive\)，因此，如果您將 `defaultCredentials` 設定為 `true`，並且指定了使用者名稱和密碼，則會採用預設網路認證，而忽略基本驗證資料。  
  
 對於基本驗證，如果您指定 `userName`，也應該要指定 `password`，以便對郵件伺服器驗證自己。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=fullName> 屬性可用來從適用的組態檔中取得 `userName` 屬性的目前值。  <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=fullName> 屬性可用來從適用的組態檔中取得 `password` 屬性的目前值。  `password` 屬性會因為安全性原因而無法正常輸入組態檔。  
  
 `clientDomain` 屬性會變更用戶端網域名稱，該名稱是在針對 SMTP 伺服器的初始 SMTP 通訊協定要求中使用。  `clientDomain` 屬性可以設定為本機電腦的完整網域名稱，而不是根據預設使用的本機主機名稱。  這可提供更高的 SMTP 通訊協定標準符合性。  預設值是傳送要求之本機電腦的 localhost 名稱。  <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=fullName> 屬性可用來從適用的組態檔中取得 `clientDomain` 屬性的目前值。  
  
 `targetName` 屬性會在使用延伸保護時用於進行驗證。  預設值的形式為 "SMTPSVC\/\<host\>"，其中 \<host\> 是 SMTP 郵件伺服器的主機名稱。  <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=fullName> 屬性可用來從適用的組態檔中取得 `targetName` 屬性的目前值。  
  
 `enableSsl`  屬性會指定是否使用 SSL 來存取 SMTP 郵件伺服器。  <xref:System.Net.Mail.SmtpClient?displayProperty=fullName> 類別只透過如 RFC 3207 中定義的傳輸層安全性，來支援 SMTP Service Extension for Secure SMTP。  在這個模式中，SMTP 工作階段會在未加密的通道上開始，然後用戶端會向伺服器發出 STARTTLS 命令，以切換至使用 SSL 的安全通訊。  如需詳細資訊，請參閱由「網際網路工程任務推動小組」\(IETF\) 發行的 RFC 3207。  
  
 替代的連線方法是在傳送任何通訊協定命令之前，首先建立 SSL 工作階段。  這種連線方法有時稱為 SMTPS，並會依預設使用連接埠 465。  目前不支援使用 SSL 的這種替代連線方法。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=fullName> 屬性可用來從適用的組態檔中取得 `enableSsl` 屬性的目前值。  
  
## 範例  
 下列範例中，程式碼會指定適當的 SMTP 參數，使用預設的網路認證傳送電子郵件。  
  
```  
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
  
## 請參閱  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=fullName>   
 <xref:System.Net.Configuration.SmtpSection?displayProperty=fullName>   
 <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)