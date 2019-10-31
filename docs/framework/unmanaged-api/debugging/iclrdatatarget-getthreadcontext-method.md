---
title: ICLRDataTarget::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 0d34577f0f785bc851646423b8cd732ab4d1dae0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113855"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext 方法
取得目標進程中指定執行緒的目前執行內容。 這個方法是由 common language runtime 資料存取服務所呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>參數  
 `threadID`  
 在目標進程中線程的作業系統識別碼。  
  
 `contextFlags`  
 在指定要傳回之內容部分的旗標。 此執行將會至少傳回內容的這些部分。  
  
 `contextSize`  
 在內容的大小。  
  
 `context`  
 脫銷要放置內容之緩衝區的指標。  
  
 `context` 緩衝區中的資料必須是 Win32 `CONTEXT` 結構的格式。 內容會指定處理器特定的暫存器資料，因此 Win32 `CONTEXT` 結構的定義取決於處理器的架構。 如需 Win32 `CONTEXT` 結構的定義，請參閱 WinNT 標頭檔。  
  
## <a name="remarks"></a>備註  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
