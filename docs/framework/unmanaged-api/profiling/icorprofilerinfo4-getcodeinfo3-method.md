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
ms.openlocfilehash: 164e042ab0f1a275ff07b917658024e22c2d7b0b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862020"
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
 脫銷可用[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構總數的指標。  
  
 `codeInfos`  
 [out] 呼叫者提供的緩衝區。 方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。  
  
## <a name="remarks"></a>備註  
 方法類似于 [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)，不同之處在于它會取得包含指定 IP 位址之函式的 JIT 重新編譯識別碼。`GetCodeInfo3`  
  
> [!NOTE]
> `GetCodeInfo3` 可以觸發垃圾收集，而[GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)則不會。 如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT。  
  
 範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。  
  
 `GetCodeInfo3` 傳回之後，您必須確認 `codeInfos` 緩衝區夠大，足以包含所有[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構。 若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。 如果 `cCodeInfos` 除以[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構的大小小於 `pcCodeInfos`，請配置較大的 `codeInfos` 緩衝區、以新的、較大的大小更新 `cCodeInfos`，然後再次呼叫 `GetCodeInfo3`。  
  
 或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo3`，以取得正確的緩衝區大小。 接著，您可以將 `codeInfos` 緩衝區大小設定為 `pcCodeInfos`中傳回的值，乘以[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構的大小，然後再次呼叫 `GetCodeInfo3`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetCodeInfo2 方法](icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
