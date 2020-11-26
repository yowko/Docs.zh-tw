---
title: 在聯合案例中混合信任通信協定
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248171"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>在聯合案例中混合信任通信協定

有些情況下，聯合用戶端會與信任版本不相同的服務和安全性權杖服務 (STS) 進行通訊。 WSDL 服務可包含 `RequestSecurityTokenTemplate` 判斷提示 (Assertion)，其中 WS-Trust 項目的版本與 STS 不同。 在這種情況下，Windows Communication Foundation (WCF) 用戶端會將從收到的 WS-Trust 元素轉換 `RequestSecurityTokenTemplate` 成符合 STS 信任版本。 WCF 只會處理標準系結的不相符信任版本。 WCF 可辨識的所有標準演算法參數都是標準系結的一部分。 本主題說明服務和 STS 之間有各種信任設定的 WCF 行為。  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP Feb 2005 和 STS Feb 2005  

 信賴憑證者 (Relying Party，RP) WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含下列項目：  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 用戶端組態檔包含參數清單。  
  
 WCF 無法區分用戶端與服務參數;它會新增所有參數，並將它們傳送至 `RequestSecurityTokenTemplate` (RST) 。  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP Trust 1.3 和 STS Trust 1.3  

 RP WSDL 在其 `RequestSecurityTokenTemplate` 區段內包含了下列項目：  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 用戶端組態檔所包含的 `secondaryParameters` 項目，會包裝 RP 所指定的參數。  
  
 `EncryptionAlgorithm`如果專案內有，WCF `CanonicalizationAlgorithm` `KeyWrapAlgorithm` 會從 RST 下的最上層元素移除、和專案 `SecondaryParameters` 。 WCF 會將 `SecondaryParameters` 元素附加至未修改的外寄 RST。  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP Trust Feb 2005 和 STS Trust 1.3  

 RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 用戶端組態檔包含參數清單。  
  
 從用戶端設定檔中，WCF 無法區分服務與用戶端參數。 因此，WCF 會將所有參數轉換為信任版本1.3 命名空間。  
  
 WCF 會處理 `KeyType` 、和元素，如下所示 `KeySize` `TokenType` ：  
  
- 下載 WSDL，建立繫結，然後指派 RP 參數中的 `KeyType`、`KeySize` 和 `TokenType`。 用戶端組態檔隨即產生。  
  
- 現在用戶端可以變更組態檔中的任何參數。  
  
- 在執行時間期間，WCF 會將所有指定的參數複製到 `AdditionalTokenParameters` 用戶端設定檔的區段中，但和除外， `KeyType` `KeySize` `TokenType` 因為這些參數是在設定檔產生期間所考慮的。  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP Trust 1.3 和 STS Trust Feb 2005  

 RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 用戶端組態檔所包含的 `secondaryParamters` 項目，會包裝 RP 所指定的參數。  
  
 WCF 會將區段內指定的所有參數複製 `SecondaryParameters` 到最上層 RST 元素，但不會將它們轉換成 2005 WS-Trust 命名空間。
