---
title: ICorDebugDataTarget::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2db073f6bde3ded27f8e1aa41bfcb87e764745f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748938"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext 方法
傳回針對指定的執行緒目前的執行緒內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>參數  
 `dwThreadID`  
 [in]要擷取之內容的執行緒識別碼。 識別碼是由作業系統定義的。  
  
 `contextFlags`  
 [in]表示應讀取內容的哪些部分的平台相依旗標的位元組合。  
  
 `contextSize`  
 [in] `pContext` 的大小。  
  
 `pContext`  
 [out]將儲存執行緒內容緩衝區。  
  
## <a name="remarks"></a>備註  
 在 Windows 平台，`pContext`必須是`CONTEXT`（在 WinNT.h 中定義） 的結構，這是適用於所指定的機器類型[icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法。 `contextFlags` 必須有相同的值，如同`ContextFlags`欄位`CONTEXT`結構。 `CONTEXT`結構是處理器特定; 請參閱 WinNT.h 檔案，如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
