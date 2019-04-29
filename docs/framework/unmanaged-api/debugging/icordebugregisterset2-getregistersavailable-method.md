---
title: ICorDebugRegisterSet2::GetRegistersAvailable 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1522d643a69c47eec03770a8f51756dd4250075a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782820"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable 方法
取得位元組陣列，提供可用的暫存器的點陣圖。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `numChunks`  
 [in] `availableRegChunks` 陣列的大小。  
  
 `availableRegChunks`  
 [out]位元組陣列，其中每個位元對應暫存器。 如果使用暫存器，則會設定註冊的對應位元。  
  
## <a name="remarks"></a>備註  
 CorDebugRegister 列舉之值的指定不同的微處理器的暫存器。 每個值的較高的五位元是索引`availableRegChunks`的位元組陣列。 每個值的較低的三位元識別索引位元組中的位元位置。 指定`CorDebugRegister`值，指定特定的暫存器，用來遮罩中的暫存位置的判斷如下：  
  
1. 擷取存取中的正確位元組所需的索引`availableRegChunks`陣列：  
  
     `CorDebugRegister` 值 >> 3  
  
2. 擷取元零所在的最小顯著性的位元的位元位置內的索引的位元組：  
  
     `CorDebugRegister` 值 & 7  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
