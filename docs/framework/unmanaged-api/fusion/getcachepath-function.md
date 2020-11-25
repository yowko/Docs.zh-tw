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
ms.openlocfilehash: c22f0701cfda4523f595366a97435ef8da08b0cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724464"
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
 在 [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) 值，表示快取元件的來源。  
  
 `pwzCachePath`  
 擴展傳回的路徑指標。  
  
 `pcchPath`  
 [in，out]要求的最大長度， `pwzCachePath` 以及傳回時的實際長度 `pwzCachePath` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ASM_CACHE_FLAGS 列舉](asm-cache-flags-enumeration.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
