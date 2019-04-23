---
title: 使用訊息安全性來保護訊息的安全
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: cf014c8aa972c45140a523573b9806996062b40f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171999"
---
# <a name="securing-messages-using-message-security"></a>使用訊息安全性來保護訊息的安全
本章節將討論 WCF 訊息安全性時使用<xref:System.ServiceModel.NetMsmqBinding>。  
  
> [!NOTE]
>  之前閱讀本主題，建議您先閱讀[安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)。  
  
 下圖提供使用 WCF 的佇列通訊概念模型。 此圖例和術語是要用來說明  
  
 傳輸安全性概念。  
  
 ![已排入佇列應用程式圖表](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "分散式佇列圖")  
  
 當傳送佇列使用 WCF 訊息時，WCF 訊息附加做為訊息佇列 (MSMQ) 訊息的主體。 傳輸安全性會保護整個 MSMQ 訊息的安全，而訊息 (或 SOAP) 安全性只能保護 MSMQ 訊息本文的安全。  
  
 訊息安全性的重要概念是用戶端必須保護接收應用程式 (服務) 之訊息安全，這點不同於用戶端要保護目標佇列之訊息安全的傳輸安全性。 保護 WCF 訊息使用訊息安全性時，此情況下，MSMQ 並無任何作用。  
  
 WCF 訊息安全性會將與現有安全性基礎結構，例如憑證或 Kerberos 通訊協定整合的 WCF 訊息中的安全性標頭。  
  
## <a name="message-credential-type"></a>訊息認證類型  
 使用訊息安全性時，服務和用戶端可提供認證來彼此驗證。 您可以將 <xref:System.ServiceModel.NetMsmqBinding.Security%2A> 模式設定為 `Message` 或 `Both` (也就是同時使用傳輸安全性與訊息安全性) 來選取訊息安全性。  
  
 該服務可以使用 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 屬性來檢查用來驗證用戶端的認證。 這個屬性也可以用來進行服務所選擇實作的進一步授權檢查。  
  
 本章節會說明不同的認證類型，以及如何搭配佇列使用這些認證。  
  
### <a name="certificate"></a>憑證  
 憑證認證類型會使用 X.509 憑證來識別服務和用戶端。  
  
 在一般案例中，用戶端和服務都會由受信任的憑證授權單位發行有效的憑證。 接著在連線建立之後，用戶端會使用服務的憑證來驗證該服務的有效性，以決定是否能夠信任該服務。 同樣地，服務會使用該用戶端的憑證來驗證用戶端託管。  
  
 由於佇列中斷的關係，用戶端和服務可能不會在同時位於線上。 因此，用戶端和服務必須超出範圍地交換憑證。 尤其是用戶端因為有在其信任的存放區中保存服務的憑證 (該憑證可以鏈結至憑證授權單位)，所以它必定會信任自己是與正確的服務進行通訊。 為了驗證用戶端，服務會使用訊息附加的 X.509 憑證來比對在其存放區中的憑證，以便確認該用戶端的真實性。 同樣的，該憑證一定會鏈結至憑證授權單位。  
  
 在執行 Windows 的電腦上，憑證會保存在幾種存放區中。 如需有關不同存放區的詳細資訊，請參閱[憑證存放區](https://go.microsoft.com/fwlink/?LinkId=87787)。  
  
### <a name="windows"></a>Windows  
 Windows 訊息認證類型會使用 Kerberos 通訊協定。  
  
 Kerberos 通訊協定是驗證網域上使用者的安全性機制，其可讓通過驗證的使用者透過網域上的其他實體來建立安全內容。  
  
 針對佇列通訊使用 Kerberos 通訊協定時所存在的一個問題，就是包含金鑰發佈中心 (KDC) 所發佈之用戶端身分識別的票證相對存留較短。 A*存留期*表示票證的有效性的 Kerberos 票證相關聯。 因此，若為高度幕後性，您就無法確定該權杖對負責驗證用戶端的服務是否仍然有效。  
  
 請注意，當使用這個認證類型時，服務必須在 SERVICE 帳戶下執行。  
  
 選擇訊息認證時會預設使用 Kerberos 通訊協定。 如需詳細資訊，請參閱 <<c0> [ 探索 Kerberos、 Windows 2000 中的分散式安全性的通訊協定](https://go.microsoft.com/fwlink/?LinkId=87790)。  
  
### <a name="username-password"></a>Username Password  
 使用這個屬性，用戶端便可使用訊息之安全性標頭中的使用者名稱密碼，來向伺服器進行驗證。  
  
### <a name="issuedtoken"></a>IssuedToken  
 用戶端可以使用安全性權杖服務來發行權杖，而此權杖會接著附加到訊息，以便服務用來驗證該用戶端。  
  
## <a name="using-transport-and-message-security"></a>使用傳輸和訊息安全性  
 當同時使用傳輸安全性和訊息安全性時，在傳輸層級和 SOAP 訊息層級中用來保護訊息安全的必須是相同的憑證。  
  
## <a name="see-also"></a>另請參閱

- [使用傳輸安全性來保護訊息的安全](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [訊息佇列上的訊息安全性](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
- [安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [保護服務和用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
