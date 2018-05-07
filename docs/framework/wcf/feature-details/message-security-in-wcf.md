---
title: WCF 中的訊息安全性
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 27f8354cf4d96f8da408cffa3cef42ab9609c76d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="message-security-in-wcf"></a>WCF 中的訊息安全性
Windows Communication Foundation (WCF) 有兩種主要的模式，可提供安全性 (`Transport`和`Message`) 和第三個模式 (`TransportWithMessageCredential`) 的結合這兩者。 本主題將說明訊息安全性以及使用的原因。  
  
## <a name="what-is-message-security"></a>什麼是訊息安全性？  
 訊息安全性會使用 WS-Security 規格來保護訊息的安全。 此 WS-Security 規格說明 SOAP 訊息的加強功能，以確保 SOAP 訊息層級 (而非傳輸層級) 的機密性、完整性和驗證。  
  
 簡單的說，訊息安全性與傳輸安全性不同，它會連同訊息保護 (簽章或加密)，和每個訊息一起封裝安全性憑證和宣告。 藉由修改內容將安全性直接套用至訊息，可讓該安全訊息在有關安全性的方面上獨立。 這會啟用一些在使用傳輸安全性時不可能發生的案例。  
  
## <a name="reasons-to-use-message-security"></a>使用訊息安全性的理由  
 在訊息層級的安全性中，所有的安全性資訊都會封裝在訊息中。 使用訊息層級安全性取代傳輸層級安全性來保護訊息的安全有下列優點：  
  
-   端對端安全性。 如 Secure Sockets Layer (SSL) 等傳輸安全性，只有在通訊是點對點時才會保護訊息安全。 如果訊息在到達最終接收者之前，傳送至一個或多個 SOAP 媒介 (例如路由器)，則只要一個媒介從網路讀取該訊息，該訊息本身便不受保護。 此外，用戶端驗證資訊只供第一個媒介使用，且如有需要，必須再次傳輸到以超出範圍方式接收的最終接收者。 即使整個路由在個別躍點之間使用 SSL 安全性也適用。 由於訊息安全性是直接和訊息一起運作，並在其中保護 XML 的安全，因此不論在到達最終接收者之前包含多少個媒介，安全性都會伴隨訊息。 這會啟用真正的端對端安全性案例。  
  
-   增加的彈性。 可簽署或加密部分訊息 (而非整個訊息)。 這表示媒介可以檢視為它們提供的部分訊息。 如果傳送者需要讓媒介看到訊息中的部分資訊，但希望確保不會遭到竄改，可以只簽署而不加密。 由於簽章是訊息的一部分，因此最終接收者可以確認已完整接收訊息中的資訊。 有一種案例可能會有根據 Action 標頭值傳送訊息的 SOAP 媒介服務。 根據預設，WCF 不會加密動作值，但是如果使用訊息安全性會簽署它。 因此，此資訊可供所有媒介使用，但是無法變更。  
  
-   支援多重傳輸。 您可以使用許多不同的傳輸來傳送安全訊息，例如具名管道和 TCP，而不必依賴通訊協定來達到安全性。 使用傳輸層級安全性，所有的安全性資訊都會限定在單一特定傳輸連線的範圍內，並且無法從訊息內容本身取得。 不論您使用何種傳輸來傳輸訊息，訊息安全性都可以保護訊息的安全，且安全性內容會直接內嵌在訊息中。  
  
-   支援一整組認證和宣告。 訊息安全性是以 WS-Security 規格為基礎，提供可傳輸 SOAP 訊息內任何類型宣告的可延伸架構。 和傳輸安全性不同的是，您可以使用的驗證機制 (或宣告) 集合不受傳輸功能的限制。 WCF 訊息安全性包括多種類型的驗證和宣告傳輸，而且可以擴充來支援其他類型，視。 例如，基於這些原因，聯合認證案例一定要有訊息安全性。 如需同盟案例 WCF 支援的詳細資訊，請參閱[同盟和發出的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
## <a name="how-message-and-transport-security-compare"></a>如何比較訊息和傳輸安全性  
  
### <a name="pros-and-cons-of-transport-level-security"></a>傳輸層級安全性的優缺點  
 傳輸安全性有下列優點：  
  
-   不需要通訊方瞭解 XML 層級的安全性概念。 這可以增進互通性，例如當使用 HTTPS 來保護通訊安全時。  
  
-   普遍提升效能。  
  
-   提供硬體加速器。  
  
-   可使用資料流。  
  
 傳輸安全性有下列缺點：  
  
-   僅限躍點對躍點。  
  
-   有限且無法延伸的認證集合。  
  
-   與傳輸相關。  
  
### <a name="disadvantages-of-message-level-security"></a>訊息層級安全性的缺點  
 訊息安全性有下列缺點：  
  
-   效能  
  
-   無法使用訊息資料流。  
  
-   需要實作 XML 層級的安全性機制及支援 WS-Security 規格。 這可能會影響互通性。  
  
## <a name="see-also"></a>另請參閱  
 [保護服務和用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [如何：使用傳輸安全性和訊息認證](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft Patterns and Practices，第 3 章： 實作的傳輸與訊息層級安全性](http://go.microsoft.com/fwlink/?LinkId=88897)
