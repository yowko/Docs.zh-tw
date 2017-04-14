---
title: "憑證的選取和驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 憑證的選取和驗證
<xref:System.Net> 類別支援數種選項，並驗證 <xref:System.Security.Cryptography.X509Certificates> 針對 Secure Sockets Layer \(SSL\) 連線。  用戶端可以選取一或多個憑證驗證加入至伺服器。  伺服器可以要求用戶端憑證有驗證的一個或多個特定屬性。  
  
## 定義  
 憑證是包含公開金鑰、屬性的 ASCII 位元組資料流 \(例如版本號碼、編號和到期日\) 和從憑證授權單位的數位簽章。  憑證是用來建立加密的連接或驗證用戶端至伺服器。  
  
## 用戶端憑證選取和驗證  
 用戶端可以針對特定的 SSL 連線選取一或多個憑證。  用戶端憑證可以與 Web 伺服器或 SMTP 電子郵件伺服器的 SSL 連線。  用戶端將憑證加入 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 或 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別之物件的集合。  使用電子郵件 \(例如，憑證集合是 <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>執行個體\) 與 <xref:System.Net.Mail.SmtpClient> 類別的 <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> 屬性。  <xref:System.Net.HttpWebRequest> 類別具有類似的 <xref:System.Net.HttpWebRequest.ClientCertificates%2A> 屬性。  
  
 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 和類別之間的主要差異在於私密金鑰必須位於 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 類別的憑證存放區。  
  
 即使憑證加入集合與特定的 SSL 連線，憑證不會傳送至伺服器，除非伺服器要求它們。  如果有多個用戶端憑證以連接設定，則會使用最好一個根據考慮在伺服器所提供的憑證簽發者清單和用戶端憑證簽發者名稱之間的比對演算法。  
  
 <xref:System.Net.Security.SslStream> 類別提供對 SSL 交換的更多控制。  用戶端可以指定使用的用戶端憑證的委派挑選。  
  
 遠端伺服器會驗證用戶端憑證有效，用以簽署由適當的憑證授權單位。  委派可以加入 <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> 強制憑證驗證。  
  
## 用戶端憑證選取範圍  
 .NET Framework 選取用戶端憑證以下列方式提供給伺服器:  
  
1.  如果用戶端憑證先前提供給伺服器，快取憑證，當第一次呈現和對後續的用戶端憑證要求中重複使用。  
  
2.  如果委派存在，請永遠使用從委派的結果當做用戶端憑證選取。  嘗試使用快取的憑證，如果可能，但是，請不要使用快取的匿名認證，如果委派傳回 null，而且憑證集合不是空的。  
  
3.  如果這是用戶端憑證的第一個要求， Framework 列舉 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 的憑證或 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別與物件相關聯的連接，位於伺服器所提供的憑證簽發者清單和用戶端憑證簽發者名稱相符。  比對的第一個憑證傳送至伺服器。  如果憑證不相符或憑證集合是空的，則一個匿名認證傳送至伺服器。  
  
## 提供憑證上設定的工具  
 有許多工具提供用戶端和伺服器憑證設定可供使用。  
  
 *Winhttpcertcfg.exe* 工具可以用來設定用戶端憑證。  *Winhttpcertcfg.exe* 工具來做為其中一個工具 Windows Server 2003 Resource Kit。  這個工具也可做為下載為 Windows Server 2003 Resource Kit Tools 一部分位於 www.microsoft.com。  
  
 *HttpCfg.exe* 工具可以用來設定 <xref:System.Net.HttpListener> 類別的伺服器憑證。  *HttpCfg.exe* 工具提供做為其中一組適用於 Windows Server 2003 和 Windows XP Service Pack 2 的支援工具。  根據預設*HttpCfg.exe* 和其他支援工具在 Windows Server 2003 或 Windows XP 但未安裝。  在 Windows Server 2003。  支援工具在 Windows Server 2003 CD\-ROM 個別安裝與下列資料夾和檔案:  
  
 \\Support\\Tools\\Suptools.msi  
  
 對於使用 Windows XP Service Pack 2 中，使用 Windows XP 支援工具可從 www.microsoft.com 下載。  
  
 為 *HttpCfg.exe* 工具版本的原始程式碼也會做為範例 Windows Server SDK。  做為在下列資料夾下，的 Windows SDK 的一部分。 *HttpCfg.exe* 範例的預設原始程式碼隨網路範例:  
  
 *C:\\Program Files\\Microsoft SDKs\\Windows\\v1.0\\Samples\\NetDS\\http\\serviceconfig*  
  
 除了這些工具之外， <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 和 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別用於載入憑證提供方法從檔案系統。  
  
## 請參閱  
 [網路程式設計的安全性](../../../docs/framework/network-programming/security-in-network-programming.md)   
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)