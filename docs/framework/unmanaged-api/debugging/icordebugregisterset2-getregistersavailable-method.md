---
title: "ICorDebugRegisterSet2::GetRegistersAvailable 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f91b30b2ab50fc74049365d5c290bbaae1e20b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable 方法
取得位元組陣列提供的可用暫存器的點陣圖。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `numChunks`  
 [in] `availableRegChunks` 陣列的大小。  
  
 `availableRegChunks`  
 [out]位元組陣列，其中每個位元對應暫存器。 如果使用暫存器，則會設定暫存器的對應位元。  
  
## <a name="remarks"></a>備註  
 CorDebugRegister 列舉的值會指定不同的微處理器的暫存器。 每個值的上方的五個位元皆為的索引`availableRegChunks`的位元組陣列。 每個值的較低的三位元會識別索引位元組中的位元位置。 指定`CorDebugRegister`指定特定的暫存器，遮罩中的暫存位置的值決定，如下所示：  
  
1.  擷取存取正確的位元組中所需的索引`availableRegChunks`陣列：  
  
     `CorDebugRegister`值 >> 3  
  
2.  擷取其中位元 0 是最小顯著性位元的位元位置內的索引的位元組：  
  
     `CorDebugRegister`值 （& s) 7  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
