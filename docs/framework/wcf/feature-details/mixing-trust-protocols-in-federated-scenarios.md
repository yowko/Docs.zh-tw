---
title: 在聯合案例中混合信任通信協定
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: ce5c3a1875d84d98068dcc78d8346a88bc0b28f3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182902"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>在聯合案例中混合信任通信協定
有些情況下，聯合用戶端會與信任版本不相同的服務和安全性權杖服務 (STS) 進行通訊。 WSDL 服務可包含 `RequestSecurityTokenTemplate` 判斷提示 (Assertion)，其中 WS-Trust 項目的版本與 STS 不同。 在這種情況下，Windows Communication Foundation (WCF) 用戶端會將從收到的 Ws-trust 元素轉換`RequestSecurityTokenTemplate`成符合 STS 信任版本。 WCF 會處理只能在標準繫結時不相符的信任版本。 WCF 所辨識的所有標準演算法參數是標準繫結的一部分。 本主題說明使用各種服務與 STS 之間的信任設定 WCF 行為。  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP Feb 2005 和 STS Feb 2005  
 信賴憑證者 (Relying Party，RP) WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含下列項目：  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 用戶端組態檔包含參數清單。  
  
 WCF 無法分辨用戶端和服務的參數;它將所有參數，並將它們傳送`RequestSecurityTokenTemplate`(RST)。  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP Trust 1.3 和 STS Trust 1.3  
 RP WSDL 在其 `RequestSecurityTokenTemplate` 區段內包含了下列項目：  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 用戶端組態檔所包含的 `secondaryParameters` 項目，會包裝 RP 所指定的參數。  
  
 WCF 會移除`EncryptionAlgorithm`，`CanonicalizationAlgorithm`並`KeyWrapAlgorithm`項目最上層的項目，如果這些是存在於在 RST 下從`SecondaryParameters`項目。 WCF 會附加`SecondaryParameters`傳出的 RST 項目。  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP Trust Feb 2005 和 STS Trust 1.3  
 RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 用戶端組態檔包含參數清單。  
  
 從用戶端組態檔中，WCF 無法分辨服務和用戶端的參數而定。 因此 WCF 會將所有參數都轉換成信任 1.3 版命名空間。  
  
 WCF 的控制代碼`KeyType`， `KeySize`，和`TokenType`項目，如下所示：  
  
-   下載 WSDL，建立繫結，然後指派 RP 參數中的 `KeyType`、`KeySize` 和 `TokenType`。 用戶端組態檔隨即產生。  
  
-   現在用戶端可以變更組態檔中的任何參數。  
  
-   在執行階段，WCF 會複製到指定的所有參數`AdditionalTokenParameters`以外的用戶端組態檔區段`KeyType`，`KeySize`和`TokenType`，這些參數會包含在組態檔，因此層代。  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP Trust 1.3 和 STS Trust Feb 2005  
 RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 用戶端組態檔所包含的 `secondaryParamters` 項目，會包裝 RP 所指定的參數。  
  
 WCF 會將內指定的所有參數都複製`SecondaryParameters`區段最上層 RST 項目，但不會將它們轉換成 2005 Ws-trust 命名空間。
