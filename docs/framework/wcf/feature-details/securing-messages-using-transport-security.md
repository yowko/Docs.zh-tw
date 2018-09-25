---
title: 使用傳輸安全性來確保訊息的安全
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
author: BrucePerlerMS
ms.openlocfilehash: 1c2eafc4d1b955fe99d1c18314c490d7205b3f29
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108265"
---
# <a name="securing-messages-using-transport-security"></a>使用傳輸安全性來確保訊息的安全
本節討論訊息佇列 (MSMQ) 的傳輸安全性，您可以使用這項傳輸安全性確保傳送至佇列之訊息的安全。  
  
> [!NOTE]
>  之前閱讀本主題，建議您先閱讀[安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)。  
  
 下圖提供使用 Windows Communication Foundation (WCF) 的佇列通訊概念模型。 這張圖與用語可用來解釋傳輸安全性的概念。  
  
 ![已排入佇列應用程式圖表](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "分散式佇列圖")  
  
 當傳送佇列訊息時使用 WCF 與<xref:System.ServiceModel.NetMsmqBinding>，WCF 訊息會附加為 MSMQ 訊息本文。 傳輸安全性保障整個 MSMQ 訊息 (MSMQ 訊息標頭或屬性和訊息本文) 的安全。 因為是 MSMQ 訊息本文，使用傳輸安全性也會保護 WCF 訊息。  
  
 傳輸安全性的重要概念是用戶端必須滿足安全性要求，才能讓訊息傳至目標佇列。 這種概念與訊息安全性不同，訊息安全性保障訊息的目的是為了接收該訊息之應用程式的安全。  
  
 使用 <xref:System.ServiceModel.NetMsmqBinding> 與 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 的傳輸安全性，會影響 MSMQ 訊息在傳輸佇列與目標佇列之間傳輸時保障安全的方式，保障安全的意思是：  
  
-   簽署訊息以確保不會被竄改。  
  
-   加密訊息以確保不會被看見或竄改。 這只是建議，可自由選擇。  
  
-   針對不可否認性，識別訊息寄件人的目標佇列管理員。  
  
 在 MSMQ 中，目標佇列擁有存取控制清單 (ACL)，用來檢查用戶端是否擁有傳送訊息至目標佇列的授權，這部分與驗證無關。 同時也檢查接收的應用程式是否擁有自目標佇列接收訊息的權限。  
  
## <a name="wcf-msmq-transport-security-properties"></a>WCF MSMQ 傳輸安全性屬性  
 MSMQ 使用 Windows 驗證安全性。 它使用 Windows 安全性識別項 (SID) 識別用戶端，並使用 Active Directory 目錄服務作為驗證用戶端時的憑證授權單位。 這需要安裝整合 Active Directory 的 MSMQ。 因為使用 Windows 網域 SID 來識別用戶端，故此安全性選項僅在用戶端與服務皆屬相同的 Windows 網域之一部分才有意義。  
  
 MSMQ 也能對未以 Active Directory 註冊的訊息附加憑證。 在這種狀況下，它能確保訊息使用附加的憑證進行簽章。  
  
 WCF 會提供這兩個選項為 MSMQ 傳輸安全性的一部分，而且是傳輸安全性的重要樞紐。  
  
 根據預設，傳輸安全性為啟用狀態。  
  
 有了這些基礎之後，下列章節將詳述隨附於 <xref:System.ServiceModel.NetMsmqBinding> 與 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>的傳輸安全性屬性。  
  
#### <a name="msmq-authentication-mode"></a>MSMQ 驗證模式  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> 會要求使用 Windows 網域安全性或外部以憑證為基礎的安全性，藉此保障訊息的安全。 在這兩種驗證模式中，WCF 已排入佇列的傳輸通道會使用`CertificateValidationMode`服務組態中指定。 憑證驗證模式可指定用來檢查憑證效力的機制。  
  
 啟用傳輸安全性後，預設的設定值為 <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>。  
  
#### <a name="windows-domain-authentication-mode"></a>Windows 網域驗證模式  
 若選擇使用 Windows 安全性，就需要整合 Active Directory。 <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> 是預設的傳輸安全性模式。 當此設定時，WCF 通道會將 Windows SID 附加至 MSMQ 訊息，並使用取自 Active Directory 的內部憑證。 MSMQ 使用此內部憑證確保訊息安全。 接收方的佇列管理員會使用 Active Directory 來搜尋並尋找符合的憑證以驗證用戶端，並檢查 SID 與用戶端是否相符。 若以 `WindowsDomain` 驗證模式內部產生的憑證或 `Certificate` 驗證模式外部產生的憑證附加於訊息時，那麼即使目標佇列未標示需要驗證，仍然會執行驗證步驟。  
  
