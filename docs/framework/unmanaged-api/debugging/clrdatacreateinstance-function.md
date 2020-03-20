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
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179355"
---
# <a name="clrdatacreateinstance-function"></a>CLRDataCreateInstance 函式
為指定的目標項創建介面物件。  
  
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
 [在]要具現化的介面的識別碼。  
  
 `target`  
 [在]指向使用者實現的[ICLRDataTarget](iclrdatatarget-interface.md)物件的指標，該物件表示要為其創建介面物件的目標項。  
  
 `iface`  
 [出]指向返回介面物件位址的指標。  
  
## <a name="remarks"></a>備註  
 該`ICLRDataTarget`物件由調試應用程式的編寫器實現。 實現取決於表示的目標項的類型。 目標項可以是進程、記憶體傾印、遠端電腦等。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** ClrData.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](debugging-global-static-functions.md)
