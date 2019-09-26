---
title: CLRDataCreateInstance 函式
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d44f9b5dc42147959d3f1d127a64d39258f515
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274269"
---
# <a name="clrdatacreateinstance-function"></a>CLRDataCreateInstance 函式
為指定的目標專案建立介面物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>參數  
 `iid`  
 在要具現化之介面的識別碼。  
  
 `target`  
 在使用者實[ICLRDataTarget](iclrdatatarget-interface.md)物件的指標，表示要建立介面物件的目標專案。  
  
 `iface`  
 脫銷傳回之介面物件的位址指標。  
  
## <a name="remarks"></a>備註  
 `ICLRDataTarget`物件是由偵錯工具的寫入器所執行。 此實作為相依于所表示的目標專案類型。 目標專案可能是進程、記憶體傾印、遠端電腦等等。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](debugging-global-static-functions.md)
