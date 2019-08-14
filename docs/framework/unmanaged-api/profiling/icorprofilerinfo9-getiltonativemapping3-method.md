---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 46ceef43806fda9956797935c5eeec61f865dc6e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973788"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9:: GetILToNativeMapping3 方法
  
 假設機器碼的起始位址, 會傳回這個程式碼編譯版本的原生到 IL 對應資訊。   
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```  
  
#### <a name="parameters"></a>參數  
 `pNativeCodeStartAddress` \
 在原生函式開頭的指標。

 `cMap` \
 [in] `map` 陣列的大小上限。 

 `pcMap` \
 脫銷可用的 COR_DEBUG_IL_TO_NATIVE_MAP 結構總數。

 `map` \
 脫銷[COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md)結構的陣列, 其中每一個都會指定位移。           `GetILToNativeMapping3` 方法傳回之後，`map` 將會包含部分或所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。

## <a name="remarks"></a>備註  
 啟用階層式編譯時, 方法可能會有一個以上的機器碼主體。 [ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)會傳回所有機器碼主體的起始位址。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerInfo9 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

