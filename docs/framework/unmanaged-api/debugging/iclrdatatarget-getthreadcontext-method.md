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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179173"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext 方法
獲取目標進程中給定執行緒的當前執行上下文。 此方法由通用語言運行時資料訪問服務調用。  
  
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
 [在]目標進程中線程的作業系統識別碼。  
  
 `contextFlags`  
 [在]指定要返回上下文的哪些部分的標誌。 實現將至少返回上下文的這些部分。  
  
 `contextSize`  
 [在]上下文的大小。  
  
 `context`  
 [出]指向要在其中放置上下文的緩衝區的指標。  
  
 緩衝區中`context`的資料必須採用 Win32`CONTEXT`結構的格式。 上下文指定特定于處理器的寄存器資料，因此 Win32`CONTEXT`結構的定義取決於處理器的體系結構。 有關 Win32`CONTEXT`結構的定義，請參閱 WinNT.h 標標頭檔。  
  
## <a name="remarks"></a>備註  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** ClrData.idl， ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
