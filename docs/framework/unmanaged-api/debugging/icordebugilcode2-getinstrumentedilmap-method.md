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
ms.openlocfilehash: c6fdb7040620bb7a5b6aea6e0dc41e08d6f346d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210354"
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
 [in] `map` 陣列的儲存體容量。 如需詳細資訊，請參閱「備註」一節。  
  
 pcMap  
 [out] 寫入至對應陣列的 COR_IL_MAP 值數目。  
  
 map  
 [out] COR_IL_MAP 值陣列，這些值提供從分析工具檢測 IL 對應至原始方法 IL 的相關資訊。  
  
## <a name="remarks"></a>備註  
 如果分析工具藉由呼叫[ICorProfilerInfo：： SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)方法來設定對應，偵錯工具就可以呼叫這個方法來抓取對應，並在計算堆疊追蹤和變數存留期的 IL 位移時，在內部使用對應。  
  
 如果 `cMap` 為0，且 `pcMap` 為非**null**， `pcMap` 則會設定為可用 COR_IL_MAP 值的數目。 如果 `cMap` 不是零，則代表 `map` 陣列的儲存體容量。 當此方法傳回時， `map` 會包含最多個 `cMap` 專案，而且 `pcMap` 會設定為實際寫入陣列的 COR_IL_MAP 值數目 `map` 。  
  
 如果 IL 未經檢測，或是分析工具未提供對應，此方法會傳回 `S_OK`，並將 `pcMap` 設為 0。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo::SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2 介面](icordebugilcode2-interface.md)
- [偵錯介面](debugging-interfaces.md)
