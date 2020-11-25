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
ms.openlocfilehash: 74256f35804ff59f04952a1ac20ac7866e8f5683
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732810"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK 函式指標

指向函式，該函式會通知主機等候控制碼 (<xref:System.Threading.WaitHandle>) 已發出信號或已超時。  
  
 在 .NET Framework 4 中，此函式指標已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>參數  

 `lpParameter`  
 在物件的指標，該物件包含主機所定義的資訊。  
  
 `TimerOrWaitFired`  
 [in] `true` 如果等候控制碼超時，或 `false` 已收到信號。  
  
## <a name="remarks"></a>備註  

 指向函式的函式 `WAITORTIMERCALLBACK` 是回呼函式，而且必須由主控應用程式的寫入器實作為。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorWks.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
