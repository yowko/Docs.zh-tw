---
title: "ICorDebugVariableHomeEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum::Next 方法
取得指定的數目[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)包含本機變數和引數的函式中的相關資訊的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in] 要擷取的物件數目。  
  
 `homes`  
 陣列的指標，其中每個指向[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)提供本機變數或函式的引數的相關資訊的物件。  
  
 `pceltFetched`  
 [out]物件中實際傳回的執行個體數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回下列值。  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|已成功完成命令。|  
|`S_FALSE`|擷取執行個體的實際數目，如中所反映`pceltFetched`，小於要求的執行個體數目。|  
  
## <a name="remarks"></a>備註  
 [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法會擷取最多`celt`物件列舉值的目前位置開始。 方法傳回時，`pceltFetched`包含實際的擷取的物件數目。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugVariableHomeEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
