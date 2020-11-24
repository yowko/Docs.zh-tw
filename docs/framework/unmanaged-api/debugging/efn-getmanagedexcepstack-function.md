---
title: _EFN_GetManagedExcepStack 函式
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: b86277836b1be48c9f8020d59071aba8c5b1e457
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676227"
---
# <a name="_efn_getmanagedexcepstack-function"></a>\_EFN \_ GetManagedExcepStack 函式

給予 Managed 例外狀況物件位址後，會傳回內部包含堆疊追蹤版本的字串。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a>參數  

 `Client`  
 在正在進行調試的用戶端。  
  
 `StackObjAddr`  
 在衍生自的 managed 物件指標 <xref:System.Exception> 。  
  
 szStackString  
 擴展傳回的字串。  
  
 `cbString`  
 擴展字串緩衝區中的可用字元數。  
  
## <a name="remarks"></a>備註  

 如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE 具有0xa0 的設備值和錯誤碼0x1000。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](debugging-global-static-functions.md)
