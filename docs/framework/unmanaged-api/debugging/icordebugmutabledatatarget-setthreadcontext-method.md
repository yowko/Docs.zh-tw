---
title: ICorDebugMutableDataTarget::SetThreadContext 方法
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: a6df6bf030ad339f5d02b95cd191b30db60aa167
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210146"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext 方法
設定執行緒的內容 (登錄值)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>參數  
 `dwThreadID`  
 [in] 作業系統定義的執行緒識別項。  
  
 `contextSize`  
 [in] 所要寫入的 `pContext` 緩衝區大小。  
  
 `pContext`  
 [in] 所要寫入的位元組指標。  
  
## <a name="remarks"></a>備註  
 `SetThreadContext` 方法會針對作業系統定義之 `dwThreadID` 引數所指定的執行緒，更新目前的內容。 內容記錄的格式取決於[ICorDebugDataTarget：： GetPlatform](icordebugdatatarget-getplatform-method.md)方法所指定的平臺。 在 Windows 上，這是[內容](/windows/win32/api/winnt/ns-winnt-arm64_nt_context)結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugMutableDataTarget 介面](icordebugmutabledatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
