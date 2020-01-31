---
title: PFN_CLRDataCreateInstance 函式指標
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: 433f34447d3bd1a57ca1e289cb0eab3facac2c69
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790362"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance 函式指標
指向可為指定的目標專案建立介面物件的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
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
 `ICLRDataTarget` 物件是由偵錯工具的寫入器所執行。 此實作為相依于所表示的目標專案類型。 目標專案可能是進程、記憶體傾印、遠端電腦等等。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯全域靜態函式](debugging-global-static-functions.md)