> [!NOTE]
>  建立佇列時，您可標示佇列為驗證佇列，表示佇列需要對傳送訊息至佇列的用戶端進行驗證。 如此可確保佇列只會接受已驗證的訊息。  
  
 訊息附加的 SID 也會用來和目標佇列的 ACL 檢查比對，確保用戶端擁有發送訊息至佇列的授權。  
  
#### <a name="certificate-authentication-mode"></a>憑證驗證模式  
 若選擇使用憑證驗證模式，則不需要整合 Active Directory。 事實上，在某些狀況下，例如以工作群組模式 (未整合 Active Directory) 安裝 MSMQ，或是使用 SOAP Reliable Messaging Protocol (SRMP) 傳輸通訊協定傳送訊息至佇列時，只有 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> 起作用。  
  
 傳送 WCF 訊息時<xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>，WCF 通道不會將 Windows SID 附加至 MSMQ 訊息。 如此一來，目標佇列 ACL 必須允許 `Anonymous` 使用者存取，才可傳送至佇列。 接收方的佇列管理員會檢查 MSMQ 訊息是否使用憑證簽章，但不會進行任何驗證。  
  
 其宣告和身分識別資訊的憑證中已填入<xref:System.ServiceModel.ServiceSecurityContext>WCF 已排入佇列的傳輸通道。 服務可使用此資訊執行它自己對寄件人的驗證。  
  
### <a name="msmq-protection-level"></a>MSMQ 保護層級  
 保護層級會說明如何保護 MSMQ 訊息以確保不會被竄改。 它是在 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 屬性中指定。 預設值是 <xref:System.Net.Security.ProtectionLevel.Sign>。  
  
#### <a name="sign-protection-level"></a>簽章保護層級  
 當使用 `WindowsDomain` 驗證模式內部產生的憑證或 `Certificate` 驗證模式外部產生的憑證時，MSMQ 訊息會使用內部產生的憑證簽章。  
  
#### <a name="sign-and-encrypt-protection-level"></a>簽章與加密保護層級  
 當使用 `WindowsDomain` 驗證模式內部產生的憑證或 `Certificate` 驗證模式外部產生的憑證時，MSMQ 訊息會使用內部產生的憑證簽章。  
  
 除了對訊息簽章之外，MSMQ 訊息還使用取自 Active Directory 的憑證公開金鑰進行加密。此 Active Directory 屬於裝載目標佇列之接收方的佇列管理員所有。 傳送佇列管理員會確定 MSMQ 訊息在傳輸中已加密。 接收佇列管理員會使用內部憑證的私密金鑰解密 MSMQ 訊息，並將訊息以明文儲存於佇列 (若已驗證並授權) 中。  
  
> [!NOTE]
>  若要加密訊息，需要能存取 Active Directory (`UseActiveDirectory` 的 <xref:System.ServiceModel.NetMsmqBinding> 屬性必須設為 `true`) 並且能同時使用於 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> 及 <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>。  
  
#### <a name="none-protection-level"></a>無保護層級  
 這代表 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 設定為 <xref:System.Net.Security.ProtectionLevel.None>的時候。 這對任何其他驗證模式而言，不是有效值。  
  
> [!NOTE]
>  若 MSMQ 訊息已簽章，則 MSMQ 會檢查訊息是否以附加的憑證 (內部或外部) 簽章，而不理會佇列狀態，亦即佇列是否為驗證過的佇列。  
  
### <a name="msmq-encryption-algorithm"></a>MSMQ 加密演算法  
 加密演算法可指定用來在網路上加密 MSMQ 訊息的演算法。 這個屬性只能在 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 設定為 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> 時使用。  
  
 支援的演算法為 `RC4Stream` 與 `AES`，預設為 `RC4Stream`。  
  
 只有在送件人已安裝 MSMQ 4.0 時，您才可以使用 `AES` 演算法。 除此之外，目標佇列必須也必須裝載於 MSMQ 4.0 上。  
  
### <a name="msmq-hash-algorithm"></a>MSMQ 雜湊演算法  
 雜湊演算法會指定建立 MSMQ 訊息數位簽章所使用的演算法。 接收佇列管理員會使用與此相同的演算法，驗證 MSMQ 訊息。 只有在 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 設為 <xref:System.Net.Security.ProtectionLevel.Sign> 或 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> 時，才會使用這個屬性。  
  
 支援的演算法為 `MD5`、`SHA1`、`SHA256` 和 `SHA512`。 預設為 `SHA1`。  
  
## <a name="see-also"></a>另請參閱  
 [訊息佇列](https://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)  
 [安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [保護服務和用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
