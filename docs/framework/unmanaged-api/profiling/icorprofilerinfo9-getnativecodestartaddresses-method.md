---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973808"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses 方法
  
 假設有 functionId 和 rejitId, 會列舉此程式碼中所有目前存在之已編譯版本的原生程式碼起始位址。   
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 在應傳回其原生程式碼起始位址的函式識別碼。  
  
 `reJitId`  
 [in] 經過 JIT 重新編譯的函式識別。 
  
 `cCodeStartAddresses` \
 [in] `codeStartAddresses` 陣列的大小上限。

 `pcCodeStartAddresses` \
 脫銷可用的位址數目。

 `codeStartAddresses` \
 脫銷的`UINT_PTR`陣列, 其中每一個都是所指定函式的原生主體的起始位址。 

## <a name="remarks"></a>備註  
 啟用階層式編譯時, 函數可能會有一個以上的機器碼主體。 

## <a name="requirements"></a>需求  
 **平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerInfo9 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

