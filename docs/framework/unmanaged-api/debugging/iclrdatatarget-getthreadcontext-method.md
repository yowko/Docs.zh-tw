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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bac7e46bd499a680906e67b41175e099f96ecc3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604440"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext 方法
取得目標處理序中指定的執行緒目前的執行內容。 這個方法是由通用語言執行階段資料存取服務呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
#### <a name="parameters"></a>參數  
 `threadID`  
 [in]目標處理序中的執行緒作業系統識別項。  
  
 `contextFlags`  
 [in]旗標，指定要傳回的內容中哪些部分。 實作會傳回至少這些組件的內容。  
  
 `contextSize`  
 [in]內容的大小。  
  
 `context`  
 [out]在其中放置內容緩衝區的指標。  
  
 中的資料`context`Win32 的格式必須是緩衝區`CONTEXT`結構。 這個內容會指定特定處理器的暫存器資料，因此 Win32 定義`CONTEXT`結構取決於處理器架構。 請參閱 WinNT.h 標頭檔來定義的 Win32`CONTEXT`結構。  
  
## <a name="remarks"></a>備註  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl, ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
