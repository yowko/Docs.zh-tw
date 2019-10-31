---
title: GetCachePath 函式
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: 13e1468ef5a48f18910c1f8082cdd7c4849da14a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132689"
---
# <a name="getcachepath-function"></a>GetCachePath 函式
使用指定的旗標，取得快取元件的路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>參數  
 `dwCacheFlags`  
 在[ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)值，表示快取元件的來源。  
  
 `pwzCachePath`  
 脫銷傳回到路徑的指標。  
  
 `pcchPath`  
 [in、out]要求的最大長度 `pwzCachePath`，並在傳回時，`pwzCachePath`的實際長度。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ASM_CACHE_FLAGS 列舉](asm-cache-flags-enumeration.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
