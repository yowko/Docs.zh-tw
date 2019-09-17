---
title: ICorProfilerInfo4::GetCodeInfo3 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912708"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 方法
取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>參數  
 `functionID`  
 [in] 與機器碼關聯的函式識別碼。  
  
 `reJitId`  
 [in] 經過 JIT 重新編譯的函式識別。  
  
 `cCodeInfos`  
 [in] `codeInfos` 陣列的大小。  
  
 `pcCodeInfos`  
 脫銷可用[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構總數的指標。  
  
 `codeInfos`  
 [out] 呼叫者提供的緩衝區。 方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。  
  
## <a name="remarks"></a>備註  
 方法類似于 [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)，不同之處在于它會取得包含指定 IP 位址之函式的 JIT 重新編譯識別碼。`GetCodeInfo3`  
  
> [!NOTE]
> `GetCodeInfo3`可以觸發垃圾收集，而[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)則不會。 如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT。  
  
 範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。  
  
 傳回`GetCodeInfo3`之後，您必須確認`codeInfos`緩衝區夠大，足以包含所有的[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構。 若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。 如果`cCodeInfos`除以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) `codeInfos` `cCodeInfos`結構的大小小於`GetCodeInfo3` ，請配置較大的緩衝區，以新的、較大的大小來更新，然後再呼叫一次。 `pcCodeInfos`  
  
 或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo3`，以取得正確的緩衝區大小。 接著，您可以將`codeInfos`緩衝區大小設定為中`pcCodeInfos`傳回的值，乘以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構的大小，然後再呼叫`GetCodeInfo3`一次。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl，Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetCodeInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
