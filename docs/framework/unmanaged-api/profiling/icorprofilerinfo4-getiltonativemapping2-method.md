---
title: ICorProfilerInfo4::GetILToNativeMapping2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad83c376816c2203cd78a83b8664fa90b0e109fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780820"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 方法
針對指定函式的 JIT 重新編譯版本中所包含的程式碼，取得從 Microsoft Intermediate Language (MSIL) 位移到原生位移的對應。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in] 包含程式碼的函式 ID。  
  
 `pReJitId`  
 [in] 經過 JIT 重新編譯的函式識別。 身分識別必須是在.NET Framework 4.5 中的零。  
  
 `cMap`  
 [in] `map` 陣列的大小上限。  
  
 `pcMap`  
 [out]可用的 COR_DEBUG_IL_TO_NATIVE_MAP 結構總數。  
  
 `map`  
 [out] `COR_DEBUG_IL_TO_NATIVE_MAP` 結構的陣列，每個結構都有指定位移。           `GetILToNativeMapping2` 方法傳回之後，`map` 將會包含部分或所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。  
  
## <a name="remarks"></a>備註  
 `GetILToNativeMapping2` 類似於[icorprofilerinfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)方法，不同之處在於它可讓分析工具指定重新編譯的函式的識別碼在未來版本。  
  
> [!NOTE]
>  [Icorprofilerfunctioncontrol:: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)因此已被 JIT 重新編譯的函式不能有不同的 IL-原生對應，在.NET Framework 4.5 中，未實作方法原本已編譯的函式。 因此，`GetILToNativeMapping2`無法呼叫具有非零 JIT 重新編譯識別碼，在.NET Framework 4.5。  
  
           `GetILToNativeMapping2` 方法會傳回 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構的陣列。 陣列中的項目可以有傳達原生指令的特定範圍對應至特殊的區域，程式碼 （例如，初構），其`ilOffset`欄位設定為值[CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)列舉型別。  
  
           `GetILToNativeMapping2` 傳回之後，您必須確認 `map` 緩衝區夠大，可以包含所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。 若要這樣做，請比較 `cMap` 的值與 `pcMap` 參數的值。 如果 `pcMap` 值乘以 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構的大小之後大於 `cMap`，請配置較大的 `map` 緩衝區，以新的較大大小更新 `cMap`，然後重新呼叫 `GetILToNativeMapping2`。  
  
 或者，您也可以先使用長度為零的 `map` 緩衝區來呼叫 `GetILToNativeMapping2`，以取得正確的緩衝區大小。 接著您就可以將緩衝區大小設定為 `pcMap` 中傳回的值，並再次呼叫 `GetILToNativeMapping2`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetILToNativeMapping 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
