---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f3c0a3525c87fbf39199c15a6619ff4a0d2acc42
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973848"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3 方法
  
  將 managed 程式碼指令指標對應至 FunctionID。 這個方法適用于動態和非動態方法。    
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```  
  
#### <a name="parameters"></a>參數  
 `ip`  
 在Managed 程式碼中的指令指標。  

 `pFunctionId`  
 脫銷函數識別碼。  
  
 `pReJitId`  
 脫銷函式之 JIT 重新編譯版本的識別。  
  
## <a name="remarks"></a>備註  
 這個方法適用于動態和非動態方法。 它是[GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)的超集合, 僅適用于具有中繼資料的函式。
  

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本:** [!包含[net_current_v472plus](../../../../includes/net-current-v472plus.md)  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerInfo8 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

