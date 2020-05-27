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
ms.openlocfilehash: ee5dd611888ec52e360ef45fab4c01e9c5b2d6bb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009442"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK 函式指標
指向函式，該函式會通知主機等候控制碼（ <xref:System.Threading.WaitHandle> ）已發出信號或超時。  
  
 這個函式指標在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpParameter`  
 在物件的指標，其中包含主機所定義的資訊。  
  
 `TimerOrWaitFired`  
 [in] `true`如果等候控制碼超時，則為， `false` 如果已收到信號，則為。  
  
## <a name="remarks"></a>備註  
 點的函式 `WAITORTIMERCALLBACK` 是回呼函式，必須由主控應用程式的寫入器來執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscorwks.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
