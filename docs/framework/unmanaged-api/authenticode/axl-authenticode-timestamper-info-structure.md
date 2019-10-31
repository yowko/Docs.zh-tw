---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 036397928703aea6199a59ae9c1e66153c30ec7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132496"
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`cbSize`|此結構的大小。|  
|`dwError`|錯誤碼。|  
|`algHash`|雜湊演算法。|  
|`ftTimestamp`|時間戳記的時間。|  
|`pChainContext`|時間戳記程式的鏈結內容。  請參閱[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context)結構。|  
  
## <a name="see-also"></a>請參閱

- [Authenticode](index.md)
