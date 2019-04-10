---
title: ICorDebugILCode2::GetInstrumentedILMap 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4197b018ea85402762a8591b40f3503c02af3974
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222870"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 將對應從分析工具檢測中繼語言 (IL) 位移傳回至此執行個體的原始方法 IL 位移。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>參數  
 cMap  
 [in] `map` 陣列的儲存體容量。 如需詳細資訊，請參閱＜備註＞一節。  
  
 pcMap  
 [out]COR_IL_MAP 值寫入至對應陣列數目。  
  
 map  
 [out]可提供有關對應從分析工具檢測 IL 的原始方法 il COR_IL_MAP 值的陣列。  
  
## <a name="remarks"></a>備註  
 如果分析工具藉由呼叫設定的對應[icorprofilerinfo:: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)方法，偵錯工具可以呼叫此方法來擷取對應，並計算 IL 位移堆疊時，在內部使用對應追蹤及變數存留期。  
  
 如果`cMap`為 0 並`pcMap`是非**null**，`pcMap`設為 可用的 COR_IL_MAP 值數目。 如果 `cMap` 不是零，則代表 `map` 陣列的儲存體容量。 方法傳回時，`map`會包含最多`cMap`項目，並`pcMap`設定為實際寫入至 COR_IL_MAP 值數目`map`陣列。  
  
 如果 IL 未經檢測，或是分析工具未提供對應，此方法會傳回 `S_OK`，並將 `pcMap` 設為 0。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
