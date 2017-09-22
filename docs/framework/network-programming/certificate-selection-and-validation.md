---
title: "憑證的選取和驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
caps.latest.revision: 15
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6c926968b9cc5e5b0bf8db0c6bac88e676f45375
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="certificate-selection-and-validation"></a>憑證的選取和驗證
<xref:System.Net> 類別支援數種方式來選取並驗證 <xref:System.Security.Cryptography.X509Certificates>，以進行安全通訊端層 (SSL) 連線。 用戶端可以選取一或多個憑證，以向伺服器驗證它自己。 伺服器可能需要用戶端憑證具有一或多個特定屬性，來進行驗證。  
  
## <a name="definition"></a>定義  
 憑證是一個 ASCII 位元組資料流，包含公開金鑰、屬性 (例如版本號碼、序號和到期日) 以及來自憑證授權單位的數位簽章。 憑證是用來建立加密連線，或向伺服器驗證用戶端。  
  
## <a name="client-certificate-selection-and-validation"></a>用戶端憑證選取和驗證  
 用戶端可以選取特定 SSL 連線的一或多個憑證。 用戶端憑證可以與網頁伺服器或 SMTP 郵件伺服器的 SSL 連線建立關聯。 用戶端會將憑證新增至 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 或 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別物件集合。 使用電子郵件作為範例，憑證集合是與 <xref:System.Net.Mail.SmtpClient> 類別之 <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> 屬性建立關聯的 <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection> 執行個體。 <xref:System.Net.HttpWebRequest> 類別具有類似的 <xref:System.Net.HttpWebRequest.ClientCertificates%2A> 屬性。  
  
 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 與 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別之間的主要差異，在於私密金鑰必須位在 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 類別的憑證存放區中。  
  
 即使將憑證新增至集合，並與特定 SSL 連線建立關聯，也不會將任何憑證傳送至伺服器，除非伺服器要求它們。 如果在連線上設定多個用戶端憑證，將會根據演算法來使用最佳用戶端憑證，而演算法考慮伺服器所提供的憑證簽發者清單與用戶端憑證簽發者名稱之間的相符項目。  
  
 <xref:System.Net.Security.SslStream> 類別甚至可更進一步控制 SSL 交握。 用戶端可以指定委派，以挑選要使用的用戶端憑證。  
  
 遠端伺服器可以確認用戶端憑證有效、最新並且是由適當的憑證授權單位所簽署。 委派可以新增至 <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A>，以強制執行憑證驗證。  
  
## <a name="client-certificate-selection"></a>用戶端憑證選擇  
 .NET Framework 使用下列方式選取要向伺服器呈現的用戶端憑證：  
  
1.  如果先前向伺服器呈現用戶端憑證，則會在第一次呈現時快取憑證，並重複用於後續的用戶端憑證要求。  
  
2.  如果具有委派，請一律使用委派結果作為可選取的用戶端憑證。 可能的話，請嘗試使用快取的憑證；但是，如果委派已傳回 Null，而且憑證集合不是空的，則不會使用快取的匿名認證。  
  
3.  如果這是用戶端憑證的第一個挑戰，Framework 會列舉與連線建立關聯之 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> 或 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別物件中的憑證，以尋找伺服器所提供的憑證簽發者清單與用戶端憑證簽發者名稱之間的相符項目。 第一個符合的憑證會傳送至伺服器。 如果沒有相符的憑證，或憑證集合是空的，則會將匿名認證傳送至伺服器。  
  
## <a name="tools-for-certificate-configuration"></a>憑證組態的工具  
 數個工具可進行用戶端和伺服器憑證組態。  
  
 *Winhttpcertcfg.exe* 工具可以用來設定用戶端憑證。 *Winhttpcertcfg.exe* 工具隨附為 Windows Server 2003 Resource Kit 的其中一個工具。 您可以在 www.microsoft.com 下載此工具，作為 Windows Server 2003 Resource Kit Tools 的一部分。  
  
 *HttpCfg.exe* 工具可以用來設定 <xref:System.Net.HttpListener> 類別的伺服器憑證。 *HttpCfg.exe* 工具隨附為 Windows Server 2003 和 Windows XP Service Pack 2 的其中一個支援工具。 在 Windows Server 2003 或 Windows XP 上，預設不會安裝 *HttpCfg.exe* 和其他支援工具。 在 Windows Server 2003 上。 從 Windows Server 2003 CD-ROM 的下列資料夾和檔案中個別安裝支援工具：  
  
 \Support\Tools\Suptools.msi  
  
 若要與 Windows XP Service Pack 2 搭配使用，您可以從 www.microsoft.com 下載 Windows XP 支援工具。  
  
 *HttpCfg.exe* 工具版本的原始程式碼也會提供為 Windows Server SDK 的範例。 在下列資料夾下，*HttpCfg.exe* 範例的原始程式碼預設會與網路範例一起安裝為 Windows SDK 的一部分：  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 除了這些工具之外，<xref:System.Security.Cryptography.X509Certificates.X509Certificate> 和 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別還會提供從檔案系統載入憑證的方法。  
  
## <a name="see-also"></a>另請參閱  
 [網路程式設計的安全性](../../../docs/framework/network-programming/security-in-network-programming.md)   
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)

