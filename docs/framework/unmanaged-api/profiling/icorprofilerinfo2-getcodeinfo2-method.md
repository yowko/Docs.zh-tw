---
title: ICorProfilerInfo2::GetCodeInfo2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 04ce9ebded4be7ac3b20a4ceb78dd02294bbff4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502889"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 方法
取得與指定 `FunctionID` 相關聯的原生程式碼範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>參數  
 `functionID`  
 [in] 與機器碼關聯的函式識別碼。  
  
 `cCodeInfos`  
 [in] `codeInfos` 陣列的大小。  
  
 `pcCodeInfos`  
 脫銷可用[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)結構總數的指標。  
  
 `codeInfos`  
 [out] 呼叫者提供的緩衝區。 方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。  
  
## <a name="remarks"></a>備註  
 範圍是以遞增的 Microsoft 中繼語言 (MSIL) 位移順序來排序。  
  
 `GetCodeInfo2` 傳回之後，您必須確認 `codeInfos` 緩衝區夠大，可以包含所有 `COR_PRF_CODE_INFO` 結構。 若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。 如果 `cCodeInfos` 除以 `COR_PRF_CODE_INFO` 結構的大小之後小於`pcCodeInfos`，請配置較大的 `codeInfos` 緩衝區，以新的較大大小更新 `cCodeInfos`，然後重新呼叫 `GetCodeInfo2`。  
  
 或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo2`，以取得正確的緩衝區大小。 您可以將 `codeInfos` 緩衝區大小設定為 `pcCodeInfos` 中傳回的值，乘以 `COR_PRF_CODE_INFO` 結構的大小，然後重新呼叫 `GetCodeInfo2`。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetCodeInfo3 方法](icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
