---
title: GetPublicKeyToken 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: e41be6407076a2609a83a5be3b0c42d28914ec38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720338"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken 方法

抓取給定 keyfile 或金鑰容器的公開金鑰 token。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `pszKeyFile`  
 金鑰的檔案名。  
  
 `pszKeyContainer`  
 金鑰容器的名稱。  
  
 `pvPublicKeyToken`  
 要儲存金鑰權杖的位址。  
  
 `pcbPublicKeyToken`  
 指定所表示之緩衝區的大小（以位元組為單位） `pvPublicKeyToken` 。 傳回時，包含實際使用的位元組數目。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
