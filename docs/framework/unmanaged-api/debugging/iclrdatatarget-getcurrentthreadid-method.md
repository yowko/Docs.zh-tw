---
title: ICLRDataTarget::GetCurrentThreadID 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: 3a355822710394e9351f10be78dea283e2e9907c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703586"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a>ICLRDataTarget::GetCurrentThreadID 方法

取得目前線程的作業系統識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a>參數  

 `threadID`  
 擴展目標進程之目前線程的作業系統識別碼指標。  
  
## <a name="remarks"></a>備註  

 如果目標進程沒有目前的執行緒， `GetCurrentThreadID` 方法可能會失敗。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
