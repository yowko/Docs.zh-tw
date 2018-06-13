---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c89845008307e4cfb00d0f9b9a168a43ba5378c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402359"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a>AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構
定義 Authenticode 時間戳記程式資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`cbSize`|此結構的大小。|  
|`dwError`|錯誤碼。|  
|`algHash`|雜湊演算法。|  
|`ftTimestamp`|時間戳記的時間。|  
|`pChainContext`|時間戳記程式的鏈結內容。  請參閱[CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx)結構。|  
  
## <a name="see-also"></a>另請參閱  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
