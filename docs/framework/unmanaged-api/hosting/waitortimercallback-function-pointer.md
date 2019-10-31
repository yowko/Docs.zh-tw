---
title: WAITORTIMERCALLBACK 函式指標
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: db6a20dee21b6c8bbd55fa9b52a159a00fe310d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092029"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK 函式指標
Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.  
  
 This function pointer has been deprecated in the .NET Framework 4.  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpParameter`  
 [in] A pointer to an object that contains information defined by the host.  
  
 `TimerOrWaitFired`  
 [in] `true` if the wait handle timed out, or `false` if it was signaled.  
  
## <a name="remarks"></a>備註  
 The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** MSCorEE.h  
  
 **Library:** MSCorWks.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
