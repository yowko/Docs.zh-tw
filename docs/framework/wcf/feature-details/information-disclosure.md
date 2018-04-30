---
title: 資訊洩露
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1b3da2dc36dca913c638ce269213903c2a024a04
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="information-disclosure"></a>資訊洩露
資訊洩漏讓攻擊者可以取得與系統有關的寶貴資訊。 因此，公開資訊時，請務必考慮您要公開的是哪些資訊，以及是否會遭到惡意使用者的使用。 下列列出可能的資訊洩漏攻擊，並針對各種攻擊提供減少受到攻擊的方法。  
  
## <a name="message-security-and-http"></a>訊息安全性和 HTTP  
 如果您正在使用 HTTP 傳輸層上的訊息層級安全性，請注意，訊息層級安全性不會保護 HTTP 標頭。 保護 HTTP 標頭的唯一方法就是使用 HTTPS 傳輸取代 HTTP。 HTTPS 傳輸使用 Secure Sockets Layer (SSL) 通訊協定加密整個訊息，包括 HTTP 標頭。  
  
## <a name="policy-information"></a>原則資訊  
 維持原則的安全相當重要，特別是在原則中公開敏感的發行權杖需求或權杖簽發者資訊的聯合案例中。 在這些情況中，建議保護聯合服務的原則端點，以避免攻擊者取得與服務有關的資訊，例如放在發行權杖中的宣告類型，或將用戶端重新導向至惡意的權杖簽發者。 例如，攻擊者可以透過重新設定聯合信任鏈結來找出使用者名組/密碼組，以終止執行中間人攻擊的簽發者。 同時，也建議透過原則擷取來取得繫結的同盟用戶端，確認他們信任所取得之同盟信任鏈結中的簽發者。 如需同盟案例的詳細資訊，請參閱[同盟](../../../../docs/framework/wcf/feature-details/federation.md)。  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>記憶體傾印會洩漏宣告資訊  
 應用程式失敗時，Dr.Watson 等產生的記錄檔會包含宣告資訊。 這項資訊不應該匯出到其他實體，例如支援團隊等，否則可能會一併匯出包含私人資料的宣告資訊。 只要不將記錄檔傳送給未知的實體，即可減少這種情況。 如需詳細資訊，請參閱[Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160)。  
  
## <a name="endpoint-addresses"></a>端點位址  
 端點位址包含與端點通訊所需的資訊。 SOAP 安全性必須在交換的安全性交涉訊息中加入完整位址，以便在用戶端和伺服器之間交涉對稱金鑰。 因為安全性交涉是開機處理序，所以在執行此處理序期間無法將位址標頭加密。 因此，位址不應含有任何機密資料，否則會導致發生資訊洩漏攻擊。  
  
## <a name="certificates-transferred-unencrypted"></a>未加密的憑證傳輸  
 當您使用 X.509 憑證驗證用戶端時，會在 SOAP 標頭內明確傳送憑證。 請注意，這樣可能會洩漏個人可識別資訊 (PII)。 這不是 `TransportWithMessageCredential` 模式的問題，此模式會以傳輸層級安全性加密整個訊息。  
  
## <a name="service-references"></a>服務參考  
 服務參考是其他服務的參考。 例如，服務可能傳遞服務參考到運作中的用戶端。 服務參考也可以搭配*信任身分識別驗證器*，內部元件，以確保目標主體的身分識別洩漏資訊，例如應用程式資料或認證給目標之前。 如果遠端信任識別無法確認或不正確，傳送者應確保不會洩漏可能危害到自己、應用程式或使用者的資料。  
  
 安全防護包括下列：  
  
-   服務參考假設為可以信任。 每次傳送服務參考執行個體時，小心確保它們不會遭到竄改。  
  
-   有些應用程式會提供使用者體驗，可根據服務參考中的資料以及經由遠端主機證實的信任資料，互相建立信任。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 有提供這類機能的擴充點，但是使用者必須加以實作。  
  
## <a name="ntlm"></a>NTLM  
 在預設情況下，Windows 網域環境中的 Windows 驗證會使用 Kerberos 通訊協定來驗證和授權使用者。 如果基於某個原因而無法使用 Kerberos 通訊協定，請使用 NT LAN Manager (NTLM) 做為後援。 透過將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> 屬性設定為 `false`，即可停用此行為。 允許 NTLM 時要注意的問題包括：  
  
-   NTLM 會公開用戶端使用者名稱。 如果使用者名稱需要保密，請將繫結上的 `AllowNTLM` 屬性設定為 `false`。  
  
-   NTLM 不會提供伺服器驗證。 因此，當您使用 NTLM 做為驗證通訊協定時，用戶端無法確保能與正確的服務通訊。  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>指定用戶端認證或無效的識別強制 NTLM 使用  
 當建立用戶端、指定沒有網域名稱的用戶端認證或指定無效的伺服器識別時，會導致使用 NTLM 取代 Kerberos 通訊協定 (如果 `AlllowNtlm` 屬性設定為 `true`)。 由於 NTLM 不會驗證伺服器，因此資訊可能會遭到洩漏。  
  
 比方說，它可指定 Windows 用戶端認證沒有網域名稱，如下列 Visual C# 程式碼所示。  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 程式碼沒有指定網域名稱，因此將會使用 NTLM。  
  
 如果有指定網域，但使用端點識別功能來指定無效的服務主體名稱，則會使用 NTLM。 如需有關如何指定端點身分識別的詳細資訊，請參閱[服務識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## <a name="see-also"></a>另請參閱  
 [安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [權限提高](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [阻絕服務](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [竄改](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [重新執行攻擊](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
