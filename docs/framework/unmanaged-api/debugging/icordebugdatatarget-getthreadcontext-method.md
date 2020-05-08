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
ms.openlocfilehash: 79708aa5a2abcb8d7465f82a8beb918484c193b9
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976547"
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
 在 Windows 平臺上`pContext` ，必須是`CONTEXT`適用于[ICorDebugDataTarget：： GetPlatform](icordebugdatatarget-getplatform-method.md)方法所指定之電腦類型的結構（定義于 WinNT. h）。 `contextFlags`必須具有與`ContextFlags` `CONTEXT`結構的欄位相同的值。 結構`CONTEXT`是處理器特定的;如需詳細資訊，請參閱 WinNT. h 檔案。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugDataTarget 介面](icordebugdatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
