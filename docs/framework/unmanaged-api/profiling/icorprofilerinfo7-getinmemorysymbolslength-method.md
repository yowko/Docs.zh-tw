---
title: ICorProfilerInfo7：： GetInMemorySymbolsLength 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 46ffa5cb4fac6988240d32cb1939cc25bdf0a412
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686068"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7：： GetInMemorySymbolsLength 方法

[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 傳回記憶體中符號資料流程的長度。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>參數  

 `moduleId`  
 在包含記憶體中資料流程之模組的識別碼。  
  
 pCountSymbolBytes  
 擴展 `DWORD` 值的指標，當方法傳回時，會包含資料流程的長度（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 `S_OK`如果可以判斷記憶體資料流程的長度，此方法會傳回，即使它是零 (0) 。  
  
 如果是使用建立方法，則方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC` <xref:System.Reflection.Emit?displayProperty=nameWithType> 。  
  
## <a name="remarks"></a>備註  

 如果模組有記憶體內的符號，資料流程的長度就會放在中 `pCountSymbolBytes` 。 如果模組沒有記憶體內的符號，則為 `*pCountSymbolBytes = 0` 。  
  
> [!NOTE]
> 目前的執行不支援反映。發出。 如果模組是使用反映來建立，則方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo7 介面](icorprofilerinfo7-interface.md)
