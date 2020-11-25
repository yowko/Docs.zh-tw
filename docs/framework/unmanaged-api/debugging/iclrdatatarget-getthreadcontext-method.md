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
ms.openlocfilehash: 35b7bff5d4d778a429ddc1dcd0206e6e8970ee4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703495"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext 方法

取得目標進程中指定執行緒的目前執行內容。 Common language runtime 資料存取服務會呼叫這個方法。  
  
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
 在旗標，指定要傳回內容中的哪些部分。 此實作為會傳回至少內容的這些部分。  
  
 `contextSize`  
 在內容的大小。  
  
 `context`  
 擴展要放置內容的緩衝區指標。  
  
 緩衝區中的資料 `context` 必須採用 Win32 結構的格式 `CONTEXT` 。 內容會指定處理器特定的登錄資料，因此 Win32 結構的定義 `CONTEXT` 取決於處理器的架構。 請參閱 WinNT 標頭檔中的 Win32 `CONTEXT` 結構定義。  
  
## <a name="remarks"></a>備註  

 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
