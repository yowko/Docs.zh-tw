---
title: "在聯合案例中混合信任通信協定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7031e222b152bfa61e13e0e4a44b5ad9418b07c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>在聯合案例中混合信任通信協定
有些情況下，聯合用戶端會與信任版本不相同的服務和安全性權杖服務 (STS) 進行通訊。 WSDL 服務可包含 `RequestSecurityTokenTemplate` 判斷提示 (Assertion)，其中 WS-Trust 項目的版本與 STS 不同。 在這個情況下，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端會將從 `RequestSecurityTokenTemplate` 收到的 WS-Trust 元素轉換成符合 STS 信任版本。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 只會處理標準繫結的不相符信任版本。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以識別的所有標準演算法參數都包含在標準繫結中。 本主題將透過該服務和 STS 之間的各種信任設定來說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的行為。  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP Feb 2005 和 STS Feb 2005  
 信賴憑證者 (Relying Party，RP) WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含下列項目：  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 用戶端組態檔包含參數清單。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 無法分辨用戶端和服務的參數，因此它會加入所有參數，並以 `RequestSecurityTokenTemplate` (RST) 傳送這些參數。  
  
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
  
 如果 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元素中有 `EncryptionAlgorithm`、`CanonicalizationAlgorithm` 和 `KeyWrapAlgorithm` 元素，則 `SecondaryParameters` 會在 RST 下從最上層元素移除這些元素。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將 `SecondaryParameters` 元素原封不動地附加至傳出的 RST。  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP Trust Feb 2005 和 STS Trust 1.3  
 RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 用戶端組態檔包含參數清單。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 無法從用戶端組態檔分辨服務和用戶端的參數。 因此 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將所有參數轉換成 Trust 1.3 版命名空間 (Namespace)。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會處理 `KeyType`、`KeySize` 和 `TokenType` 項目，如下所示：  
  
-   下載 WSDL，建立繫結，然後指派 RP 參數中的 `KeyType`、`KeySize` 和 `TokenType`。 用戶端組態檔隨即產生。  
  
-   現在用戶端可以變更組態檔中的任何參數。  
  
-   在執行階段期間，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將指定的所有參數複製到用戶端組態檔的 `AdditionalTokenParameters` 區段，但不包括 `KeyType`、`KeySize` 和 `TokenType`，因為這些參數已經在產生組態檔期間執行過任務。  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將指定於 `SecondaryParameters` 區段內的所有參數複製到最上層 RST 項目，但是不會將這些參數轉換成 2005 WS-Trust 命名空間。
