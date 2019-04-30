---
title: ICorDebugILCode::GetEHClauses 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995544"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 傳回針對此中繼語言 (IL) 所定義之例外狀況處理 (EH) 子句清單的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>參數  
 `cClauses`  
 [in] `clauses` 陣列的儲存體容量。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `pcClauses`  
 [out] 其資訊寫入至 `clauses` 陣列的子句數。  
  
 子句  
 [out]陣列[CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)包含有關例外狀況處理子句針對此 IL 定義的物件。  
  
## <a name="remarks"></a>備註  
 如果`cClauses`為 0 並`pcClauses`是非**null**，`pcClauses`設為 可用的例外狀況處理子句數。 如果 `cClauses` 不是零，則代表 `clauses` 陣列的儲存體容量。 傳回方法時，`clauses` 會包含 `cClauses` 項目的最大值，且 `pcClauses` 會設為實際寫入至 `clauses` 陣列的子句數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugILCode 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [CorDebugEHClause 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
