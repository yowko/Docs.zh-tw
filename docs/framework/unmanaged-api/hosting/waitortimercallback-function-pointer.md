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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65af5303468904ee40da4d567381782af70bfb38
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776494"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK 函式指標
指向主應用程式等候處理的函式 (<xref:System.Threading.WaitHandle>) 已收到信號或逾時。  
  
 在.NET Framework 4 中，已被取代此函式指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpParameter`  
 [in]物件，包含主機所定義的資訊指標。  
  
 `TimerOrWaitFired`  
 [in]`true`如果逾時等候控制代碼，或`false`，表示收到信號。  
  
## <a name="remarks"></a>備註  
 函式，其中`WAITORTIMERCALLBACK`點是回呼函式，而且必須在裝載應用程式寫入器實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorWks.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
