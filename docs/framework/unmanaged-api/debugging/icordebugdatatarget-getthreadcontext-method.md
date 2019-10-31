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
ms.openlocfilehash: 278320391615eddaa8ba878ef87f802f30cddb95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122030"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext 方法
傳回指定之執行緒的目前線程內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>參數  
 `dwThreadID`  
 在要抓取其內容之執行緒的識別碼。 識別碼是由作業系統所定義。  
  
 `contextFlags`  
 在平臺相依旗標的位元組合，表示應該讀取內容的哪個部分。  
  
 `contextSize`  
 [in] `pContext` 的大小。  
  
 `pContext`  
 脫銷將儲存執行緒內容的緩衝區。  
  
## <a name="remarks"></a>備註  
 在 Windows 平臺上，`pContext` 必須是 `CONTEXT` 結構（定義于 WinNT. h 中），適用于[ICorDebugDataTarget：： GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法所指定的電腦類型。 `contextFlags` 必須具有與 `CONTEXT` 結構的 `ContextFlags` 欄位相同的值。 `CONTEXT` 結構是處理器特定的;如需詳細資訊，請參閱 WinNT. h 檔案。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
