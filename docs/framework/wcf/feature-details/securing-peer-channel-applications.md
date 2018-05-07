---
title: 確保對等通道應用程式安全
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: 725e629a187261a5bc50d880f75b942734df960b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="securing-peer-channel-applications"></a>確保對等通道應用程式安全
和 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 下的其他繫結一樣，`NetPeerTcpBinding` 預設已啟用安全性，並且會提供傳輸和訊息型安全性 (或兩者皆提供)。 這個主題會討論這兩種類型的安全性。 安全性類型則是由繫結規格中的安全性模式標記所指定 (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`)。  
  
## <a name="transport-based-security"></a>傳輸型安全性  
 對等通道支援兩種可用來保護傳輸的驗證認證類型，這兩種類型都需要在相關聯的 `ClientCredentialSettings.Peer` 上設定 `ChannelFactory` 屬性：  
  
-   密碼。 用戶端會運用已知的機密密碼來驗證連線。 使用這個認證類型時，`ClientCredentialSettings.Peer.MeshPassword` 必須傳遞有效的密碼並選擇性傳遞 `X509Certificate2` 執行個體。  
  
-   憑證。 將會使用特定的應用程式驗證。 使用這個認證類型時，您必須在 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 中使用實體 `ClientCredentialSettings.Peer.PeerAuthentication` 實作。  
  
## <a name="message-based-security"></a>訊息型安全性  
 使用訊息安全性時，應用程式可以簽署傳輸訊息，因此所有接收方都可驗證是否從信任的一方傳出訊息，而且該訊息並沒有遭到竄改。 目前對等通道僅支援 X.509 認證的訊息簽署。  
  
## <a name="best-practices"></a>最佳作法  
  
-   本節會討論保護對等通道應用程式安全的最佳做法。  
  
### <a name="enable-security-with-peer-channel-applications"></a>啟用對等通道應用程式的安全性  
 有鑑於對等通道通訊協定的分散式特性，在不安全的網狀結構中很難強制施行網狀結構成員資格、機密性和隱私權。 而記住用戶端和解析程式服務之間的安全通訊也相當重要。 在套用對等名稱解析通訊協定 (PNRP) 時，請使用安全名稱來避免詐騙和其他常見攻擊。 啟用連線用戶端使用上的安全性以連絡解析程式服務，即可保護自訂解析程式服務，而這包括了訊息和傳輸型安全性。  
  
### <a name="use-the-strongest-possible-security-model"></a>使用最強的可能安全性模型  
 例如，如果網狀結構的每個成員都需要個別識別，請使用憑證型驗證模型。 如果不可能這樣做，請使用密碼型驗證，再使用目前的建議以保持其安全。 這包括僅與受信任的對象共用密碼、使用安全媒介傳輸密碼、經常變更密碼以及確保密碼為強式 (長度至少為八個字元，其中至少包括大小寫字母、數字和特殊字元)。  
  
### <a name="never-accept-self-signed-certificates"></a>永不接受自我簽署的憑證  
 永不接受以主體名稱為基礎的憑證認證。 請注意，任何人都可建立憑證，而任何人也都可以選擇您要驗證的名稱。 若要避免可能發生詐騙，請根據發行授權單位的認證來驗證憑證 (信任的簽發者或根憑證授權單位)。  
  
### <a name="use-message-authentication"></a>使用訊息驗證  
 使用訊息驗證以驗證源自於信任來源的訊息，並驗證傳輸期間沒有任何人竄改訊息。 如果不使用訊息驗證，就很容易讓惡意用戶端詐騙或竄改網狀結構中的訊息。  
  
## <a name="peer-channel-code-examples"></a>對等通道程式碼範例  
 [對等通道案例](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>另請參閱  
 [對等通道安全性](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [建置對等通道應用程式](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
