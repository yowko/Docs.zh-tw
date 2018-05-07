---
title: ICorDebugGuidToTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c156be3af49ac99f040360bda9f60f21a9ad66b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next 方法
取得指定的數目[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應輸入資訊的 Guid 的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]要擷取的 GUID 型別對應物件數目。  
  
 `values`  
 [out]陣列的指標，其中每個指向[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應物件[!INCLUDE[wrt](../../../../includes/wrt-md.md)]對應 ICorDebugType 物件的 GUID。  
  
 `pceltFetched`  
 [out]數目的指標[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)中實際傳回的物件`values`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugGuidToTypeEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
