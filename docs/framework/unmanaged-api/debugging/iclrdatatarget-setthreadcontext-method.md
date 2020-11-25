---
title: ICLRDataTarget::SetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: c135c051637858682c22db58d562e1d50eea562b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723697"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext 方法

在目標進程中，設定指定之執行緒的目前內容。 Common language runtime (CLR) 資料存取服務會呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>參數  

 `threadID`  
 在目標進程中線程的作業系統識別碼。  
  
 `contextSize`  
 在內容的大小。  
  
 `context`  
 在包含內容之緩衝區的指標。  
  
 緩衝區中的資料 `context` 將採用 Win32 結構的格式 `CONTEXT` 。 內容會指定處理器特定的登錄資料，因此 Win32 結構的定義 `CONTEXT` 取決於處理器的架構。 請參閱 WinNT 標頭檔中的 Win32 `CONTEXT` 結構定義。  
  
## <a name="remarks"></a>備註  

 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
