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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff2ddb1e98f3455c6915acf8149f528176228425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765462"
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance 函式指標
指向函式來建立指定的目標項目介面物件。  
  
## <a name="syntax"></a>語法  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>參數  
 `iid`  
 [in]要具現化的介面識別項。  
  
 `target`  
 [in]使用者實作的指標[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)物件，表示要建立的介面物件的目標項目。  
  
 `iface`  
 [out]傳回的介面物件的位址指標。  
  
## <a name="remarks"></a>備註  
 `ICLRDataTarget`物件藉由偵錯的應用程式的寫入器。 實作取決於所表示的目標項目類型。 目標項目可能是處理程序、 記憶體傾印、 遠端電腦，等等。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
