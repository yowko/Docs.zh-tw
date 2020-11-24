---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: b6852519da6cf4e12669aa2efa24862053adbc03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674238"
---
# <a name="axl_authenticode_timestamper_info-structure"></a>AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構

定義 Authenticode 時間戳記程式資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`cbSize`|此結構的大小。|  
|`dwError`|錯誤碼。|  
|`algHash`|雜湊演算法。|  
|`ftTimestamp`|時間戳記的時間。|  
|`pChainContext`|時間戳記程式的鏈結內容。  請參閱 [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) 結構。|  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](index.md)
